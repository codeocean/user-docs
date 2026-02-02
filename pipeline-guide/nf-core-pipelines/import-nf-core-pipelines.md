---
description: A general introduction to importing from nf-core.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/pipeline-guide/nf-core-pipelines/import-nf-core-pipelines
---

# Import nf-core pipelines

## Import an nf-core pipeline&#x20;

1. From the Sidebar, create a new Pipeline by **Import from nf-core**
2. Select the pipeline name and version
3. Click on **Import**. &#x20;

<figure><img src="../../.gitbook/assets/import nf-core.gif" alt=""><figcaption></figcaption></figure>

## Successful Import

<figure><img src="../../.gitbook/assets/nf-core (1).png" alt=""><figcaption></figcaption></figure>

## Attaching Data and Setting Parameters

Input data will be required for nf-core pipelines. Data Assets of any type can be attached to nf-core pipelines.&#x20;

* Read the `README.md` file in the `/pipeline` folder to understand the required input files and parameters.
  * The "Usage" section of the Readme will have links to more detailed usage documentation and parameter documentation.
* The Pipelines parameters are generally located in the `nextflow.config` file. These can be manually changed here or via the Pipeline's automatically generated App Panel.

{% hint style="info" %}
To use External Data Assets in a pipeline, [Assumable Roles](../components-of-a-pipeline/pipeline-settings.md#aws-iam-role) must be configured. If this isn't configured in your deployment or you're unsure if it is, contact your Code Ocean admin.
{% endhint %}

## Running the Pipeline

The nf-core Pipeline can be run like any other Pipeline in Code Ocean, by clicking Reproducible Run.

## Exception Handling&#x20;

If the Pipeline has failed, we recommend you set the following in the [**Pipeline Settings**](../components-of-a-pipeline/pipeline-settings.md)**:**

* Run using **On Demand** Instances is recommended. **Spot** resources may drop out, requiring Retry set to Max Attempts and pressing Reproducible Run if you repeatedly lose machines due to availability.  &#x20;
* Run with Cache from the Previous Run to avoid rerunning the part of the Pipeline that completed successfully.
* Set the **Error Strategy** to **Retry** with **Number of Retries** to **10.** This will try to resolve internal conflicts due to endpoints and/or service interruptions before stopping.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-26 at 11.45.57.png" alt=""><figcaption></figcaption></figure>
