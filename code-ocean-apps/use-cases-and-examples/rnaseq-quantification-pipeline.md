---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/code-ocean-apps/use-cases-and-examples/rnaseq-quantification-pipeline
---

# RNASeq Quantification Pipeline

This RNASeq Pipeline aligns sequencing reads (single or paired end), sorts and indexes the alignment (.bam), counts features, and conducts a differential gene expression analysis.

The Pipeline uses the following four Apps Library Capsules:&#x20;

1. STAR Alignment
2. Sambamba Sort & Index
3. FeatureCounts
4. DESeq2

## Creating Prerequisite Data Assets&#x20;

Code Ocean has supplied the datasets needed to run the Pipeline on the codeocean-public-data S3 bucket. Create a Data Asset from the public S3 bucket below.  For more details, see [Adding a New Data Asset](../../data-assets-guide/adding-a-new-dataset.md).

1. Example Sequencing Reads

**Bucket Name:** `codeocean-public-data`

**Path:** `example_datasets/Normox`

<div><figure><img src="https://lh7-us.googleusercontent.com/8sOFHfNhEOIm5DJz1omV7n_oQBZCngp1J-Md5LNcUl4hH5_FGLFvzUqYc-O8LZqa2EoLnOaCGH5ZwBvOQgbogKwnTrIiDgu5mzlZ4nDILO4gUlv8XH2iAUEOQplTV40LXjuAvBzgezBxTpNgUVb_h_g" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/Screenshot 2024-01-29 at 11.08.00.png" alt=""><figcaption></figcaption></figure></div>

{% hint style="info" %}
In this example dataset containing reads from different samples, all reads for each sample will be in a separate folder. The Pipeline will pass each folder to the downstream alignment, allowing each sample to process in parallel.
{% endhint %}

2. hg38 Annotation

**Bucket Name** - `codeocean-public-data`

**Path** - `genomes/hg38_Annotation`

<div><figure><img src="https://lh7-us.googleusercontent.com/I-c1uJq3-0pZ6qTFYcFwWjVaLqA6jXdDWc0rkh_NYBalzc0kUYRrNyTc1oJ3205tAWpi3HxLvDXs-ps5SmMSUIToH1UgSq-bkPAc3KEPjDLKROLEbmba4UNYxXgn20GMa1FJB05QvgqHBPvd6euK4k8" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/Screenshot 2024-01-29 at 11.08.22.png" alt=""><figcaption></figcaption></figure></div>

{% hint style="info" %}
Here, we assume the reads are aligning to hg38, but any reference can be used.
{% endhint %}

3. hg38 Star Index

**Bucket Name** - `codeocean-public-data`

**Path** - `example_datasets/STAR_GRCh38_GENCODE_Release_21_Index/star_index/`

<div><figure><img src="https://lh7-us.googleusercontent.com/zsonDSlEKKvldGMAhC6CA06yRJpXAKuyZI-u6ZcP4oQ7Q2Aw0vLrwVVHI_UeOVg9kTdlsJ9FrGnUbxe8gtINuXgfFDtvrudNULO4ByWDmtPgODZ9EUz5caI04hN6iBGMgsuTyXSsNvS-wpwGuLippD8" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/Screenshot 2024-01-29 at 11.08.42.png" alt=""><figcaption></figcaption></figure></div>

{% hint style="info" %}
In order to create a reference for a different genome,  visit the **STAR Generate Genome Index Capsule** in the Apps Library and follow the README to create a compatible index for STAR.
{% endhint %}

## Create a Pipeline

<figure><img src="../../.gitbook/assets/Screen Shot 2024-02-07 at 12.14.51 PM.png" alt=""><figcaption></figcaption></figure>

### Attach Data Assets

* Click **Manage Data Assets**
* Attach STAR Index, Annotation, and Example Sequencing Reads Data Assets.&#x20;

<div><figure><img src="https://lh7-us.googleusercontent.com/Q8aUtBvEh54SNskbwFYU4AtMb1joR4tM_VcdOwO-xF72VecZJOVMjH57ILQCUOkzJ9T_J2zU71yj0ishcVFQG0kL1Hs-kEWdVqioQZ1Si4G3-8QEgNjOSkee9EHmpId9B5CUgnlDAn0E9YTsdzAzfnE" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/Screenshot 2024-01-29 at 11.09.31.png" alt=""><figcaption></figcaption></figure></div>

### Design Matrix

The design matrix specifies metadata associated with the samples, i.e. tumor vs normal, tissue type, etc. In order to create the design matrix:

1. Create a Folder named **DesignMatrix**
2. Create `metadata.csv` with the following 3 columns:
   * Run
   * Condition
   * Batch

**Run** should match the prefix for the .bam file output for the sample. **Condition** and **Batch** should indicate any metadata conditions to take into account to differentiate the samples in DESeq2.

<div><figure><img src="https://lh7-us.googleusercontent.com/RZmVX_zvxVRY-hgMvLL9ZYEn04Alq8PwXtZGHgU3dtOshq2rdi6lBveNpiXV6lQ4CmPwngruQKHa23OXtktDwYv0i2D7f_a85t4_aZiDcZiiDaYllcvfpTlz_buxWQhNaL7hNEzhEy1u9puTMmv3m80" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/Screenshot 2024-01-29 at 11.09.55.png" alt=""><figcaption></figcaption></figure></div>

### Assemble Pipeline

Add the following Code Ocean Apps Capsules to the Pipeline Builder area:&#x20;

* STAR Alignment
* Sambamba Sort & Index
* FeatureCounts
* DESeq2

### Configure Connections

In order to configure the connection for each step:

1. Click **Settings** ![](../../.gitbook/assets/Gear.png)
2. **Reads** **Dataset** to **STAR Alignment** is set to **Default.**
3. **HG38 Star Index** to **STAR Alignment** is set to **Collect.**
4. **STAR Alignment** to **Sambamba Sort & Index** is set to **Default.**
5. **Sambamba Sort** & **Index** to **FeatureCounts** is set to **Collect.**
6. **Annotation Data Asset** to **FeatureCounts** is set to **Default.**
7. **FeatureCounts** to **DESeq2** is set to **Default.**
   * Set the destination to **Counts\_data.**

<figure><img src="../../.gitbook/assets/Screenshot 2024-01-29 at 11.12.00.png" alt=""><figcaption></figcaption></figure>

7. Create and attach DesignMatrix - `metadata.csv` to DESeq2.&#x20;
   * Select Connection to **Default,** set the destination to **Counts\_data.**

<figure><img src="../../.gitbook/assets/Screenshot 2024-01-29 at 11.12.37.png" alt=""><figcaption></figcaption></figure>

### Completed Pipeline&#x20;

<figure><img src="../../.gitbook/assets/Screen Shot 2024-02-07 at 1.59.56 PM.png" alt="" width="361"><figcaption></figcaption></figure>

### Configure App Panel

On the App Builder tab, click Create App.  Click Create App again if prompted. Click Finish.

<div><figure><img src="https://lh7-us.googleusercontent.com/k395SPqV7lwqFTdC_Wglgclk9N9VsWOfvpoW8JbZPjXkszBaAIXKQVM5oMEJ0gCiwFERzCCTYg_fizSdfSucSjn1_zmrTGkNSZwYI9sgn8h8l_N07SbmoIPdEJJd-gflzw5ONnqxEVXQKYoCr1MKLyc" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/GIF Recording 2024-02-07 at 2.49.39 PM.gif" alt=""><figcaption></figcaption></figure></div>

### Parameters

Configure the App Panel as follows.&#x20;

Reference READMEs in Capsules to find out more about the parameters used.&#x20;

<figure><img src="../../.gitbook/assets/Screen Shot 2024-02-08 at 12.39.33 PM (2).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screen Shot 2024-02-08 at 12.41.12 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screen Shot 2024-02-08 at 12.41.29 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screen Shot 2024-02-08 at 12.41.43 PM.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The DESeq2 “Design formula” is based on the columns supplied in the design matrix.&#x20;
{% endhint %}

### Results

<div><figure><img src="https://lh7-us.googleusercontent.com/E6kXuwU0Z8c81EiF7W6aR2HhRX58I4YjBkVwmYbEPFzboKkyd7beDkBB3PmK_6sumwrFpiqQBtwBVTepD-su6Z5s-mdtdJXc5WzJ3ZnFlv10d75uX1CiDBqJRJgHtxhLfTsvIEY91wVCuvUvUHnc1II" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/Screen Shot 2024-02-08 at 1.03.19 PM.png" alt=""><figcaption></figcaption></figure></div>

* nextflow
  * Consists of logs describing actions of nextflow.
* DESeq2\_results.csv&#x20;
  * .csv file with the results table.
* MA\_plot.png
  * MA plots display a log ratio (M) vs an average (A) in order to visualize the differences between two groups. In general, we expect the expression of genes to remain consistent between conditions, so the MA plot should be similar to the shape of a trumpet with most points residing on a y intercept of 0.
* PCA.png
  * Visualize how the samples group by treatment.
* volcano\_plot.png&#x20;
  * The volcano plot enables it to simultaneously capture the effect size and significance of each tested gene.
* plots\_by\_gene
  * A folder containing a file for each gene that plots the normalized counts for a single gene to get an idea of what is occurring for that gene across the sample cohort.
