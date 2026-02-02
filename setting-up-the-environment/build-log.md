---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/setting-up-the-environment/build-log
---

# Build Log

The Build Log is automatically generated whenever the system builds the environment, regardless of whether the build succeeds or fails. It is particularly useful for troubleshooting environment build errors and issues. Once a run is complete, the Build Log appears in the `/results` folder as the `buildLog` file. If the run is conducted in a Cloud Workstation, the Build Log is accessible as a link in the Timeline.

<figure><img src="../.gitbook/assets/image (176).png" alt=""><figcaption></figcaption></figure>

The Build Log provides a sequential record of all Docker commands and their outputs during the environment build process. Below is a screenshot showing steps from an example environment to demonstrate how the Build Log documents the build process.

For instance, Step 1 always involves pulling the Base Image using the Docker `FROM` command. As shown in the screenshot, the Build Log displays the Docker command and the results of its execution.

<figure><img src="../.gitbook/assets/image (333).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
If the Capsule's environment has not changed since its last build and the Capsule has been used recently, the environment will not be rebuilt, and no Build Log will be generated.
{% endhint %}
