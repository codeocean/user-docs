---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/cloud-workstation/launching-a-cloud-workstation/using-matlab-in-code-ocean
---

# Using MATLAB in Code Ocean



### Adding MathWork Credentials&#x20;

To use MATLAB Web Desktop in a Cloud Workstation, ensure your MathWorks user credentials are configured in your account. These credentials are required to access MATLAB via a Reproducible Run.

|                                                                                                                                                   |                                                                                                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| <p></p><p>1. Click the <strong>Account</strong> icon at the bottom left of Code Ocean.</p>                                                        |                                                          ![](<../../.gitbook/assets/Screenshot 2024-02-29 at 5.25.14 PM.png>)                                                          |
| <ol start="2"><li>In the top right of the "Credentials" page, click "Add Credentials" -> "MathWorks Credentials".</li></ol>                       | <p><img src="../../.gitbook/assets/Screenshot 2024-02-29 at 5.22.37 PM.png" alt=""></p><p><img src="../../.gitbook/assets/Screenshot 2024-02-29 at 5.22.44 PM.png" alt=""></p><p> </p> |
| <ol start="3"><li>Enter your MATLAB username and password and click "Add Credential" to add your MathWorks Credentials to your account.</li></ol> |                                                          ![](<../../.gitbook/assets/Screenshot 2024-02-29 at 5.22.50 PM.png>)                                                          |

### Using the MATLAB Cloud Workstation

Click the MATLAB icon in the Cloud Workstation Panel to enter the **MATLAB Cloud Workstation**.

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-29 at 5.32.33 PM.png" alt="" width="563"><figcaption></figcaption></figure>

Once the Cloud Workstation has loaded, authenticate using your MathWorks license credentials (username and password) in the pop-up window.

![](<../../.gitbook/assets/image (304).png>)

The system will attempt to establish the connection and status information will be displayed.

![](<../../.gitbook/assets/image (256).png>)

Once connected, you will enter the MATLAB Web Desktop IDE. Here, you can use the **Control** **tab** to manage your MATLAB sessions.

![](<../../.gitbook/assets/image (232).png>)

{% hint style="warning" %}
If using a Matlab 2022a and 2002b image, the license will remain unavailable for a few minutes (\~15) after the Cloud Workstation is closed. To avoid this delay, deploy a Matlab 2023 image instead.
{% endhint %}
