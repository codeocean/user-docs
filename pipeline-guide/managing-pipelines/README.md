---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/pipeline-guide/managing-pipelines
---

# Managing Pipelines

## Sharing Pipelines

Sharing a Pipeline means that others can continue working from what you’ve developed—either in the same Pipeline or in a duplicate Pipeline.&#x20;

You can set Pipeline permissions to collaborate with users and groups within your organization. Only authorized users can view/duplicate, or edit your Pipeline. Shared Pipelines are updated in near real-time with any changes made in the Pipeline.

It is best practice to utilize Group sharing to ensure that new users will have all relevant Pipelines available to them when they join, and that there will be no lost assets when team members leave. Reach out to your Admin to configure Groups through your company’s chosen Identity Provider.

<figure><img src="https://lh7-us.googleusercontent.com/mHm9etWJ34WFM1IbSHbwIkdFD8dPnKWHkLZt1YBIwF9gUSAHW6MGnFIFrGSNe8A1FfC2PeRy7lrMHq-uNQlBJrAC4RRop1qLE1e6w1NJHTvCdhuN_GS1-M10ewWZqRDLBheficPRHNLGzOPlhvMKKL0" alt="" width="375"><figcaption></figcaption></figure>

{% hint style="info" %}
You can share a Pipeline with secrets/credentials just like any other Pipeline. To learn more about setting up secrets in Code Ocean, refer to the[ Secret Management Guide](../../compute-capsule-basics/secret-management-guide/).

Navigate to [Running a Pipeline with Secrets](../components-of-a-pipeline/capsules.md#running-a-pipeline-with-secrets) to learn how to run a shared Pipeline with a secret.
{% endhint %}

### Managing Pipeline Permissions

The three types of permission for a Pipeline are: Owner, Editor, and Viewer.

| Action                      | Viewer                   | Editor                   | Owner                    |
| --------------------------- | ------------------------ | ------------------------ | ------------------------ |
| View a Pipeline             | <p>​</p><p>✅</p>         | <p>​</p><p>✅</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> |
| Download a Pipeline         | <p>​</p><p>✅</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> |
| Export a Pipeline           | <p>​</p><p>✅</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> |
| Edit files in a Pipeline    | <p>​</p><p>❌</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> |
| Execute a Reproducible Run  | <p>​</p><p>✅</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> |
| Edit Pipeline's permissions | <p>​</p><p>❌</p><p>​</p> | <p>​</p><p>❌</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> |
| Delete a Pipeline           | <p>​</p><p>❌</p><p>​</p> | <p>​</p><p>❌</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> |

### Setting Permissions for Collaborators

1. Click Share at the top right corner of the Pipeline. A permissions setting form opens.

<figure><img src="https://lh7-us.googleusercontent.com/h2u5aVNRpCsZiWsQ8jPadI3pZNP_ZJ8uZvZIEA-L-6Js0KuEjaOr2yAztjsYufzjgGBgxzlouoepuiVA7NQNGJq83nMOUU-C8AnT1BiN-zJAaRpnGL6nQfdEHIQEUykT8QtWk2MSl-_CeKVkF5u8j3w" alt=""><figcaption></figcaption></figure>

2. Type the name of the collaborator to invite or select the name from the drop-down menu. If groups are set up in your organization, they will also appear in the drop-down menu.  <br>
3. Click the desired user’s name/email address in the dropdown to add the collaborator. The system adds the user to the Pipeline permissions list. The permission is set as Viewer by default

<figure><img src="https://lh7-us.googleusercontent.com/zLCOSl2KEf7vqYZSUExaR99BTfwnN45_L-MTh7-kiZd7ksDPdm_iGnlOk7sSNhcQlXEbtC0Fw5c_btfrpNlzi92nIE4iJS_RvaxzzFKZ_fVcjApFLi67B0LLeBaf-UP-s_jFA6kzyVhZUYi3xjou6k8" alt="" width="375"><figcaption></figcaption></figure>

4. To change a user's permissions or remove a user, click the down arrow next to the user, and choose the relevant option.

<figure><img src="https://lh7-us.googleusercontent.com/MBV_qK3EDE55F0c1dwkIGf4scdzTqlTDG0aU-1uc0Kkc2HgkEUrERIc_OdbSPr-qFaUP5MlMB9KCgpCh2Cv8CCzCFkkuKmg3a_dYXHm2R_IFGTEAdDus4PUglrU9iitUn7Po_oAlM2TDo9t-TzTH3pE" alt="" width="375"><figcaption></figcaption></figure>

5. Click Save in the bottom right corner of the pop up to close the Pipeline permissions setting form.
6. To make a Pipeline visible to all internal users, under General Access, Everyone select Viewer

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-23 at 2.52.39 PM (1).png" alt="" width="375"><figcaption></figcaption></figure>

7. To share the Pipeline with Data Assets check Share Assets. To share only the Pipeline without Data Assets, ensure that Share Assets is deselected.
8. You can add more than one collaborator by repeating steps 2-3 before Saving.<br>

#### **Modifying/Removing Collaborators from the Pipeline Permissions**

1. Click Share at the top right corner of the Pipeline. A permissions settings form opens.<br>
2. Navigate to the collaborator you want to modify.<br>
3. To change a user's permissions or remove a user, click on the drop-down menu next to the user, and select the relevant option.<br>
4. Click Save to close the Pipeline permissions setting form.

### Owner/Admin Ability to Capture, Delete, and Rename Runs

Capsule Owners and Admins have the ability to rename and delete runs from other users, as well as create Result Data Assets from those runs. Code Ocean Admins also have the ability to see all runs on Release Capsules and rename or delete those runs.

<figure><img src="../../.gitbook/assets/rename run.gif" alt="" width="281"><figcaption></figcaption></figure>

### Working on a Shared Pipeline

#### View Mode

When you add a collaborator with the permission to view the Pipeline, the collaborator can view all the folders and files from the Pipeline IDE, download individual files, export, and duplicate the Pipeline.

To execute or modify code in the Pipeline as a Viewer, you will need to duplicate the Pipeline prior to editing.

<figure><img src="https://lh7-us.googleusercontent.com/q7wtzdEzmGSEEfJDxwVRyjBeTUKaK-Quttsp2Sbq5gS4_lH-6kgjSDzMHFAmlzFa6lrqlAaxLmLdhZg3Wr84g0Td1yqWoP1NdFOgIoqsE7SiYFWSSffpVhcEiwfhBqgNh7EWod-W1FneT5AVmEi2AeA" alt=""><figcaption></figcaption></figure>

Anyone with View Access can attach secrets to the Pipeline that is shared with them

<figure><img src="https://lh7-us.googleusercontent.com/hQsQYCVtzU0OgdWydLo5lTaxok7j63OXwG5P4F3055bDG5IxfDDz8LE0kGzHYYsAYSK2l54P9rlK7l0WXkg115UFoib2L-aF6XWJ5x3rmgwyKatPLBiPdL7twCWpG_3khLH_5x4m7xCCG2i0ccdLmI8" alt="" width="563"><figcaption></figcaption></figure>

#### ​Edit Mode

When you share a Pipeline with not edit permission, the collaborator can change any file's content and execute code in a Pipeline. Only one user can edit the shared Pipeline at any given time. All collaborators can view the same Pipeline simultaneously. When a collaborator is editing the Pipeline, all others will see the Pipeline in the view-only mode indicated by a message on top of the center section of the Pipeline IDE and the deactivated buttons in the right Timeline section.

<figure><img src="https://lh7-us.googleusercontent.com/sofHbQ5SDWOkbylh4ywx2msIqxv8-cf7jkFpuDd99AR4J0Y53IT1_GYdhir0-xLx-Srscq4MmMAY3CBvwDYABL5NMMO2Snx7-W89igTR9VR1PHQL0MNTZ_OJDQfEWsHcdLYEuGzpPZDGI2aqDwnlPPQ" alt=""><figcaption></figcaption></figure>

<br>

Click Start editing to begin editing above the Editor in the center. If a collaborator's name appears in the message, they are forced into the read-only mode after your click.

{% hint style="info" %}
Before you Start edit the Pipeline when a collaborator appears to be editing, it is strongly recommended that you communicate with your collaborator in advance, so they don't lose their work.
{% endhint %}

## Duplicating a Pipeline

### How to create a private copy of either release or unreleased code

Duplicating a Pipeline allows you to create a copy of it while keeping the original unchanged. To duplicate a Pipeline:

1. Navigate to your My Pipelines Dashboard,&#x20;
2. Click on the Pipeline you would like to duplicate, which will open the Pipeline IDE
3. Click Pipeline in the menu at the top of the screen
4. Select Duplicate. This process will create an exact copy of the Pipeline, which will be added directly to your My Pipelines Dashboard

<figure><img src="https://lh7-us.googleusercontent.com/NNe4LuFm6AWtGHCX00MH71l1HEsV25xDFv3pMRlolBj11fOdrGjq3vGDp34VQ8VXSQkes7IJbhFEDNQ9tJVJM__ASzB2Z4dcTgnCgJzocJ82P-vjM17TBQIY33Imp-G3KJ7eV8l1Dqcn_750bvxDV_0" alt=""><figcaption></figcaption></figure>

## Archiving a Pipeline

Pipelines and Data Assets can be archived to reduce clutter in the Pipelines/Data Assets list. Archiving removes a Pipeline/Data Asset from the 'All' view, making them accessible through the Archive view.

1. Navigate to your **My Pipelines Dashboard**.

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-23 at 2.31.37 PM (1).png" alt="" width="160"><figcaption></figcaption></figure>

2. &#x20;To archive a Pipeline directly from your dashboard, click the **Archive** icon associated with the relevant Pipeline<br>

<figure><img src="https://lh7-us.googleusercontent.com/dcV-eJpjpkesl9o9oyvsTi_gXK5qkuVOI1legA19MmFWC39b7FB3tbpjg96Uo4Xc9GHlmtrIO_HgRU6elI0mQ6MVK9E1fns1TaseOu3dC0kwCzGOigC1xThY_wwKbNvjemb4B6MFqP_kpEQvnu4m8Co" alt=""><figcaption></figcaption></figure>



## Restoring an Archived Pipeline

Once a Pipeline is archived, it can be easily restored&#x20;

1. To view your archived Pipelines, click the **Go to Archive** icon in top right of your **My Pipelines Dashboard** . All of your archived Pipelines will be listed on this screen.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-23 at 2.35.21 PM (1).png" alt=""><figcaption></figcaption></figure>

4. To restore a Pipeline from the Archive, scroll the cursor over the Pipeline and click the **Restore Pipeline icon**.

<figure><img src="https://lh7-us.googleusercontent.com/RkCtF0YlLDBS-BLgB_7-fntBEsgvUrhSPJSa0pWCgbw1Uh3H-1jiyhsEhMdOr0G3_DCs2toqnuoapac4TyRgpOMC0TkSrXAJ6hg5oD5w_MWJg01rMCN6VVJWI8QudiE6RgpHdyZIXi72wcNSz2Mjss0" alt=""><figcaption></figcaption></figure>

5. Once all desired Pipelines have been restored, click Back to My Pipelines to return.
