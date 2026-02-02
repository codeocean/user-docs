---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/setting-up-the-environment/starter-environment
---

# Selecting a Starter Environment

## Navigate to the Environment Editor

Click the `/environment` folder to open the Environment Editor. Code Ocean uses Docker as the underlying tool to build and preserve the Capsule environment. When adding a package, the Environment Editor writes the information to a Dockerfile in the `/environment` folder.

<figure><img src="../.gitbook/assets/capsule_env_dockerfile.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Any edit made in the `/environment` folder triggers a change in the Dockerfile, which **could result in a complete rebuild** of the Docker image during a subsequent Reproducible Run or Cloud Workstation session. The wait time for the Docker image rebuild varies according to the number and complexity of packages installed.
{% endhint %}

## Selecting a Starter Environment

The first step when setting up the computational environment is to select a Starter Environment, (also known as a Docker base image). The Environment Editor lists all the Starter Environments available and allows you to search by name, version, language, and tags.

{% hint style="info" %}
In addition to determining the base software and package managers that will be available in the Capsule, the Starter Environment also determines if GPU or CPU Compute Resources will be available from within the Capsule. You can learn more about Compute Resources [here](compute-resources.md).
{% endhint %}

If the Starter Environment has multiple versions, the latest version will be displayed by default and you can click the version dropdown to choose a different version.

<figure><img src="../.gitbook/assets/choose_env.png" alt=""><figcaption></figcaption></figure>

Click **Select** to choose the Starter Environment.&#x20;

You can view all of the packages installed in a Starter Environment by clicking the drop-down menu to expand/collapse the package managers that were installed. Click on a package manager to open an information box listing the packages installed via that package manager along with their version numbers.&#x20;

![](../.gitbook/assets/env_packages.png)

![](https://docs.codeocean.com/~gitbook/image?url=https:%2F%2F1603030414-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252Fa5AT4eq2XLAGmfb36GJm%252Fuploads%252FTJRVWgpwcY0g7YAM3hux%252FGIF%2520Recording%25202024-02-09%2520at%25201.37.53%2520PM.gif%3Falt=media%26token=239f0363-d54d-4522-91b6-a97825de27bb\&width=768\&dpr=4\&quality=100\&sign=c1e46590d2c0ecd8a43a928c2a036b2a9ab5bb7eb89abd2470c20d98fbe43b93)

## Considerations When Choosing a Starter Environment

* **When not using a pre-installed language**, use a base Ubuntu (16.04,18.04,20.04) environment.
* **When proprietary software**, such as MATLAB or Stata is required, begin from an environment with the proprietary language.
* **When using a GPU**, select an environment with GPU access. These are labeled accordingly, or will reference CUDA or a deep learning framework. You can easily filter for GPU Starter Environments by typing "GPU" in the search box.

## Starter Environments for Specific Cloud Workstations

If you would like to work in a Cloud Workstation, it may be required to choose a Starter Environment which supports that Cloud Workstation. Below is a guide to the available Cloud Workstations and their compatible programming languages and Starter Environments.

| Cloud Workstation                                         | Compatible Language | Note                                                                         |
| --------------------------------------------------------- | ------------------- | ---------------------------------------------------------------------------- |
| Terminal                                                  | all                 |                                                                              |
| Jupyter Lab/ Jupyter Notebook                             | mostly Python       | <p>You can install other kernels and <br>use different languages</p>         |
| RStudio                                                   | R                   |                                                                              |
| MATLAB                                                    | MATLAB              | View the information box below for more detail.                              |
| Code-Server (VSCode)                                      | all                 |                                                                              |
| <p>Ubuntu Desktop (IGV, </p><p>Pytorch Desktop, etc.)</p> | all                 | Requires use of Ubuntu Desktop Starter Environment                           |
| Shiny                                                     | R                   |                                                                              |
| IGV                                                       | all                 | Requires use of Starter Environment with IGV installed (i.e. Ubuntu Desktop) |
| Streamlit                                                 | Python              |                                                                              |

{% hint style="info" %}
The MATLAB Cloud Workstation is a MATLAB interface that requires specific licenses and configurations set up in a MATLAB Starter Environment. To use the Matlab Cloud Workstation, you must choose MATLAB as your Starter Environment.

You need MATLAB credentials for executing Reproducible Runs and entering the Cloud Workstation. Visit [this article](../cloud-workstation/launching-a-cloud-workstation/using-matlab-in-code-ocean.md) for more details.
{% endhint %}

### Dockerfiles In Code Ocean&#x20;

When you first select your Starter Environment, a Dockerfile will be created in your `environment` folder. This file contains all the necessary commands that will be used to build your custom environment in your Capsule during computations. As more packages are added via the Environment Editor they will be synchronously added to the Dockerfile.

![](<../.gitbook/assets/dockerfile (1).png>)

To manually customize your Capsule environment you can open the Dockerfile and unlock it. This is not recommended as it will permanently disable the Environment Editor and all subsequent changes to the environment will need to be made through the Dockerfile.

<figure><img src="../.gitbook/assets/unlock.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/env_editor_disabled.png" alt="" width="563"><figcaption></figcaption></figure>

## Copy the Environment from an Existing Capsule

Click **Select Capsule** for a shortcut to quickly copy the environment from an existing Capsule. This will copy over the Starter Environment, as well as any packages, environment variables, and Post-Install Script. If a Release Capsule is selected, a dropdown list allows you to choose a specific version if multiple versions are available. If a non-Release Capsule is selected, the latest environment will be copied.&#x20;

{% hint style="info" %}
This method is a one-time copy and no link is maintained between Capsule environments.&#x20;
{% endhint %}

<figure><img src="../.gitbook/assets/capsule_env (1).png" alt=""><figcaption></figcaption></figure>

