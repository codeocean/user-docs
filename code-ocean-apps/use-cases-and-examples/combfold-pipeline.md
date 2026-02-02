---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/code-ocean-apps/use-cases-and-examples/combfold-pipeline
---

# CombFold Pipeline

The CombFold Pipeline predicts the structure of large protein complexes starting from the sequences of chains in their complex (up to at least 18,000 amino acids and 32 subunits).&#x20;

### Pipeline Structure

This Pipeline uses the following three Machine Learning Capsules:&#x20;

1. CombFold - Prepare Fasta
2. Streamlit ColabFold: AlphaFold2 using MMseqs2
3. CombFold - Combinatorial Assembly

The Pipeline will look like the following.&#x20;

<div><figure><img src="https://lh7-us.googleusercontent.com/9BrteyUr_y8jM-PRcUbD6-bKKMnQQu6kRu0LRA9zFlpA2759pI4whG-RBQkGc0fz54RGfYWb5-8mBxS-CKjxe7s4i9KGXxklSs3mOZvz82uOljZay47GyobUJfepP-skT2hX-HRR04SaH33WfZ1Pap0" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/Screenshot 2024-01-29 at 10.57.30.png" alt=""><figcaption></figcaption></figure></div>

### Create Data Assets

Create a "**json**" subfolder inside the `/data` folder and upload a subunit json (json is described in the CombFold capsules README and on [GitHub](https://github.com/dina-lab3D/CombFold#stage-1---defining-subunits)).

You can Create a Data Asset containing the ColabFold Model from the Code Ocean Bucket or download from the [Alphafold Github repository](https://github.com/google-deepmind/alphafold). To use the public bucket, fill in the following information as a new Data Asset:&#x20;

<div><figure><img src="https://lh7-us.googleusercontent.com/yfBbJNRrpf7YOaOf3JX4k32aUb-eE8vTzHxPSBvsfLkK_glBg0aJ1bUNZ0Ru_vkDgiLWphrtWzaHDrXTebDGQJ1kQ-9xcLu5qXnmOsZSAiWTOukpFWIfvI2i2hQkk8iOv70GAbLzgRrv2PhwHFz03wU" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/Screenshot 2024-01-29 at 10.59.18.png" alt=""><figcaption></figcaption></figure></div>

**Bucket Name:** codeocean-public-data

**Path:** models/colabfold

### Attach Data Assets

1. Click Manage Data Assets
2. Attach the **ColabFold Trained Model.**

<figure><img src="../../.gitbook/assets/image (519).png" alt=""><figcaption></figcaption></figure>

3. Drag the **ColabFold Trained Model** Data Asset and the "**json"** folder onto the Pipeline UI.&#x20;

### Create Pipeline

1. Create a Pipeline and add the Capsules from Code Ocean Apps: **CombFold - prepare fasta**, **Streamlit ColabFold: AlphaFold2 using MMseqs2**, **CombFold - Combinatorial Assembly**

<div><figure><img src="https://lh7-us.googleusercontent.com/4T6QSfOsI61PWlV8x4zZRbNbS1UZ-gNhJirb08RG09TmBuMI6UWHpqQqkuQHESECv0nu3Zk9P9X0Kx5fwYVRDwSO4qMWtM7X21X8QHB6OS9rxAEXtqvHFzqsJk9hxSg1wzeB5AKwX3Op0Os-Zqtsqjk" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/Screenshot 2024-01-29 at 11.00.21.png" alt="" width="533"><figcaption></figcaption></figure></div>

2. Connect **CombFold - prepare fasta** to **Streamlit ColabFold: AlphaFold2 using MMseqs2** using Flatte&#x6E;**.** Set the Source to “capsule/results/fasta\_pairs/\*”

<figure><img src="../../.gitbook/assets/image (514).png" alt="" width="563"><figcaption><p>Set Source and Connection type</p></figcaption></figure>

{% hint style="info" %}
Flatten passes each output fasta subunit to be processed in parallel by ColabFold.&#x20;
{% endhint %}

2. Connect **Streamlit ColabFold: AlphaFold2 using MMseqs2** to **CombFold - Combinatorial Assembly** using Collec&#x74;**.** Set the Source to “capsule/results/\*/pdb\_files/\*”

<figure><img src="../../.gitbook/assets/image (515).png" alt="" width="563"><figcaption></figcaption></figure>

{% hint style="info" %}
**Collect** passes all subunits are passed together downstream for assembly.
{% endhint %}

2. Connect "json" using **Default** to both Comb Fold Capsules.
3. Connect "**ColabFold**" to **Streamlit ColabFold: AlphaFold2 using MMseqs2**  using **Collect**. Set “capsule/data/colabfold” as the Destination.
4. \[optional] Connect **CombFold - Prepare Fasta** to **Results**. Set “pipeline/results/pairs” as the **Destination**.
5. \[optional] Connect **Streamlit ColabFold: AlphaFold2 using MMseqs2** to **Results**. Set **"**&#x70;ipeline/results/ColabFold” as the **Destination**.
6. &#x20;Connect **CombFold - Combinatorial Assembly Capsule** to **Results**. Set “pipeline/results/CombFold" as the **Destination**.
7. To run the Pipeline, click **Reproducible Run** in the top right corner of the IDE.

### Viewing Outputs

The protein structure can be viewed in the **CombFold/make\_figure.html** file or it can be viewed using the Mol\* Viewer for PDB Files in the Apps Library.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-29 at 09.21.35.png" alt=""><figcaption></figcaption></figure>
