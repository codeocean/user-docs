---
description: Steps for running code as you find it on Code Ocean locally.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/pipeline-guide/managing-pipelines/exporting-pipelines-to-your-local-machine
---

# Exporting Pipelines to your Local Machine

## Export...

Code Ocean allows editors and viewers to download an entire Pipeline. Click the **Pipeline** menu and select **Export**:

<figure><img src="../../.gitbook/assets/export pipeline.png" alt=""><figcaption></figcaption></figure>

This will download the `/pipeline` folder, `/metadata` folder, and instructions for running this code outside of Code Ocean. When you unzip this, you will see something like the following (this screenshot comes from a Mac):&#x20;

<figure><img src="../../.gitbook/assets/exported files.png" alt=""><figcaption></figcaption></figure>

* The `/metadata` folder has a file called `metadata.yml` with information about the Capsule.
* The `/pipeline` folder contains the Nextflow script in the `main.nf` file and Nextflow configurations in the `nextflow.config` file.  If a user has defined Secrets in the Environment Editor of any Capsule, these variables will be white-listed in the `nextflow.config` file and the `REPRODUCING.md` file will provide instructions for creating the appropriate Secrets locally. In addition, `nextflow.config` will include the Pipeline's App Panel parameters.

## Clone via Git...&#x20;

Alternatively, all Git tracked files can be exported as a Pipeline repository via **Pipeline** -> **Clone via Git**.

<figure><img src="../../.gitbook/assets/clone via git.png" alt=""><figcaption></figcaption></figure>

To access this Pipeline, the username and password will be the email used to log into your Code Ocean deployment and the personal access token generated on the box with the link to clone.&#x20;

<figure><img src="../../.gitbook/assets/clone via git2.png" alt="" width="446"><figcaption></figcaption></figure>

**This is the recommended practice if you are going to continue to make commits and changes to the Pipeline, so that changes can continue to be tracked.** The data will have to be transported separately.

## Running the Pipeline outside of Code Ocean

To reproduce your Pipeline outside of Code Ocean, the steps are the following:

### Prerequisites:

1. Ensure Nextflow is installed and can be used on your local machine.
2. Ensure docker is installed and can be used on your local machine.
3. Generate an API key in your Code Ocean User Account (More information can be found [here](../../code-ocean-api/authentication.md)).

### Logging into the docker registry&#x20;

In the exported/cloned Capsule directory on your local machine, run the following command:

```
docker login <EMAIL USED TO LOGIN TO CODE OCEAN> <REGISTRY>
```

The registry for `docker login` can be found on the FROM statement on the first line of your Capsule Dockerfile (for example, the registry from the below example is  `registry.codeocean.com`).

```
FROM registry.codeocean.com/codeocean/r-base:3.4.4-ubuntu18.04
```

The registry can also be found at the end of a `buildLog` of a successful Capsule environment build.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-27 at 10.48.45 AM.png" alt="" width="563"><figcaption></figcaption></figure>

After you execute the `docker login` command you will be prompted for a password - enter the API key previously generated.

{% hint style="info" %}
Required Data Assets must be downloaded separately, and can be saved into the `/data` folder.  If the Data Assets are External, they can be downloaded during run time. See the [Nextflow documentation](https://www.nextflow.io/docs/latest/aws.html) for how to connect to AWS.&#x20;
{% endhint %}

### Running the Pipeline

In your terminal, navigate to the `pipeline` folder within the folder where you've extracted the Pipeline and execute the following command, adjusting parameters as needed:

```shell
NXF_VER=22.10.8 DATA_PATH=$PWD/../data nextflow -log ../results/nextflow/nextflow.log run main.nf -resume
```

Edit the `nextflow.config` file found inside the same folder as needed:

* Enter your parameters (by process name) into the `params` section. For named parameters, the format is `"--name1=value --name2=value"`. For ordered parameters, the format is `"param1_value param2_value"`.
* Capsule secrets can be set in the `containerOptions` parameter in each of the `withName` sections within the `process` section.  You must replace the environment variable values with the actual secret values. Alternatively, if you have any of the required environment variables already set in your environment, you can add an `envWhitelist` parameter in the `docker` section and specify the relevant environment variable names there, and remove them from the relevant `containerOptions` parameters.

See [Nextflow configuration documentation](https://www.nextflow.io/docs/latest/config.html#configuration-file) for further details.

{% hint style="info" %}
When exporting a Pipeline as a zip file, the unzipped folder will contain a file `REPRODUCING.md` which contains the above mentioned instructions for how to reproduce the Pipeline's results locally, with notes on the necessary prerequisites and commands.&#x20;

Reproducing your results locally is likely to be less user-friendly than reproducing results on Code Ocean. Docker requires some familiarity with the command line.
{% endhint %}
