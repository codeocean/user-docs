---
description: Create a new Capsule by copying an existing git repository with a URL.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/compute-capsule-basics/version-control/importing-a-capsule-from-a-git-provider
---

# Importing a Capsule from a Git Provider

Code Ocean allows you to create Capsules by importing existing Git repositories. There are two primary methods: **Copy from Git** and **Clone from Git**. If you are importing from a private repo, you will need to add your Git provider credentials to your Account.&#x20;

## Copy from Git

You can create a Capsule or Pipeline by copying the contents of a Git repository. This method imports the files but does not maintain a link to the original repository.

1. Click + on the Sidebar.&#x20;
2. Click **Copy from Git.**
3. Enter the URL of the Git repository

<figure><img src="../../.gitbook/assets/copy public git.gif" alt=""><figcaption></figcaption></figure>

### How files are organized

* Files in the Git repository are placed into the corresponding folders in the Capsule if the names match the default folder structure (e.g., `/code`, `/data`).
* Any additional files or folders are imported into the **Other Files** section.

### Important Notes

* The Starter Environment must be specified before the Capsule can be run.&#x20;
* There is **no link** between the Capsule and the original Git repository. Changes in one will not be reflected in the other.

## Clone from Git

In Code Ocean, a Capsule or Pipeline can be created by cloning an existing git repository in your organization's account. Unlike copying from Git, this method maintains a connection between the Capsule and the repository. For more information about connecting your organization's Git account to Code Ocean, see the [Git Provider Integration Guide](../../git-provider-integration-guide/github-integration-user-guide.md).&#x20;
