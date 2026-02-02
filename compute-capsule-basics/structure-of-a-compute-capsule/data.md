---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/compute-capsule-basics/structure-of-a-compute-capsule/data
---

# Data

The `/data` folder contains files used as input for computations and serves as a central repository for managing data within a Capsule. The `/data` folder supports uploading files directly or using Data Assets for reproducibility and collaboration.

For reproducibility, any files written to the `/data` folder during a Reproducible Run are deleted once the run is complete.

## Recommended Practices for Data Usage and Storage

It is best practice to use **Data Assets** to store and manage data files. Data Assets facilitate sharing data across the organization and internal Data Assets guarantee reproducibility. See the [Data Asset Guide](../../data-assets-guide/) for more information. For small datasets, it is possible to upload data files and subfolders directly to the `/data` folder but this is not recommended.

<figure><img src="../../.gitbook/assets/image (37).png" alt="" width="375"><figcaption></figcaption></figure>

Below are properties of data depending on the location and type of Data Asset.

<table data-full-width="false"><thead><tr><th width="108">Folder</th><th width="172.6153846153846">Type of Dataset</th><th width="147.44818652849742">Shareability</th><th width="479">Recommended Usage</th></tr></thead><tbody><tr><td>Data</td><td>local (directly upload to Capsule)</td><td>Only current Capsule</td><td>Small or example dataset to test the capsule</td></tr><tr><td>Data</td><td>Internal Dataset</td><td>Across Capsule</td><td>The Data Asset will be saved in VPC's AWS storage. Works well with immutable data that only need to import to Code Ocean's VPC once.</td></tr><tr><td>Data</td><td>External Dataset</td><td>Across Capsule</td><td>The Data Asset will need an AWS credential to access. Works well with a confidential Data Asset. Data Asset can be changed if the source is changed.</td></tr><tr><td>Scratch (CW)</td><td>local (created in the Capsule)</td><td>Only current Capsule</td><td>Access this only in the Cloud Workstation for storing the intermediate large Data Asset/output file. Usually will be converted into an internal Data Asset for sharing across the capsule and for downstream analysis.</td></tr><tr><td>Scratch (RR)</td><td>local (created in the Capsule)</td><td>Only current run</td><td>Temporary storage during Reproducible Run for large data that might exceed the Capsule's size limit.</td></tr></tbody></table>
