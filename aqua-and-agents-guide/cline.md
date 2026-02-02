---
metaLinks:
  alternates:
    - https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/aqua-and-agents-guide/cline
---

# Cline

Cline is a cutting-edge coding agent for developers, pre-configured via AWS Bedrock and embedded in the Code Ocean [VS Code](../cloud-workstation/launching-a-cloud-workstation/using-vs-code-in-code-ocean.md) (code server) Cloud Workstation. All users have been given the appropriate IAM role to access AWS Bedrock.&#x20;

### To configure Cline within the VS Code Cloud Workstation:

1. Launch the VS Code Cloud Workstation.
2. Click the Cline icon to navigate to the Cline page.&#x20;
3. Click **Use your own API key**.
4. In the API Provider dropdown, select **Amazon Bedrock**.
5. Select **AWS Profile**.
6. Enter the AWS Profile Name (leave empty for default) and AWS Region.
7. Check Use cross-region inference.
8. Click **Let’s go!**

<figure><img src="../.gitbook/assets/Screenshot 2025-09-16 at 11.05.47 AM.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
This setup must be performed once per browser session, as the configuration is stored locally, which is a behavior defined by Cline.&#x20;
{% endhint %}

Once configured, Cline can connect to the Code Ocean MCP server, enabling it to perform Code Ocean actions directly through the MCP. &#x20;

See [Model Context Protocol (MCP)](model-context-protocol-mcp.md) for more information on Code Ocean’s public MCP. <br>
