---
description: Learn to create, use, and share Data Assets in Code Ocean
metaLinks:
  alternates:
    - https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/data-assets-guide
---

# Data Assets Guide

Data Assets make it easy to share and find data within your organization and improve the performance of Capsule computations. A single Data Asset can simultaneously be used by multiple users across many Capsules or Pipelines. This is possible because Data Assets are independent cloud storage on AWS S3 or EFS. Data Assets are mounted to a Capsule with read only access, which reduces the Capsule's size and speeds up the computation.&#x20;

Code Ocean utilizes S3 Intelligent Tiering to automatically move data across 3 instant-access tiers and 2 archive tiers to optimize storage costs when access patterns change. This results in cost savings while maintaining the same performance as standard S3. Similarly, Code Ocean utilizes EFS Intelligent Tiering, which can automatically transition between Standard, Infrequent Access, and Archive based on access patterns to save on cost without compromising performance. These can be configured by the deployment Administrator.&#x20;



This guide covers the following:

1. Get to know the different [types of Data Assets](types-of-data-assets.md).&#x20;
2. How to [create a new Data Asset](adding-a-new-dataset.md).&#x20;
3. How to [capture a result](capturing-a-result/) as a Data Asset.
4. How to [attach and remove Data Assets from a Capsule](attaching-datasets-to-a-capsule.md).&#x20;
5. How to [find Data Assets](viewing-and-editing-data-assets/searching-a-data-asset.md).&#x20;
6. How to [manage Data Assets](viewing-and-editing-data-assets/)[. ](viewing-and-editing-data-assets/)

### Data Assets Overview

{% embed url="https://www.tella.tv/video/data-demo-1-aqns" %}

