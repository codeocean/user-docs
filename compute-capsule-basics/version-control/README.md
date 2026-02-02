---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/compute-capsule-basics/version-control
---

# Version Control

Code Ocean integrates Git for version control , allowing seamless management of file versions within a Capsule. Each Capsule is a Git repository, enabling you to perform Git operations through the Capsule IDE or any command-line interface (CLI) in a Cloud Workstation.&#x20;

## File and Folder Status in Git

Each file and folder in the Capsule is accompanied by a small status icon that reflects its Git status:

* **Yellow icons:** Indicate files or folders with uncommitted changes.
* **Green icons:** Appear after selecting **Commit Changes**, signaling that changes have been committed to Git.

| Icon                                                                           | Is tracked by Git? | Is committed? |
| ------------------------------------------------------------------------------ | ------------------ | ------------- |
|  <img src="../../.gitbook/assets/image (138).png" alt="" data-size="original"> | Yes                | Yes           |
| ![](<../../.gitbook/assets/image (85).png>)                                    | Yes                | No            |
| ![](<../../.gitbook/assets/image (110).png>)                                   | No                 | No            |

## Additional options from Cloud Workstation

The Capsule IDE supports basic Git features such as committing and viewing differences (diffing). For more advanced Git operations such as revert, log, or managing remotes, you can use the CLI in a Cloud Workstation.

You can also amend the git commit comment in the terminal from a Cloud Workstation.

## .gitignore

The `.gitignore` file in the Capsule specifies files or folders to exclude from version control and Git will not keep track of changes in these files.

* The files and folder in `.gitignore` are indicated with a gray icon ![](<../../.gitbook/assets/image (110).png>)&#x20;
* Code Ocean automatically adds`/data/`to the `.gitignore` to follow best practices of excluding data files from version control.

![](<../../.gitbook/assets/image (247).png>)

## Duplicate a Capsule

When duplicating a Capsule, both the committed history and uncommitted changes are copied to the new Capsule.

To duplicate a Capsule:

1. From the top menu, click **Capsule** and select **Duplicate**.
2. You will be redirected to the duplicated Capsule.
3. Click **Show Prior History** to view the commit history from the parent Capsule.

## **S**witching Branches

You can switch between Git branches in your Capsule using the branch drop-down menu as shown below. By default, the primary branch is `master` unless otherwise defined in the remote Git repository.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-19 at 7.18.02 PM.png" alt="" width="331"><figcaption></figcaption></figure>

* Branch switching is disabled while there are uncommitted changes -- once you start editing the Capsule, the drop-down button for switching branches is disabled until all of the changes are committed.
* Using the CLI in a Cloud Workstation, you can also execute native Git commands to create, delete, or manage branches. These changes sync to the Capsule and appear in the branch list and other relevant locations.

{% hint style="info" %}
This feature is especially useful when the Capsule is linked to an external Git repository (e.g. GitHub, GitLab, etc.).
{% endhint %}
