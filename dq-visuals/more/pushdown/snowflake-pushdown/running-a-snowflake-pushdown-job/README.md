# Running a Snowflake Pushdown job

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQCoreComponents/Running%20a%20Snowflake%20Pushdown.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

{% hint style="info" %}
As of 2022.08, Snowflake Pushdown is only available as a private beta for participating customers. Since this is a beta feature, some capabilities may be limited.&#x20;
{% endhint %}

This section shows you how to get started with the three scanning methods of a Snowflake Pushdown job.

## Getting started

1. From Explorer, select your Snowflake connection with the ![](../../../../../.gitbook/assets/dq-pushdown-icon.png) icon next to it.\
   **Note:** For the ![](../../../../../.gitbook/assets/dq-pushdown-icon.png) icon to be visible, you need to enable Pushdown when you establish your Snowflake connection.
2. Select your schema.
3. Click Create DQ Job.\
   \>> The Job creator page opens.
4. Select a scanning method. Since the steps and procedures vary by scanning method, refer to the documentation associated with each scanning method for further instructions.

| Scanning method                           | Description                                                                              |
| ----------------------------------------- | ---------------------------------------------------------------------------------------- |
| [Full Scan](running-a-full-scan.md)       | Scans your full table to show all results. This is the standard scanning method.         |
| [Partial Scan](running-a-partial-scan.md) | Scans a section of your table for more targeted results than a full scan.                |
| [SQL Query](scanning-with-sql-query.md)   | Allows you to manually write and compile a SQL query for an advanced scan of your table. |

{% hint style="info" %}
**Note:** More advanced layers beyond basic profile jobs will soon be available to customers participating in the private beta.
{% endhint %}

### AdaptiveRules

AdaptiveRules are common metrics used to observe changes to your data. These can be applied or removed from the AdaptiveRules tab on the Add Layers workflow by selecting or deselecting AdaptiveRules.&#x20;

The following table shows a list of AdaptiveRules measured by Collibra Data Quality and whether they are applied by default.

| AdaptiveRule type | Subtype      | Description                                                           | Default? |
| ----------------- | ------------ | --------------------------------------------------------------------- | -------- |
| **Availability**  | N/A          | Observe changes to the row count and loading time in your table.      | N/A      |
|                   | Row count    | Monitor the row count change in your table.                           | True     |
|                   | Loading time | Monitor loading time changes.                                         | False    |
| **Distribution**  | N/A          | Observe the number of unique values in a table.                       | N/A      |
|                   | Uniqueness   | Monitor a column's cardinality within the range of previous DQ Jobs   | True     |
| **Conformity**    | N/A          | Observe columns with values that fall outside of the normal range.    | N/A      |
|                   | Min          | Monitor columns with min values outside the normal range.             | False    |
|                   | Mean         | Monitor columns with mean values outside the normal range.            | False    |
|                   | Max          | Monitor columns with max values outside the normal range.             | False    |
| **Completeness**  | N/A          | Observe columns in your table containing null values or empty fields. | N/A      |
|                   | Null values  | Monitor columns for null values.                                      | True     |
|                   | Empty values | Monitor columns for empty data.                                       | True     |

{% hint style="info" %}
You can always apply or remove AdaptiveRules, but if you bypass the configuration, the DQ Job will still run correctly with the default AdaptiveRules applied.
{% endhint %}

### Shapes

A shape is the format of data in a string column. Enabling Shapes lets you discover inconsistencies in the data formats of a column. For example, when analyzing a date column, Collibra DQ may detect different string formats of the same meaning, such as 11-15-2022, 11/15/2022, and 11.15.2022.&#x20;

The Shapes feature is on by default, but you can choose to toggle it off. You can also manually control the advanced options by checking the Manual checkbox.&#x20;

| Option                  | Description                                                                                                                                                                                                            |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Occurrences**         | Set occurrences between 0.001-5 to show shapes that occur less than the percentage you set.                                                                                                                            |
| **Format per column**   | Set format per column between 0-100 to identify columns with more formats than the number you set. This helps identify columns that are too noisy, meaning they do not have a consistent format for detection.         |
| **Character length**    | Set character length between 0-100 to identify string lengths that are greater than the number you set. Character lengths beyond the set value are considered free from fields and do not have a format for detection. |
| **Data shape granular** | Considers the length of the shape and differentiates between numerical and letter formats. For the length of a shape to be detected, data shape granular must be enabled.                                              |

### Replay

Replay gives you a historical behavior profile of your data by looking back into past runs to show how the data looked on a certain day, month, or year. To enable Replay, select the dropdown icon on the Run button and select **Replay**.&#x20;
