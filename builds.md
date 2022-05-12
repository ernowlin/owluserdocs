# Builds

Starting in 2022.04 the builds will follow a new naming convention to designate which optional drivers are packaged.  This is a requirement to only deliver containers with specific jar files.&#x20;

{% hint style="info" %}
**Please note the optional drivers only impact container versions of Collibra Data Quality and does not impact Standalone installation packages.**
{% endhint %}

## **Available Containers**

<details>

<summary><strong>2022.05</strong></summary>

#### Collibra Data Quality

* 2022.05-L-701
* 2022.05-AL-703
* 2022.05-L-714
* 2022.05-AL-715
* 2022.05-H-716
* 2022.05-AHM-717
* 2022.05-HM-718
* 2022.05-ABGCSHMS-719
* 2022.05-720 (Secure Build)

#### Spark

* 3.2.0-2022.05-L-701
* 3.2.0-2022.05-AL-703
* 3.2.0-2022.05-L-714
* 3.2.0-2022.05-AL-715
* 3.2.0-2022.05-H-716
* 3.2.0-2022.05-AHM-717
* 3.2.0-2022.05-HM-718
* 3.2.0-2022.05-ABGCSHMS-719
* 3.2.0-2022.05-720 (Secure Build)

</details>

<details>

<summary>2022.04</summary>

**Collibra Data Quality**

* 2022.04-L-303&#x20;
* 2022.04-AL-302&#x20;
* 2022.04-296&#x20;
* 2022.04-A-295&#x20;
* 2022.04-ALL-294 2
* 022.04-ABHGCSGCRS-291

**Spark**

* 3.2.0-2022.04-L-303&#x20;
* 3.2.0-2022.04-AL-302&#x20;
* 3.2.0-2022.04-296&#x20;
* 3.2.0-2022.04-A-295&#x20;
* 3.2.0-2022.04-ALL-294&#x20;
* 3.2.0-2022.04-ABHGCSGCRS-291

</details>

{% hint style="success" %}
The default build is considered the Secure Build with no optional drivers included and no critical vulnerabilities.
{% endhint %}

### Example Docker pull commands for a build with Livy

Docker pull [https://gcr.io/owl-hadoop-cdh/owl-agent:2022.05-L-714](https://gcr.io/owl-hadoop-cdh/owl-agent:2022.05-L-714)

Docker pull [https://gcr.io/owl-hadoop-cdh/owl-livy:3.2.0-2022.05-L-714](https://gcr.io/owl-hadoop-cdh/owl-livy:3.2.0-2022.05-L-714)

Docker pull [https://gcr.io/owl-hadoop-cdh/owl-web:2022.05-L-714](https://gcr.io/owl-hadoop-cdh/owl-web:2022.05-L-714)

Docker pull [https://gcr.io/owl-hadoop-cdh/spark:3.2.0-2022.05-L-714](https://gcr.io/owl-hadoop-cdh/spark:3.2.0-2022.05-L-714)

## **Description**

Example: 2022.04-ABDGCSHLMS-302

2022-4: Release number

302 - A unique build number appended&#x20;

## **Default Drivers**&#x20;

_Always Packaged_

* SQL Server
* Oracle
* Snowflake
* Redshift
* S3
* ADLS
* Postgres
* Mysql
* Teredata
* Sybase
* Db2
* Dremio

## **Optional Drivers**

_Please select drivers_

* ABGCSHLMS (Drivers Initial in alphabetical order):
  * A : Athena
  * B : BigQuery
  * D = Databricks
  * GCS : Google Cloud Storage Connector
  * H : Hive
  * L : Livy
  * M : MongoDB
  * S : Solr
