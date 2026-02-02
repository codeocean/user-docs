---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/compute-capsule-basics/structure-of-a-compute-capsule/code
---

# Code

The `/code` folder contains all the scripts used in a Capsule. You can add files or folders to the `/code` folder in the following ways:

* **Add via File Navigator:** Use the **plus signs** at the top of the File Navigator.
* **Upload from Local System:** Use the drop-down menu to drag and drop code files or folders from your local computer into the `/code` folder.

<figure><img src="../../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>

## **The Code Folder and Reproducible Runs**

* For reproducibility purposes, files written to the `/code` folder during a Reproducible Run are deleted once the run is completed.&#x20;
* A `run` file (i.e., driver script) is the entry point into the Capsule during a Reproducible Run, and automates an end-to-end workflow.

<figure><img src="../../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The key file paths to know for use in your Capsule code are `/code` , `/data` , `/results` , and `/scratch`. These paths correspond to the workspace panes:

* code
* data&#x20;
* results
* scratch
{% endhint %}

## Best Practices for Paths

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

## Editing files

Code Ocean supports multi-line editing for efficient code management.

* **To create a multi-line cursor:**
  * **Mac:** Hold **Option** and click to place additional cursors.
  * **Windows:** Hold **Ctrl+Alt** and click to place additional cursors.
* **To return to a single cursor:** Press **Escape**.
