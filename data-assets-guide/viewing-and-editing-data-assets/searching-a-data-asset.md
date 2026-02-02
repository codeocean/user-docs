---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/data-assets-guide/viewing-and-editing-data-assets/searching-a-data-asset
---

# Finding Data Assets

All your Data Assets are accessible on the **My Data Dashboard**. Use the available search and filtering options to quickly locate the specific Data Assets you need.

### The Search Box

Use the search box to search for Data Assets. Combine with Data Asset Filters and Metadata Filters to narrow down the search. For example, use the External filter to only search for Data Assets that are stored externally, or search tags in the Metadata Filters.

{% hint style="info" %}
Search can be refined by combining field-specific queries in the search bar, for example:\
`name:RNA-seq tag:genomics`. Note that while the UI often refers to this field as **Title**, the search syntax requires using **`name`**.
{% endhint %}

<figure><img src="../../.gitbook/assets/Screen Shot 2024-12-11 at 2.32.55 PM.png" alt=""><figcaption><p>My Data Dashboard</p></figcaption></figure>

### Filter Data Assets

Data Assets can be filtered using:

* **All**—Includes all Data Assets.
* **Favorites**—Includes those marked as favorite.
* **Source**—Includes all sources detected in the deployment.&#x20;
* **Type**—Includes Data, Results, and Combined.
* **Access**—Includes Created by Me, Owned by Me, Shared with Me, and Admin.&#x20;
* **Storage**—Includes Internal and External assets.&#x20;

{% hint style="info" %}
Filters and search can be used together to narrow down results and find Data Assets more easily.&#x20;

Only admins will see the additional "**Admin**" option under the Access filter that will show all assets across all dashboards and side panels.&#x20;
{% endhint %}

## Metadata Search UI

To align with FAIR principles (Findable, Accessible, Interoperable, Reusable), Code Ocean provides a UI for locating Data Assets using Custom Metadata fields. In the **Metadata Filters Menu**, users can toggle metadata fields and enter keywords to refine their search.

Data Assets displayed under the applied filters have the specified field populated and match the entered keyword.

1.  Click the **Metadata Filters** button in the filters row.

    <figure><img src="../../.gitbook/assets/Screen Shot 2024-12-11 at 2.35.52 PM.png" alt="" width="375"><figcaption></figcaption></figure>
2. Locate the field to filter and switch on the toggle button.
3. Expand the field and modify the inputs.

<figure><img src="../../.gitbook/assets/GIF Recording 2024-12-11 at 2.33.57 PM.gif" alt=""><figcaption><p>Custom Metadata Filters</p></figcaption></figure>

{% hint style="info" %}
Keys in Categories will appear at the bottom of the list in **Metadata Filters**, and will include the Category name in italics. To manage what Categories are shown in Metadata Filters, click **Categories** next to the search bar and select/de-select the Categories you wish to see.&#x20;
{% endhint %}

## Making Data Assets Discoverable

When Data Assets are discoverable, they will appear in searches. Metadata is shown, but the Data Asset cannot be previewed, downloaded, attached, or run in Capsules or Pipelines. The name and email address of the owner are displayed. To view or edit this Data Asset, contact the owner to request access.

To make a Data Asset discoverable, select **Discoverable** in the dropdown list under **General Access** in the **Sharing and Permissions Menu**.&#x20;

<figure><img src="../../.gitbook/assets/discoverable (1).png" alt=""><figcaption></figcaption></figure>

