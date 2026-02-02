---
description: >-
  Pipelines allow users to separate steps of a workflow into reusable pieces,
  automate the start of subsequent steps, specify resources individually, and
  parallelize workflows by connecting Capsules.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/onboarding/quick-start-guides/create-a-pipeline-in-5-minutes
---

# Create a Pipeline in 5 minutes

## Create a new Pipeline

Click on the plus sign in the top right corner to create a new research product.  Users can create a new Pipeline, copy from a public git repo, or clone from a private git repo.  In this case we will **Create New**.&#x20;

![](<../../.gitbook/assets/new pipeline.png>)

{% hint style="info" %}
Cloning from your organization's private Git account enables the use of Code Ocean's Git Sync feature which ensures your Code Ocean Pipeline and the associated Git repository stay in sync.
{% endhint %}

There are 3 main components of a Code Ocean Pipeline User Interface: File Navigation/ App Builder, Editor, and Reproducibility Panel.  Navigate to the metadata editor by clicking metadata in the File Tree to rename the Pipeline, edit the description, and add authors and tags.&#x20;

<figure><img src="https://lh7-us.googleusercontent.com/jIuFkviR2uGFf4jv6BlQgOQnyJb8dVUqWHSKCpMCf1qgHGxbQUWEazUstKah7ter1_A_weD430XUOslKWvsixoxbnq8DTcR7g5Mv4uMA7VAdlGjUQtH18XtZWiPwmiVKMix4RNzrJZ7Yf1o4-XzQm9s" alt=""><figcaption></figcaption></figure>

## Add Capsules to the Pipeline

1. From the pipeline tab, you will see the Add Capsules menu.  In the Add Capsules menu, find the capsules you want to add by first using the filter for My Capsules or Code Ocean Apps.  Code Ocean Apps are pre-built capsules that are tested to work in Pipelines.  Users can filter and sort My Capsules and Code Ocean Apps Capsules, and use free text search to find their Capsule. &#x20;

<figure><img src="https://lh7-us.googleusercontent.com/QarWHJ8VccP4bxKZMnM6nLl9RQcQzpP0HxEAHGmxYXCQlhz4YtHvN4YpPgudJUpiOqFxcd-fNPTxZIVPQylEwLhc8IIFedxFhMyyb0XNJ_jBMkeFF5GIU3eK2_RkZfC1ddQnNY-mU6AlK804ZL1HcR8" alt=""><figcaption></figcaption></figure>

2. Each capsule has its own card.  Press the 3 dots to drag the card onto the Pipeline Editor.  For release Capsules, a pop up will prompt you to select which version of the Capsule to use.

<figure><img src="../../.gitbook/assets/GIF Recording 2024-02-01 at 10.55.40 AM.gif" alt=""><figcaption></figcaption></figure>

## Form Capsule Connections

1. To pass files (data or results) from one Capsule to another, a Capsule connection must be created.  Click + at the bottom of the Capsule and drag it to another Capsule to pass data from the output of one Capsule to the input of another.

![](<../../.gitbook/assets/Screen Shot 2024-02-01 at 11.05.22 AM.png>)

2. To ensure that the Capsule's results are saved after each run, connect the Capsule to the Results Bucket. Click + at the bottom of the Capsule and drag it to the Results Bucket.

![](<../../.gitbook/assets/pipeline 5 min.png>)

## Attach the Data Asset

To attach a Data Asset to the pipeline's **data** folder:

1. Click **Manage Assets** next to the **data** folder of the file tree system
2. Find the desired Data Asset, and click the plus sign to add it to the Pipeline Builder. &#x20;
3. To use the data asset in the Pipeline, drag and drop the Data Asset from the data folder to the Pipeline Builder canvas.

<figure><img src="https://lh7-us.googleusercontent.com/2XTIz7Ax-yPogznZLzgHGEUNANPK_Pkc7L-rmJ_mUFoBYiDqn-oJOkfgKGr-D0YEkuodhm1joSYD8sAcmS-H8DPhrPthUgt00XvUlwlrN0DWfGwmuiIgze2zNsteXFPWUcgaNx0wMbBln-4dhNtEHq8" alt="" width="375"><figcaption></figcaption></figure>

4. Create a connection from the data asset to the capsule by dragging the plus sign to the capsule. Data assets can be connected to multiple capsules.

<figure><img src="https://lh7-us.googleusercontent.com/5NCNg1letHnbRtaJHUSN5ZccSqD9HgjTeUYtgugmTZB_tkse-5s_KThidheB3Na6ZGPxkoJKUXzm_vB01YorYyoPPwoDsZNaqVyvj5px1qkZ5MLzzP8EcFTlKhbBGRd0hPldITnxmniayLwwpey2CyQ" alt="" width="375"><figcaption></figcaption></figure>

## Configure the Connections

Options can be specified for which files to pass between Data Asset and Capsules or Capsule to Capsule.

1. Click on the gear in the middle of the data to Capsule connection.
2. In the pop-up menu, specify which folders or files to pass from the source to the destination.  The destination folder can be renamed. &#x20;
3. Select a connection type: default, collect, or flatten.  See [Connection Types](../../pipeline-guide/components-of-a-pipeline/map-paths.md#connection-type-definitions) for more details.&#x20;

<figure><img src="https://lh7-us.googleusercontent.com/sk-z8Gn-97hNdd0ahB_QRn4TGujUOyY4-bngjLB_1tl67fUee3iEsm1NLTJwDVRZbuE5jaVuF8MtilHxstryXYhjvVSKzZgWO5C5UFJhQdqDmsukjgahaCCk3hPdcEUs-vgm1yNa9YVxVnWWxFmE6qY" alt=""><figcaption></figcaption></figure>

## Run the Pipeline

1. To run the Pipeline click **Reproducible Run** at the top of the Timeline.&#x20;
2. Once the run is complete, the contents of the Results Bucket can be viewed in the Timeline&#x20;

## View the Pipeline

The bottom left of the Pipeline Editor has five options for viewing the Pipeline:

* Zoom in - magnifies the Pipeline
* Zoom out - minimizes the Pipeline
* Fit view - shows the Pipeline in its entirety
* Lock - disables moving Capsules
* Eye toggle - shows the:
  * Connection types
  * CPUs
  * Memory
  * Data Type: Internal, External and Result
  * Capsule Type: Release, Code Ocean Apps

<figure><img src="https://lh7-us.googleusercontent.com/SgV4ayrXUElcjZVfIj6NEM0xgukAVNeRrGQPerrPDseyR9OieMImpXwHxwGymFODjp3wHCeKU15Qq4joXBTdMwFE_OeHvivaJMkOc4flE9qaynHgiWq_-iKVHkkVx-a0JMJBbrqDccR0NArRsNH_Zxs" alt=""><figcaption></figcaption></figure>
