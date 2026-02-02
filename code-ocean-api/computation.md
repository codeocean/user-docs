---
metaLinks:
  alternates:
    - https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/code-ocean-api/computation
---

# Computation

## Prerequisites

* Generated [Access Token](authentication.md) with Capsule Scope
* The Computation ID

The Computation ID can only be accessed from the Computation Object.

&#x20;A typical use case is to use:

* [List Capsule Computations](capsule.md#listing-capsule-computations)
* [Run Computation](computation.md#run-computation)

Both methods will have the Computation ID in the Response that can be used in Computations API for further tracking and getting results.

{% hint style="info" %}
When running a Pipeline, the Data Asset mount point will be the mount point of the Data Asset currently attached to the Pipeline. If the Pipeline does not have a mount point accessible (from a Data Asset) and the user attempts to run the Pipeline with a replaced Data Asset in the API, they will encounter an error due to an incorrect file path.&#x20;

When replacing Data Assets, it is only possible to replace External Data Assets with other External Assets and Internal Data Assets with other Internal Assets. &#x20;
{% endhint %}

{% tabs %}
{% tab title="Computation Object" %}
*   <mark style="color:green;">id</mark> `string`

    Computational id
*   <mark style="color:$success;">created</mark> `float64`

    Computation create time
*   <mark style="color:$success;">name</mark> `string`

    Display name of the Computation
* <mark style="color:$success;">owner</mark> `string`\
  Computation owner's ID. Value will be `release` for computations in Release Capsules/Pipelines.
* <mark style="color:$success;">owner\_email</mark> `string`\
  Computation owner's email address. No value is returned for computations in Release Capsules/Pipelines.
*   <mark style="color:$success;">run\_time</mark> `integer`&#x20;

    Total run time in seconds
* <mark style="color:$success;">cloud\_workstation</mark> `boolean` Indicates whether this Computation is a cloud workstation
* <mark style="color:$success;">state</mark> `enum`
  * <mark style="color:$success;">initializing</mark>, <mark style="color:$success;">running</mark>, <mark style="color:$success;">finalizing</mark>, <mark style="color:$success;">completed</mark>
* <mark style="color:$success;">end\_status</mark> `enum`
  * <mark style="color:$success;">stopped</mark>, <mark style="color:$success;">failed</mark>, <mark style="color:$success;">succeeded</mark>
*   <mark style="color:$success;">exit\_code</mark> `integer`

    Value will be 0 when the code runs successfully and non-zero when it doesn't. Any error in a Pipeline will have an exit code value of 1. Only exists once <mark style="color:$success;">state</mark> (above) is <mark style="color:$success;">completed</mark>.
*   <mark style="color:$success;">has\_results</mark> `boolean`

    Indicates whether the Computation has results
*   <mark style="color:$success;">parameters</mark> `array` (Optional)

    Run parameters

    *   <mark style="color:$success;">name</mark> `string`&#x20;

        Parameter name

        * <mark style="color:$success;">value</mark> `string` Parameter value
*   <mark style="color:$success;">data\_assets</mark> `array<dictionary>` (Optional)

    Attached Data Assets

    *   <mark style="color:$success;">id</mark> `string`

        Attached Data Asset ID
    *   <mark style="color:$success;">mount</mark> `string`

        Attached Data Asset mount
* <mark style="color:$success;">nextflow\_profile</mark> `string` (Optional)\
  Pipeline Nextflow profile
* <mark style="color:$success;">processes</mark> `array<dictionary>` (Optional)\
  Pipeline processes information
  * <mark style="color:$success;">name</mark> `string`\
    Pipeline process name (as it appears in the main.nf)
  * <mark style="color:$success;">capsule\_id</mark> `string`\
    ID of the Capsule executed in the process
  * <mark style="color:$success;">version</mark> `boolean`\
    Capsule version in case it's Released
  * <mark style="color:$success;">public</mark> `boolean`\
    Indicates the Capsule is a Code Ocean App
  * <mark style="color:$success;">parameters</mark> `array<dictionary>`\
    Run Parameters
    * <mark style="color:$success;">name</mark> `string`\
      Parameter Label
    * <mark style="color:$success;">param\_name</mark> `string`\
      Parameter Name
    * <mark style="color:$success;">value</mark> `string`\
      Parameter Value
{% endtab %}
{% endtabs %}

## Get Computation

<mark style="color:blue;">`GET`</mark> `https://{codeocean-domain}/api/v1/computations/{computation_id}`

This API allows for the retrieval of information from a Computational run.

#### Path Parameters

| Name                                                | Type    |
| --------------------------------------------------- | ------- |
| `computation_id`<mark style="color:red;">`*`</mark> |  string |

**Scope**

| Type    | Permission |
| ------- | ---------- |
| Capsule | Read       |

<details>

<summary><strong>Request Example Bash</strong></summary>

```bash
curl https://{codeocean-domain}/api/v1/computations/c229ed13-ec06-43d0-abd9-4d481af3f5e3 \
   -u "cop_d23dasd312":
```

</details>

<details>

<summary>Request Example Python SDK</summary>

{% code overflow="wrap" %}
```python
computation = client.computations.get_computation(computation_id="8f174aed-64ce-43eb-9c16-64d25da84bda")
```
{% endcode %}

</details>

<details>

<summary>Response</summary>

[Computation Object](computation.md#computation-object)

</details>

## List Computation Result Files&#x20;

<mark style="color:green;">`POST`</mark> `https://{codeocean-domain}/api/v1/computations/{computation_id}/results`

This API allows for listing of result files generated by a Computation.&#x20;

#### Path Parameters

| Name                                                | Type   |
| --------------------------------------------------- | ------ |
| `computation_id`<mark style="color:red;">`*`</mark> | string |

**Request Body**

<table><thead><tr><th width="188">Name</th><th width="168">Type</th><th>Description</th></tr></thead><tbody><tr><td>path</td><td>string</td><td>The path of the folder. Empty path will retrieve the <code>/results</code> root folder.</td></tr></tbody></table>

**Scope**

| Type    | Permission |
| ------- | ---------- |
| Capsule | Read       |

<details>

<summary>Request Example Bash</summary>

```bash
curl -H "Content-Type: application/json" -u ${CUSTOM_KEY}: -X POST https://${co_domain}/api/v1/computations/${computation_id}/results --data-raw '{"path": "subfolder"}'
```

</details>

<details>

<summary>Request Example Python SDK</summary>

```python
result_paths = client.computations.list_computation_results(
    computation_id=computation_id,
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
            "name":"result.txt",
            "path":"subfolder/result.txt",
            "size":0,
            "type":"file"
        }
    ]
}
```

</details>

## Get Result File URLs

<mark style="color:blue;">`GET`</mark> `https://{codeocean-domain}/api/v1/computations/{computation_id}/results/urls?path={path_to_file}`

This API allows for the generation of two URLs to a Computation result file:

* `download_url` - signed URL for downloading the file
* `view_url` - signed URL for viewing the file in the browser

{% hint style="info" %}
This API was introduced in Code Ocean version 4.0. The previous Get Result File Download URL API is deprecated but will be supported until August 2026.
{% endhint %}

#### Path Parameters

| Name                                                | Type   |
| --------------------------------------------------- | ------ |
| `computation_id`<mark style="color:red;">`*`</mark> | string |
| `path_to_file`<mark style="color:red;">`*`</mark>   | string |

**Scope**

| Type    | Permission |
| ------- | ---------- |
| Capsule | Read       |

<details>

<summary>Request Example Bash</summary>

```bash
curl https://{domain}/api/v1/computations/9390055d-7884-4997-8dfc-88bf7445b617/results/urls?path=GSM12345_R1_fastqc.html \
   -u "cop_d23dasd312":
```

</details>

<details>

<summary><strong>Request Example Python SDK</strong></summary>

{% code overflow="wrap" %}
```python
urls = client.computations.get_result_file_urls(
    computation_id="8f174aed-64ce-43eb-9c16-64d25da84bda",
    path="GSM12345_R1_fastqc.html",
)
```
{% endcode %}

</details>

<details>

<summary><strong>Response</strong></summary>

* <mark style="color:green;">download\_url</mark> `string` Download file URL
* <mark style="color:green;">view\_url</mark> `string` View file URL

</details>

## Delete Computation

<mark style="color:red;">`DELETE`</mark> `https://{domain}/api/v1/computations/{computation_id}`

This API allows for the deletion of a Computational run. If it is running, the Computation will stop.

#### Path Parameters

| Name                                                | Type    |
| --------------------------------------------------- | ------- |
| `computation_id`<mark style="color:red;">`*`</mark> |  string |

**Scope**

| Type    | Permission |
| ------- | ---------- |
| Capsule | Read/Write |

<details>

<summary><strong>Request Example Bash</strong></summary>

```bash
curl -X DELETE https://${co_domain}/api/v1/computations/${computation_id} \
   -u ${ACCESS_TOKEN}:
```

</details>

<details>

<summary>Request Example Python SDK</summary>

{% code overflow="wrap" %}
```python
client.computations.delete_computation(computation_id="8f174aed-64ce-43eb-9c16-64d25da84bda")
```
{% endcode %}

</details>

## Rename Computation

<mark style="color:purple;">`PATCH`</mark> `https://{domain}/api/v1/computations/{computation_id}?name={computation_name}`

This API allows for the renaming of an existing Computational run immediately after it has been initiated.<br>

**Request Body**

| Name                                                | Type   |
| --------------------------------------------------- | ------ |
| `computation_id`<mark style="color:red;">`*`</mark> | string |
| `computation_name`                                  | string |

**Scope**

| Type    | Permission |
| ------- | ---------- |
| Capsule | Read/Write |

<details>

<summary><strong>Request Example Bash</strong></summary>

```bash
curl --location --request PATCH https://${co_domain}/api/v1/computations/${computation_id}?name=${computation_name} \
--header 'Content-Type: application/json' \
-u ${ACCESS_TOKEN}: 
```

</details>

<details>

<summary>Request Example Python SDK</summary>

{% code overflow="wrap" %}
```python
client.computations.rename_computation(
    computation_id=computation_id,
    name=new_name
)
```
{% endcode %}

</details>

## Run Capsule

<mark style="color:green;">`POST`</mark> `https://{domain}/api/v1/computations`

This API allows for the running of Capsules/Pipelines with Data Assets and Ordered or Named Parameters.

**Prerequisite**

Before using this API call, you may need AWS Cloud Credentials configured as Secrets or an Assumable Role, if you are using Data Assets from Cloud Resources.&#x20;

#### Request Body

| Name                                             | Type           |
| ------------------------------------------------ | -------------- |
| `capsule_id`<mark style="color:red;">`*`</mark>  | string         |
| `pipeline_id`                                    | string         |
| `nextflow_profile`                               | string         |
| `data_assets`<mark style="color:red;">`*`</mark> | array\<dict>   |
|       `id`<mark style="color:red;">`*`</mark>    | string         |
|      `mount`                                     | string         |
| `parameters`                                     | array\<string> |
| `named_parameters`                               | array\<dict>   |
| `processes`                                      | array\<dict>   |

### **Scope**

| Type       | Permission |
| ---------- | ---------- |
| Capsule    | Read/Write |
| Data Asset | Read       |

<details>

<summary>Request Example Bash</summary>

```bash
curl -X POST https://{domain}/api/v1/computations \
   -u "cop_d23dasd312": \
   -H "Content-Type: application/json" \
   --data-raw '{
     "capsule_id": "4bc97533-6eb4-48ac-966f-648548a756d2"
   }'
```

</details>

<details>

<summary><strong>Request Example Python SDK</strong></summary>

```python
from codeocean.computation import RunParams

run_params = RunParams(capsule_id="4bc97533-6eb4-48ac-966f-648548a756d2")

computation = client.computations.run_capsule(run_params)
```

</details>

<details>

<summary>Response</summary>

[Computation Object](computation.md#computation-object)

</details>

### Run Capsule with Data Assets and Ordered Parameters

<details>

<summary>Request Example Bash</summary>

```bash
curl -X POST "https://codeocean.[my-domain].com/api/v1/computations" \
   --header "Content-Type: application/json" \
   -u "cop_d23dasd312": \
   --data-raw '{
      "capsule_id":"eb082456-d031-4a42-80b0-f209b8728927",
      "data_assets" : [
        {
            "id": "eeefcc52-b445-4e3c-80c5-0e65526cd712",
            "mount": "Reference"
        }
    ],
       "parameters": [
         "75","1","HS25","SingleEnded","","","1","","","","","","","False","False"
       ]  
}'
```

</details>

<details>

<summary>Request Example Python SDK</summary>

```python
from codeocean.computation import RunParams, DataAssetsRunParam

data_assets=[
        DataAssetsRunParam(id="1az0c240-1a9z-192b-pa4c-22bac5ffa17b",
                              mount="Reference")
        ]    

run_params = RunParams(capsule_id="4bc97533-6eb4-48ac-966f-648548a756d2",
                       data_assets=data_assets,
                       parameters=[
                              "75","1","HS25","SingleEnded"
                              ]    
                )

computation = client.computations.run_capsule(run_params)
```

</details>

### Run Capsule with Data Assets and Named Parameters

<details>

<summary>Request Example Bash</summary>

```bash
curl -X POST "https://codeocean.[my-domain].com/api/v1/computations" \
   --header "Content-Type: application/json" \
   -u "cop_d23dasd312": \
   --data-raw '{
       "capsule_id":"4c4cd610-83bf-4a9b-9dfb-3faf6c29d11b",
       "data_assets" : [
        {
            "id": "9c5cf74f-196b-4ed1-868c-8cf95c1f7182",
            "mount": "Reference"
        }
    ],
       "named_parameters": [
		{
			"param_name": "NumberOfThreads",
			"value": "1"
		},
    {
			"param_name":"NumberOfFiles",
			"value": "10"
		} 
	]
}'
```

</details>

<details>

<summary>Request Example Python SDK</summary>

```python
from codeocean import CodeOcean
from codeocean.computation import RunParams, DataAssetsRunParam, NamedRunParam

data_assets=[
        DataAssetsRunParam(id="1az0c240-1a9z-192b-pa4c-22bac5ffa17b",
                              mount="Reference")
        ]    
      
named_parameters=[
              NamedRunParam(param_name="NumThreads",value="2")
                       ]

run_params = RunParams(
              capsule_id="4bc97533-6eb4-48ac-966f-648548a756d2",
              data_assets=data_assets,
              named_parameter=named_parameters    
               )

computation = client.computations.run_capsule(run_params)
```

</details>

### Run Pipeline

<details>

<summary>Request Example Bash</summary>

```bash
curl -X POST "https://codeocean.[my-domain].com/api/v1/computations" \
   --header "Content-Type: application/json" \
   -u "cop_d23dasd312": \
   --data-raw '{
     "pipeline_id": "4bc97533-6eb4-48ac-966f-648548a756d2"
    }'
```

</details>

<details>

<summary><strong>Request Example Python SDK</strong></summary>

```python
from codeocean.computation import RunParams, PipelineProcessParams

run_params = RunParams(
                pipeline_id="4bc97533-6eb4-48ac-966f-648548a756d2"
                )

computation = client.computations.run_capsule(run_params)
```

</details>

### Run Pipeline with Data Assets and Ordered Capsules

<details>

<summary>Request Example Bash</summary>

```bash
curl -X POST "https://codeocean.[my-domain].com/api/v1/computations" \
   --header "Content-Type: application/json" \
   -u "cop_d23dasd312": \
   --data-raw '{
       "pipeline_id":"e7a77780-b8ae-439e-89ac-fac2549da91b",
       "data_assets" : [
        {
            "id": "eeefcc52-b445-4e3c-80c5-0e65526cd712",
            "mount": "Reference"
        }
    ],
	"processes": [
		{
			"name": "capsule_art_simulation_illumina_1",
			"parameters": [
				"75","1","HS25","SingleEnded","","","1","","","","","","","False","False"
			]		
		},
		{
			"name": "capsule_copy_of_fast_qc_2",
			"parameters": [
				""
			]		
		}
	]
}'
```

</details>

<details>

<summary>Request Example Python SDK</summary>

```bash
from codeocean.computation import RunParams, DataAssetsRunParam, PipelineProcessParams

data_assets=[
        DataAssetsRunParam(id="1az0c240-1a9z-192b-pa4c-22bac5ffa17b",
                              mount="Reference")
        ]    
    
processes=[
          PipelineProcessParams(
                    name="capsule_star_alignment_1",
                    parameters=[
                        "1","_R1_fastq.gz","R2_fastq.gz"
                        ]
                  )
        ]
        
run_params = RunParams(
                    capsule_id="4bc97533-6eb4-48ac-966f-648548a756d2",
                    data_assets=data_assets,
                    processes=processes    
               )

computation = client.computations.run_capsule(run_params)
```

</details>

### Run Pipeline with Data Asset and Named Capsules

<details>

<summary>Request Example Bash</summary>

```bash
curl -X POST "https://codeocean.[my-domain].com/api/v1/computations" \
   --header "Content-Type: application/json" \
   -u "cop_d23dasd312": \
   --data-raw '{
       "pipeline_id":"4c4cd610-83bf-4a9b-9dfb-3faf6c29d11b",
       "data_assets" : [
        {
            "id": "eeefcc52-b445-4e3c-80c5-0e65526cd712",
            "mount": "Reference"
        }
    ],
	"processes": [
		{
			"name": "capsule_np_create_files_test_3",
			"named_parameters": [
				{
					"param_name": "NumFiles",
					"value": "1"
				} 
			]
		},
		{
			"name": "capsule_np_add_number_test_gh_4",
			"named_parameters": [
				{
					"param_name": "AddNumber",
					"value": "1"
				} 
			]
		}
	]
}'
```

</details>

<details>

<summary>Request Example Python SDK</summary>

```bash
from codeocean.computation import (
                   RunParams, 
                   DataAssetsRunParam, 
                   PipelineProcessParams,
                   NamedRunParam
                 )

data_assets=[
        DataAssetsRunParam(id="1az0c240-1a9z-192b-pa4c-22bac5ffa17b",
                              mount="Reference")
        ]    
    
processes=[
          PipelineProcessParams(
                    name="capsule_bwa_alignment_5",
                    named_parameters=[
                          NamedRunParam(param_name="NumThreads",value="2")
                           ]
        ]
        
run_params = RunParams(
                    capsule_id="4bc97533-6eb4-48ac-966f-648548a756d2",
                    data_assets=data_assets,
                    processes=processes    
               )

computation = client.computations.run_capsule(run_params)
```

</details>

### Run Pipeline with Data Assets and Ordered + Named Capsules

<details>

<summary>Request Example Bash</summary>

```bash
curl -X POST "https://codeocean.[my-domain].com/api/v1/computations" \
   --header "Content-Type: application/json" \
   -u "cop_d23dasd312": \
   --data-raw '{
       "pipeline_id":"cd4ef788-b404-4406-8bda-76b5e41a7b8d",
       "data_assets" : [
        {
            "id": "eeefcc52-b445-4e3c-80c5-0e65526cd712",
            "mount": "Reference"
        }
    ],
    "processes": [
		{
			"name": "capsule_art_simulation_illumina_1",
			"parameters": [
				"75","1","HS25","SingleEnded","","","1","","","","","","","False","False"
			]		
		},
		{
			"name": "capsule_np_create_files_test_3",
			"named_parameters": [
				{
					"param_name": "NumFiles",
					"value": "1"
				} 
			]
		},
	]
}'
```

</details>

<details>

<summary><strong>Request Example Python SDK</strong></summary>

```python
from codeocean.computation import (
                   RunParams, 
                   DataAssetsRunParam, 
                   PipelineProcessParams,
                   NamedRunParam
                 )

data_assets=[
        DataAssetsRunParam(id="1az0c240-1a9z-192b-pa4c-22bac5ffa17b",
                              mount="Reference")
        ]    
    
processes=[
          PipelineProcessParams(
                    name="capsule_bwa_alignment_5",
                    named_parameters=[
                          NamedRunParam(param_name="NumThreads",value="2")
                           ],
         PipelineProcessParams(
                    name="capsule_star_alignment_1",
                    parameters=[
                        "1","_R1_fastq.gz","R2_fastq.gz"
                        ]  
        ]
        
run_params = RunParams(
                    capsule_id="4bc97533-6eb4-48ac-966f-648548a756d2",
                    data_assets=data_assets,
                    processes=processes    
               )

computation = client.computations.run_capsule(run_params)
```

</details>
