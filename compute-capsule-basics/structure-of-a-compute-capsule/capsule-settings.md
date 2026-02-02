---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/compute-capsule-basics/structure-of-a-compute-capsule/capsule-settings
---

# Capsule Settings

The Capsule Settings menu is accessible by clicking the gear icon <img src="https://lh7-us.googleusercontent.com/Ay-niUKpxW8Ue8Qj7AKp7l0fG2OaoO1WWV0oXs6FpLGbNDiRmwZwkzhHGUs-FJKTTqHrXdGrER0nG0D4iuBIlWXWrk1OfOyeALtoJmOJ58G9zz4GovdZx47gL_mDS_t4y9n9pfyVkbgJIBpxg7iso8M" alt="" data-size="line">in the top right of the Capsule UI. The menu contains the following 3 tabs:

1. [Secrets](capsule-settings.md#secrets)
2. [Automation](capsule-settings.md#automation)
3. [MLflow Tracking](capsule-settings.md#mlflow)



## Secrets

Use Secrets or private credentials in Capsules to access required resources without exposing your private credentials to collaborators. Under the **Credentials** tab, Capsule creators can add Secrets to their Capsule, and individual users can attach their own Secrets prior to running the Capsule.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2025-10-21 at 10.14.26 AM.png" alt="" width="375"><figcaption></figcaption></figure>

See [Secrets Management Guide](../secret-management-guide/) for more information on how to create and use Secrets.&#x20;

## Automation

Capsules and Pipelines can be configured with post-run automations. These automations trigger another Capsule to run immediately after a run completes, enabling follow-up tasks such as creating a Result Data Asset, modifying asset sharing permissions, or updating Data Asset metadata. In the **Automation** tab, users can select a Capsule and specify whether it should triggered after every run or only when the initial run is successful. Once configured, these settings apply to all Reproducible Runs of the Capsule initiated from the UI or API.

When the initial run finishes, the Capsule ID, Computation ID, and Exit Code are passed as environment variables to the automation Capsule.

Runs associated with automation will show clear deep linking in the Timeline: "**Open Automation Run**" and "**Automated From**".

<figure><img src="../../.gitbook/assets/Screenshot 2025-10-20 at 2.35.08 PM.png" alt="" width="195"><figcaption></figcaption></figure>

## MLflow

If MLflow is enabled in your Code Ocean deployment, under the **MLflow** tab, users can enable MLflow tracking for their Capsule. Doing so will ensure that models created in that Capsule can be tracked, managed, and deployed using MLflow. &#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2025-10-21 at 11.46.54 AM.png" alt="" width="375"><figcaption></figcaption></figure>

See [MLflow Guide](../../ml-flow/) for more information on Code Ocean's native MLflow integration.&#x20;
