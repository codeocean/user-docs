---
description: Learn about MLflow permissions.
metaLinks:
  alternates:
    - https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/ml-flow/mlflow-permissions
---

# MLflow Permissions

Capsule and Pipeline permissions automatically propagate to the associated MLflow experiment. Currently, this feature applies only to Capsules and Pipelines shared with individual users. Support for General Access permissions will be introduced in a future version.&#x20;

Please note that while Admins can view all Capsules and Pipelines within the deployment, they can only access those for which they have explicit permissions in MLflow.&#x20;

Additionally, while users with viewer permissions can run Capsules and Pipelines, MLflow does not permit users with read-only permissions to create runs. As a result, viewer runs for tracked Capsules and Pipelines will fail to log in MLflow. This applies exclusively to non-Release Capsules and Pipelines.&#x20;

### **Release Capsules and Pipelines**

In Code Ocean, users can only access their own runs in Release Capsules and Pipelines. To facilitate this same experience in MLflow, a separate experiment is created for each user with access to these Release Capsules and Pipelines.&#x20;

Viewers of Release Capsules and Pipelines can perform MLflow tracked runs and it is considered best practice for viewers to conduct these tracked runs in a Release version of the Capsule or Pipeline.
