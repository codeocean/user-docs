---
description: Steps for running code as you find it on Code Ocean locally.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/compute-capsule-basics/managing-capsules/exporting-capsules-to-your-local-machine
---

# Exporting Capsules to your Local Machine

Code Ocean allows authors and readers to download an entire Capsule. Click the **Capsule** tab in the menu and select **Export**:

<figure><img src="https://downloads.intercomcdn.com/i/o/465530099/c87906aa6c598c37cd081516/ac679064-1c03-42c8-9c28-e673d4211d10" alt=""><figcaption></figcaption></figure>

This will prompt a download screen where you can download the environment template, metadata, code, and, optionally, the data. When you unzip this, you will see something like the following (this screenshot comes from a Mac):&#x20;

<figure><img src="https://downloads.intercomcdn.com/i/o/76433548/8190be05b84f3c71488e8882/Screen+Shot+2018-09-14+at+2.32.38+PM.png" alt="" width="375"><figcaption></figcaption></figure>

* `/code` contains your Capsule's code, and `/data` contains your Capsule's data if you chose to include it as part of the export.&#x20;
* `/metadata` contains a file called `metadata.yml`&#x20;
* The `/environment` folder contains, at a minimum, a file called [`Dockerfile`](../../setting-up-the-environment/starter-environment.md#dockerfiles-in-code-ocean) . If you've employed a [postInstall script](../../setting-up-the-environment/the-post-install-script.md), you will see a `postInstall` file as well.&#x20;
  *   `Dockerfile`  is the recipe for rebuilding your Capsule's computational environment locally. Each will begin with a line like:

      ```
      FROM registry.<acmecorp>.codeocean.com/codeocean/r-base:3.4.4-ubuntu18.04
      ```

      This tells the Dockerfile from where to pull the Docker image.\
      If the environment has been customized further, there will be more commands like:

      ```
      ARG DEBIAN_FRONTEND=noninteractiveRUN apt-get update \    && apt-get install -y --no-install-recommends \      "curl=7.47.0-1ubuntu2.2" \      "gcc=4:5.3.1-1ubuntu1" \      "libnlopt-dev=2.4.2+dfsg-2" \      "pandoc=1.16.0.2~dfsg-1" \    && rm -rf /var/lib/apt/lists/*
      ```

      &#x20;and so on.

{% hint style="warning" %}
The file permissions are lost when zipped, so when unzipping an exported Capsule, both the run and postInstall scripts are not executable anymore.&#x20;

If you'd like to preserve the file permissions, you must `chmod +x` both files before uploading to GitHub.
{% endhint %}

Alternatively, all Git tracked files can be exported as a Capsule repository via Capsule -> Clone via Git.

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-27 at 10.34.36 AM.png" alt="" width="375"><figcaption></figcaption></figure>

To access this Capsule, the username and password will be the email used to log into your Code Ocean deployment and the personal access token generated on the box with the link to clone.

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-27 at 10.35.07 AM.png" alt="" width="563"><figcaption></figcaption></figure>

**(This is the recommended practice if you are going to continue to make commits and changes to the Capsule, so that changes can continue to be tracked).** The data will have to be transported separately.

To reproduce your Capsule outside of Code Ocean, the steps are as follows:<br>

### Prerequisites:

Complete the following:

1. Ensure docker can be used on your local machine and is installed
2. Generate an API key in your Code Ocean User Account (More information can be found [here](../../code-ocean-api/authentication.md))

### Logging into the docker registry&#x20;

In the exported/cloned Capsule directory on your local machine, run the following command:

```
docker login <EMAIL USED TO LOGIN TO CODE OCEAN> <REGISTRY>
```

The registry for `docker login` can be found on the FROM statement on the first line of your Capsule Dockerfile (for example, the registry from the below example is  `registry.codeocean.com`)

```
FROM registry.codeocean.com/codeocean/r-base:3.4.4-ubuntu18.04
```

The registry can also be found at the end of a `buildLog` of a successful Capsule environment build&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-27 at 10.48.45 AM.png" alt="" width="563"><figcaption></figcaption></figure>

After you execute the `docker login` command you will be prompted for a password - enter the API key previously generated

### Locating/Copying capsule identifier&#x20;

In the Capsule you would like to run on Code Ocean, find the metadata tag in the metadata section:

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-27 at 10.57.00 AM.png" alt=""><figcaption></figcaption></figure>

&#x20;Click the clipboard icon to copy it.

### Running your capsule&#x20;

On your local machine, navigate to the exported capsule directory and run the following command

```
docker run --platform linux/amd64 --rm \
  --workdir /code \
  --volume "$PWD/code":/code \
  --volume "$PWD/data":/data \
  --volume "$PWD/results":/results \
  <REGISTRY>/capsule/<METADATA TAG> \
  bash run
```

In your exported Capsule directory, the results will appear in the `./results` directory

{% hint style="info" %}
When exporting a capsule as a zip file, the unzipped folder will contain a file `REPRODUCING.md` which contains the above mentioned instructions for how to reproduce the Capsule's results locally, with notes on the necessary prerequisites and commands.&#x20;

Reproducing your results locally is likely to be less user-friendly than reproducing results on Code Ocean. Docker requires some familiarity with the command line.
{% endhint %}
