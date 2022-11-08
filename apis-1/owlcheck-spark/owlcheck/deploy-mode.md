---
description: Yarn and Cluster
---

# Deploy Mode

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQApis/Deploy%20Mode.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

### Deploy Mode Client

```
--deploy-mode client
```

### Deploy Mode Cluster

```
--deploy-mode cluster
```

### Job Stuck in ACCEPTED State

yarn.Client: Application report for application\_1557720962505\_0085 (state: ACCEPTED)\
yarn.Client: Application report for application\_1557720962505\_0085 (state: ACCEPTED)

If running in cluster mode make sure you are passing in the below

```bash
--deploy-mode cluster
--master yarn         # or spark master
-h 123.45.6.77:2181   # host to owl metastore
```
