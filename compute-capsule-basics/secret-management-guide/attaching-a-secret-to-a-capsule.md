---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/compute-capsule-basics/secret-management-guide/attaching-a-secret-to-a-capsule
---

# Accessing a Secret in a Capsule

## Attaching a Secret to a Capsule

1. Click on **environment** to display the Environment editor in a Capsule.
2. Scroll down to see the Secrets section.
3. Click **+ Add secret to Capsule**, and a drop-down menu that contains the secret list from your account settings page will appear.
4. Select the type of credential you wish to add from the dropdown.
5. Select the secret you wish to attach from the dropdown.

![](<../../.gitbook/assets/ezgif.com-gif-maker (3).gif>)

{% hint style="info" %}
If there are no secrets configured on your account page, the + **Attach secret to Capsule** button will be disabled with a reminder message below. To attach the secret, you must [set up your secret in the account settings page first](adding-editing-a-secret-in-the-account-settings-page.md).&#x20;

<img src="../../.gitbook/assets/[Access secret in capsule] attaching secret to capsule - button disabled.png" alt="" data-size="original">
{% endhint %}

### Automated Implementation of AWS Credentials in Capsules

When accessing an external Data Asset created from a private S3 bucket during a Capsule run, Code Ocean will automatically check the user's [Secrets](adding-editing-a-secret-in-the-account-settings-page.md) or [Assumable Roles](https://app.gitbook.com/s/FxC5loTDxWAlAbRU5bo1/the-admin-dashboard/assume-roles) and use the appropriate credentials. This also works if there are multiple Data Assets attached to the Capsule that each require different credentials -- Code Ocean will automatically use all appropriate credentials/roles that have been configured for the user allowing them to access the Data Assets.

### Edit the Title of the Attached Secret

After you selected the secret, you can verify the secret type and the secret's title in the drop-down menu and the secret's title above it. The secret's title is the same as its name by default. To edit the title, click on the pencil icon. &#x20;

<figure><img src="../../.gitbook/assets/Accessing a Secret in a Capsule - Edit the Title of the Attached Secret (1).gif" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
When sharing a Capsule with other users, the secret's title should help them to easily identify and pick the right secret to use in the Capsule.
{% endhint %}

## Using a Secret as an Environment Variable

After attaching a secret in the environment editor, the system will save the secret as environment variables and save only the variable names in either an `environment.yml` file or a `secrets.json` file, depending on when the Capsule was created.

### Understanding the `environment.yml` / `secrets.json`

The system will generate the `environment.yml` / `secrets.json`  automatically when you attach secrets in the Capsule.&#x20;

The content depends on the secret's type and is associated with the required field during set up.

* **type**: there are four types, corresponding to the four types of secrets.
* **id**: a random alphanumeric string.
* **description**: the secret's title for identification on the environment page.
* **specific fields**: depend on the secret's type.

Here are example screenshots of each type of secret:

{% tabs %}
{% tab title="AWS" %}
![](<../../.gitbook/assets/2 AWS yml.png>)
{% endtab %}

{% tab title="Database" %}
![](<../../.gitbook/assets/3 DB yml.png>)
{% endtab %}

{% tab title="API" %}
![](<../../.gitbook/assets/4 api yml.png>)
{% endtab %}

{% tab title="Custom Key" %}
![](<../../.gitbook/assets/5 custom key yml.png>)
{% endtab %}
{% endtabs %}

{% hint style="info" %}
The specific fields are all in upper case with an underscore in between. These are the environment variables that can be referred to in the script.
{% endhint %}

{% hint style="info" %}
If you attach a few secrets of the same type, a number will be added to the specific fields of the same secret type to differentiate them.

Here is an example of two custom keys:

![](<../../.gitbook/assets/6 duplicate key.png>)
{% endhint %}

If your application requires specific variable names for your secrets, they can be edited in the `environment.yml` file, which will change the names to which the secrets are copied over from the default names.

If your Capsule has a `secrets.json` file, click **Set Environment Variable Names** in the secret's actions menu to edit these names.&#x20;

<figure><img src="../../.gitbook/assets/TorchDrug (2).gif" alt=""><figcaption></figcaption></figure>

### Using a Secret in Script

After you attach a secret in the Capsule, the system will save the encrypted secret. When you run the Capsule, the secret will be set as an environment variable in the computation. To visualize this, you can print out your secret in the script by retrieving the environment variable.

Different programming languages have different commands to retrieve the environment variable. Below are examples of calling a custom key in Bash (run script), Python, and R. In this example, we added a custom secret to the Capsule. The value is `demo`, and it is saved in the `CUSTOM_KEY` environment variable.

{% tabs %}
{% tab title="Bash (run script)" %}
In Bash, use `${VAR}` to retrieve the specific variable ({VAR} is the variable name).

![](<../../.gitbook/assets/6 Use a Secret in the Script bash.png>)
{% endtab %}

{% tab title="Python" %}
In Python, use the `getenv` function in `os` module to get the environment variable.

![](<../../.gitbook/assets/7 Use a Secret in the Script python.png>)
{% endtab %}

{% tab title="R" %}
In R, use `Sys.getenv('VAR')` to get the environment variable.

![](<../../.gitbook/assets/8 Use a Secret in the Script R.png>)
{% endtab %}
{% endtabs %}

{% hint style="info" %}
You can access a secret as an environment variable from a Cloud Workstation as well.
{% endhint %}

{% hint style="danger" %}
Printing out secrets is not usually a good practice. The code in this section is for demonstration purposes only. If you use the print command to verify the accessibility of the attached secret, remember to remove the print command afterward.
{% endhint %}

## Using a Secret during Build Time

User Secrets (AWS Cloud Credentials, Database Credentials, API Credentials, and Custom Keys) are available during environment builds with the values accessible in the Dockerfile and postInstall under their typical environment variable names.&#x20;

{% hint style="info" %}
Note: To make secrets available at build time, make sure to commit changes in your Capsule before attaching the secrets.
{% endhint %}
