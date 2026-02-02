---
description: Learn how to enable MLflow tracking in Capsules and Pipelines.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/ml-flow/enable-mlflow-tracking
---

# Enable MLflow Tracking

## Prerequisites

Ensure MLflow is enabled in your Code Ocean deployment. If it is, you will see the MLflow icon to enter the MLflow tracking server dashboard via the Navigation sidebar. Reach out to your Code Ocean admin if you require MLflow to be enabled.&#x20;

## Enable MLflow Tracking in a Capsule

Enabling MLflow tracking in a Capsule ensures that models created in that Capsule can be tracked, managed, and deployed using MLflow. &#x20;

To enable MLflow tracking within your Capsule:

1. Open the Capsule in which you want to enable MLflow tracking.&#x20;
2. Open the **Capsule Settings** panel from the top right corner.
3. Navigate to the **MLflow** tab.
4. Enable tracking by toggling ON “**Track this Capsule**”.&#x20;
5. Add MLflow Code: Include the necessary MLflow tracking code in your Capsule’s training script. See more information below.
6. Run your Capsule. MLflow will automatically create a new experiment in your tracking server, and all runs will be tracked accordingly.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXecHoxmqo7TGRMdGZSrlsArCOfKVY9hJMtx8hbhNVALKPqT6dEwoJ1ZYlzuXktpICkSHIvDvAUt1qKf9q4PbdUG5NTmAk4oCbT6rS7glgdVdW5nmY4jRuPCRgYy15wL3PjZpspozaaqAbjGN06U9OFHhQ2j?key=V2mion4JrIuNYQV2joZ06w" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
For Capsules running MLflow created prior to Code Ocean 4.2, you may need to update the MLflow package to maintain compatibility. Code Ocean 4.2 and newer versions run MLflow v3.6.&#x20;
{% endhint %}

### To start tracking models, add the following snippets to your training code:

```
# python for libraries that support autologging: Fastai, Gluon, Keras, LightGBM, PyTorch, Scikit-learn, Spark, Statsmodels, XGBoost,  just use autolog

import mlflow
mlflow.autolog()

# If possible, it is recommended to add the name of the library before autolog:
# example :
import mlflow
mlflow.fastai.autolog()

# other libraries that do not support autologging can still be logged using the convention:
(for example for 'prophet'):
with mlflow.start_run():
   mlflow.prophet.log_model(model, "model")
   mlflow.log_param("seasonality_mode", params["seasonality_mode"])
   
   mlflow.log_metric("mae", mae)
   df.to_csv("data.csv", index=False)
   mlflow.log_artifact("data.csv", artifact_path="data")
   forecast.to_csv("forecast.csv", index=False)
   mlflow.log_artifact("forecast.csv", artifact_path="forecast")

Usage with R:

# Install and load the MLflow package
install.packages("mlflow")
library(mlflow)

# Start a MLflow run
mlflow_start_run()
mlflow_log_param("learning_rate", 0.01)
mlflow_log_metric("rmse", 0.02)
model <- lm(mpg ~ ., data = mtcars)
model_path <- "lm_model"
saveRDS(model, model_path)
mlflow_log_artifact(model_path)
mlflow_end_run()

Usage with JAVA:

xml
<dependency> 
<groupId>org.mlflow</groupId> <artifactId>mlflow-client</artifactId> <version>1.29.0</version> 
</dependency>
java
import org.mlflow.api.proto.Service.*;
import org.mlflow.tracking.MlflowClient;

public class MLflowExample {
public static void main(String[] args) {
MlflowClient client = new MlflowClient("http://localhost:5000");
String experimentId = client.createExperiment("MyExperiment");
RunInfo runInfo = client.createRun(experimentId);
String runId = runInfo.getRunId();

client.logParam(runId, "learning_rate", "0.01");
client.logMetric(runId, "rmse", 0.02);
client.logArtifact(runId, new File("path/to/your/model"));
client.setTerminated(runId);
}
}
```

It is recommended to give a run a name, by adding mlflow.start\_run(run\_name =“run name”), otherwise, MLflow gives each run a random name.&#x20;

{% hint style="info" %}
MLflow’s autolog feature automatically tracks key information from machine learning models during training, including parameters, metrics, and model artifacts, without requiring much manual coding. When using autolog, MLflow automatically captures these details for supported libraries like TensorFlow, PyTorch, and Scikit-learn. For libraries with specific autolog implementations (e.g., mlflow.sklearn.autolog()), this can provide deeper integration by logging library-specific details and configurations. However, it’s important to ensure that the library’s version is compatible with MLflow’s autologging, and to monitor for potential performance issues or unintended behavior, such as logging excessive data or missing custom metrics.
{% endhint %}

## **Enable MLflow Tracking in a Pipeline**

MLflow model tracking integrates seamlessly with Code Ocean Pipelines, taking advantage of Nextflow’s powerful parallel processing capabilities.&#x20;

To enable MLflow tracking within your Pipeline, you can add a tracked Capsule to your Pipeline, or start tracking a Capsule that is already part of your Pipeline. Run your Pipeline and MLflow will automatically create a new experiment in your tracking server. All runs will be tracked accordingly.&#x20;

See [Enable MLflow Tracking in a Capsule](enable-mlflow-tracking.md#enable-mlflow-tracking-in-a-capsule) above for more information on how to track a Capsule using MLflow.&#x20;

{% hint style="info" %}
MLflow tracking is only supported in Pipelines built with the Code Ocean Pipelines Builder UI and is not supported in custom Pipelines.&#x20;
{% endhint %}
