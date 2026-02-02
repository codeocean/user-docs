---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/data-assets-guide/viewing-and-editing-data-assets
---

# Managing Data Assets

You can easily manage all your Data Assets on the My Data page.&#x20;

Code Ocean provides a detailed page for each Data Asset. The Data Asset's information can vary per Data Asset type (see [Types of Data Assets](../types-of-data-assets.md) for more information).

On the details page, you can do the following:

* Search the Data Asset for specific files
* See the list of files in the Data Asset
* Preview the files' content
* Download individual files
* Get a sharing link for individual files
* Download all the files in the Data Asset as a zip file
* Edit the notes, tags, title, and default folder
* Archive and delete the Data Asset
* Share the Data Asset
* Expand the view to the entire window

## View General Information

| Data Asset ID                                   | ID of the Data Asset                                                                                                                                      |
| ----------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Description                                     | A markdown supported description of the Data Asset                                                                                                        |
| Files and Number of files                       | The files included in the Data Asset and how many files are included                                                                                      |
| Created On                                      | Data Asset creation time                                                                                                                                  |
| Created By                                      | The name of the user who created the Data Asset                                                                                                           |
| Number of Files                                 | How many files the Data Asset contains                                                                                                                    |
| Size                                            | The size of the Data Asset                                                                                                                                |
| <p>Provenance<br>Code Version<br>Run Script</p> | <p>Relevant only for captured results. The version of the code (commit ID) when capturing the Data Asset.<br>The script that generated the Data Asset</p> |
| Tags                                            | Tags provided when the Data Asset was created.                                                                                                            |
| Custom Metadata                                 | Custom metadat provided when the Data Asset was created.                                                                                                  |

<figure><img src="../../.gitbook/assets/image (48).png" alt="" width="563"><figcaption></figcaption></figure>

## Share Data Assets

Sharing Data Assets allows you to share the Data Asset with collaborators. Click **Share** to share the Data Asset.

<figure><img src="../../.gitbook/assets/image (49).png" alt="" width="188"><figcaption></figcaption></figure>

In Set permissions for Data Asset:

1. Enter the email address or select an address from the dropdown list.
2. Click **Add.**

{% hint style="info" %}
More than one user can be added and the status of **Owner,** or **Viewer** can be selected, a user can be removed by selecting  **Remove Permissions**. \
\
Data Assets can be set to **Discoverable** to the entire organization or to groups of users. The access allows specified users to find the Data Asset in searches, view the metadata, and see the name and email address of the owner, users can request additional access.
{% endhint %}

{% hint style="info" %}
**Copy Link** copies the URL of the Data Asset for easy distribution. Only users with **Viewer** or **Owner** permissions can see the page.
{% endhint %}

### Permission Types

There are two types of permissions **Viewer** and **Owner**.

| Action                                             | Viewer               | Owner                |
| -------------------------------------------------- | -------------------- | -------------------- |
| Search keywords within the Data Asset              | :white\_check\_mark: | :white\_check\_mark: |
| Search the list of files                           | :white\_check\_mark: | :white\_check\_mark: |
| Preview the files inside the Data Asset            | :white\_check\_mark: | :white\_check\_mark: |
| Download all the files in the Data Asset           | :white\_check\_mark: | :white\_check\_mark: |
| Edit the tags, note, and title of the Data Asset ​ | :x:                  | :white\_check\_mark: |
| Delete the Data Asset                              | :x:                  | :white\_check\_mark: |
| Set permissions to other users                     | :x:                  | :white\_check\_mark: |

{% hint style="info" %}
To make a Data Asset visible to all internal users, check the **Set default permission to "Viewer" for all internal users** box.

For external Data Assets, since the data is not saved on Code Ocean's server, users cannot see nor download the content of the Data Asset from the My Data Dashboard.
{% endhint %}

## Download Data Assets

1. Click on the three dots on the top right to open the drop-down menu.
2. Click **Download** to download a zipped folder of the Data Asset.

<figure><img src="../../.gitbook/assets/image (51).png" alt="" width="188"><figcaption></figcaption></figure>

## Edit Data Assets

1. Click **Edit** to enable editing of the Data Asset Name, Default Folder, Details and Tags.
2. Click **Save** to keep the changes.

![](<../../.gitbook/assets/image (49).png>)

## Archive Data Assets

1. Click on the three dots on the top right to open the drop-down menu.
2. Click **Archive** to archive the dataset.

<figure><img src="../../.gitbook/assets/image (52).png" alt="" width="188"><figcaption></figcaption></figure>

## Delete Data Assets

To delete and restore Data Assets:

1. To delete a Data Asset it must first be archived.

![](<../../.gitbook/assets/image (52).png>)

2. Click the **Archive icon** to view archived Data Assets.

<figure><img src="../../.gitbook/assets/image (54).png" alt="" width="188"><figcaption></figcaption></figure>

3. Locate the Data Asset to be deleted.
4. Click on the Data Asset. From this screen, the Data Asset can be deleted or restored.

<figure><img src="../../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

## List Capsules to which a Data Asset is attached

Each Data Asset in Code Ocean has a unique ID that can be viewed in the Data Details window in the Data Dashboard or a pop-up in the capsule IDE.

The Data Asset ID can be copied to the clipboard and used to search for Capsules that have the Data Asset attached.

<figure><img src="../../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

Hover over the Attached "x times" link, and a pop-up message will appear displaying the number of Capsules and Pipelines that are using this Data Asset.

<figure><img src="../../.gitbook/assets/image (57).png" alt="" width="375"><figcaption></figcaption></figure>

You can view the Capsules and Pipelines that you own or are shared with you by clicking on **Capsule** or **Pipeline**. This automatically searches Capsules or Pipelines for the Data Asset ID.&#x20;

<figure><img src="../../.gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>

### Attach All/Detach All

**Attach All** and **Detach All** on the side panel enables the attachment or detachment of all the Data Assets on the page at once.

<figure><img src="../../.gitbook/assets/Attach Detach.gif" alt=""><figcaption></figcaption></figure>
