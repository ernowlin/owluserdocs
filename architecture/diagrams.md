---
description: Choosing your deployment
---

# Diagrams

{% hint style="info" %}
We're moving! To improve customer experience, the Collibra Data Quality User Guide is moving to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/Home.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](../) will remain accessible, but the DQ User Guide will be maintained exclusively in the Documentation Center following the 2022.11 release.&#x20;
{% endhint %}

## DQ Control to Compute to Data

As of March 2022, DQ Cloud is in private beta for select customers. General availability is expected by the end of Q2 2022. Available compute plane options will start with Collibra Edge submitting jobs to Rancher K3s and Hadoop platforms (Cloudera, Dataproc and EMR). Additional compute plane options will be added over time.

![](<../.gitbook/assets/1\_DQ\_Control\_to\_Compute\_to\_Data\_Plane (1).gif>)

## Pushdown DQ Control to Data

Exploratory at this time, Private Beta coming in 2022 Q3. Some features may be limited.

![](../.gitbook/assets/2\_Pushdown\_DQ\_Control\_to\_Data\_Plane.gif)

## Databricks to Data to DQ Control

Running DQ jobs from Scala and Pyspark notebooks is generally available.

![](<../.gitbook/assets/3\_DQ\_Compute\_(Databricks)\_to\_Data\_(Delta Lake)\_to\_Control\_Plane (1).gif>)
