---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/compute-capsule-basics/managing-capsules/collaborating-a-capsule-with-secret
---

# Sharing a Capsule with Secrets

## Sharing or Releasing a Capsule with Secrets

You can share a Capsule with secrets, just like any other Capsule. However, for reproducibility purposes, it is currently not possible to release a Capsule with secrets.&#x20;

{% hint style="danger" %}
A warning message will pop-up when a user tries to release a Capsule with secrets.

![](<../../.gitbook/assets/image (201).png>)&#x20;
{% endhint %}

## **Running a Shared Capsule with Required Secrets**

### **Run a Shared Capsule with Missing Credentials**

If you try to execute a Reproducible Run in Capsule that requires secrets and the secrets are not set, a warning message will pop up.

![](<../../.gitbook/assets/image (326).png>)

Code Ocean will still allow you to execute a Reproducible Run. However, if you don't fix the credentials, the results are likely not reproducible.

### **Check if Secrets are Required**

When using other users' Capsules, it is a good habit to check if the Capsule requires secrets.

1. Click on **environment** to display the Environment Editor.
2. Scroll down to see the **Secrets** section.
3. Check if there is a secret to fill.

The screenshot demonstrates a Capsule that requires AWS credentials and a custom key:

![](<../../.gitbook/assets/image (410).png>)

### Add Your Secret to a Shared Capsule

* Click on the drop-down menu to select the secret to attach from your account.&#x20;
* The list in the drop-down is filtered and only shows the specific type of secret in your account.
* If you don't have existing credentials to attach, the **+ Add New \[secret type]** button allows you to add a new secret:
  * The system will pop up a form for you to fill out the details depending on the [secret type](../secret-management-guide/adding-editing-a-secret-in-the-account-settings-page.md#types-of-secret).

![](<../../.gitbook/assets/Collaborating on a Capsule with a Secret - Add your Secret to a Shared Capsule.gif>)

{% hint style="info" %}
The system will store the newly added secret to your account.
{% endhint %}
