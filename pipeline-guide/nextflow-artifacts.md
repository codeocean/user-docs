---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/pipeline-guide/nextflow-artifacts
---

# Nextflow Artifacts

After a Pipeline run is completed, Nextflow produces a set of logs and reports. They contain information about the execution of the Pipeline and can serve as a helpful resource for debugging.&#x20;

These files can be accessed from the run context menu by clicking the three dots next to a run in the Pipeline Timeline. Click "Download Artifacts" to download all files.&#x20;



<figure><img src="https://lh7-rt.googleusercontent.com/slidesz/AGV_vUfWySt80ucnUzGf5brY76xsHubYarp-dKHqvW-ukhDnRQKqL7BHsQY966z2eBvWmpMDWxbHXH_1wJp-Ol743kuuKwY8dg6SbBWLaBySJFm2xAG15DDW5j89kf699EWnXnefyzlsMA=s2048?key=t704XGJtpehWmFjyHKYF166v" alt="" width="375"><figcaption></figcaption></figure>

The files are the following:

* **dag.html** - a direct acyclic graph (DAG) visualization of your Pipeline, where the vertices are the Capsule job names and the edges are the data transfer channel names.
* **nextflow.log** - a text file with detailed information about the execution of the Pipeline. This is one of the most comprehensive files and the best place to find specific technical errors that caused a Pipeline to fail.
* **report.html** - an HTML version of nextflow.log. This report has the sections Summary, Resources, and Tasks.  The Summary section reports the execution status, the launch command, overall execution time, and other workflow metadata.  The Resources section plots the distribution of resource usage for CPU, memory, job duration, and disk I/O for each workflow process.  They have two or three tabs with the raw values and a percentage representation showing what proportion of the requested resources were used. These plots are helpful to check that task resources are used efficiently. The Tasks section lists all executed tasks, reporting for each of them the status, the actual command script, and many other metrics.
* **trace.txt** - a text file that contains useful information about each process executed in your Pipeline script, including the run status of each job.

<table><thead><tr><th width="142">Field</th><th>Information provided</th></tr></thead><tbody><tr><td><strong>Task_id</strong></td><td>Task ID.</td></tr><tr><td><strong>Hash</strong></td><td>Task hash code.</td></tr><tr><td><strong>Native_id</strong></td><td>Task ID given by the underlying execution system e.g. POSIX process PID when executed locally, job ID when executed by a grid engine, etc.</td></tr><tr><td><strong>Name</strong></td><td>Task name</td></tr><tr><td><strong>Status</strong></td><td>Task status. Possible values are: COMPLETED, FAILED, and ABORTED.</td></tr><tr><td><strong>Exit</strong></td><td>POSIX process exit status.</td></tr><tr><td><strong>Submit</strong></td><td>Timestamp when the task has been submitted.</td></tr><tr><td><strong>Duration</strong></td><td>Time elapsed to complete since the submission.</td></tr><tr><td><strong>Realtime</strong></td><td>Task execution time i.e. delta between completion and start timestamp.</td></tr><tr><td><strong>%cpu</strong></td><td>Percentage of CPU used by the process.</td></tr><tr><td><strong>Peak_rss</strong></td><td>Peak of real memory. </td></tr><tr><td><strong>Peak_vmem</strong></td><td>Peak of virtual memory. </td></tr><tr><td><strong>Rchar</strong></td><td>Number of bytes the process read, using any read-like system call from files, pipes, tty, etc. </td></tr><tr><td><strong>Wchar</strong></td><td>Number of bytes the process wrote, using any write-like system call.</td></tr></tbody></table>

* **timeline.html** - an HTML timeline with a bar for each process executed in your Pipeline. As each process can spawn many tasks, colors are used to identify those tasks belonging to the same process. The bar length represents the task duration time (wall-time). The colored area in each bar represents the real execution time. The grey area to the left of the colored area represents the task scheduling wait time. The grey area to the right of the colored area represents the task termination time (clean-up and file un-staging). The numbers on the x-axis represent the time in absolute units e.g. minutes, hours, etc. Each bar displays two numbers: the task duration time and the virtual memory size peak.
