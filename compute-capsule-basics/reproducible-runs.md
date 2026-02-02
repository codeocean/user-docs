---
description: >-
  In order to perform a Reproducible Run from the Capsule IDE, the environment
  must be built and the run file must specify which script the Capsule should
  run.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/compute-capsule-basics/reproducible-runs
---

# Reproducible Runs

## Run File

The `run` file, often referred to as the **driver script**, is a bash script that generates all desired results in an automated manner without requiring human intervention. By eliminating manual input, the run file ensures consistent and reproducible results. During a Reproducible Run, the run file is executed from start to finish.

### Setting up Run File

To designate a file as the run file in a Capsule:

1. Hover over the first script to run in the Capsule.
2. Click the drop-down menu that appears on the file.
3. Select **Set as File to Run.**

<figure><img src="../.gitbook/assets/image (39).png" alt="" width="279"><figcaption></figcaption></figure>

This action creates a `run` script that serves as your main shell script. You can modify this file as needed to orchestrate your analyses.

### Properties of a good Run File <a href="#what-makes-a-good-master-script" id="what-makes-a-good-master-script"></a>

A well-designed run file should meet the following criteria:

1. **Run Headlessly:** The script should execute without requiring user input or displaying pop-ups during runtime.
2. **Perform Minimal Actions:** The run script should perform a very small number of actions, such as pointing to another script in the Capsule.

## Executing a Reproducible Run

The **Reproducible Run** button is located at the top of the Reproducibility Panel, above the Timeline.

Once you click on it, the system will prepare the machine to run your computation. The files will be temporarily locked and show the computation progress information on the Reproducibility Panel.

![](<../.gitbook/assets/image (500).png>)

You can stop the run by clicking on the **Stop Run** button. For more information, see [Stop Computation after Run Step](reproducible-runs.md#stop-computation-after-run-step). When the run is complete you are returned to the **Timeline** where the results of the run are displayed, whether it was successful or not.

<figure><img src="../.gitbook/assets/image (40).png" alt="" width="279"><figcaption></figcaption></figure>



{% hint style="info" %}
To view more information about a specific run, select **Run Details** from the drop-down menu in the Reproducibility pane.

![](<../.gitbook/assets/Screenshot 2025-04-10 at 1.30.13 PM.png>)
{% endhint %}

### Closing the browser tab during a run

Reproducible Runs are designed to persist even if the browser tab is closed. To check ongoing computations:

1. Navigate to the **My Capsules** dashboard.
2. Look for Capsules with a "running" status.
3. Click on the Capsule to view the ongoing process.

<figure><img src="../.gitbook/assets/Screen Shot 2024-02-07 at 10.05.36 AM.png" alt=""><figcaption></figcaption></figure>

## Availability of Files during Reproducible Run

<table><thead><tr><th width="153">Folder</th><th width="204">Available in Reproducible Run</th><th width="243">Path in Computation</th><th>Alternative Path in Computation</th><th data-hidden>Available in Cloud Workstation</th><th data-hidden>Path in Capsule Workspace</th></tr></thead><tbody><tr><td>Metadata</td><td><span data-gb-custom-inline data-tag="emoji" data-code="274c">❌</span></td><td>/root/capsule/metadata</td><td>-</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>/metadata</td></tr><tr><td>Environment</td><td><span data-gb-custom-inline data-tag="emoji" data-code="274c">❌</span></td><td>/root/capsule/environment</td><td>-</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>/environment</td></tr><tr><td>Code</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>/root/capsule/code</td><td>/code</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>/code</td></tr><tr><td>Data</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>/root/capsule/data</td><td>/data</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>/data</td></tr><tr><td>Results</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>/root/capsule/results</td><td>/results</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>-</td></tr><tr><td>Scratch (CW)</td><td><span data-gb-custom-inline data-tag="emoji" data-code="274c">❌</span></td><td>/root/capsule/scratch</td><td>/scratch</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>-</td></tr><tr><td>Scratch (RR)</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>/root/capsule/scratch</td><td>/scratch</td><td><span data-gb-custom-inline data-tag="emoji" data-code="274c">❌</span></td><td>/scratch</td></tr><tr><td>CW Root FS</td><td><span data-gb-custom-inline data-tag="emoji" data-code="274c">❌</span></td><td>/</td><td>-</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>-</td></tr></tbody></table>

### Referring to Files During a Run

* **Use Relative Paths:**
  * Simplify portability by using relative paths (e.g., `../data` or `../results`) wherever possible. This ensures ease of use for those running the code locally.
* **Working Directory:**
  * The initial working directory is `/code` when your code is executed. Avoid referencing `/code` explicitly by relying on relative paths instead.
* **Subfolders:**
  *   When referencing files in subfolders, use relative paths such as:

      ```
      load('../../data/my_data.csv')
      ```
  * This example navigates up two parent directories to locate `./data/my_data.csv`.

## Concurrent Runs

You can use the **Back to Timeline** button at the top of the Reproducibility Panel to return to the Capsule Timeline and execute another run concurrently.

![](<../.gitbook/assets/image (415).png>)

In the image below, there are two computations running at the same time. While computations are running, progress information is displayed in the Reproducibility Panel, and you can switch between runs by selecting **View Run Details** for any ongoing run in the Capsule **Timeline**.

<figure><img src="../.gitbook/assets/image (43).png" alt="" width="275"><figcaption></figcaption></figure>

{% hint style="info" %}
Concurrent runs can be on either Flex or Dedicated machines.
{% endhint %}

The output displayed after a run will be for the second of the two concurrent runs. The run output can be switched between concurrent runs in the console by clicking **View Output**.

## Stop Computation after Run Step

A computation can be stopped during a post-run step, such as results collection during a Reproducible Run or syncing back to the Capsule after a Cloud Workstation session. This functionality is particularly useful for saving time by skipping steps that may not be necessary, such as collecting results that are no longer required.

### **Warnings**

Before stopping a computation, a warning is displayed to highlight the consequences of stopping the run:

* **Reproducible Runs:**
  * Stopping a run will result in the loss of all generated results.
* **Cloud Workstation Sessions:**
  * Any unsaved changes to the Capsule or its environment will be discarded.
