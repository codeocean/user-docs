---
description: >-
  The Code Ocean Python SDK makes it even easier to leverage the full
  functionality of the extensive Code Ocean Public API in your Python scripts
  and applications.
metaLinks:
  alternates:
    - https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/code-ocean-api/python-sdk
---

# Python SDK

## Installation <a href="#installation" id="installation"></a>

{% hint style="info" %}
The Python SDK requires Python >=3.11 and Code Ocean >=2.19
{% endhint %}

The SDK can be installed via pip as shown below:

```bash
pip install -U codeocean
```

For development, install from source with:

```bash
pip install -e .[dev] -
```

## Authentication <a href="#authentication" id="authentication"></a>

When creating a `CodeOcean` client as shown below, you will use your Code Ocean API token. The Python library will then automatically send this key in each request. You can learn more about creating a Code Ocean API Token in our guide [here](authentication.md).

```python
from codeocean import CodeOcean​

client = CodeOcean(domain="https://{domain}", token="cop_d23dasd312")
```

## Examples <a href="#examples" id="examples"></a>

The [Capsule](capsule.md), [Computation](computation.md), and [Data Asset](data-asset.md) sections of the Code Ocean API Guide all contain examples using the Python SDK.
