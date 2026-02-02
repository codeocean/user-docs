---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/compute-capsule-basics/managing-capsules
---

# Managing Capsules

You can easily manage all your Capsules on the **My Capsules** page, or directly from the Code Ocean user interface for each particular Capsule. Code Ocean makes collaboration easier, by allowing you to share, edit access, and archive Capsules directly from the user interface.&#x20;

## Sharing Capsules

### About Sharing a Capsule

Sharing a Capsule means that others can continue working from what you’ve developed—either in the same Capsule or in a duplicate Capsule. You can set Capsule permissions to collaborate with users and groups within your organization. Only authorized users can view/duplicate, or edit your Capsule. Shared Capsules are updated in near real-time with any changes made in the Capsule.

It is best practice to utilize Group sharing to ensure that new users will have all relevant Capsules, Data, and Pipelines available to them when they join, and that there will be no lost assets when team members leave.

Reach out to your Admin to configure Groups through your organization's chosen Identity Provider.

{% hint style="info" %}
You can share a Capsule with secrets/credentials just like any other Capsule. To learn more about setting up secrets in Code Ocean, refer to the[ Secret Management Guide](../secret-management-guide/).

Navigate to[ Run a Shared Capsule with Secrets](collaborating-a-capsule-with-secret.md#run-a-shared-capsule-with-missing-credentials) to learn how to run a shared Capsule with a secret.
{% endhint %}

### Managing Capsule Permissions

#### Types of Permissions

The three types of permission for a Capsule are: Owner, Editor, and Viewer.

| Action                        | Viewer                   | Editor                   | Owner                    |
| ----------------------------- | ------------------------ | ------------------------ | ------------------------ |
| View a Capsule                | <p>​</p><p>✅</p>         | <p>​</p><p>✅</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> |
| Download a Capsule            | <p>​</p><p>✅</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> |
| Export a Capsule              | <p>​</p><p>✅</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> |
| Edit files in a Capsule       | <p>​</p><p>❌</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> |
| Execute a Reproducible Run    | <p>​</p><p>✅</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> |
| Work from a Cloud Workstation | <p>​</p><p>❌</p>         | <p>​</p><p>✅</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> |
| Edit Capsule's permissions    | <p>​</p><p>❌</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> |
| Delete a Capsule              | <p>​</p><p>❌</p><p>​</p> | <p>​</p><p>❌</p><p>​</p> | <p>​</p><p>✅</p><p>​</p> |

### Setting Permissions for Collaborators

1. Click **Share** at the top right corner of the Capsule to open the sharing and permissions settings.

<figure><img src="https://lh7-us.googleusercontent.com/GEgcZfURaA02wYxxAQaHtvbdBDw_1LjC05gJycWnrnLpEkB5Iz3ZgMlpoeAAKXwn3HRpRs6j2rsLJwxdkrRTw6RIfTScBKGf8FH2AU2W0m6lyrmBdbLU28LFmKNWQL6NmeOEhAR3zap9hIon5K8z6Ns" alt=""><figcaption></figcaption></figure>

2. Type the name of the collaborator to invite or select the name from the drop-down menu. If groups are configured in your organization, they will also appear in the drop-down menu.

<figure><img src="https://lh7-us.googleusercontent.com/I-yYEwZ79ENOW1Z-g7mwG3_gHz-hle62G_eKjKsVKD_j5rrTumRAHVtwRGsHvrHotZGu6Xlja97bMJY8uZE-HUwV59u7WWmlHrsRD6z6bw9dK53FLu-2t_lorDFjtDckBId6IC1AawLa_3WQvsd_AjU" alt="" width="375"><figcaption></figcaption></figure>

3. Click the desired user’s name/email address in the dropdown to add the collaborator. The system adds the user to the Capsule's permissions list. The permission level will be set as Viewer by default.

<figure><img src="https://lh7-us.googleusercontent.com/EDmkWVDjH86MK8pn2cvVdiTpbyRZ6punHKbr9HB2UOBoYssF_BCXd1t4U3grevSNKFjHqA-oGZtl1hOvswVVl6d5S0ZSs4I2Dkkfc3NCI6hG8PpG9v-vGU-v-qnbTuqpJr04TunCMSZTN9eY3OnnAA0" alt="" width="375"><figcaption></figcaption></figure>

4. To change a user's permissions or remove a user, click the drop-down menu next to the desired user which shows their current permissions and choose the relevant option.

<figure><img src="https://lh7-us.googleusercontent.com/P_gyRS0FsgUkS7t4cAhNuqRR9iJ2FAWFkB_YAb1t5WCZCXgynyXJw6EYYAnHG7PxIWe2KPeE-ozv1ORS4XbN5PUI0fIjw7xycfOYrCfoLT4Bdha0PqHcG5wyd58Lj004F6DhNhK3kw39uHrLJsWsWfc" alt="" width="375"><figcaption></figcaption></figure>

5. Click **Save** in the bottom right corner of the pop up to close the Capsule sharing and permissions settings.

{% hint style="info" %}
You can add more than one collaborator by repeating steps 2-3 before Saving.

To make a Capsule visible to all internal users, under General Access, Everyone select Viewer

To share the Capsule with Data Assets, check **Share Assets**. To share only the Capsule without Data Assets, ensure that **Share Assets** is deselected.
{% endhint %}

### Owner/Admin Ability to Capture, Delete, and Rename Runs

Capsule Owners and Admins have the ability to rename and delete runs from other users, as well as create Result Data Assets from those runs. Code Ocean Admins also have the ability to see all runs on Release Capsules and rename or delete those runs.

![](https://docs.codeocean.com/~gitbook/image?url=https:%2F%2F1603030414-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252Fa5AT4eq2XLAGmfb36GJm%252Fuploads%252FznOKxyDEXljogAd3QHvR%252F35e32ce5-ef3f-45d7-8627-4e2e3411fe24.gif%3Falt=media%26token=ee3fa745-154a-4cfa-8f09-7aeec031521b\&width=768\&dpr=4\&quality=100\&sign=4c4a3bd2c8d4431e6352bb2759331fa1001348227a036adad2953cee55ca0e8a)

### Working on a Shared Capsule

#### View Mode

When you add a collaborator with the permission to view the Capsule, the collaborator can view all the folders and files from the Capsule IDE, download individual files, export, and duplicate the Capsule.

To execute or modify code in the Capsule as a Viewer, you will need to duplicate the Capsule prior to editing.

Anyone with View Access can attach secrets to the Capsule that is shared with them

<figure><img src="https://lh7-us.googleusercontent.com/grijlwF2BrXBOPn-4lzWDSiXrvaEETNyLBJ6OoA8RhBMwk-dbzZTwa6gDeJ2W9N7enjEJa796k--TiQVsWS_Fu7SK_tNrtnc0LWIJwD6cvLVW5euQEPckQ9mf-VNtReA_e4pjJ81jZpkyBLuT0U8jVM" alt=""><figcaption></figcaption></figure>

#### ​Edit Mode

When you share a Capsule with the edit permission, the collaborator can change any file's content and execute code in a Capsule. Only one user can edit the shared Capsule at any given time. All collaborators can view the same Capsule simultaneously. When a collaborator is editing the Capsule, all others will see the Capsule in the view-only mode indicated by a message on top of the center section of the Capsule IDE and the deactivated buttons in the right Timeline section.

<figure><img src="https://lh7-us.googleusercontent.com/Ewe26JgQZ5voIWVhjCp-lli4zP-Du6OImJywImb0OeM5plg4LzyVIp9MOeatKrvj-oByVnrpSlGFE0Sy2ZC7WtGmoLYXU02sK3wQGuWY92ARqOQujWQvu-1UzaJFyPxMgDAJx7t-vcdyzzA-HUj6Xpw" alt=""><figcaption></figcaption></figure>

Click **Start editing** to begin editing above the Editor in the center. If a collaborator's name appears in the message, they are forced into the read-only mode after your click.

{% hint style="warning" %}
Before you decide to edit the Capsule when a collaborator appears to be editing, it is strongly recommended that you communicate with your collaborator in advance, so they don't lose their work.
{% endhint %}

When you're done, click **Finish editing**.

### Duplicating a Capsule

How to create a private copy of either released or unreleased code.

Duplicating a Capsule allows you to create a copy of it while keeping the original unchanged. To duplicate a compute capsule:

1. Navigate to your My Capsules Dashboard,&#x20;
2. Click on the Capsule you would like to duplicate, which will open the Capsule IDE
3. Click Capsule in the menu at the top of the screen
4. Select Duplicate. This process will create an exact copy of the Capsule, which will open and be added directly to your My Capsules Dashboard

<figure><img src="https://lh7-us.googleusercontent.com/2FTYAhiEhM1Niva5BXi4ZcbKBcC-6SrvZvwKRFSP8DukdH5yvkrfDp5P3B_7AubEYSGM1nB2VTElDGnh7VxfjG5MhVKhWshSTATz_Xg4acnVzrxqbMH_DRsUBfmmFZpPndUY-qanukM3erPXcJZzjvo" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/capsule duplicated.png" alt=""><figcaption></figcaption></figure>

### Archiving a Capsule

Capsules and Data Assets can be archived to reduce clutter in the Capsules/Data Assets list. Archiving removes a Capsule/Data Asset from the 'All' view, making them accessible through the Archive view

1. To begin the process of archiving your Capsule, Navigate to the **My Capsules** **Dashboard**.

![](https://lh7-us.googleusercontent.com/bDZvaP2MnX5cslvXvIpBTs9fZxgZj7gbHo3AKzX6E1OtZGY3DTQzEHRwZfSMWfCI-tRaNGQ5T3OjBrMPnQTbUrmaK2yF4eJC2YmEYrq3aSn7C_RPDgRE0-E4UJJ9b3QgL-SHghzSgh5YFS90mrXvwyE)

2. To arching your Capsule directly from the **My Capsules Dashboard**, hover over the desired Capsule and click **Archive** in the toolbar selection that appears.<br>

![](https://lh7-us.googleusercontent.com/HAXf800NaC_R9RoDaKjae8WeSkVTQvfMvK6fNBg9E_1y25cGYLSTNCw_aDdAqOEa8JXgn13ugLwnmjA61ueqzZ91IBecYvCoz9H0k9-jrHdNZpIzyWCP12dY3Os4_9BFRW1vOgctgP3LI639VP49zL4)

### Restoring an archived Capsule

1. To view an archived Capsule/Data Asset, click **Archive** in the menu. All the archived Capsules/Data Assets are listed.

![](https://lh7-us.googleusercontent.com/sRH_GT4P7Hf4uovlOF3wCTcTgOdGmT4TWv1FMXS-ZpLvE_cS8tOS3Vrv2M5HZ7eLuFMU8Wj9NpyWcfTD7H7S6TD_dnBdkhG06q6dfSAbofMzEndgvGLMt5pDW3Bb0jQfru2OOgeyZZn4ny8l73bAoSs)

2. To restore a Capsule from the Archive, scroll the cursor over the Capsule and click the **Restore Capsule** icon in the toolbar.

&#x20;![](https://lh7-us.googleusercontent.com/zOpxRonWETvBHTQn3ZqaeWPCav2C-5mWD5dOMaiGMLiAYRfhkPYSf0NWzhETL628lnzYniyVblGgcEmECuPCk3ifCNijyqizoYsqz9uC1OfIJOx33rtgXAyzi6eORvgWVns5NLHojwpgAx02UKEDdq0)

3. Click **Back to My Capsules** to return

### ​**Modify/Remove Capsule Permissions**

1. Navigate to your Capsule and click **Share** at the top right corner of the screen to open the sharing and permissions settings.
2. Navigate to the collaborator whose permissions you would like to modify.
3. Change or remove a user's permissions by clicking on the drop-down menu next to the user and selecting the appropriate option.
4. Click **Save** to close the Capsule sharing and permissions settings.
