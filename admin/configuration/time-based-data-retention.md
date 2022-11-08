---
description: Setup and Configuration
---

# Time Based Data Retention

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQAdmin/Time%20Based%20Data%20Retention.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

## **Setting up Retention Based Data Purge**

Retention based purge of data can be turned on to allow data to automatically be cleaned based on an organization's data retention policy.

### **Benefit**

Once enabled, what type of data is removed?

* data\_preview _(Drill-in records for rules, outliers, shapes, etc.)_
* dataset\_field _(profiling stats)_
* rule\_breaks _(Rule Exception records)_
* dataset\_scan _(Job Ledger)_

### **Setup**

In order to set up retention based data purge, three (3) environment variables need to be set up in the owl-env.sh configuration script. Note: a restart of the webapp is required for this configuration to take place.

* **cleaner\_retention\_enabled**
  * TRUE or FALSE on whether this feature is enabled
* **cleaner\_retention\_days**
  * Number of days to retain data
* **cleaner\_retention\_field**
  * Controls which field to use to select eligible dataset runs
  * Potential values
    * updt\_ts: consider the last time a dataset run was updated
    * run\_id: consider the run id field of the dataset

### Configuration

**Example configuration in owl-env.sh**

Organization wants to purge data where the updt\_ts is more than 1 year old

**In owl-env.sh, add the following lines**

```
export cleaner_retention_enabled=TRUE
export cleaner_retention_days=365
export cleaner_retention_field="updt_ts" 
```

### Config Map

```
autoClean: "false"
cleaner_retention_days: "180"
cleaner_retention_field: updt_ts
cleaner_retention_enabled: "true"
```

### Defaults for Auto Clean Process

{% hint style="info" %}
This is a separate rolling purge that is **distinct from the time-based retention.** This is **on by default** and uses the pre-defined limits below. You will see audit records for this clean-up process in the audit history of the admin console.
{% endhint %}

Separate from the time-based retention there is also a default auto clean mechanism that actively purges your old records. This is enabled by default and can be modified by use of the autoClean (AUTOCLEAN) boolean parameter.

```
AUTOCLEAN=false or autoClean="false" 

### Depending whether this is part of owl-env.sh 
### or the configMap of the web pod
```

These are the defaults. The row count threshold is the global limit when this is triggered. This is based on the records in the data\_preview table. The runs threshold and the dataset per row threshold are dataset-level limits that require a dataset to have at least 4 scans and at least 1000 rows.

This is an example using the owl-env.sh file to control these settings.

```
export AUTOCLEAN=true
export DATASETS_PER_ROW=1000
export RUNS_THRESHOLD=4
export ROW_COUNT_THRESHOLD=200000
```

**For example (using the settings above):**

When data\_preivew table has 200k rows\
Look for datasets with 1000+ rows in data\_prevew table\
And have at least 4 scans\
Then delete the oldest scan for those datasets

Auto clean and time-based retention run on a routine thread that triggers while the web application is running. It looks for clean-up candidates every few minutes when AUTOCLEAN=true or cleaner\_retention\_enabled=TRUE.
