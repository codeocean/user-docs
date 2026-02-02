---
description: >-
  This page is a set of instructions to utilize the Genome parameter of the
  rnaseq nf-core pipeline. It requires you to download the necessary resources.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/pipeline-guide/nf-core-pipelines/nf-core-rnaseq-tutorial/igenomes
---

# iGenomes

iGenomes are a collection of sequence and annotation files for commonly analyzed genomes. Each iGenome contains data for one species, downloaded from one source (UCSC, NCBI, or Ensembl), for one genomic build. They are available and easy to use, but not recommended because gene annotations are out of date and some iGenomes references (e.g., GRCh38) point to annotation files that use gene symbols as the primary identifier.

## Source External Data

nf-core requires a configuration file to use iGenomes resources. That file is `pipeline/conf/igenomes.config.`

<figure><img src="../../../.gitbook/assets/Screenshot 2024-02-23 at 13.27.29.png" alt=""><figcaption></figcaption></figure>

When you set the **Genome** parameter to any of the choices in the `igenomes.config`, the variables described in the json will be assumed. It is critical your S3 directory structure match this file and path structure because your **igenomes.base** will be the prefix of your S3 bucket the contents reside within. That is the text in {curly brackets}.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-03-20 at 16.10.37.png" alt=""><figcaption></figcaption></figure>

## Downloading iGenomes

You can use this [service](https://ewels.github.io/AWS-iGenomes/) to create a query to download the required files. For instance,&#x20;

```
aws s3 --no-sign-request --region eu-west-1 sync s3://ngi-igenomes/igenomes/Homo_sapiens/Ensembl/GRCh37/ ../results
```

This command can be run from a Capsule by Reproducible Run or Cloud Workstation. It will download the necessary resources required for the GRCh37 into your **Results** folder.

Next create an [External Data Asset](../../../data-assets-guide/capturing-a-result/#saving-data-assets-to-an-external-s3-bucket) from the **Results**.

{% hint style="info" %}
Using an External Data Asset allows you to leave the **iGenomes base** App Panel parameter and `igenomes.config` file as-is. Using an Internal Data Asset would require you to edit these.&#x20;

To use External Data Assets in a Pipeline, [Assumable Roles](../../components-of-a-pipeline/pipeline-settings.md#aws-iam-role) must be configured by a Code Ocean admin.
{% endhint %}

<figure><img src="../../../.gitbook/assets/Screenshot 2024-03-21 at 11.58.24.png" alt="" width="375"><figcaption></figcaption></figure>

The **path** structure must be identical to the [json](igenomes.md#sourcing-external-data) (picture above) for parameter - **GRCh37.**

<figure><img src="../../../.gitbook/assets/Screenshot 2024-03-21 at 12.00.59.png" alt=""><figcaption></figcaption></figure>

If your directory structure is as shown in the [iGenomes configuration](igenomes.md#source-external-data) file, iGenomes resources for your chosen genome will be downloaded into your bucket.
