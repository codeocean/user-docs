---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/cloud-workstation/launching-a-cloud-workstation/running-rshiny-in-code-ocean
---

# Running RShiny in Code Ocean

Interactive web applications can be created and shared in R (using the `shiny` library) with the **Shiny Cloud Workstation**.

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-20 at 12.27.52 AM.png" alt="" width="375"><figcaption></figcaption></figure>

To automatically load a Shiny app when opening the **Shiny Cloud Workstation**, ensure the appropriate Shiny files (`server.R` and `ui.R`) are placed in the root of the `/code` folder. These files cannot be located in subdirectories.

<figure><img src="../../.gitbook/assets/Screen Recording 2024-02-20 at 12.26.57 AM.gif" alt=""><figcaption></figcaption></figure>

If the `shiny.R` and `ui.R` files are in nested subdirectories within the `/code` folder, upon opening the **Shiny Cloud Workstation** the contents of `/code` will be listed with hyperlinks to all files and folders. To load your Shiny app in this case, navigate to the folder containing your Shiny app files and click to open the app.

<figure><img src="../../.gitbook/assets/Screen Recording 2024-02-20 at 12.29.10 AM (1).gif" alt=""><figcaption></figcaption></figure>
