---
description: >-
  A release Pipeline is an end-to-end reproducible version of your Pipeline that
  is saved in its current state and separate from the original.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/release-capsules-and-pipelines/creating-release-pipelines
---

# Creating Release Pipelines

The release Pipeline will inherit the sharing permissions of the original. Once it has been created, the sharing permissions of the release can be changed independently of the original.

## Releasing a pipeline

1.  Click Release with the version in the top right corner of your Pipeline to release the Pipeline.

    <figure><img src="https://lh7-us.googleusercontent.com/4_LXbiLYwhA6xLn1Usm8-l7HrNpoUQna2UYScFMEI-2Ew0D7HgJbHW5wOlR1oPAmQo2EiZ_5l1U2MOUWr2nznRP7xjtR4lLwiAJyu7i72s29fdffguBAlJ6Ot-f5l6dVNwePwPDHaItscS7IWl6jAms" alt=""><figcaption></figcaption></figure>
2. Complete the mandatory pre-release steps:
   1. Fill out the required metadata.
   2. Perform a Reproducible Run that includes all the latest changes.&#x20;
   3. Ensure all files in your Pipeline are either tracked in git or intentionally excluded from git.
   4. Make sure all Capsules in this Pipeline are release versions.
   5. Ensure your Pipeline does not contain an invalid App Panel.
   6. Set the Release functionality to specify whether your Pipeline will be released as a No-code App.
3.  Once you complete the checklist, you can release the Pipeline.



    <figure><img src="https://lh7-us.googleusercontent.com/BEi8fSVzyXA5vQMk8zW8me5_eBnxS5rNO2eqKJlJVk604cWc-U0P-DDwOWza8S18lsWd5i5sdbcvuvKGHDvm25jBnFiZSYriVRUgBMVFM9olfaHc0BAxYiLSVVRx7BNzVCTtvrIA-VSDDTae_B_R51E" alt=""><figcaption></figcaption></figure>

You can find your release Pipeline under the dedicated Internal Releases dashboard along with release Capsules that have been shared with your organization.&#x20;

For Pipelines with multiple release versions, users are able to switch seamlessly between any available version of the release Pipeline by selecting the corresponding version from the drop down menu.

<figure><img src="../.gitbook/assets/image (109).png" alt=""><figcaption></figcaption></figure>
