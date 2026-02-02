---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/data-assets-guide/capturing-a-result/provenance-of-the-result-data-asset
---

# Provenance of the Result Data Asset

The Provenance section of a Result provides a comprehensive record of how a result was generated, ensuring full traceability and reproducibility. Provenance includes a lineage graph, along with a direct link to the Capsule or Pipeline that produced the Result. Additionally, it captures the Computation ID, enabling users to trace back to the exact execution.&#x20;

Users can also view the code version and run script, along with any input Data Assets and parameters that were used in the computation. This detailed provenance information helps users verify, reproduce, and understand the origins of their results with confidence.&#x20;

## Tracking with Lineage Graph

Result Data Assets automatically have a Lineage Graph generated that shows how the results were generated and whether they are reproducible.&#x20;

In the graph, you can see which Capsules, Pipelines and Data Assets were used to produce a particular Results Data Asset. The color coding shows you if/how the final Results can be reproduced, and if a Data Asset can’t be reproduced, you’ll see exactly which step of the process or requisite data are no longer available.

The Lineage Graph can be found in the Provenance box of Result Data Assets indicated with the following badge in the UI: <img src="../../.gitbook/assets/Screenshot 2025-06-19 at 10.00.26 AM.png" alt="" data-size="line">.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2025-01-29 at 1.13.16 PM.png" alt=""><figcaption></figcaption></figure>

### Color Coding

* **Green**: The Capsule(s)/Pipeline(s) and the Data Asset(s) required are versioned and kept on the platform and it is fully reproducible.

<figure><img src="../../.gitbook/assets/Screenshot 2025-06-19 at 9.42.22 AM.png" alt="" width="563"><figcaption></figcaption></figure>

* **Red**: A Capsule, Pipeline, or Data Asset is missing for reproducing the Results Data Asset. You can hover over the Results and see why it's no longer reproducible on the platform.

<figure><img src="../../.gitbook/assets/Screenshot 2025-06-19 at 9.46.39 AM.png" alt="" width="563"><figcaption></figcaption></figure>

* **Yellow**: This Results Data Asset might be reproducible, but it cannot be guaranteed. This happens when a Capsule or Pipeline used to generate this Results Data Asset has not been Released.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2025-06-19 at 9.41.26 AM.png" alt="" width="563"><figcaption></figcaption></figure>

Results of external computations (through the API or other runs of Code Ocean Capsules or Pipelines) will be yellow when they are imported back into Code Ocean.  See [here](../../code-ocean-api/data-asset.md#create-a-result-data-asset-from-external-result) for more information about how to import an external result.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2025-06-19 at 9.49.43 AM.png" alt="" width="375"><figcaption></figcaption></figure>

## Preserve parameters when running with the App Panel

Result Data Assets can be generated from a **Run with Parameters** when using the App Panel. This type of Reproducible Run allows users to execute the Capsule with different parameters without modifying the script. Hence, the code version will not be sufficient to capture the full reproducible process.

**Parameters Values:** The values input to the App Panel are listed in the Provenance section of the Result details to record the parameters used in creating the results.

<figure><img src="../../.gitbook/assets/Screenshot 2025-01-29 at 1.14.18 PM.png" alt=""><figcaption></figcaption></figure>
