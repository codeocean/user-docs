---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/pipeline-guide/pipeline-monitoring/monitoring-dashboard
---

# Monitoring Dashboard

## General Info

The General Info section of the Monitoring Dashboard provides key details about the Pipeline run:

* Computation ID
* Run Name
* Date and timestamp the run was created
* Run duration&#x20;
* User who created the run
* Nextflow version

<figure><img src="../../.gitbook/assets/Screenshot 2025-03-13 at 10.50.57 AM.png" alt=""><figcaption></figcaption></figure>

## Resource Summary

The Resource Summary section displays a real-time summary of the resources used by the Pipeline run.&#x20;

The summary provides information on resources requested, as well as the average resource utilization of tasks that have completed successfully in a run. Checking the box "Include Cache" will include any statistics from a cache of a previous run.&#x20;

* **GPU Time**: Total GPU time across all tasks, calculated as GPUs x execution time. Note that utilization is not available for GPU usage. &#x20;
* **CPU Time**: Total CPU time across all tasks, calculated as CPU cores x execution time.
* **Memory Time**: Total memory usage across all tasks, measured as GBs × execution time.
* **Estimated Cost**: The estimated compute cost of the run, including all tasks and the head node.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2025-03-13 at 10.51.04 AM.png" alt=""><figcaption></figcaption></figure>

## Tasks Status

The Tasks Status section shows the real-time status of your Pipeline's tasks.&#x20;

* **Total** number of tasks.
* **New**: The task has been created, but not yet submitted to an executor.
* **Submitted**: The task has been submitted to an executor, but is not yet running.
* **Running**: The task has been launched by an executor.
* **Cached**: A previous valid execution of the task was found and used.
* **Completed**: The task completed successfully.
* **Failed**: The task failed.
* **Aborted**: The task was interrupted or canceled before completion.

<figure><img src="../../.gitbook/assets/Screenshot 2025-01-30 at 11.04.51 AM.png" alt="" width="563"><figcaption></figcaption></figure>

## Table of Processes

The Processes section displays all processes in the Pipeline run. For Pipelines created using the Builder UI, all processes (Capsules) are listed at the start of the run. For custom Pipelines, the table updates dynamically as the run progresses.&#x20;

An indicator on the left is color-coded based on task status:

* **Blue**: At least one task is running and there are no fails.
* **Orange**: At least one task is running and there has been at least one fail.
* **Green**: All tasks are complete with no fails (cached/succeeded).
* **Red**: All tasks are complete and there is at least one fail.
* **Gray**: All tasks are cached.

Columns on the right show an overview of process status:

* **In progress**: New, submitted, running, and retries.
* **Completed**: Completed and cached.
* **Issues detected**: Failed, aborted, and ignored.

Select a process to open the [Tasks panel](task-details.md) to view detailed task information and status.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2025-01-30 at 11.04.26 AM.png" alt=""><figcaption><p>Table View</p></figcaption></figure>

## Visual Pipeline Monitor

Pipelines created using the Builder UI include an enhanced Visual Pipeline Monitoring view. For these Pipelines, switch between the two views by clicking "Pipeline View" or "Table View".

In addition to the color-coded indicators and process statuses that you get from the Table view, the Pipeline view offers a visual representation of execution progress, giving you a clearer, more intuitive overview of where your Pipeline stands in real time. &#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2025-02-13 at 12.26.54 PM.png" alt=""><figcaption><p>Pipeline View</p></figcaption></figure>
