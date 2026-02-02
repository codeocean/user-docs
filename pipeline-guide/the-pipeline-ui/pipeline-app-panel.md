---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/pipeline-guide/the-pipeline-ui/pipeline-app-panel
---

# Pipeline App Panel

The App Builder tab on the toolbar on the left opens the App Builder. The Pipeline App Builder allows the user to turn their Pipeline into a No-Code App that passes arguments to the command line in each Capsule, and compiles the App Panels from each Capsule in the Pipeline.

To create a Pipeline App Panel, press Create App.  Note that this will deactivate the Arguments box in the Capsule Settings. &#x20;

<figure><img src="https://lh7-us.googleusercontent.com/8_4VXRRaADQytcTQ_jnLX76_CsONstFz7vxHc6dw7-PESJv14C0hNmWXGOiagsY6iHRoijAEV_3K4iIemCmQk6dL_kUIo1wbEBsnMl6rj0h04w1Crd1MQs8IIAmxAREuMGYqpweK3gIvU6uiso8XbLU" alt=""><figcaption></figcaption></figure>

The App Builder has the following sections:&#x20;

1. **General**: Enter an optional App Subtitle and Instructions for App usage.&#x20;
2. **Data**: Attach one or more Data Assets to the Capsule to specify as default data.  These Data Assets can be exchanged for other Data Assets by the user.&#x20;
3. **Parameters**: This section transfers the App Panel from each Capsule to the Pipeline.  The order of Capsules can be changed by reordering the cards. &#x20;
4. **Display Result after Run**: After a run has been performed, the file to display after subsequent runs can be selected.  &#x20;

<div align="center"><figure><img src="https://lh7-us.googleusercontent.com/Arw2qWS03bdFSUfBswOeNUQysYchD4QVc9PJKNAbjcDfRQ9A0bxcRgu2hAi1vEqvlxxXZylOGLwFaUtwdWKIh6G6etG1s114J9oVxeonyyIwkF5DqD4C7uXIBx426W1CjNNdqoAkPAYsJMqZbpbvjlw" alt=""><figcaption></figcaption></figure></div>

Once the Pipeline App Panel has been created, you will then be able to name the App, attach default Data Assets (e.g., a human reference genome or annotations), rearrange parameters grouped by Capsules, and save the App.

An example of a completed App Panel for a Pipeline with two Capsules, FastQC and MultiQC is below. Note that the parameters are grouped by Capsule.&#x20;

<figure><img src="https://lh7-us.googleusercontent.com/saGqClBqEQwciWAKj6z6SpyVybjIGnog6mLWHwtImLYcbYJ6rrk8jPuoJ5O2Fv3czxDzM0XaCZvpGegGcbo9Jon8fouHAFPj_Klh4APLyfKPzmoabDhVRvVJA2tiRRTo2N7F7DPe9FIG-Xav-_t7Bw8" alt="" width="188"><figcaption></figcaption></figure>

{% hint style="info" %}
An App Panel will be automatically created from a `nextflow_schema.json`  file when one is detected in the Pipeline.&#x20;
{% endhint %}
