---
description: >-
  Create a Code Ocean Model by registering it in MLflow, creating from a Capsule
  or Pipeline result, or by importing from Hugging Face.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/models-guide/creating-models
---

# Creating Models

## **Registering Models in MLflow**

Register models for lifecycle management and version control. Creating registered models allows you to track changes over time, while also enabling easy access to previous model versions for comparison.&#x20;

By registering a model in MLflow, a Registered Model is also created in your Code Ocean Models dashboard, complete with provenance and lineage.&#x20;

Follow these steps to register a model from a completed run, in the MLflow UI:

1. Open the **MLflow UI** from the Navigation Sidebar, or from within a Capsule or Pipeline.
2. Go to the **Experiments** tab.
3. Click on the Model from the run which you wish to register.
4. Click **Register Model**.
5. Select from the dropdown an existing model or **Create New Model**.
6. Click **Register** to complete the registration process.

## **Creating Models from the Timeline**

In addition to registering models in the MLflow UI, you can also capture any computation model, indicated in the Capsule or Pipeline Timeline by a “Model” icon, as a Code Ocean Model that includes automatically-generated provenance and lineage. These Models can be shared and attached to a Capsule or Pipeline for downstream analysis.&#x20;

{% hint style="info" %}
Code Ocean Models from the timeline can only be created using MLflow integration.&#x20;
{% endhint %}

Before capturing a model, verify that you:

1. Save the model under the /results folder and that the model files are visible in the Timeline.
2. Commit all the changes in the Capsule (click Commit Changes in the Timeline if not done yet).

Capture a Model by following these steps:

1. In your Capsule or Pipeline's Timeline, go to the model you want to capture and click the actions menu.
2. Click **Create New Model**.
3. Complete the fields:
   * **Model Name** (required)—Use a meaningful name so that others can find the model easily.
   * **Folder Name** (required)—The folder name inside a Capsule. Use a name that’s similar to the model name. Spaces and some special characters are not allowed here.&#x20;
   * **Description** (optional)—Add markdown supported text to make the Model easy to find and understand.&#x20;
   * **Tags** (optional)—Tags are another way to help other users find your model.&#x20;
   * **Custom Metadata**
4. Click **Create New Model**.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfGKEVWHk56zRCWc6wiPHDcOUNjuvCez8eIQj2MDzXgW9Fkp0rdT6VntBiuAI1M1yCLbZSgRDLkghMAEQuLvj0dtrsN0YkBprbXWL2K56JaCvyLbXw2QllXRWavY0jxBPhEHGx_uU84ibG4w2D9qi68lFxz?key=V2mion4JrIuNYQV2joZ06w" alt="" width="375"><figcaption></figcaption></figure>

After you’ve created the Model, you’ll get a link to view it on the Models page. There, you can validate that you’ve captured the correct model, edit, download and share with others.

\
Importing from Hugging Face
---------------------------

To import a model from Hugging Face:

1. Click **+ New Model** and choose **Hugging Face**.
2. Specify the **Model ID** or the **repository URL** for the Hugging Face model you would like to import.&#x20;
3. Specify the **file or folder path** that corresponds to the specific **version** of the Hugging Face model you would like to import.&#x20;
   * You may leave this field blank by checking the box "Import all files and versions of the model." Note that this will import all files and folders associated with this model.&#x20;
4. Complete the fields:
   * **Model Name** (required)—Use a meaningful name so that others can find the model easily.
   * **Folder Name** (required)—The folder name inside a Capsule. Use a name that’s similar to the model name. Spaces and some special characters are not allowed here.&#x20;
   * **Description** (optional)—Add markdown supported text to make the Model easy to find and understand.&#x20;
   * **Tags** (optional)—Tags are another way to help other users find your model.&#x20;
   * **Custom Metadata**
5. Click **Create Model**.&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2025-03-13 at 9.39.58 AM.png" alt="" width="563"><figcaption></figcaption></figure>
