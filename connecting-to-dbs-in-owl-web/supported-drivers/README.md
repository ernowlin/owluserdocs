---
description: A list of supported data source connection types.
---

# Supported Connections

{% hint style="info" %}
To access our old Supported Connections page, please [refer to 2022.03](https://dq-docs.collibra.com/v/2022.03/connecting-to-dbs-in-owl-web/supported-drivers).
{% endhint %}

## Production

The following is a list of drivers certified for production use.

### Database Connections - Currently Supported/Active

<table><thead><tr><th>Connection</th><th data-type="checkbox">Certified</th><th data-type="checkbox">Tested</th><th data-type="checkbox">Packaged</th><th data-type="checkbox">Optional packaging</th><th data-type="checkbox">Pushdown</th><th data-type="checkbox">Estimate job</th><th data-type="checkbox">Filtergram</th><th data-type="checkbox">Analyze data</th><th data-type="checkbox">Schedule</th><th data-type="checkbox">Spark agent</th><th data-type="checkbox">Yarn agent</th><th data-type="checkbox">Parallel JDBC</th><th data-type="checkbox">Session state</th><th data-type="checkbox">Kerberos password</th><th data-type="checkbox">Kerberos password manager</th><th data-type="checkbox">Kerberos keytab</th><th data-type="checkbox">Kerberos TGT</th><th data-type="checkbox">CRDB metastore</th><th data-type="checkbox">Standalone (non-Livy)</th></tr></thead><tbody><tr><td><strong>Athena</strong></td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>true</td></tr><tr><td><strong>Bigquery</strong></td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>true</td></tr><tr><td><strong>CockroachDB</strong></td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>true</td><td>true</td></tr><tr><td><strong>DB2</strong></td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>true</td></tr><tr><td><strong>Dremio</strong></td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>true</td></tr><tr><td><strong>Hive</strong></td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>true</td></tr><tr><td><strong>Impala</strong></td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>true</td></tr><tr><td><strong>MSSQL</strong></td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>true</td></tr><tr><td><strong>MYSQL</strong></td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>true</td></tr><tr><td><strong>Oracle</strong></td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>true</td></tr><tr><td><strong>Postgres</strong></td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>true</td></tr><tr><td><strong>Presto</strong></td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>true</td></tr><tr><td><strong>Redshift</strong></td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>true</td></tr><tr><td><strong>Snowflake</strong></td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>true</td></tr><tr><td><strong>Solr</strong></td><td>false</td><td>false</td><td>true</td><td>true</td><td>false</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>true</td></tr><tr><td><strong>Sybase</strong></td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td></tr><tr><td><strong>Teradata</strong></td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>true</td></tr></tbody></table>

### Database Connections - Currently Supported/Inactive

<table><thead><tr><th>Connection</th><th data-type="checkbox">Certified</th><th data-type="checkbox">Tested</th><th data-type="checkbox">Packaged</th><th data-type="checkbox">Optional packaging</th><th data-type="checkbox">Pushdown</th><th data-type="checkbox">Estimate job</th><th data-type="checkbox">Filtergram</th><th data-type="checkbox">Analyze data</th><th data-type="checkbox">Schedule</th><th data-type="checkbox">Spark agent</th><th data-type="checkbox">Yarn agent</th><th data-type="checkbox">Parallel JDBC</th><th data-type="checkbox">Session state</th><th data-type="checkbox">Kerberos password</th><th data-type="checkbox">Kerberos password manager</th><th data-type="checkbox">Kerberos keytab</th><th data-type="checkbox">Kerberos TGT</th><th data-type="checkbox">CRDB metastore</th><th data-type="checkbox">Standalone (non-Livy)</th></tr></thead><tbody><tr><td><strong>Greenplum</strong></td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>true</td></tr><tr><td><strong>MariaDB</strong></td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>true</td></tr></tbody></table>

## Under Evaluation

The following is a list of drivers which are under evaluation (not certified yet for production usage). These connections are currently ineligible for escalated support services.&#x20;

### Database Connections - TechPreview

<table><thead><tr><th>Connection</th><th data-type="checkbox">Certified</th><th data-type="checkbox">Tested</th><th data-type="checkbox">Packaged</th><th data-type="checkbox">Optional packaging</th><th data-type="checkbox">Pushdown</th><th data-type="checkbox">Estimate job</th><th data-type="checkbox">Filtergram</th><th data-type="checkbox">Analyze data</th><th data-type="checkbox">Schedule</th><th data-type="checkbox">Spark agent</th><th data-type="checkbox">Yarn agent</th><th data-type="checkbox">Parallel JDBC</th><th data-type="checkbox">Session state</th><th data-type="checkbox">Kerberos state</th><th data-type="checkbox">Kerberos password manager</th><th data-type="checkbox">Kerberos keytab</th><th data-type="checkbox">Kerberos TGT</th><th data-type="checkbox">CRDB metastore</th><th data-type="checkbox">Standalone (non-Livy)</th></tr></thead><tbody><tr><td><strong>Cassandra</strong></td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td></tr><tr><td><strong>Databricks JDBC with Simba driver</strong></td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td></tr><tr><td><strong>MongoDB</strong></td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>true</td><td>false</td><td>true</td><td>true</td><td>true</td><td>true</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>true</td></tr><tr><td><strong>SAP Hana</strong></td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td></tr></tbody></table>

### Streaming Connections - TechPreview

<table><thead><tr><th>Connection</th><th data-type="checkbox">Certified</th><th data-type="checkbox">Tested</th><th data-type="checkbox">Packaged</th><th data-type="checkbox">Optional packaging</th><th data-type="checkbox">Pushdown</th><th data-type="checkbox">Estimate job</th><th data-type="checkbox">Filtergram</th><th data-type="checkbox">Analyze data</th><th data-type="checkbox">Schedule</th><th data-type="checkbox">Spark agent</th><th data-type="checkbox">Yarn agent</th><th data-type="checkbox">Parallel JDBC</th><th data-type="checkbox">Session state</th><th data-type="checkbox">Kerberos password</th><th data-type="checkbox">Kerberos password manager</th><th data-type="checkbox">Kerberos TGT</th><th data-type="checkbox">CRDB metastore</th><th data-type="checkbox">Standalone (non-Livy)</th></tr></thead><tbody><tr><td><strong>Kafka</strong></td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td><td>false</td></tr></tbody></table>

## Files

<table><thead><tr><th>File type</th><th data-type="checkbox">Supported</th></tr></thead><tbody><tr><td><strong>CSV (and all delimiters)</strong></td><td>true</td></tr><tr><td><strong>Parquet</strong></td><td>true</td></tr><tr><td><strong>AVRO</strong></td><td>true</td></tr><tr><td><strong>JSON</strong></td><td>true</td></tr><tr><td><strong>DELTA</strong></td><td>true</td></tr></tbody></table>

### **Limitations**

**Authentication**

* DQ Jobs that require Kerberos TGT are not yet supported on Spark Standalone or Local deployments
  * Recommended to submit jobs via Yarn or K8s

### **File Limitations**

**File Sizes**

* Files with more than 250 columns supported in File Explorer, unless you have Livy enabled.
* Files larger than 5gb are not supported in File Explorer, unless you have Livy enabled.&#x20;
* Smaller file sizes will allow for skip scanning and more efficient processing
* Advanced features like replay, scheduling, and historical lookbacks require a date signature in the folder of file path

**S3**

* Please ensure no spaces in S3 connection name
* Please remember to select 'Save Credentials' checkbox upon establishing connection
* Please point to **root** bucket, not sub folders

**Local Files**

* Local files can only be run using NO\_AGENT default
* This is for quick testing, smaller files, and demonstration purposes.&#x20;
* Local file scanning is not intended for large scale production use.

**Livy**

* [Livy](https://dq-docs.collibra.com/apis/rest-apis/livy) is only supported for K8s environments

#### Spark Engine Support

* MapR is EOL and MapR spark engine not supported to run CDQ jobs.

#### Databricks

The only supported Databricks spark submit option is to use a [notebook](../../dq-job-examples/data-quality-pipelines/aws-databricks-dq-pipeline.md) to initiate the job (Scala and Pyspark options).  This is intended for pipeline developers and users knowledgeable with Databricks and notebooks.  This form factor is ideal for incorporating data quality within existing Spark ETL data flows.  The results are still available for business users to consume.  The configuration is not intended for business users to implement.

{% hint style="warning" %}
Delta Lake and JDBC connectivity has been validated against Spark 3.01 CDQ package, Databricks 7.3 LTS and SparkJDBC41.jar.  This is available as Preview.  No other combinations have been certified at this time.
{% endhint %}

{% hint style="danger" %}
Spark submit using the Databricks spark master url is not supported.&#x20;
{% endhint %}
