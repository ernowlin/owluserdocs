---
description: Create profiles based on a table, view, or file
---

# Profile (automatic)

{% hint style="info" %}
Users have the option to scan the entire dataset or users can apply custom filtering to select the depth (row filtering) and width (columns).
{% endhint %}

### Select the Scope

You can find detailed instructions about [selecting the scope](more/explorer-2.md#select-the-scope-and-define-a-query) in the Explorer section. You can run limits, by time, or full table scans if you have enough resources.

![](../.gitbook/assets/profile\_scope.gif)

### Select Options (or leave defaults)

![](<../.gitbook/assets/profile\_options (1).gif>)

### Save / Run

![Profile is on by default and is part of onboarding a dataset](<../.gitbook/assets/profile\_setup (1).gif>)

### View the Results

![](../.gitbook/assets/profile\_results.gif)

## Automatically Profile

Owl automatically profiles datasets over time to enable drill-in for detailed insights an automated data quality. A profile is just the first step towards an amazing amount of auto discovery. Visualize segments of the dataset and how how the dataset is changing over time.

Collibra Data Quality offers click or code options to run profiling.

## Dataset Profile

Collibra Data Quality creates a detailed profile of each dataset under management. This profile will later be used to both provide insight and automatically identify data quality issues.

![](<../.gitbook/assets/Screen Shot 2020-07-08 at 12.45.19 AM.png>)

### Pushdown Profiling

Collibra DQ can compute the Profile of a dataset either via Spark (default) or the Data Warehouse (Profile Pushdown) where the data lives as the engine. When the Profile is computed using the datasource DBMS the user can choose two levels of pushdown:

* Full Profile - Perform full profile calculation except for TopN
* Count - Only perform row and column counts

![](<../.gitbook/assets/pushdown (1).gif>)

{% hint style="info" %}
The following DBMS systems are supported for "Profile Pushdown"

* Impala
* Hive
* Snowflake
* Presto
* Teradata
* SQL Server
* Postgres
* Redshift
* Mysql
* Oracle
* DB2
{% endhint %}

{% hint style="danger" %}
Pushdown and parallel JDBC cannot be used together. If you are using pushdown, do not select the parallel JDBC option.
{% endhint %}

![](<../.gitbook/assets/Screen Shot 2020-05-07 at 7.28.25 PM.png>)

## Profile Insights

![](<../.gitbook/assets/Screen Shot 2020-05-07 at 7.33.16 PM.png>)

By gathering a variety of different statistics, Collibra DQ's profile can provide a great deal of insight about the dataset.

To see the difference between baseline (historical) and current values, Collibra DQ provides a **Delta %** change column. In the Delta % change column, data is represented in a pie chart for quick visualization of the changes.

To elaborate on the quality metrics:

The profile can discover attributes then helps delineate the relative metrics around numeric v. non-numeric discovered.&#x20;

* Filled - \[1] Integer - The percentage of data that is numeric (or non-numeric) in a numeric (or non-numeric) discovered column.&#x20;
* Mixed - \[String] Integer - The percentage of data that is non-numeric (or numeric) in a numeric (or non-numeric) discovered column.&#x20;
* Null - \[] - The percentage of data that has no value at all.
* Empty - \[""] - The percentage of data that has a string instance of zero length.

{% hint style="info" %}
Profile includes a range of statistics

* Actual Datatype
* Discovered Datatypes
* Percent Null
* Percent Empty
* Percent Mixed Types
* Cardinality
* Minimum
* Maximum
* Mean
* TopN / BottomN
* Value Quartiles
{% endhint %}

## Sensitive Data Detection (Semantic)

Collibra Data Quality can automatically identify any type of common PII columns.

{% hint style="info" %}
Collibra Data Quality is able to detect the following types of PII

* EMAIL
* PHONE
* ZIP CODE
* STATE CD
* CREDIT CARD
* GENDER
* SSN
* IP ADDRESS
* EIN
{% endhint %}

![](<../.gitbook/assets/Screen Shot 2020-07-08 at 12.37.10 AM.png>)

Once detected, Collibra Data Quality will tag the column in the Profile as the discovered type as well as automatically apply a rule. If the user can choose to decline any discovered tag by simply clicking on it and confirming the delete action. This action can also remove the rule associated with the tag.

![](<../.gitbook/assets/Screen Shot 2020-07-08 at 12.39.13 AM.png>)

## Correlation Matrix (Relationship)

Discover hidden relationships and measure the strength of those relationships.

![](../.gitbook/assets/owl-relationships.png)

## Histograms

Often the first step in a data science project is to segment the data. Collibra Data Quality automatically does this using histograms.

![](../.gitbook/assets/owl-histogram.png)

## Data Preview

After profiling the data, for those users with appropriate rights, Collibra Data Quality provides a glimpse of the dataset. The Data preview tab also provides a some basic insights such as highlights of Data Shape issues and Outliers (if enabled), and Column Filtergram visualization.

![](<../.gitbook/assets/Screen Shot 2020-05-07 at 7.57.29 PM.png>)
