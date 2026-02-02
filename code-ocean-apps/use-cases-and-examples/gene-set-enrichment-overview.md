---
description: Introduction to the Gene Set Enrichment Analysis (GSEA) Capsule.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/code-ocean-apps/use-cases-and-examples/gene-set-enrichment-overview
---

# Gene Set Enrichment Overview

<div><figure><img src="https://lh7-us.googleusercontent.com/E8jRbpeyBk4ayRb9BW3_YVvfLxMAYW4VKf_IHFizxZbtQQod2YfwFGEX1sr_Ssv8qKk8Z-uvVdBN5EdzzHi8oIOMeMLOvy0IzJuNjpc26B1ROVQyV-6RU3rldvLzf2UR0raNZLa0JhI-J-ZcY62cDHY" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/Screenshot 2024-01-29 at 11.03.10.png" alt=""><figcaption></figcaption></figure></div>

This Streamlit application streamlines Gene Set Enrichment Analysis (GSEA) for experimental biologists, enhancing their ability to interpret genome-wide expression data (see [Gene set enrichment analysis: A knowledge-based approach for interpreting genome-wide expression profiles](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC1239896/) for more details). The application speeds up processing using parallel computation and employs statistical methods like the Fisher's Exact Test, Hypergeometric Test, and Chi-Squared Test to calculate P-values. It also adjusts these values for false discovery rates using the Benjamini-Hochberg correction. The application presents its findings through interactive charts and bar graphs, providing users with a clear and direct visual representation of significant gene sets and their associated biological pathways. This approach makes complex data analysis more accessible and easier to understand.

The application includes Gene Ontology libraries for Biological Processes, Cellular Components, and Molecular Functions from [Human MSigDB Collections](https://www.gsea-msigdb.org/gsea/msigdb/human/collections.jsp) to reduce the need for manual input and accelerate the analysis process. Gene Ontology is used for annotation as it is widely recognized and commonly used due to its comprehensive yet user-friendly structure. It provides a standardized vocabulary for describing gene roles across various biological entities.

### Running GSEA in Code Ocean

1. Duplicate **Gene Set Enrichment Analysis (GSEA)** from the **Apps Library**.

<div align="left"><figure><img src="https://lh7-us.googleusercontent.com/ZtBzAjqy8E5DOiY6K2RKa3FOblwBcBiad2ql3MpzXjoS1M5hEZbs0tcKXt4SEA-RIe8Btl5Curoh4vK20q-4-ULadtNEK6uTSTFsrCMr0Vj9byKvleIjOV2ogw5d_v0AsptdtDg4Z9eZTJfXbOQbhzc" alt="" width="188"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/Screenshot 2024-01-29 at 11.03.43.png" alt="" width="339"><figcaption></figcaption></figure></div>

<div><figure><img src="https://lh7-us.googleusercontent.com/FjZAahaHO9dgDHTg9xePywyTUY02yTXgJQpP0djDRtzD3wRHVmu7-aSua5kOI1-BrD7QdhfV7Weq5ddh-PbACLMLXU9faliK_zH75Pk8JZ-dQlrVT4882gn8qP2B1IBXiAYe1GdjUZkz-xMhXrSNj5Q" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/Screen Shot 2024-02-07 at 10.19.44 AM.png" alt=""><figcaption></figcaption></figure></div>

2. Once in the Capsule, launch the **Streamlit** App from the Cloud Workstation panel.

<figure><img src="../../.gitbook/assets/Screen Shot 2024-02-06 at 3.42.01 PM.png" alt=""><figcaption></figcaption></figure>

### Using the GSEA Application

#### Analysis

Once the Application has launched, you will be be presented with two tabs at the top:&#x20;

**Analysis** and **Advanced Settings**

Begin using **Analysis**.

<div><figure><img src="https://lh7-us.googleusercontent.com/E8jRbpeyBk4ayRb9BW3_YVvfLxMAYW4VKf_IHFizxZbtQQod2YfwFGEX1sr_Ssv8qKk8Z-uvVdBN5EdzzHi8oIOMeMLOvy0IzJuNjpc26B1ROVQyV-6RU3rldvLzf2UR0raNZLa0JhI-J-ZcY62cDHY" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/Screenshot 2024-01-29 at 11.05.07.png" alt=""><figcaption></figcaption></figure></div>

1. In the **Input a gene set name** field, enter a name for the gene set.
2.  Below that, you have two options to input the gene set:

    \
    **Test Input:** Paste a newline-separated list of gene names directly into the provided text box.

    **File Selection:** Click the "**Select...**" dropdown to upload a gene list from the local data folder.
3. Select the **Background Gene Set** by clicking the dropdown and choosing the appropriate set of genes (e.g., HGNC symbols for Homo sapiens) that will be used for validation and reference during the enrichment analysis.
4. Use the **Select Libraries** dropdown to choose the gene set libraries against which the input set will be analyzed.
5. Once you've inputted the gene set and made the selections, click on **Validate and Submit** to proceed with the analysis.

#### Advanced Settings (Optional)

<div><figure><img src="https://lh7-us.googleusercontent.com/RnrDSq-1xIpg_0IrcsrRl5Ajbxa7t5pFfn1NBD-ZhGGkalH6S1ZiCdWZdJ8YrNgs1VtdZ7OVf6QBAwcEAaG2Fqo4OirrqYJxW5JHLwbjyBURct5dV46ElUBGz4fUTLv15MezF6hfNwoghKvFTd7v7N4" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/Screenshot 2024-01-29 at 11.05.42.png" alt=""><figcaption></figcaption></figure></div>

1. Choose the number of results you want to display by adjusting the slider under **Number of results to display**.
2. Select the P-value calculation method from the dropdown menu. Options include Fisher's Exact test, Hypergeometric test, and Chi-Squared test.
3. You can upload the background gene set and gene set libraries by dragging and dropping files into **Upload your background gene set** or **Upload gene set libraries**.

### Saving Results

Once the analysis is complete, you can view the results in the interactive chart and bar graph.

Use a link on top of the results pane to save all library results in a single TSV file for a consolidated record. To save the results from each gene set library in TSV or JSON format, use links provided under results for each library.

All the results and metadata will be automatically saved as a json file in the **results** folder. The files will be named with the input gene set name and a time stamp for convenient access and future reference.

### Reviewing the Analysis

After completing the analysis, the application displays a table that details the term name, P-value, FDR, and gene overlap size for the top ten results in each library. Additionally, the application provides a bar chart, plotted on a −log₁₀(p‐value) scale, to offer users a straightforward overview of the enrichment results.

<div><figure><img src="https://lh7-us.googleusercontent.com/1K6reRdlTE7-38tFbfjFB_wKTy3CiFEQFXNgHZI57QNTSX13SafYwvT5eYJTIf92JGboQLlXfVIo8oNEaj2nYVzEG8utjzqF-DQHizYVGQyACIiQxEUDMBu57kZP_68pFYYrXoZ63If0X47TRAKhsC8" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/Screenshot 2024-01-29 at 11.06.54.png" alt=""><figcaption></figcaption></figure></div>

<div><figure><img src="https://lh7-us.googleusercontent.com/dJ9cnuQr8J7osXO2ExYyxs0cRptfYzklKm12jfE8lhm4XWCJ7vmEAk7o0bbNmrvOn6zOV5LjvAqVVwKzQLsTTdat-sjM65XoZl3ye9hQQzz4VQ2sebm8zBwAcUcS1pfIfRxOZalkNiWMyzGl_1IzNh8" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/Screenshot 2024-01-29 at 11.07.02.png" alt=""><figcaption></figcaption></figure></div>

You can adjust the number of results displayed or re-run the analysis with different parameters or P-value calculation methods by returning to the "[Advanced settings](gene-set-enrichment-overview.md#advanced-settings-optional)" tab.
