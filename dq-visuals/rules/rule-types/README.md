# Rule Types

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQCoreComponents/Rule%20Types.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

## SQL-Based Rules

Depending on the complexity, you can choose from short-form or long-form rules.

#### **Simple**

Just the condition (short-form). For example, using the column email\_address. This runs against the dataframe and uses Spark SQL syntax. Simple rules can be thought of as everything after the where clause.

```
email_address is not null and email_address != '' 
```

#### Freeform

Where 'Simple' rules just use the condition, 'Freeform' rules use the complete SQL statement. When more complex SQL is required, you can express more with Freeform including joins, CTE's and window statements.

```
select * from @DATASET_NAME where 
email_address is not null and email_address != '' 
```

{% hint style="info" %}
All built-in spark functions are available to use. ([https://spark.apache.org/docs/2.3.0/api/sql/](https://spark.apache.org/docs/2.3.0/api/sql/)) for simple and freeform sql rules.‌
{% endhint %}

#### Native

Native rules use the SQL dialect of the underlying connection and database. Files are not eligible for native SQL rules. This is ideal if you want to use pushdown profiling and you want to use existing SQL logic. When coupled with pushdown profiling, you can achieve a very minimal infrastructure footprint.

See the [native rules section](sql-based-rules/native-sql.md) for more details.

## Stat rules

Write rules against meta data and profiling stats. Complex counts and ratios can be referenced with simple syntax.

See the[ stat rules section ](stat-rules/)for more details.

### Data Type

* **Empty check**
  * Rule type: EMPTYCHECK
  * Description: Checking whether the target column has empty values or not
* **Null check**
  * Rule type: NULLCHECK
  * Description: Checking whether the target column has _NULL_ values or not
* **Date check**
  * Rule type: DATECHECK
  * Description: Checking whether the target column has only DATE values or not
* **Integer check**
  * Rule type: INTCHECK
  * Description: Checking whether the target column has only INTEGER values or not
* **Double check**
  * Rule type: DOUBLECHECK
  * Description: Checking whether the target column has only DOUBLE values or not
* **String check**
  * Rule type: STRINGCHECK
  * Description: Checking whether the target column has only STRING values or not.
* **Mixed datatype check**
  * Rule type: DATATYPECHECK
  * **Description:** ---
