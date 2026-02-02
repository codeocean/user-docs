---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/data-assets-guide/capturing-a-result
---

# Capturing a Result

You can capture a result as a Data Asset from the Code Ocean IDE or a Cloud Workstation. This Data Asset can be saved internally to your deployment or to an external S3 location.&#x20;

## Capture Results From the IDE <a href="#from-the-code-ocean-ide" id="from-the-code-ocean-ide"></a>

Before capturing any results, verify that you:

1. Save the results under the`/results`folder and that the results are visible in the Timeline.
2. Commit all the changes in the Capsule (click **Commit Changes** if not done yet).

Capture results by following these steps:

1. In your Capsule's Timeline, go to the result you want to capture and click the drop-down menu arrow.
2.  Select **Create New Data Asset**.\
    &#x20;

    <figure><img src="../../.gitbook/assets/image (449).png" alt=""><figcaption></figcaption></figure>
3. Enter the following information:&#x20;
   * **Data Asset Name** (required)—Use a meaningful name so that others can find the dataset easily.&#x20;
   * **Folder Name** (required)—The folder name inside a Capsule. Use a name that’s similar to the dataset name. Spaces and some special characters are not allowed here.
   * **Description** (optional)—Add markdown supported text to make the Data Asset easy to find and understand.
   * **Tags** (required)—Tags are another way to help people find your dataset.
   * **Custom Metadata** — These are administrator-defined fields for which you can provide values.
4. Click **Create Data Asset**.

After you’ve captured the results, you’ll get a link to view them on the Data Assets page. There, you can validate that you’ve captured the correct results, download them, and share them.

### Capture Result from Folder

You can create a Data Asset from a specific folder of a result by right-clicking on the folder and selecting **Create New Data Asset** from the folder-level dropdown in the Capsule/Pipeline Timeline.

<figure><img src="../../.gitbook/assets/image (493).png" alt=""><figcaption></figcaption></figure>

## Capture from a Cloud Workstation

Capture Data Assets from the Cloud Workstation by following these steps:

1. Click on **Capture Data Asset** from the title bar in the Cloud Workstation. The Capture Data Asset pane appears.
2. Enter the following information:&#x20;
   * **Folder** (required)—Choose the folder you want to capture. Note: to capture the `/results` folder, make sure to generate results in `/root/capsule/results/`.
   * **Metadata**
     * **Title** (required)—Enter a meaningful name that helps users identify the Data Asset.
     * **Description** (optional)— Provide enough information so that, in the future, you and others can understand what you captured and why.
     * **Tags** (required)—Enter tags that will make it easy for you and other users to find your Data Asset. This is especially important when you capture multiple results from the same Capsule or run script. Code Ocean remembers tags that have already been used in the organization.
   * **Provenance -** check Provenance to save the commit ID and originating script.&#x20;
     * **Originating Script** (required)— Validate the run script you used to produce the results. This allows you to distinguish between runs of the same Capsule.
     * Commit and push any change from `/root/capsule/`.&#x20;
3. Click **Capture Data Asset**.

After you’ve captured the Data Asset, you’ll get a link to view them on the **My Data Dashboard**. There, you can validate that you’ve captured the correct Data Asset, download them, and share them.

{% hint style="info" %}
By default, a new Data Asset is private (i.e. only the owner can see it).  To learn more about sharing a Data Asset with others, go to [Sharing Data Assets](../viewing-and-editing-data-assets/#share-data-assets).&#x20;
{% endhint %}

![](<../../.gitbook/assets/Screen Recording 2022-03-14 at 02.56.12 PM.gif>)

## Saving Data Assets to an External S3 bucket

In both the Capsule IDE and Cloud Workstations, result Data Assets can be saved to an External S3 Bucket or custom S3 endpoint (if admin configured). This requires setting [secrets](../../compute-capsule-basics/secret-management-guide/attaching-a-secret-to-a-capsule.md).&#x20;

Enter the following information:

* **Bucket Name** (required)— The name of the bucket.
* **Path** (required)— A specific folder or file in the bucket.
* **Data Asset Name** (required)—Use a meaningful name so that others can find the dataset easily.&#x20;
* **Folder Name** (required)—The folder name inside a capsule. Use a name that’s similar to the dataset name. Spaces and some special characters are not allowed here.
* **Description** (optional)—Add markdown supported text to make the Data Asset easy to find and understand.
* **Tags** (required)—Tags are another way to help people find your dataset.
* **Custom Metadata** — These are administrator-defined fields for which you can provide values.

<figure><img src="../../.gitbook/assets/Screen Shot 2024-03-05 at 2.50.50 PM.png" alt="" width="374"><figcaption></figcaption></figure>

