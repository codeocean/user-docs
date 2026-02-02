---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/aqua-and-agents-guide/model-context-protocol-mcp
---

# Model Context Protocol (MCP)

Model Context Protocol (MCP) is an open standardized protocol that allows agents to work with tools (e.g. APIs and knowledge bases).&#x20;

The Code Ocean MCP server is publicly available under an MIT license on our Github page at: [github.com/codeocean/codeocean-mcp-server](http://github.com/codeocean/codeocean-mcp-server). The repository includes installation guides for popular tools such as Cline, VS Code, Claude Desktop, Cursor, and more.

At its core, the MCP server is a wrapper around Code Ocean’s [Python SDK](../code-ocean-api/python-sdk.md), which itself uses the Code Ocean [public API](../code-ocean-api/).

To connect the MCP server to a Code Ocean deployment, a user will need to:

1. [Create an access token](../code-ocean-api/authentication.md#to-create-an-access-token) within their user account settings.&#x20;
2. Configure the MCP server to use that token, according to the instructions found in the appropriate [installation guide](https://github.com/codeocean/codeocean-mcp-server).

{% hint style="info" %}
If you’re using Aqua inside Code Ocean, you don’t need to do any installation, as the MCP server is already integrated, so Aqua can act on your behalf out-of-the-box.

However, for external tools, such as Cline, Claude Desktop, or Cursor, you will need to set up and configure the MCP server yourself.&#x20;
{% endhint %}

Once configured, the MCP server enables an agent to directly call Code Ocean APIs and perform platform actions, as if it were another user in the system.

Furthermore, as an agent acts on behalf of a user, its capabilities are always tied to the permissions of the specific user it is assisting via the API access token it's using. In other words, what Aqua can do depends entirely on what the user is allowed to do within Code Ocean.<br>
