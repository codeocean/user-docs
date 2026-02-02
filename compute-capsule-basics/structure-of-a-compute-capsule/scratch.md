---
description: Working with Intermediate Data in Code Ocean
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/compute-capsule-basics/structure-of-a-compute-capsule/scratch
---

# Scratch

The `/scratch` folder is directory that provides virtually unlimited storage, allowing large intermediate data to be easily utilized within a Capsule. Its behavior differs between **Cloud Workstation** sessions and **Reproducible Runs**.

## Cloud Workstation Scratch&#x20;

For Cloud Workstation (CW) sessions, the `/scratch` folder is a mounted EFS volume whose contents will persist throughout the lifetime of the Capsule. Files written to scratch during a CW session will be visible in the capsule IDE after the session is Shut Down and will be available in all subsequent sessions unless deleted by the user. These files will not be available during a Reproducible Run.

The `/scratch` folder is a convenient location to store large data before [creating a Data Asset](../../data-assets-guide/capturing-a-result/) from either the Capsule IDE or during a CW session.

{% hint style="info" %}
It is best practice to delete files from scratch that are no longer needed to avoid taking up unnecessary storage. Should the Capsule be deleted, the `/scratch` folder will be deleted as well.
{% endhint %}

## Reproducible Run Scratch

For Reproducible Runs, the `/scratch` folder functions as a temporary folder that is empty at the start of the run and will be emptied before the end of the run. The Capsule workspace (i.e. the core files excluding Data Assets) is limited to 5GB and therefore a Reproducible Run will fail if this limit is exceeded by creating new files during the run. The `/scratch` folder can be used during a run to safely create files or work with intermediate data of any size. Since the folder is emptied before the end of each run, any results must be moved to the results folder.

{% hint style="warning" %}
The Reproducible Run `/scratch` is not the same folder as Cloud Workstation `/scratch`. The Reproducible Run scratch is emptied before the end of each run, the content will not be visible in the Capsule IDE.
{% endhint %}
