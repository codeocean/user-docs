---
description: >-
  The Pipeline Settings menu provides several options to customize how the
  Pipeline runs.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/pipeline-guide/components-of-a-pipeline/pipeline-settings
---

# Pipeline Settings

The following settings options are described in this guide:&#x20;

1. [Syntax Version: DSL2](pipeline-settings.md#syntax-version-dsl2)
2. [Nextflow Version ](pipeline-settings.md#nextflow-version)
3. [Run with Cache](pipeline-settings.md#run-with-cache)
4. [Config Profiles](pipeline-settings.md#profiles)
5. [Error Strategy](pipeline-settings.md#error-strategy)
6. [Debugging Options](pipeline-settings.md#debugging-options)
7. [Instance Type](pipeline-settings.md#reproducible-run)
8. [Select AWS IAM Role](pipeline-settings.md#select-aws-iam-role)
9. [Secrets](pipeline-settings.md#secrets)
10. [Post-Run Automation](pipeline-settings.md#post-run-automation)

Open the Pipeline Settings menu by clicking the gear icon <img src="https://lh7-us.googleusercontent.com/Ay-niUKpxW8Ue8Qj7AKp7l0fG2OaoO1WWV0oXs6FpLGbNDiRmwZwkzhHGUs-FJKTTqHrXdGrER0nG0D4iuBIlWXWrk1OfOyeALtoJmOJ58G9zz4GovdZx47gL_mDS_t4y9n9pfyVkbgJIBpxg7iso8M" alt="" data-size="line">in the top right of your Pipeline.

<figure><img src="../../.gitbook/assets/Screenshot 2025-10-20 at 2.21.19 PM.png" alt="" width="375"><figcaption></figcaption></figure>

## General

### Syntax Version: DSL2

By default, newly created Pipelines run Nextflow's latest workflow syntax, DSL2. Older Pipelines running DSL1 can be optionally migrated to DSL2 via the Pipeline Settings menu.&#x20;

### Nextflow Version&#x20;

Users can select one of the follow Nextflow versions to run when the `main.nf` file is unlocked: 22.10.8, 23.10.0, or 24.10.4. For more information on unlocking the Nextflow file, see [Nextflow File](nextflow-file.md). For more information on Nextflow versions, see the [Nextflow documentation](https://www.nextflow.io/docs/latest/dsl1.html).

### Run with Cache

This option allows users to configure whether or not the Pipeline should run using cached data from a previous run. By default, the Pipeline runs with cache, which automatically resumes the run from the first step in the Pipeline where a change has been made.

For example, in the Pipeline below, if the Map Paths menu between FastQC and MultiQC has been changed but the inputs and outputs of FastQC have not changed, users can resume the run and the Pipeline will start at MultiQC using the cached output of FastQC. The timeline report of the resumed run is shown below.

<figure><img src="../../.gitbook/assets/Screen Shot 2024-02-20 at 10.55.13 AM.png" alt=""><figcaption><p>The Pipeline's timeline.html shows the Pipeline using the cached outputs of FastQC and only running the MultiQC step again.</p></figcaption></figure>

If users select "Run without cache", the Pipeline will restart from the beginning. However, cached data can still be used for an individual run by selecting "Resume Run" in the dropdown menu of a result in the Timeline.

<figure><img src="../../.gitbook/assets/Screen Shot 2024-02-20 at 11.23.17 AM.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Resuming the most recent run is equivalent to a Reproducible Run when "Run with cache from the previous run" is selected.
{% endhint %}

Performing a Reproducible Run with the cache will search for Pipeline runs with the same data, Capsule, and Map Paths. For the data to be the same, the contents of the Data Asset or local files must not have changed, including the contents of an External bucket, and the mount point (folder name) must be the same. Cached data can be used from any previous run of the Pipeline even if the Pipeline has since been duplicated or other runs have been performed in the meantime. Running with cache of runs that were performed concurrently is best done with the Resume Run button.&#x20;

### Profiles

Available only for custom Pipelines with the Pipeline editor unlocked, users can specify Nextflow config profiles, in a comma-separated list. Profiles are pre-defined settings that tell Nextflow how and where to run your Pipeline.&#x20;

Any profiles used during a run will be recorded in the Timeline and Result Provenance, for traceability and reproducibility.

### Error Strategy

To define a Pipeline's behavior when an error is encountered, users can choose from the following Nextflow error strategies:&#x20;

* **Default**: Your Pipeline will use any error strategy configured in a `nextflow.config` file or in the Nextflow script itself. Otherwise, the default is to terminate the execution.
* **Terminate**: When an error condition is encountered, your pipeline will terminate the execution and pending jobs will be killed.
* **Finish**: When an error condition is encountered, your pipeline will initiate an orderly shutdown, pending the completion of any submitted jobs.
* **Ignore**: When an error condition is encountered, your pipeline will ignore process execution errors.
* **Retry**: When an error condition is encountered, your pipeline will re-submit the process for execution. The user will be able to set the minimum and maximum number of retry attempts.

<figure><img src="../../.gitbook/assets/error strategy.png" alt="" width="467"><figcaption></figcaption></figure>

{% hint style="info" %}
**Maximum number of Retries** is the maximum number of times an individual process instance can be resubmitted.&#x20;

**Maximum number of Errors** is the total errors accumulated for a given process, across all instances.
{% endhint %}

### Debugging Options <a href="#pipelines-automatic-nf-core-app-panel-creation" id="pipelines-automatic-nf-core-app-panel-creation"></a>

Unchecking the "Verbose log" box will hide the terminal output of each process.

## Compute Resource

### Reproducible Run

Users can choose to run the Pipeline using entirely On Demand or entirely Spot instances. The default setting is On Demand, but users can select Spot instances to save on compute resource cost. See [Compute Resources](../../setting-up-the-environment/compute-resources.md) for more information.

### Cloud Workstation

Available for custom Pipelines only, users can select the compute resource for interactive Pipeline development in a Cloud Workstation. See [Compute Resources](../../setting-up-the-environment/compute-resources.md) for more information.

{% hint style="info" %}
The Cloud Workstations are currently for Pipeline development only. Users will not be able to run their Pipelines within this environment.&#x20;
{% endhint %}

## Credentials

### AWS IAM Role

AWS Identity and Access Management (IAM) roles are created in AWS and assigned specific permissions so that Code Ocean (and other trusted identities) can perform actions in AWS. Pipelines run with a default IAM role.&#x20;

If external Data Assets are used in a Pipeline, users must select a role with permissions to access AWS batch and the external data. In addition, Capsules that have AWS credentials as a secret require an IAM role. Admins must define these roles in AWS and provide access through an Identity Provider.

{% hint style="info" %}
Users can view their Assumable Roles in their Account page under **Roles and Secrets.**
{% endhint %}

### Secrets

For Pipelines created through the UI, all Capsule Secrets are automatically listed under the **Credentials** tab. This centralizes secret management, making it easy to view and configure all secrets required for the Pipeline run in one place.

For custom Pipelines, you can add Secrets to your Pipeline to access non-AWS resources. Add Secrets to your Pipeline with the following steps:

1. Click **+ Add secret to Pipeline**, and a drop-down menu that contains the secret list from your account settings page will appear. AWS Cloud credentials will not be listed.&#x20;
2. Select the type of credential you wish to add from the dropdown.
3. Select the secret you wish to attach from the dropdown.

For information regarding additional Secrets actions, visit the [Secrets Management Guide](../../compute-capsule-basics/secret-management-guide/attaching-a-secret-to-a-capsule.md).&#x20;

## Automation

### Post-Run Automation

Capsules and Pipelines can be configured with post-run automations. These automations trigger another Capsule to run immediately after a run completes, enabling follow-up tasks such as creating a Result Data Asset, modifying asset sharing permissions, or updating Data Asset metadata.

In the **Automation** tab, users can select a Capsule and specify whether it should triggered after every run or only when the initial run is successful. Once configured, these settings apply to all Reproducible Runs of the Pipeline initiated from the UI or API.

When the initial run finishes, the Capsule ID, Computation ID, and Exit Code are passed as environment variables to the automation Capsule.

Runs associated with automation will show clear deep linking in the Timeline: "**Open Automation Run**" and "**Automated From**".

<figure><img src="../../.gitbook/assets/Screenshot 2025-10-20 at 2.35.08 PM (1).png" alt="" width="195"><figcaption></figcaption></figure>
