---
description: >-
  Although Capsules generally function the same when run in a Pipeline, there
  are a few important differences which are outlined below.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/pipeline-guide/capsule-vs-pipeline-differences
---

# Capsule vs Pipeline Differences

1. [Symbolic Links](capsule-vs-pipeline-differences.md#symbolic-links)
2. [AWS Secrets](capsule-vs-pipeline-differences.md#aws-secrets)
3. [The /root/capsule/data Directory Does Not Exist](capsule-vs-pipeline-differences.md#the-root-capsule-data-directory-does-not-exist)
4. [Data Copying for External Data](capsule-vs-pipeline-differences.md#data-copying-for-external-data)

## Symbolic Links

When running a Capsule, Data Assets are mounted directly into the Capsule’s data folder. Whereas in a Pipeline, Internal Data Assets are mounted to a /tmp directory and made available in the Capsule’s data folder via a symbolic link. See the following line from a Pipeline’s `main.nf`:

`ln -s "/tmp/data/reads/$path1" "capsule/data/$path1"`&#x20;

This means that certain commands that work in a Capsule may not work in a Pipeline if they don’t follow symbolic links. For example, the following code lists the full path to every file in the data folder. It returns the expected output in a Capsule but returns nothing when running the Capsule in a Pipeline.

```
for file in $(find ../data -name "*"); do
   echo $file 
done
```

In this case the `-L` flag must be used which indicates the find command should follow symlinks.

```
for file in $(find -L ../data -name "*"); do
   echo $file 
done
```

## AWS Secrets

When accessing AWS resources in a Capsule, you can attach AWS Cloud Credential secrets. In a Pipeline, AWS secrets attached to the Capsule will be ignored and instead you must select an IAM role in the [Pipeline Settings](components-of-a-pipeline/pipeline-settings.md#aws-iam-role). This is because only one set of AWS credentials can be used in a Pipeline, and they must have access to the Code Ocean managed AWS Batch resources as well as the AWS resources the Capsule is attempting to access.

Selecting an AWS IAM role is also mandatory when using External Data in a Pipeline.

## The /root/capsule/data Directory Does Not Exist

In a Capsule there are a variety of ways to reference the data folder, i.e. `/data`, `../data` from the code folder, or `/root/capsule/data`. In a Pipeline `/root` does not exist, so `/data` or `../data` must be used.

## Data Copying for External Data

In a Capsule, an External Data Asset is mounted to the data folder using [s3fs](https://github.com/s3fs-fuse/s3fs-fuse). This allows you to interact with the underlying S3 bucket as if it were a local filesystem, without any data duplication. Nextflow does not yet support the use of s3fs, so in a Pipeline, the contents of the External Data Asset are copied at runtime to the AWS Batch machine(s) running the computation.

The Map Paths menu can be used to improve Pipeline performance by ensuring only necessary data is copied. In this example, only the 494.54 MB `image_volumes` folder will be copied to the Capsule instance instead of the entire 450.21 GB `abc_atlas` Data Asset.

<figure><img src="../.gitbook/assets/data copying.png" alt=""><figcaption></figcaption></figure>

In contrast, Internal Data Assets are optimized to provide improved performance. The underlying EFS storage is mounted directly to the AWS Batch machine(s) running the computation, allowing Internal Data Assets to be used without any data copying. As such, it’s a best practice to use Internal Data Assets for data that remains unchanged across Pipeline runs.
