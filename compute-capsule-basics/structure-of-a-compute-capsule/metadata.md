---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/compute-capsule-basics/structure-of-a-compute-capsule/metadata
---

# Metadata

The `/metadata` folder contains essential details about the research project, including the title, research field, description, project authors, and tags. Metadata is critical for releasing a Capsule and enables quicker, more accurate search results via keyword searches. All metadata is indexed and searchable on the **Code Ocean Internal Release** page.

In a Capsule, the metadata folder has the path of `/metadata` . While this folder is not visible during a Reproducible Run, it is accessible in any Cloud Workstation.

## Metadata Editor

1. Click the `/metadata` folder to open the **Metadata Editor**.&#x20;
2. Enter the information in the text fields provided:

* **Name:**&#x20;
  * Enter the Capsule's title.&#x20;
  * Use a name that's easy to search and understand for both yourself and collaborators.&#x20;
  * Follow internal naming conventions if applicable.
* **Research field**:&#x20;
  * Specify the relevant research domain or field.
* **Description**:&#x20;
  * Use markdown supported text to provide a clear description of the Capsule and ensure its purpose is easily understood by you and your collaborators in the future.
* **Authors**:&#x20;
  * List the names of all individuals who contributed to creating the Capsule.
* **Tags**:&#x20;
  * Add relevant keywords to improve searchability and discoverability.

<figure><img src="../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

## The metadata.yml file

Most of the information you enter in the **Metadata Editor** is stored in the `metadata.yml` file within the `/metadata` folder. It can be opened and edited directly as a plain text file.

<figure><img src="../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

## The Capsule ID

The Capsule ID is listed on the metadata page and is required for certain API operations, such as the [Get Capsule API](../../code-ocean-api/capsule.md#get-capsule). Click the clipboard icon next to the Capsule ID to copy it.

<figure><img src="../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

## Uploading a Cover Image

Adding a representative cover image enhances intelligibility and discoverability on Code Ocean’s **Internal Releases Dashboard**.\
\
To update your Capsule's cover image:

1. Navigate to your Capsule's `/metadata` folder.&#x20;
2. Hover over the current image.
3. Click **Upload Image**.&#x20;

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>
