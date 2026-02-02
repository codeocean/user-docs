---
description: >-
  This section will explain how to configure the settings of the Capsule in a
  Pipeline, including the Capsule version, resources, and command line
  arguments.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/pipeline-guide/components-of-a-pipeline/capsule-settings
---

# Capsule Settings

To open the Capsule Settings, double click on a Capsule or hover over a Capsule and click the gear icon.  It will open the this box:

<figure><img src="https://lh7-us.googleusercontent.com/loNqS1nXydQMbCn1unw5pCFD5jm5Ow3peFBgJNBYUjaM8StxleiC1dbCSsRWPAwMbUdMpDaicLw1t6WgTVwqm5zBaljvgDlyFMQOubuR50Yn3gWANv_5QH81Zgz7V8lbXjk2PT63hQhJC8vuGsXEI5Y" alt=""><figcaption></figcaption></figure>

At the top of the Capsule Settings is the name of the Capsule with an information icon to view the description of the Capsule from the Capsule metadata.  Open the Capsule by clicking Go to this capsule.

## Version

If the Capsule has been released or it is from the Code Ocean Apps Library, there is a dropdown menu to select the version of the Capsule to use in the Pipeline, and a button to Use the Latest Version.  The version used by the Pipeline will remain unchanged if a new version of the Capsule is released.

## Compute Resources

Once a Capsule is added to a Pipeline, it will inherit the resources selected in the Capsule's environment editor. The Capsule Settings menu can then be used to modify the resources allocated to the Capsule, independent of those set in the environment editor.

Each CPU based Capsule can be allocated a maximum of 192 cores and 4096 GB RAM. GPU based Capsules can be allocated a maximum of 8 GPUs, 192 cores and 4096 GB RAM.&#x20;

By default all Capsules will run on dedicated machines. Pipelines can be configured to run on spot instances in the [Pipeline Settings](pipeline-settings.md#instance-type).&#x20;

{% hint style="info" %}
When a power-of-two value (e.g. 8, 16, 32 GB) is requested for Capsule memory, Code Ocean automatically adjusts the value in `main.nf` to 15/16 of the requested amount. This helps optimize resource allocation and avoid unintended higher costs. &#x20;
{% endhint %}

## Arguments

Capsule run script arguments can be entered into the Capsule Settings box for each Capsule.  Arguments must be separated by spaces. If an argument includes a space, such as the title of a plot, it should be in quotes.&#x20;

It is recommended to create an App Panel for the Pipeline rather than supplying arguments. If there is an[ App Panel](../the-pipeline-ui/pipeline-app-panel.md) for the Pipeline, the Arguments section will be disabled.
