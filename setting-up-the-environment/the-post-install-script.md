---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/setting-up-the-environment/the-post-install-script
---

# Post-Install Script

The Post-Install script is a customizable bash script used to install complex packages that cannot be installed through a package manager, require building from source, or need a specific order of operations. For these scenarios, use the Post-Install script. This script allows you to execute any command that can run on a Linux system (e.g., `curl`, `unzip`, `tar`, or `git clone`). The script is located below the package managers in the Environment Editor.

![](<../.gitbook/assets/Screen Shot 2024-02-01 at 2.10.24 PM.png>)

Since the Post-Install script runs during the build phase, its commands are only executed once and cached as part of your Capsule's custom environment.

### Important Notes

* **No `sudo` Commands:** Many software installation instructions may include commands like `sudo apt-get install python-dev`. On Code Ocean, `sudo` is neither necessary nor available and should be omitted.
* **Restricted Folder Access:** The Post-Install script cannot access the `/code` or `/data` folders.
* **Working Directory:**
  * The working directory for the Post-Install script is the root directory (`/`).
  * For example, if you create a folder with `mkdir mylibrary`, you can later refer to it as `/mylibrary`.
* **Accessing `/opt`:**
  * The `/opt` folder is accessible during both the Post-Install script execution and reproducible runs.
  * For example, you can Use `/opt` to store source files or downloaded files, configure the package, and then add `/opt` to the `PATH` to make the package available during a Reproducible Run.

**Environment Folder Size Limit:**

* The Environment folder has a 100MB size limit.

<figure><img src="../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>
