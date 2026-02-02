---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/pipeline-guide/the-pipeline-ui/file-tree-system
---

# File Tree System

The Files tab on the toolbar on the left opens the Files panel. Core Files includes the `/metadata`, `/pipeline`, and `/data` folders. Results includes the `/results` folder, and additional files are organized under Other Files.‌

<figure><img src="../../.gitbook/assets/Screen Shot 2024-02-02 at 1.46.14 PM.png" alt=""><figcaption></figcaption></figure>

| Folder   | Purpose                                                                                                      | Contents                                                    |
| -------- | ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------- |
| Metadata | Store information about the Pipeline, like the pipeline name, research field, description, author, and tags. | metadata.yml                                                |
| Pipeline | Store the nextflow code depicted in the Pipeline editor that is run during a Reproducible Run.               | main.nf                                                     |
| Data     | Store data attached to the Pipeline.                                                                         | internal or external attached Data Assets, local data files |
| Results  | Store the results from any Capsule attached to the Results Bucket.                                           | Results from the most recent  run of the Pipeline           |

{% hint style="info" %}
Icons next to the files and folders in the File Tree System will be green if all changes are tracked by git, yellow if new changes are not tracked by git, and gray if they are ignored by git.&#x20;
{% endhint %}

{% hint style="info" %}
The shared memory (SHM) for standalone Capsules and Capsules (processes) in a Pipeline is 4GB.&#x20;
{% endhint %}

## Size Limitation

The limitation of the Pipeline workspace is 5GB. This includes contents of the `/metadata` and `/pipeline` folders, and local files in the `/data` folder.&#x20;
