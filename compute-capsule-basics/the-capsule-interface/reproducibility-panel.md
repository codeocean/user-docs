---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/compute-capsule-basics/the-capsule-interface/reproducibility-panel
---

# Reproducibility Panel

Within the Reproducibility Panel, the Timeline provides a managed history of the Capsule, including its creation, runs, and releases. The Timeline is also the hub of version management in the Capsule as this is where Git commit prompts will appear and you can view information regarding specific commits.

## The 1-Click Commit

Every edit from the IDE is automatically saved and staged by default to the Capsule's corresponding Git repository. The Commit Changes button appears in the Timeline after each new edit.&#x20;

1\. In **Describe what changed**, explain your actions, or leave the default commit message.&#x20;

2\. Click **Commit Changes** to commit your changes to the Git history stored in the Capsule and push the commits to the Capsule's Git repository.

<figure><img src="../../.gitbook/assets/image (47).png" alt="" width="306"><figcaption></figcaption></figure>

## Viewing Changes

The Timeline shows the history of the Reproducible Run (marked with a blue circle <img src="../../.gitbook/assets/Snip20201015_74.png" alt="" data-size="line">) and the committed changes to this Capsule (marked with a green circle <img src="../../.gitbook/assets/Snip20201015_75.png" alt="" data-size="line">).

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-19 at 1.46.07 PM.png" alt="" width="295"><figcaption></figcaption></figure>

### View Committed Changes

Click **committed** to display the status update of committed changes. In the image below, you can see the files that were added.

<figure><img src="../../.gitbook/assets/Screen Recording 2024-01-10 at 12.08.58.83 PM.gif" alt=""><figcaption></figcaption></figure>

Click **Back to Timeline** to return to the IDE.

### View Uncommitted Changes

1. Click on the `run` file in the left section.
2. Copy and paste `# view the power of git` to line 10.&#x20;



<figure><img src="../../.gitbook/assets/image (530).png" alt=""><figcaption></figcaption></figure>

In your Timeline, you’ll see one uncommitted change, which is the piece of code you added. Click **1 uncommitted change** to see the details.

<figure><img src="../../.gitbook/assets/5 uncommited details (1).png" alt=""><figcaption></figcaption></figure>

Click the down-arrow and from the menu select **View Changes**. A Git compare view will open up in the middle workspace. Here you can view the changes you made.

<figure><img src="../../.gitbook/assets/Screen Recording 2024-01-10 at 12.11.48.93 PM.gif" alt=""><figcaption></figcaption></figure>

## Timeline Events Filter and Search

Events in the Timeline can be filtered to show All events, Commits, All Runs, My Runs, or Releases. The search bar can be used to search computation names of Reproducible Runs, commit messages, and release versions to further select what is visible in the Timeline.

<figure><img src="https://lh7-us.googleusercontent.com/WG4AHFQZAtMyFY0-rsr19iQghPkcNV16GnVjVGcm1bixAKl3zIFJyl5ra4zEIKHWofB0dByJO3TOGYqX77kN_ITfhFvJxG-2jli8hMJfq5KrHG5sfbEF958kmYSYukYJ2Fvsk9u30H-RTmFnDVX6QtE" alt="" width="375"><figcaption></figcaption></figure>

## Reproducible Runs and Cloud Workstations

At the top of the Reproducibility Panel are code execution options for your Capsule to work with your specific capsule files, environment and compute resources.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-28 at 11.24.29 AM.png" alt="" width="300"><figcaption></figcaption></figure>

With your capsule contents and configuratio, you can execute a run script beginning to end via a Reproducible Run, or you can work in a popular programming IDE for more in depth development with a Cloud Workstation. For more detailed information on the two functionalities refer to the following pages:

* [Reproducible Runs](../reproducible-runs.md)
* [Cloud Workstations](../../cloud-workstation/)
