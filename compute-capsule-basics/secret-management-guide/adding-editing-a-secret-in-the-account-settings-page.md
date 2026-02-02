---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/compute-capsule-basics/secret-management-guide/adding-editing-a-secret-in-the-account-settings-page
---

# Setting a Secret in the Account Settings Page

## Navigating to the User Secrets Section

The User Secrets section is on the account page. To view the account page:

Click the **Account** icon from the panel.

<figure><img src="../../.gitbook/assets/image (142).png" alt="" width="103"><figcaption></figcaption></figure>

Select **Roles and Secrets**.

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-08 at 11.22.16 AM.png" alt="" width="285"><figcaption></figcaption></figure>

## Adding a New Secret

1. Click **Add secret**.
2. Select the secret type you want to add (see a detailed explanation below).
3. Complete the required fields.
4. Click **Save Changes**.

## Types of Secrets

Currently, Code Ocean supports four types of secrets:

{% tabs %}
{% tab title="AWS Cloud Credentials " %}
Credentials to connect to AWS services.

![](<../../.gitbook/assets/Code Ocean 2022-03-13 at 4.52.49 PM.png>)

|                                                                    |                                                                                                                                                                                                       |
| ------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p></p><p><strong>Short Description</strong></p>                   | <p></p><p>The name of the secret. Choose a name you and your colleagues can easily recognize and understand.</p>                                                                                      |
| <p><strong>AWS</strong> <br><strong>Access Key ID</strong></p>     | <p>Copy and paste AWS Access Key ID. <br>Check this article to <a href="https://docs.aws.amazon.com/powershell/latest/userguide/pstools-appendix-sign-up.html">find your AWS credentials</a>.</p>     |
| <p><strong>AWS</strong> <br><strong>Secret Access Key</strong></p> | <p>Copy and paste AWS Secret Access Key. <br>Check this article to <a href="https://docs.aws.amazon.com/powershell/latest/userguide/pstools-appendix-sign-up.html">find your AWS credentials</a>.</p> |
| **AWS Region**                                                     | <p>Specify the region value of the AWS S3 service (e.g. us-east-1).</p><p>Check this article to <a href="https://docs.aws.amazon.com/general/latest/gr/s3.html">find S3 regions</a>.</p>              |
{% endtab %}

{% tab title="Database Credentials" %}
Credentials to connect to your database.

![](<../../.gitbook/assets/Code Ocean 2022-03-13 at 4.53.37 PM.png>)

|                        |                                                                                                    |
| ---------------------- | -------------------------------------------------------------------------------------------------- |
| **Short Description**  | The name of the secret. Choose a name you and your colleagues can easily recognize and understand. |
| **Database User Name** | The user name to connect to your database.                                                         |
| **Database Password**  | The password to connect to your database.                                                          |
{% endtab %}

{% tab title="Databricks Credentials" %}
Credentials to connect to your Databricks SQL Warehouse.

<figure><img src="../../.gitbook/assets/Screenshot 2024-03-27 at 9.37.45 AM.png" alt=""><figcaption></figcaption></figure>

|                       |                                                                                                                                                                                                                                             |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Short Description** | The name of the secret. Choose a name you and your colleagues can easily recognize and understand.                                                                                                                                          |
| **Token**             | Databricks workspace Personal Access Token. For more information on generating this token, read the Datbricks article [here](https://docs.databricks.com/en/dev-tools/auth/pat.html#databricks-personal-access-tokens-for-workspace-users). |
{% endtab %}

{% tab title="API Credentials" %}
Credentials to connect to an external API. (Not the Code Ocean API.)

![](<../../.gitbook/assets/Code Ocean 2022-03-13 at 4.54.27 PM.png>)

|                       |                                                                                                    |
| --------------------- | -------------------------------------------------------------------------------------------------- |
| **Short Description** | The name of the secret. Choose a name you and your colleagues can easily recognize and understand. |
| **API Key**           | The key to the API.                                                                                |
| **API Secret**        | The secret of the API.                                                                             |
{% endtab %}

{% tab title="Custom Key" %}
Create a custom key.

![](<../../.gitbook/assets/Code Ocean 2022-03-13 at 4.55.42 PM.png>)

|                       | Title                                                                                              |
| --------------------- | -------------------------------------------------------------------------------------------------- |
| **Short Description** | The name of the secret. Choose a name you and your colleagues can easily recognize and understand. |
| **Value**             | The value of the custom key.                                                                       |
{% endtab %}
{% endtabs %}

## **Editing a Secret**

1. Click on the short description of the secret you want to edit.
2. Modify the field accordingly.
3. Click **Save Changes**.



