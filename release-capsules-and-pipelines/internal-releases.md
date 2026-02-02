---
description: >-
  The Internal Releases dashboard displays release Capsules and Pipelines that
  have been shared with the entire organization.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/release-capsules-and-pipelines/internal-releases
---

# Internal Releases

## Creating an Internal Release

A Capsule or Pipeline will appear on the Internal Releases Dashboard if it is a release and accessible to everyone in the organization. The release Capsule or Pipeline will inherit the sharing permissions of the original Capsule or Pipeline, but can be changed independently after it is released. If the original Capsule was not shared with everyone, the following steps show how the release Capsule or Pipeline can be shared to make it available on the Internal Releases Dashboard:&#x20;

1.  From the release Capsule, click **Share** to set the permissions for the Capsule. <br>

    <figure><img src="../.gitbook/assets/share_release_V212.png" alt=""><figcaption></figcaption></figure>
2. Change the General Access permissions so Everyone in this organization can View.

<figure><img src="../.gitbook/assets/Screen Shot 2024-02-12 at 4.35.11 PM.png" alt=""><figcaption></figcaption></figure>

3. Click **Save**.

## Browsing Internal Releases

Browse the Internal Releases dashboard by clicking the Release icon on the left side bar from anywhere in Code Ocean.

<figure><img src="../.gitbook/assets/Screen Shot 2024-02-12 at 9.04.37 PM.png" alt=""><figcaption></figcaption></figure>

A Capsule or Pipeline's metadata can be previewed by clicking anywhere on its card, or it can be opened directly by clicking the **Open Capsule** or **Open Pipeline** link. A Capsule or Pipeline on the Internal Releases Dashboard will always open on the latest version.&#x20;

{% hint style="info" %}
The Internal Releases dashboard can be filtered by No-Code Apps to display any Capsules that use RShiny, Streamlit, Ubuntu, or IGV, and Capsules released as App Panel accessible only.&#x20;
{% endhint %}

{% hint style="warning" %}
Admins have the ability to delete a release Capsule. Refer to the Admin Guide for the instructions on how to do so.
{% endhint %}
