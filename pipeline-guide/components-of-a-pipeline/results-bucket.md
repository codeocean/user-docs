---
description: This section explains how to save and view the output of a Pipeline.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/pipeline-guide/components-of-a-pipeline/results-bucket
---

# Results Bucket

Only files written to the Results Bucket will be saved after a Reproducible Run.

## Writing files to the Results Bucket

After a Reproducible Run, only outputs from Capsules connected to the Results Bucket will be saved in Code Ocean. However, intermediate results will be saved to an S3 bucket. These files are automatically deleted after 30 to avoid occupying unnecessary storage.

The Results Bucket will automatically appear once you add the first Capsule to the Pipeline building area. To save outputs to the Results Bucket, you must connect a Capsule to the Results Bucket.

In this example, results from both the FastQC and the MultiQC Capsules will be saved to the Results Bucket.

<div align="center"><img src="../../.gitbook/assets/GIF Recording 2024-02-01 at 2.10.35 PM.gif" alt=""></div>

## Viewing Results after a Reproducible Run&#x20;

Results from the most recent Reproducible Run can be accessed from the `/results` folder in the File Tree and results from all Reproducible Runs can be accessed from the Pipeline Timeline.&#x20;

A Data Asset can be created from results by clicking “Create New Result” in the drop down menu next to the Run Name in the Timeline or the `/results` folder. For more information refer to[ Capturing a Result](../../data-assets-guide/capturing-a-result/).

<figure><img src="https://lh7-us.googleusercontent.com/_PGgz5rx28H9m2n3EjvQM11IdWNjsJrYcOLAFuqMeuRgcjQC2jCykCUH_bqvh5119QAKcto_R-fN9qnS6Ia3cVsw31ctu_A2sxUTUhGeZbml-PuJCFsDdMkLTzb5crCXFErcizsH6ymtCk1KhvhH8gE" alt="" width="375"><figcaption></figcaption></figure>
