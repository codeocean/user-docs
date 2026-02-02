---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/setting-up-the-environment/compute-resources
---

# Compute Resources

A computation—whether a Reproducible Run or a Cloud Workstation session—runs as a Docker container occupying a compute slot on an EC2 instance in AWS. The instance type is determined by the Starter Environment you select, and will support either a general-purpose machine or one with GPU resources.

After selecting the Starter Environment, adjust the compute resources by choosing the number of slots to allocate for your computation. The default compute resource is based on the machine type of the starter environment.

{% hint style="info" %}
To optimize resource usage, the system shuts down Cloud Workstation sessions after a period of idleness, as configured by the admin (CPU usage <5%).
{% endhint %}

## Setting Compute Resources

1. From the Environment editor, click **Select Compute Resources**.
2. Select the allocation type.
3. Select the number of slots or specific instance type.
4. Click **Apply**.

![](<../.gitbook/assets/pick compute resource.gif>)

## Methods of Allocating Compute Resources

A Capsule allocates compute resources in two ways:&#x20;

* Flex
* Dedicated

### Flex Machine

Flex resources are the default option for running your Capsule. This method attempts to allocate the selected compute resource (slots) on a running worker machine in the deployment's fleet of workers. If none of them have enough available slots, a new machine is added to the fleet in order to meet the need. This allows low-intensity computations to run on the same EC2 instances to reduce the cost by avoiding turning on an additional instance.

Using flex resources ensures your organization gets the most value out of running machines in your deployment. When all slots become empty, i.e. there are no computations running on the EC2 instance, the EC2 instance will remain immediately available for computations for a short period of time then automatically shutdown. The period of time an unused flex worker will remain available before automatically shutting down is configured during initial deployment or upgrade, and the default time is 1 hour.&#x20;

{% hint style="info" %}
If you select a more powerful compute resource for a Capsule, it requires more available compute slots to launch a computation instantly. It may increase the chance of activating a new EC2 instance which could increase both cost and waiting time.
{% endhint %}

### Dedicated Machine

Selecting a dedicated machine launches a new Amazon EC2 instance exclusively for your computation. There are dedicated machines with a wide range of specifications, for example, CPUs from 0.5 GB RAM to 4000 GB RAM, to ensure that there are always resources available to match your needs.&#x20;

For AI/ML use cases, it is important to know how much of the available RAM is GPU-specific. This information is included in the description of every dedicated compute resource.

<figure><img src="../.gitbook/assets/gpu ram.webp" alt=""><figcaption></figcaption></figure>

Use dedicated machines when you have a computation with high compute demand or need a specific configuration for the EC2 instance. Keep in mind that it takes approximately two minutes to start up a new instance and the more powerful machine you choose, the higher the hourly cost (Refer to [AWS EC2 pricing website](https://aws.amazon.com/emr/pricing/) for more details). You also have the option to choose the spot instance to reduce cost.

The EC2 instance will shut down directly after the computation is complete that is, the machine will shut down immediately after the reproducible run ends or the Cloud Workstation session is closed.&#x20;

### Spot Instances

Spot instances allow you to provision unused capacity of a currently running dedicated machine at less than one tenth of the original cost. Since the machine is not reserved, your computation may be interrupted without notice.

## Provisioning sufficient resources

To determine if your capsule needs higher compute resources, you can monitor usage and RAM metrics in two ways:

1. At the top of your screen when in a Cloud Workstation<br>

![](<../.gitbook/assets/ram used.gif>)

2\.  In the Capsule Timeline after a Reproducible Run

<figure><img src="../.gitbook/assets/Screenshot 2025-04-10 at 1.39.50 PM (1).png" alt="" width="375"><figcaption></figcaption></figure>

If your computation exceeds the resources you’ve allocated in a Cloud Workstation, you will get an error message such as:

![](https://lh6.googleusercontent.com/ReIcFUQtiExJg7ofYRFQi4NjWjAvwCkgGZYxUs8hu6rgJKD-Nk5ByFvJVuoZs1wSh-Sa2lj4pSM7RhofKU9_dwfcezXBU6AdEZ05sXXXebsMDa4mv7vWPbr6l6zXFR6FRFgatz97hC2d4hhxQb4WV7Y)

If your computation exceeds allocated resources during a Reproducible Run, it will terminate abruptly. If there are no flex machines with more resources, you should use a dedicated machine. Start by slowly increasing the memory and cores of your dedicated machine depending on your use case.

## User Interface Feedback

If a compute resources is no longer available, the system displays a notification on the screen.

<figure><img src="../.gitbook/assets/UI NotAvailable.png" alt=""><figcaption></figcaption></figure>
