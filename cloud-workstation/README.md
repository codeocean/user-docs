---
metaLinks:
  alternates:
    - https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/cloud-workstation
---

# Working in a Cloud Workstation

For development in your Capsule, you can use one of our Cloud Workstations—well-known programming IDEs (integrated development environments) launched with your selected Docker environment and compute resources.<br>

<figure><img src="../.gitbook/assets/image (534).png" alt=""><figcaption></figcaption></figure>

## The Compute Environment for a Cloud Workstation

The system starts an EC2 machine and launches a Docker container using the Capsule's compute environment configured in the Environment Editor. Visit the [Environment](../compute-capsule-basics/structure-of-a-compute-capsule/environment.md) page to learn how to establish the environment. Once the compute environment is established, you will enter the Cloud Workstation with full access to the Capsule.&#x20;

{% hint style="info" %}
In the Cloud Workstation, you work directly within the Docker container. During a Reproducible Run, the system submits your computation to a Docker container, syncs the results folder back to the Capsule, and stops the container once the run is complete.
{% endhint %}

The Cloud Workstation offers a native experience, similar to working locally. For example, you can execute commands in the terminal, or execute a chunk of code in JupyterLab.

<table><thead><tr><th width="186">Folder</th><th width="200">Available in Cloud Workstation</th><th width="179">Path in Capsule Workspace</th><th data-hidden>Available in Reproducible Run</th><th data-hidden>Alternative Path in Computation</th><th data-hidden>Path in Computation</th></tr></thead><tbody><tr><td>Metadata</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>/metadata</td><td><span data-gb-custom-inline data-tag="emoji" data-code="274c">❌</span></td><td>-</td><td>/root/capsule/metadata</td></tr><tr><td>Environment</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>/environment</td><td><span data-gb-custom-inline data-tag="emoji" data-code="274c">❌</span></td><td>-</td><td>/root/capsule/environment</td></tr><tr><td>Code</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>/code</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>/code</td><td>/root/capsule/code</td></tr><tr><td>Data</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>/data</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>/data</td><td>/root/capsule/data</td></tr><tr><td>Results</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>-</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>/restuls</td><td>/root/capsule/results</td></tr><tr><td>Scratch (CW)</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>-</td><td><span data-gb-custom-inline data-tag="emoji" data-code="274c">❌</span></td><td>/scratch</td><td>/root/capsule/scratch</td></tr><tr><td>CW Root FS</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>-</td><td><span data-gb-custom-inline data-tag="emoji" data-code="274c">❌</span></td><td>-</td><td>/</td></tr></tbody></table>

This guide covers the following:

1. [Launching different types of Cloud Workstations](launching-a-cloud-workstation/)
2. [Exiting a Cloud Workstation session](types-of-terminating-a-cloud-workstation.md)

