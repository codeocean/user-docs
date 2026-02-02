---
metaLinks:
  alternates:
    - https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/code-ocean-api/data-asset
---

# Data Asset

## Prerequisites

* Generated [Access Token](authentication.md) with Datasets scope
* The Data Asset's ID

You can find Data Asset's ID below the title.

<figure><img src="../.gitbook/assets/DataAsset (1).png" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="Data Asset Object" %}
*   <mark style="color:$success;">created</mark> `float64`

    Data Asset creation time.
*   <mark style="color:$success;">description</mark> `string`&#x20;

    Data Asset description.
*   <mark style="color:$success;">field</mark> `string`

    Field of research.
*   <mark style="color:$success;">id</mark> `integer`

    Metadata id.
*   <mark style="color:$success;">last\_transferred</mark> `integer`&#x20;

    Time Data Asset's files were last transferred to a different S3 storage location.&#x20;
*   <mark style="color:$success;">last\_used</mark> `integer`

    Time Data Asset was last used in seconds from unix epoch.
*   <mark style="color:$success;">mount</mark> `string`&#x20;

    The default mount folder of the Data Asset.
*   <mark style="color:$success;">name</mark> `string`

    Name of the Data Asset.
* <mark style="color:$success;">owner</mark> `string`\
  Data Asset owner's ID.
* <mark style="color:$success;">owner\_email</mark> \
  Data Asset owner's email address.
*   <mark style="color:$success;">size</mark> `string`

    Size in bytes of the Data Asset.
*   <mark style="color:$success;">state</mark> `enum`

    Data Asset creation state.

    *   <mark style="color:$success;">draft</mark>

        Data Asset is still being created.
    *   <mark style="color:$success;">ready</mark>

        Data Asset is ready to use.
    *   <mark style="color:$success;">failed</mark>

        Data Asset creation failed.
*   <mark style="color:$success;">source\_bucket</mark>&#x20;

    Information regarding the bucket from which the Data Asset was created.

    *   <mark style="color:$success;">bucket</mark> `string`

        The original buckets name
    * <mark style="color:$success;">origin</mark> `enum`
      * <mark style="color:$success;">aws</mark>
      * <mark style="color:$success;">local</mark>
      * <mark style="color:$success;">gcp</mark>
    *   <mark style="color:$success;">prefix</mark> `string`

        The folder in the s3 bucket from which the Data Asset would be created.
*   <mark style="color:$success;">tags</mark> `list<string>`

    Keywords for searching the Data Asset by.
*   <mark style="color:$success;">transfer\_error</mark>

    The error that occurred during the last transfer attempt if it failed.
*   <mark style="color:$success;">type</mark> `enum`

    Type of the Data Asset.&#x20;

    * <mark style="color:$success;">dataset</mark>
    * <mark style="color:$success;">result</mark>
    * <mark style="color:$success;">combined</mark>
    * <mark style="color:$success;">model</mark>
* <mark style="color:$success;">app\_parameters</mark> `list`\
  The name and value of app panel parameters used to generate the result Data Asset.
*   <mark style="color:$success;">contained\_data\_assets</mark> `list`

    List of structs containing information about the contained Data Assets, if the Data Asset is of type `combined`.
*   <mark style="color:$success;">custom\_metadata</mark> `dictionary`

    According to custom metadata fields defined by deployment admin and values that were set by the user.
* <mark style="color:$success;">nextflow\_profile</mark> `string`\
  Pipeline Nextflow profile used to generate the result Data Asset.
*   <mark style="color:$success;">provenance</mark> `dictionary`

    Shows the Data Asset provenance if type is `result`.

    *   <mark style="color:$success;">commit</mark>

        Commit hash of the Capsule or Pipeline used to generate the result.
    *   <mark style="color:$success;">run\_script</mark>

        Run script of the Capsule or Pipeline computation that generated the result.
    *   <mark style="color:$success;">data\_assets</mark>

        Data Assets attached to the Capsule or Pipeline when the result was generated.
    *   <mark style="color:$success;">docker\_image</mark>

        Docker image used to create the Data Asset.
    *   <mark style="color:$success;">capsule</mark>

        Capsule used to create the Data Asset.
    * <mark style="color:$success;">computation</mark>\
      Computation that generated the result.
{% endtab %}
{% endtabs %}

## Create Data Asset

<mark style="color:green;">`POST`</mark> `https://{codeocean-domain}/api/v1/data_assets`

This API allows for the creation of Data Assets from either an S3 bucket or the results of a computation.&#x20;

{% hint style="info" %}
Admins and Capsule/Pipeline owners can create a Data Asset from another user's run.
{% endhint %}

**Prerequisite**

Before using this API call, you may require AWS Cloud Credentials configured as Secrets or an Assumable Role. You can find more information about managing secrets [here](../compute-capsule-basics/secret-management-guide/).

#### Request Body

<table><thead><tr><th width="296">Name</th><th>Type/Values</th><th>Description</th></tr></thead><tbody><tr><td><code>name</code><mark style="color:red;">*</mark></td><td>string</td><td>Data Asset name.</td></tr><tr><td><code>description</code></td><td>string</td><td>Data Asset description.</td></tr><tr><td><code>mount</code><mark style="color:red;">*</mark></td><td>string</td><td>Data Asset default mount folder.</td></tr><tr><td><code>tags</code><mark style="color:red;">*</mark></td><td>list/string</td><td>Keywords applied to the Data Asset to aid in searching.</td></tr><tr><td><code>custom_metadata</code></td><td>string custom field - string number custom field - number <br>date custom field - number (unix epoch format timestamp in seconds)</td><td><p>Map of key value pairs, according to custom metadata fields defined by the admin.</p><p></p></td></tr><tr><td><code>source</code><mark style="color:red;">*</mark></td><td> struct - <code>aws</code> , <code>computation</code> , or <code>cloud_workstation</code>  </td><td></td></tr><tr><td>    <code>aws</code><mark style="color:red;">*</mark></td><td> </td><td></td></tr><tr><td>        <code>endpoint_name</code></td><td>string</td><td>Provide name of the custom S3 endpoint where the bucket is stored.</td></tr><tr><td>        <code>bucket</code><mark style="color:red;">*</mark></td><td>string</td><td>The S3 bucket from which the Data Asset would be created.</td></tr><tr><td>        <code>prefix</code><mark style="color:red;">*</mark></td><td>path </td><td>The folder in the S3 bucket from which the Data Asset would be crated.</td></tr><tr><td>        <code>keep_on_external_storage</code><mark style="color:red;">*</mark></td><td>boolean</td><td>When set to true, the Data Asset files will not be copied to Code Ocean.</td></tr><tr><td>        <code>public</code><mark style="color:red;">*</mark></td><td>boolean</td><td>When set to true, Code Ocean will try to access the source bucket without credentials.</td></tr><tr><td>        <code>use_input_bucket</code></td><td>boolean</td><td>When set to true, Code Ocean will try to create the Data Asset from an internal input bucket. Only allowed to Admin users. All <code>aws</code> properties ignored except <code>prefix</code>.</td></tr><tr><td>    <code>computation</code></td><td> </td><td></td></tr><tr><td>        <code>id</code></td><td>string</td><td>Computation ID.</td></tr><tr><td>        <code>path</code></td><td>path</td><td>Results path. Leave empty to capture all result files.</td></tr><tr><td>    <code>cloud_workstation</code></td><td></td><td></td></tr><tr><td>        <code>id</code></td><td>string</td><td>Computation ID.</td></tr><tr><td>        <code>path</code></td><td>string</td><td>Capsule path (must not be empty).</td></tr><tr><td>        <code>run_script</code></td><td>string</td><td>Path to the script that was executed relative to the <code>/Capsule</code> folder. Existence determines if the data would be of type <code>result</code> in cases when it was not the default <code>code/run</code>.</td></tr><tr><td>    <code>target</code></td><td> struct</td><td>Optional for designating an S3 storage location outside of Code Ocean. Only applicable for <code>source</code> type of <code>computation</code>.</td></tr><tr><td>    <code>aws</code></td><td> </td><td></td></tr><tr><td>        <code>endpoint_name</code></td><td>string</td><td>Optional to provide name of the custom S3 endpoint where the bucket is stored.</td></tr><tr><td>        <code>bucket</code></td><td>string</td><td>The S3 bucket in which the Data Asset would be created.</td></tr><tr><td>        <code>prefix</code></td><td>path </td><td>The folder in the S3 bucket in which the Data Asset would be created</td></tr><tr><td><code>results_info</code></td><td>struct</td><td>When the source of the data is a result in an S3 bucket originating from an exported Capsule/Pipeline, additional information can be provided to populate lineage &#x26; provenance. </td></tr><tr><td>    <code>capsule/pipeline_id</code></td><td>string</td><td>The ID of the Capsule or Pipeline that was executed. Must be provided when using <code>results_info</code>.</td></tr><tr><td>    <code>version</code></td><td>integer </td><td>Capsule or Pipeline Release version.</td></tr><tr><td>    <code>commit</code></td><td>string</td><td>Commit hash of Capsule/Pipeline code at time of execution.</td></tr><tr><td>    <code>run_script</code></td><td>string</td><td>Path to the script that was executed relative to the <code>/Capsule</code> folder in cases when it was not the default <code>code/run</code>.</td></tr><tr><td>    <code>data_assets</code></td><td>array&#x3C;string></td><td>IDs of Data Assets used during the run.</td></tr><tr><td>    <code>parameters</code></td><td>array&#x3C;dictionary></td><td>Run Parameters.</td></tr><tr><td>        <code>name</code></td><td> string</td><td>Parameter label.</td></tr><tr><td>        <code>param_name</code></td><td>string</td><td>Parameter name.</td></tr><tr><td>        <code>value</code></td><td>string</td><td>Parameter value.</td></tr><tr><td>    <code>nextflow_profile</code></td><td>string</td><td>Pipeline Nextflow Profile</td></tr><tr><td>    <code>processes</code></td><td>array</td><td>Pipeline processes' information.</td></tr><tr><td>        <code>name</code></td><td>string</td><td>Pipeline process name as it appears in the <code>main.nf</code> script.</td></tr><tr><td>        <code>capsule_id</code></td><td>string</td><td>The ID of the Capsule executed in the process.</td></tr><tr><td>        <code>version</code></td><td>integer</td><td>Release Capsule version.</td></tr><tr><td>        <code>public</code></td><td>boolean</td><td>When set to true, indicates the Capsule is a public Code Ocean App.</td></tr><tr><td>        <code>parameters</code></td><td>array&#x3C;string></td><td>Run parameters.</td></tr><tr><td>            <code>name</code></td><td>string</td><td>Parameter title.</td></tr><tr><td>            <code>param_name</code></td><td>string</td><td>Parameter name.</td></tr><tr><td>            <code>value</code></td><td>string</td><td>Parameter value.</td></tr></tbody></table>

**Scope**

| Type       | Permission   |
| ---------- | ------------ |
| Data Asset | Read & Write |

### Create a Data Asset from a Public S3 Bucket

<details>

<summary>Request Example Bash</summary>

```bash
curl -X POST https://{codeocean-domain}/api/v1/data_assets \
   -u 'cop_d23dasd312': \
   -H 'Content-Type: application/json' \
   --data-raw '{
      "name": "import public AWS bucket with dataset api",
      "description": "meaningful-c",
      "mount": "citations",
      "tags": ["Genomics"],
      "source": {
         "aws": {
             "public": true,
             "bucket": "codeocean-public-data",
             "prefix": "example_datasets/ATAC/hg38_2bit/"
         }
      }
   }'
```

</details>

<details>

<summary>Request Example Python SDK</summary>

```python
from codeocean.data_asset import DataAssetParams, Source, AWSS3Source

data_asset_params = DataAssetParams(
    name="Dataset From Bucket",
    description="S3 bucket import",
    mount="my-data",
    tags=["my", "data"],
    source=Source(
        aws=AWSS3Source(
            bucket="codeocean-public-data",
            prefix="example_datasets/ATAC/hg38_2bit/",
            public="true",
        ),
    ),
)

data_asset = client.data_assets.create_data_asset(data_asset_params)
```

</details>

### Create a Data Asset from a Private S3 Bucket

<details>

<summary><strong>Request Example Bash</strong></summary>

```bash
curl -X POST https://{codeocean-domain}/api/v1/data_assets \
   -u 'cop_d23dasd312': \
   -H 'Content-Type: application/json' \
   --data-raw '{
      "name":"import private AWS bucket with Data Asset API",
      "description":"meaningful-c",
      "mount":"citations",
      "tags":["Genomics"],
      "source":
         {
         "aws":
                 {
                  "bucket":"codeocean-private-data",
                  "prefix":"example_datasets/ATAC/hg38_2bit/"
                 }
         }
}'
```

</details>

<details>

<summary>Request Example Python SDK</summary>

```python
from codeocean.data_asset import DataAssetParams, Source, AWSS3Source

data_asset_params = DataAssetParams(
    name="Dataset From Bucket",
    description="S3 bucket import",
    mount="my-data",
    tags=["my", "data"],
    source=Source(
        aws=AWSS3Source(
            bucket="codeocean-private-data",
            prefix="example_datasets/ATAC/hg38_2bit/",
        ),
    ),
)

data_asset = client.data_assets.create_data_asset(data_asset_params)
```

</details>

### Create an External Result Data Asset

<details>

<summary>Request Example Bash</summary>

```bash
curl -X POST https://{codeocean-domain}/api/v1/data_assets
   -H 'Content-Type: application/json' \
   -u 'cop_d23dasd312': \
   --data-raw '{
       "name": "RNA-Sequencing",
       "description": "these are reads from an experiment", 
       "mount": "Reads",
       "tags": ["Genomics", "RNA"],
       "source": 
         {
         "computation": 
                 {
                         "id":”8f174aed-64ce-43eb-9c16-64d25da84bda”,
                         “path”:”Alignment/” (Alignment is a folder in Results)
                 }
},
      “target”:
         {
         “aws”:
                 {
                         “bucket”:”my-bucket”,
                         “prefix”:”deposit/my/results/”
                 }
         }
}'
```

</details>

<details>

<summary>Request Example Python SDK</summary>

```python
from codeocean.data_asset import (
        DataAssetParams, 
        Source,
        ComputationSource, 
        Target,
        AWSS3Target
        )
        
data_asset_params = DataAssetParams(
    name="RNA-Sequencing",
    description="these are reads from an experiment",
    mount="Reads",
    tags=["Genomics", "RNA"],
    source=Source(
        computation=ComputationSource(
            id="8f174aed-64ce-43eb-9c16-64d25da84bda",
            path="Alignment/"
        ),
    ),
    target=Target(
        aws=AWSS3Target(
            bucket="my-bucket",
            prefix="deposit/my/results/"
        )
    )
    
data_asset = client.data_assets.create_data_asset(data_asset_params)
```

</details>

### Create a Result Data Asset

<details>

<summary>Request Example Bash</summary>

```bash
curl -X POST https://{codeocean-domain}/api/v1/data_assets \
-H 'Content-Type: application/json' \
-u 'cop_d23dasd312': \ 
   --data-raw '{
       "name": "Data asset From API",
       "description": "An example for creating data asset from CO API",
       "mount": "some-folder",
       "tags": [ "keyword1", "keyword2" ],
       "source": {
         "computation": {
          "id": "8f174aed-64ce-43eb-9c16-64d25da84bda"
       }
    }
}'
```

</details>

<details>

<summary>Request Example Python SDK</summary>

```python
from codeocean.data_asset import (
        DataAssetParams, 
        Source,
        ComputationSource
        )
        
data_asset_params = DataAssetParams(
    name="RNA-Sequencing",
    description="these are reads from an experiment",
    mount="Reads",
    tags=["Genomics", "RNA"],
    source=Source(
        computation=ComputationSource(
            id="8f174aed-64ce-43eb-9c16-64d25da84bda",
            path="Alignment/"
        ),
    )
)
    
data_asset = client.data_assets.create_data_asset(data_asset_params)
```

</details>

### Create a Result Data Asset from External Result

<details>

<summary>Request Example Bash</summary>

```
curl -X POST https://codeocean.[my-domain].com/api/v1/data_assets \
   -u "cop_YTM2OGRlO": \
   -H 'Content-Type: application/json' \
   --data-raw '{
      "name": "Test the New API",
      "description": "meaningful-c",
      "mount": "citations",
      "tags": ["Genomics"],
      "source": {
         "aws": {
             "public": true,
             "bucket": "codeocean-public-data",
             "prefix": "unit_test/Images/"
         }
      },
      "results_info": {
         "capsule_id": "8398ed85-f61f-4e58-aead-82759c238f99",
         "run_script":"code/run",
         "data_assets":[
                "76630c77-8293-4442-9b26-3eb8f7292940",
                "de855853-8aed-4262-8072-a9c1e9ea1a6c"
         ],
         "parameters":[
                {
                        "name":"Number of Threads",
                        "value":"1"
                }
         ]
        }
   }'
```

</details>

<details>

<summary>Request Example Python SDK - Capsule</summary>

```
from codeocean.data_asset import (
    DataAssetParams,
    Source,
    AWSS3Source,
    ResultsInfo,
    Param
)

data_asset_params = DataAssetParams(
        name="Dataset From External Computation",
        description="This Data Asset was imported from Outside",
        mount="Results",
        tags=["SDK"],
        source=Source(
            aws=AWSS3Source(
                bucket="codeocean-public-data",
                prefix=f"unit_test/Reads/",
                public=True,
                keep_on_external_storage=False
                )
            )
        ),
        results_info=ResultsInfo(
              capsule_id='8398ed85-f61f-4e58-aead-82759c238f99',
              version='1',
              commit='123',
              run_script='code/run',
              data_assets=[
                  "76630c77-8293-4442-9b26-3eb8f7292940",
                  "de855853-8aed-4262-8072-a9c1e9ea1a6c"
                ],
              # Ordered Parameters 
              parameters=Param(
                  name='Number of Threads',
                  value='1'
                  )
              # Named Parameters
              parameters=Param(
                  param_name='Number of Threads',
                  value='1'
              )
            
```

</details>

<details>

<summary>Request Example Python SDK - Pipeline</summary>

```
from codeocean.data_asset import (
    DataAssetParams,
    Source,
    AWSS3Source,
    ResultsInfo,
    Param
)

data_asset_params = DataAssetParams(
        name="Dataset From External Computation",
        description="This Data Asset was imported from Outside",
        mount="Results",
        tags=["SDK"],
        source=Source(
            aws=AWSS3Source(
                bucket="codeocean-public-data",
                prefix=f"unit_test/Reads/",
                public=True,
                keep_on_external_storage=False
                )
            )
        ),
        results_info=ResultsInfo(
              pipeline_id='8398ed85-f61f-4e58-aead-82759c238f99',
              version='1',
              data_assets=[
                  "76630c77-8293-4442-9b26-3eb8f7292940",
                  "de855853-8aed-4262-8072-a9c1e9ea1a6c"
                ],
              processes=PipelineProcess(
                  name='FastQC',
                  capsule_id='8398ed85-f61f-4e58-aead-82759c238f99'
                  version='1',
                  public=False,
                  # Ordered Parameters
                  parameters=Param(
                      name='Number of Threads',
                      value='1'
                  )
                  # Named Parameters
                  parameters=Param(
                      param_name='Number of Threads',
                      value='1'
              )
            
```

</details>

### Create a Combined Data Asset

<details>

<summary>Request Example Bash</summary>

```
curl -X POST https://codeocean.[my-domain].com/api/v1/data_assets \
   -u "cop_YTM2OGRlO": \
   -H 'Content-Type: application/json' \
   --data-raw '{
      "name": "My Combined Assets",
      "description": "Create a Combined Data Asset",
      "mount": "Reads",
      "tags": ["Genomics"],
      "data_asset_ids":[
            '75fe2606-f414-469a-a309-b7d74f169885',
            '10bc2606-d321-987z-d365-c7c12a989235
            ]
         }'
```

</details>

<details>

<summary>Request Example Python SDK</summary>

```python
from codeocean.data_asset import (
        DataAssetParams
        )
        
data_asset_params = DataAssetParams(
    name="My Combined Assets",
    description="Create a Combined Data Asset",
    mount="Reads",
    tags=["Genomics"],
    data_asset_ids=[
            '75fe2606-f414-469a-a309-b7d74f169885',
            '10bc2606-d321-987z-d365-c7c12a989235'
            ]
        )
    
data_asset = client.data_assets.create_data_asset(data_asset_params)
```

</details>

### Create a Data Asset with Custom Metadata Tags

<details>

<summary><strong>Request Example Bash</strong></summary>

```bash
curl -X POST https://{codeocean-domain}/api/v1/data_assets
   -H 'Content-Type: application/json' \
   -u 'cop_d23dasd312': \ 
   --data-raw '{
       "name": "myDatasetFromPublic",
       "description": "a descriptive description",
       "mount": "Mymount",
       "tags": ["t1", "t2"],
       "custom_metadata":
         {
                 "some_field": "one", 
                 "another_field": 1, 
                 "dateField": 1676246400 
        }, 
       "source": 
         {
         "computation": 
                 {
                   "id":”computation_ID”,
                   "path": "/path/to/folder/" (remove if want all Results)
                 }
         }
}'
```

</details>

<details>

<summary><strong>Request Example Python SDK</strong></summary>

```python
from codeocean.data_asset import (
        DataAssetParams, 
        Source,
        ComputationSource
        )
        
data_asset_params = DataAssetParams(
    name="RNA-Sequencing",
    description="these are reads from an experiment",
    mount="Reads",
    tags=["Genomics", "RNA"],
    custom_metadata={"Project": "Bulk RNA", "Medallion": "Bronze"},
    source=Source(
        computation=ComputationSource(
            id="8f174aed-64ce-43eb-9c16-64d25da84bda",
            path="Alignment/"
        ),
    )
)
    
data_asset = client.data_assets.create_data_asset(data_asset_params)
```

</details>

<details>

<summary>Response</summary>

[Data Asset Object](data-asset.md#data-asset-object).

</details>

{% hint style="info" %}
The API only returns a confirmation of the validity of the creation request, not the success of the creation, since the creation takes time. Poll on the dataset details and monitor its state until it’s ready.
{% endhint %}

## Get Data Asset

<mark style="color:blue;">`GET`</mark> `https://{codeocean-domain}/api/v1/data_assets/{data_asset_id}`&#x20;

This API retrieves metadata for your Data Asset.

#### Path Parameters

| Name                                               | Type    |
| -------------------------------------------------- | ------- |
| `data_asset_id` <mark style="color:red;">\*</mark> |  string |

**Scope**

| Type       | Permission   |
| ---------- | ------------ |
| Data Asset | Read & Write |

<details>

<summary>Request Example Bash</summary>

<pre class="language-bash"><code class="lang-bash">curl https://{codeocean-domain}/api/v1/data_assets/4bc97533-6eb4-48ac-966f-648548a756d2 \
<strong>   -u 'cop_d23dasd312':
</strong></code></pre>

</details>

<details>

<summary>Request Example Python SDK</summary>

```python
data_asset = client.data_assets.get_data_asset(dataset_id="4bc97533-6eb4-48ac-966f-648548a756d2")
```

</details>

## Update Metadata

<mark style="color:$warning;">`PUT`</mark> `https://{codeocean-domain}/api/v1/data_assets/{data_asset_id}`

This API allows for the updating of a Data Asset's metadata.

#### Path Parameters

| Name                                              | Type   |
| ------------------------------------------------- | ------ |
| `data_asset_id`<mark style="color:red;">\*</mark> | string |

#### Request Body

| Name                                            | Type       |
| ----------------------------------------------- | ---------- |
| `name`<mark style="color:red;">\*</mark>        | string     |
| `description`<mark style="color:red;">\*</mark> | string     |
| `tags`<mark style="color:red;">\*</mark>        | string     |
| `mount`<mark style="color:red;">\*</mark>       | string     |
| `custom_metadata`                               | dictionary |

**Scope**

| Type       | Permission |
| ---------- | ---------- |
| Data Asset | Write      |

<details>

<summary>Request Example Bash</summary>

```bash
curl -X PUT https://{codeocean-domain}/api/v1/data_assets/d36665a7-ef59-4b8e-a799-bee7f83ee317 \
   -H 'Content-Type: application/json' \
   -u 'cop_d23dasd312': \
   --data-raw '{
        "name": "Modified The Name",
        "description": "a new description from the API!",
        "tags": ["I","Am","New"],
        "mount": "NewMount"
}'
```

</details>

<details>

<summary>Request Example Python SDK</summary>

```python
from codeocean.data_asset import DataAssetUpdateParams

data_asset_params = DataAssetUpdateParams(
    name="Modified The Name",
    description="a new description from the SDK!",
    tags=["I","Am","New"],
    mount="NewMount",
)

data_asset = client.data_assets.update_metadata(
    dataset_id="4bc97533-6eb4-48ac-966f-648548a756d2",
    update_params=data_asset_params,
)
```

</details>

<details>

<summary><strong>Response</strong></summary>

[Data Asset Object](data-asset.md#data-asset-object)

</details>

## Archiving/Unarchiving a Dataset

<mark style="color:purple;">`PATCH`</mark> `https://{codeocean-domain}/api/v1/data_assets/{data_asset_id}/archive?archive={true|false}`&#x20;

This API allows for the archiving and retrieval of your Data Asset.&#x20;

#### Path Parameters

| Name                                              | Type   |
| ------------------------------------------------- | ------ |
| `data_asset_id`<mark style="color:red;">\*</mark> | string |

#### Query Parameters

| Name                                        | Type    |
| ------------------------------------------- | ------- |
| `archive`<mark style="color:red;">\*</mark> | boolean |

**Scope**

| Type       | Permission   |
| ---------- | ------------ |
| Data Asset | Read & Write |

<details>

<summary>Request Example Bash</summary>

```bash
Archiving a Dataset

curl -X PATCH https://{codeocean-domain}/api/v1/data_assets/e25ec103-a712-4882-a9fa-3cd5a80438a8/archive?archive=true
   -u 'cop_d23dasd312': 

Unarchiving a Dataset


curl -X PATCH https://{codeocean-domain}/api/v1/data_assets/e25ec103-a712-4882-a9fa-3cd5a80438a8/archive?archive=false
   -u 'cop_d23dasd312':
```

</details>

<details>

<summary>Request Example Python SDK</summary>

```python
client.data_assets.archive_data_asset(
    data_asset_id="edf1a1df-4e97-4888-9e2a-92bf70e341e8",
    archive=True,
)
```

</details>

## Search Data Assets

<mark style="color:green;">`POST`</mark> `https://{codeocean-domain}/api/v1/data_assets/search`

This API allows for the searching of Data Assets in your deployment.&#x20;

#### Request Body (all fields optional)

<table><thead><tr><th width="239">Name</th><th width="172">Type or Value</th><th>Description</th></tr></thead><tbody><tr><td><code>offset</code></td><td>int</td><td>Specifies the starting index for the search.</td></tr><tr><td><code>limit</code></td><td>int</td><td>Specifies how many items to return (up to 1000, defaults to 100).</td></tr><tr><td><code>next_token</code></td><td>string</td><td>Represents the token for the next page of results as provided in the previous response. If both <code>from</code> and <code>next_token</code> are set, the <code>from</code> parameter is ignored.</td></tr><tr><td><code>sort_order</code></td><td><code>asc</code>, <code>desc</code></td><td>Determines the result sort order. Must be provided with <code>sort_field</code>, otherwise ignored.</td></tr><tr><td><code>sort_field</code></td><td><code>created</code>, <code>type</code>, <code>name</code>, <code>size</code> </td><td>Determines the field to sort by (default <code>created</code>).</td></tr><tr><td><code>query</code></td><td><code>string</code></td><td>Determines the search query. Can be a free text or in the form of “<code>name:... tag:... run_script:... commit_id:...</code>”.</td></tr><tr><td><code>type</code></td><td><code>dataset</code>, <code>result</code>, <code>combined</code>, or <code>model</code></td><td>Specifies the type of Data Asset to include in the response. If omitted results may include all types.</td></tr><tr><td><code>ownership</code></td><td><code>created</code>, <code>shared</code></td><td><p>Search Data Asset by ownership. <code>created</code> - Only Data Assets created by the user.</p><p><code>shared</code> - Data Assets shared with the user.</p><p>** Defaults to all accessible, and admins will have access to all Data Assets in the system.</p></td></tr><tr><td><code>origin</code></td><td><code>internal</code>, <code>external</code></td><td>Designates whether to return only internal/external Data Assets.</td></tr><tr><td><code>favorite</code></td><td>boolean</td><td>Search only favorite Data Assets.</td></tr><tr><td><code>archived</code></td><td>boolean</td><td>Search only archived Data Assets.</td></tr><tr><td><code>filters</code></td><td>list</td><td></td></tr><tr><td>    <code>key</code></td><td>string</td><td>Field key can be each of <code>name</code>, <code>description</code>, <code>tags</code>, any custom field key defined by the admin.</td></tr><tr><td>    <code>value</code></td><td></td><td>Field value to be included/excluded (optional).</td></tr><tr><td>    <code>values</code></td><td></td><td>Field values in case of multiple values (optional).</td></tr><tr><td>    <code>range</code></td><td></td><td>Field range to be included/excluded (only one of min/max must be set).</td></tr><tr><td>        <code>min</code></td><td>number</td><td></td></tr><tr><td>        <code>max</code></td><td>number</td><td></td></tr><tr><td>    <code>exclude</code> </td><td>boolean</td><td>Whether to include/exclude the field value.</td></tr></tbody></table>

#### Response

<table><thead><tr><th width="238">Name</th><th width="149">Type</th><th width="330">Description</th></tr></thead><tbody><tr><td>has_more</td><td>boolean</td><td>Indicates if there are more results.</td></tr><tr><td>next_token</td><td>number</td><td>Specifies the next page token for the next request.</td></tr><tr><td>results</td><td>array </td><td>Array of Data Assets found.</td></tr></tbody></table>

<details>

<summary>Request Example Bash</summary>

```bash
curl -X POST https://{codeocean-domain}/api/v1/data_assets/search
   -u 'cop_d23dasd312': \
   -H 'Content-Type: application/json' \
   --data-raw '{
        "offset": 0,
        "limit": 10,
        "sort_order": "desc",
        "sort_field": "name",
        "type": "dataset",
        "ownership": "created",
        "favorite": false,
        "archived": false,
        "query": "tag:bioinforma name:Saccro"
}'
```

</details>

<details>

<summary>Request Example Python SDK</summary>

<pre class="language-python"><code class="lang-python"><strong>from codeocean.data_asset import DataAssetSearchParams
</strong>
data_asset_params = DataAssetSearchParams(
    offset=0,
    limit=10,
    sort_order="desc",
    sort_field="name",
    type="dataset",
    ownership="created",
    archived=False,
    favorite=False,
    query="tag:bioinforma"
)

data_assets = client.data_assets.search_data_assets(data_asset_params)
</code></pre>

</details>

<details>

<summary>Request Example Python SDK - Search with Custom Metadata Filter</summary>

<pre class="language-python"><code class="lang-python"><strong>from codeocean.components import SearchFilter
</strong>from codeocean.data_asset import DataAssetSearchParams

data_asset_params = DataAssetSearchParams(
    offset=0,
    limit=100,
    sort_order="desc",
    sort_field="name",
    archived=False,
    favorite=False,
    query="",
    filters=[
        SearchFilter(
            key="experiment type",
            value="MRI"
        ), 
        SearchFilter(
            key="subject id",
            value="12345"
        )
    ]
)

data_asset_search_results = client.data_assets.search_data_assets(data_asset_params)
</code></pre>

</details>

<details>

<summary>Request Example Python SDK - Search for >1000 Data Assets  </summary>

<pre class="language-python"><code class="lang-python"><strong>from codeocean.data_asset import DataAssetSearchParams
</strong><strong>
</strong>data_asset_params = DataAssetSearchParams(
    offset=0,
    limit=1000,
    sort_order="desc",
    sort_field="name",
    archived=False,
    favorite=False
)

data_assets = client.data_assets.search_data_assets_iterator(data_asset_params)
</code></pre>

</details>

{% hint style="info" %}
The `search_data_assets_iterator` function iteratively calls the `search_data_assets` function to return a list of all the Data Assets that match the `data_asset_params` query. The `limit` parameter is the page size, i.e. the number of Data Assets to return on each iteration, and as such setting it to `1000` provides the best performance. &#x20;
{% endhint %}

<details>

<summary><strong>Response</strong></summary>

{

&#x20;     'has\_more': True/False,    (indicates whether there are more results)

&#x20;     'next\_token': 'sometoken',

&#x20;     'results': \[[Data Asset Object](data-asset.md#data-asset-object)]

}

</details>

## Update Permissions of a Data Asset

<mark style="color:green;">`POST`</mark> `https://{codeocean-domain}/api/v1/data_assets/{data_asset_id}/permissions`

This API allows for the updating of a Data Asset's user access permissions in your deployment.&#x20;

#### Path Parameters

| Name                                              | Type   |
| ------------------------------------------------- | ------ |
| `data_asset_id`<mark style="color:red;">\*</mark> | string |

#### Request Body

| Name                                         | Type         |
| -------------------------------------------- | ------------ |
| `users`<mark style="color:red;">\*</mark>    | array\<dict> |
| `groups`<mark style="color:red;">\*</mark>   | array\<dict> |
| `everyone`<mark style="color:red;">\*</mark> | string       |
| `share_assets`                               | bool         |

<details>

<summary>Request Example Bash</summary>

<pre class="language-bash"><code class="lang-bash">curl -X POST https://{codeocean-domain}/api/v1/data_assets/{data_asset_id}/permissions \
  -u 'cop_d23dasd312': \
  -H 'Content-Type: application/json' \
  --data-raw '{
       "users": [{"email": "john@codeocean.com", "role":"owner"}]
       "groups": [{"group":"ad-group","role":"viewer"}],
       "everyone": "viewer",
       "share_assets": "true"
<strong>  }'
</strong></code></pre>

</details>

<details>

<summary>Request Example Python SDK</summary>

<pre class="language-python"><code class="lang-python"><strong>from codeocean.data_asset import (
</strong>    Permissions
)
                
from codeocean.components import (
<strong>    UserPermissions,
</strong><strong>    EveryoneRole,
</strong><strong>    UserRole,
</strong><strong>)
</strong><strong>                
</strong>update_permissions = Permissions(
    users=[
        UserPermissions(
            email="jake@codeocean.com",
            role=UserRole(value="owner"),
        ),
    ],
    everyone=EveryoneRole(value="viewer"),
    share_assets=True,
)    

client.data_assets.update_permissions(
    data_asset_id="e25ec103-a712-4882-a9fa-3cd5a80438a8",
    permissions=update_permissions,
)
</code></pre>

</details>

## Delete Data Asset

<mark style="color:$danger;">`DELETE`</mark> `https://{codeocean-domain}/api/v1/data_assets/{data_asset_id}`&#x20;

This API deletes a Data Asset.

#### Path Parameters

| Name                                               | Type    |
| -------------------------------------------------- | ------- |
| `data_asset_id` <mark style="color:red;">\*</mark> |  string |

**Scope**

| Type       | Permission   |
| ---------- | ------------ |
| Data Asset | Read & Write |

<details>

<summary>Request Example Bash</summary>

<pre class="language-bash"><code class="lang-bash">curl DELETE https://{codeocean-domain}/api/v1/data_assets/4bc97533-6eb4-48ac-966f-648548a756d2 \
<strong>   -u 'cop_d23dasd312':
</strong></code></pre>

</details>

<details>

<summary>Request Example Python SDK</summary>

```python
data_asset = client.data_assets.delete_data_asset(dataset_id="4bc97533-6eb4-48ac-966f-648548a756d2")
```

</details>

## Transfer Data Asset

<mark style="color:green;">`POST`</mark> `https://{codeocean-domain}/api/v1/data_assets/{data_asset_id}/transfer`

This is an **Admin only API** that allows transferring a Data Asset's files to a different S3 storage location. This can be used to convert an Internal Data Asset to External, or to change the storage location of an External Data Asset. When applied to Result Data Assets, provenance information is maintained.

{% hint style="info" %}
When transferring files from an External Data Asset linked to a public S3 bucket, the S3 bucket should have **ACLs disabled** as described [here](https://docs.aws.amazon.com/AmazonS3/latest/userguide/ensure-object-ownership.html).&#x20;
{% endhint %}

#### Path Parameters

<table><thead><tr><th width="239">Name</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td><code>target</code><mark style="color:red;">*</mark></td><td>struct</td><td>Struct defining target storage location.</td></tr><tr><td>    <code>aws</code><mark style="color:red;">*</mark></td><td></td><td></td></tr><tr><td>        <code>bucket</code><mark style="color:red;">*</mark></td><td>string</td><td>The S3 bucket the Data Asset's files will be transferred into. </td></tr><tr><td>        <code>prefix</code><mark style="color:red;">*</mark></td><td>string</td><td>The folder in the S3 bucket in which the Data Asset files will be placed.</td></tr><tr><td><code>force</code></td><td>boolean</td><td>Perform the transfer even if there are Release Pipelines using it.</td></tr></tbody></table>

#### Request Body

| Name                                               | Type    |
| -------------------------------------------------- | ------- |
| `data_asset_id` <mark style="color:red;">\*</mark> |  string |

{% hint style="info" %}
Changing the storage location of a Data Asset will break a Pipeline it's used in due to how the Data Asset is referenced in the `main.nf` file. As such, the `force` field must be used when transferring a Data Asset used by a Release Pipeline and the Release Pipeline must then be updated.
{% endhint %}

<details>

<summary>Request Example Bash</summary>

```bash
curl -X POST 'http://{codeocean-domain}/api/v1/data_assets/{data_asset_id}/transfer' \
-u "cop_d23dasd312": \
-H 'Content-Type: application/json' \
--data-raw '{
  "target": {
    "aws": {
      "bucket": "MY_BUCKET",
      "prefix": "PREFIX"
    }
  }
}'
```

</details>

<details>

<summary>Request Example Python SDK</summary>

```python
from codeocean.data_asset import TransferDataParams, Target, AWSS3Target

transfer_data_params = TransferDataParams(
    target=Target(
        aws=AWSS3Target(
            bucket="MY_BUCKET",
            prefix="prefix/"
        )
    ),
    force=True
)

client.data_assets.transfer_data_asset(
    data_asset_id=data_asset_id,
    transfer_params=transfer_data_params
)
```

</details>

## List Data Asset Files

<mark style="color:green;">`POST`</mark> `https://{codeocean-domain}/api/v1/data_assets/{data_asset_id}/files`

This API allows for listing of an Internal Data Asset's files.

{% hint style="info" %}
To list files in an External Data Asset, interact with the S3 bucket directly using e.g. the AWS CLI. S3 information can be obtained from the `source_bucket` field of the get data asset API.&#x20;
{% endhint %}

#### Path Parameters

| Name                                              | Type   |
| ------------------------------------------------- | ------ |
| `data_asset_id`<mark style="color:red;">\*</mark> | string |

**Request Body**

<table><thead><tr><th width="188">Name</th><th width="168">Type</th><th>Description</th></tr></thead><tbody><tr><td>path</td><td>string</td><td>The path of a folder within the Data Asset. Empty <code>path</code> will retrieve a list of all files or folders at the root level.</td></tr></tbody></table>

**Scope**

| Type       | Permission |
| ---------- | ---------- |
| Data Asset | Read       |

<details>

<summary>Request Example Bash</summary>

```bash
curl -H "Content-Type: application/json" -u ${CUSTOM_KEY}: -X POST https://${co_domain}/api/v1/data_assets/${data_asset_id}/files --data-raw '{"path": "subfolder"}'
```

</details>

<details>

<summary>Request Example Python SDK</summary>

```python
file_paths = client.data_assets.list_data_asset_files(
    data_asset_id=data_asset_id,
    path="subfolder",
)
```

</details>

<details>

<summary>Response</summary>

```bash
{
    "items":[
        {
            "name":"data.txt",
            "path":"subfolder/data.txt",
            "size":77177296,
            "type":"file"
        }
    ]
}
```

</details>

## Get Data Asset File URLs

<mark style="color:blue;">`GET`</mark> `https://{codeocean-domain}/api/v1/data_assets/{data_asset_id}/files/urls?path={path_to_file}`

This API allows for the generation of two URLs to a file in an Internal Data Asset:

* `download_url` - Signed URL for downloading the file.
* `view_url` - Signed URL for viewing the file in the browser.

{% hint style="info" %}
This API was introduced in Code Ocean version 4.0. The previous Get Data Asset File Download URL API is deprecated but will be supported until August 2026.
{% endhint %}

#### Path Parameters

| Name                                              | Type   |
| ------------------------------------------------- | ------ |
| `data_asset_id`<mark style="color:red;">\*</mark> | string |
| `path_to_file`<mark style="color:red;">\*</mark>  | string |

#### Scope

| Type       | Permission |
| ---------- | ---------- |
| Data Asset | Read       |

<details>

<summary>Request Example Bash</summary>

```bash
curl -H "Content-Type: application/json" -u ${CUSTOM_KEY}: -X GET https://${co_domain}/api/v1/data_assets/${data_asset_id}/files/urls?path=${path_to_file}
```

</details>

<details>

<summary>Request Example Python SDK</summary>

```python
url = client.data_assets.get_data_asset_file_urls(
    data_asset_id=data_asset_id,
    path=file_paths.items[2].name,
)
```

</details>

<details>

<summary>Response</summary>



* <mark style="color:green;">download\_url</mark> `string` Download file URL
* <mark style="color:green;">view\_url</mark> `string` View file URL

</details>
