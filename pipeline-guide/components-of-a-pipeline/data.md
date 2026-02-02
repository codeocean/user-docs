---
description: >-
  This section explains how to use data in a Pipeline, including external Data
  Assets, and how to remove or replace data.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/pipeline-guide/components-of-a-pipeline/data
---

# Data

## Adding Data to a Pipeline

You can add data to your Pipeline by attaching a Data Asset from the **Manage** button next to the `/data` folder or uploading data.&#x20;

Once your data are in the File Tree system, you can drag and drop the folder into the Pipeline editor and connect it to a Capsule.

![](../../.gitbook/assets/adding_data_pipeline.gif)

Uploaded (local) data files must be placed inside a folder before they can be dropped into the Pipeline editor. Using local files will increase run time compared to internal Data Assets. It is best practice to use Data Assets instead of local files because using Data Assets allows the same Data Asset to be easily reused in multiple Pipelines and Capsules, and enhances reproducibility by ensuring an accurate Lineage Graph.

{% hint style="info" %}
The Pipeline will only use data that is dragged onto the Pipeline editor and connected to a Capsule.&#x20;
{% endhint %}

## Removing or Replacing Data from a Pipeline

To remove a Data Asset from the Pipeline editor you can hover over it and click the garbage can icon <img src="https://lh7-us.googleusercontent.com/z5n5e7ik4Qzn4UBWwWyzAh4XJSN54YSMK6ylFZGbnO71_OyJBFZn45qLJI6u4ebT5im94b3tfCjf3lZhURPqCvbvxmVtPWAKhEQQZmBQu0bs0TyW_B9lgr3p3yrZr7BQ_Nvya9vtNbtfm5CYP0M5BRM" alt="" data-size="line">.

![](../../.gitbook/assets/delete_data_pipeline.gif)

The replace feature can be used to substitute a Data Asset while maintaining all connections and mappings.&#x20;

{% hint style="info" %}
Data Assets must be attached to the Pipeline's `/data` folder to appear in the Replace Data menu.
{% endhint %}

<figure><img src="../../.gitbook/assets/replace_data_pipeline.gif" alt=""><figcaption></figcaption></figure>

## Using External or Combined Data Assets

External Data Assets and Combined Data Assets can be used in a Pipeline. To use Data Assets linked to an AWS S3 bucket, a [custom IAM role](pipeline-settings.md#aws-iam-role) must be selected in the Pipeline Settings menu, regardless of whether the S3 bucket is private or public. See[ Pipeline Settings](pipeline-settings.md#aws-iam-role) for more information.

{% hint style="info" %}
If you are working with external data created from a custom S3 endpoint that does not support Assumable Roles, these Data Assets cannot be used in Pipelines.&#x20;

Whether or not a custom S3 endpoint works with AWS Assumable Roles depends on the endpoint.&#x20;
{% endhint %}
