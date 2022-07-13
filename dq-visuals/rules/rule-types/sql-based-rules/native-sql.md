---
description: >-
  With Native SQL expressions we provide capability to use your existing
  validation statements, even if they use database-specific
  (Postgre/DB2/Oracle/MSSQL/etc.) functions or expressions.
---

# Native

This is commonly used when using pushdown profiling and/or pre-existing SQL validations exist in a specific syntax. Native rules are often referred to as pushdown rules.

![](<../../../../.gitbook/assets/image (118).png>)

If you have rules already written in Oracle, Sybase, or DB2 syntax - Copy/Paste the rule directly into the Native SQL section.

When creating a Native SQL rule, keep the following in mind:

* The SQL query must be a valid expression that can be run as a subquery. To avoid pulling large amounts of data into memory, Collibra Data Quality will wrap your expression so it only fetches the number of rows returned. Rules should be written such that the query returns the anomalous rows.
* The SQL query must take less than 30 minutes to run. It is recommended to use partitioned columns for efficiency.
* When testing the SQL query from the app, it is helpful if it takes less than 30 seconds to run. You can add a limit to reduce query time, or test the query in your SQL Editor.

{% hint style="info" %}
Testing native rules can be done quickly by limiting the results or using an external SQL IDE as well.
{% endhint %}

{% hint style="warning" %}
This rule type is not eligible to store break records, just the score itself! Additionally the rule will apply the logic directly to the JDBC connection. Native rules will run on the entire population of the data, regardless of any scope set for the DQ job (-q flag defined in the scope section of Explorer). Any filter or predicate clause entered in the -q flag should be added to the logic of the Native rule as well.
{% endhint %}
