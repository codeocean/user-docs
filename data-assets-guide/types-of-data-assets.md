---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/data-assets-guide/types-of-data-assets
---

# Types of Data Assets

## <img src="../.gitbook/assets/Screenshot 2025-06-19 at 10.00.22 AM.png" alt="" data-size="line"> Data

### <img src="../.gitbook/assets/Screenshot 2025-06-19 at 10.01.31 AM.png" alt="" data-size="line"> Internal Data&#x20;

An internal Data is a copy of the dataset on Code Ocean in the virtual private cloud deployment. This is achieved by [uploading data from a local machine](adding-a-new-dataset.md#upload-from-your-local-machine) or [importing data from a cloud provider](adding-a-new-dataset.md#import-from-a-cloud-provider), for example, AWS or Google Cloud. An immutable copy of the data will be saved on your deployment. Authorized users can download these from the Data Assets page and access or attach them in a Capsule or Pipeline. These assets are saved on your deployment's S3 and are cached to your deployment's EFS for quick access when they are actively being used.

### <img src="../.gitbook/assets/Screenshot 2025-06-19 at 10.01.35 AM.png" alt="" data-size="line"> External Data (A Remote Link)

Datasets can be[ added as a link to the remote bucket on AWS S3](adding-a-new-dataset.md#establish-an-external-link-to-aws-s3-bucket). To establish the link, AWS credentials must be provided during setup (see [Secret Management Guide](../compute-capsule-basics/secret-management-guide/) for details). The data will remain in its original location, and will only be linked to your Code Ocean deployment. Only users with authorization to access the original source will have access via Code Ocean and they will need to provide the appropriate credentials for using the External Data Asset in a Capsule or Pipeline. Since the data is not saved in Code Ocean, it cannot be directly downloaded.

{% hint style="info" %}
Workflows that use External Data Assets cannot be guaranteed to be reproducible.
{% endhint %}

## <img src="../.gitbook/assets/Screenshot 2025-06-19 at 10.00.26 AM.png" alt="" data-size="line"> Results

### <img src="../.gitbook/assets/Screenshot 2025-06-19 at 10.01.31 AM.png" alt="" data-size="line"> Internal Result&#x20;

A captured Internal Result is a Data Asset created from the [output of a Capsule or Pipeline computation](capturing-a-result/). It records the origin of this result, including the Capsule code version, type of run, input Data Assets, and Lineage Graph. These assets are saved on S3 and are cached on EFS for quick access when they are actively being used.

{% hint style="info" %}
The Lineage Graph and Provenance are automatically recorded for Result Data Assets.&#x20;
{% endhint %}

### <img src="../.gitbook/assets/Screenshot 2025-06-19 at 10.01.35 AM.png" alt="" data-size="line"> External Result

External Results can be created from Capsule or Pipeline results and are stored at a user-specified location in S3. External Results automatically generate a Lineage Graph and Provenance.

<figure><img src="../.gitbook/assets/New Data Asset.gif" alt="" width="375"><figcaption></figcaption></figure>

## <img src="../.gitbook/assets/Screenshot 2025-06-19 at 10.01.24 AM (1).png" alt="" data-size="line">Combined Data

Combined Data are Data Assets created from two or more External Data Assets that are already in your account. When used in Pipelines, Combined Data allow you to parallelize at the level of Data Asset, instead of the items within a single Data Asset. Combined Data store the metadata of the Data Assets that comprise it.

{% hint style="info" %}
To use External Data Assets and Combined Data Assets in a Pipeline, [Assumable Roles](../pipeline-guide/components-of-a-pipeline/pipeline-settings.md#aws-iam-role) must be configured. These can be configured in your deployment by a Code Ocean Administrator.
{% endhint %}
