---
description: >-
  Code Ocean uses Access Tokens to authenticate requests. You can view and
  manage your access tokens from within your Dashboard under Access Tokens.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/code-ocean-api/authentication
---

# Authentication

## To create an Access Token

1. Sign in to Code Ocean.
2. Click **Account.**
3. Click **Access Tokens.**
4. Click **Generate New Token.**
5. Provide the **Token Name.**&#x20;
6. **Select Scopes** allows you to select permissions for each resource.&#x20;
7. Click **Add Token.**
8. Click **Copy** to copy the Token, or click **Copy Token & Create Secret** to copy the token and store it as a secret in your Code Ocean account.
9. Click **Save Changes**.

<div align="center"><figure><img src="../.gitbook/assets/create access token.gif" alt=""><figcaption></figcaption></figure></div>

{% hint style="warning" %}
The access token only shows when it is created, so be sure to copy it or click **Copy Token & Create Secret** to copy the token and store it as a secret in your Code Ocean account.

**You will not be able to access it again.**&#x20;

By adding the access token as a secret in your Code Ocean account, it will be easily accessible in a Capsule. See the [Accessing a Secret in a Capsule](../compute-capsule-basics/secret-management-guide/attaching-a-secret-to-a-capsule.md) page for more information.
{% endhint %}

## To view an Access Token

1. Navigate to **Account.**
2. Click **Access Tokens** and a list of Access Tokens will be shown.

## To delete an Access Token

1.  Next to the Token, click the garbage can <img src="../.gitbook/assets/Delete.gif" alt="" data-size="line">.<br>

    <div align="center"><figure><img src="../.gitbook/assets/Delete API.gif" alt="" width="375"><figcaption></figcaption></figure></div>
2. Click **Delete**.

## Using an access token in API requests

### cURL

Authentication to the API is performed via [HTTP Basic Auth](http://en.wikipedia.org/wiki/Basic_access_authentication). Provide your access token as the basic authentication username value. You do not need to provide a password.

<pre class="language-bash"><code class="lang-bash"><strong>curl https://{domain}/api/v1/capsules/4bc97533-6eb4-48ac-966f-648548a756d2 \
</strong>  -u "cop_d23dasd312"
</code></pre>

### Python SDK

Use your access token when creating a `CodeOcean` client. The Python library will then automatically send this key in each request.

<pre class="language-bash"><code class="lang-bash"><strong>$ pip install codeocean
</strong></code></pre>

```python
from codeocean import CodeOcean

client = CodeOcean(domain="https://{domain}", token="cop_d23dasd312")
```
