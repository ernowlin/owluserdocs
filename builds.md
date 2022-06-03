# Builds

Builds follow a naming convention to indicate which [optional](builds.md#optional-drivers) drivers are packaged. &#x20;

{% hint style="info" %}
**Please note the optional drivers only impact container versions of Collibra Data Quality and does not impact Standalone installation packages.**
{% endhint %}

## **Available Containers**

<details>

<summary><strong>2022.05</strong></summary>

#### Collibra Data Quality

* 2022.05-L-714
* 2022.05-AL-715
* 2022.05-H-716
* 2022.05-AHM-717
* 2022.05-ABGCSHMS-719
* 2022.05-D-721
* 2022.05-AD-723
* 2022-05-BDG-751
* 2022.05.2-L-737
* 2022.05.2-AHM-738
* 2022.05.2-HM-739
* 2022.05.2-H-740

#### Spark

* 3.2.0-2022.05-L-714
* 3.2.0-2022.05-AL-715
* 3.2.0-2022.05-H-716
* 3.2.0-2022.05-AHM-717
* 3.2.0-2022.05-ABGCSHMS-719
* 3.2.0-2022.05-D-721
* 3.2.0-2022.05-AD-723
* 3.2.0.2022.05-BDG-751
* 3.2.0-2022.05.2-L-737
* 3.2.0-2022.05.2-AHM-738
* 3.2.0-2022.05.2-HM-739
* 3.2.0-2022.05.2-H-740

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

## Config Map Example

These are the configs to change the versions. For a complete list of versions for CDQ and Spark, refer to the Available Containers section above.

```
--set global.version.owl=2022.05-720 --set global.version.spark=3.2.0-2022.05-720
```

## Pull Examples

docker pull [https://gcr.io/owl-hadoop-cdh/owl-agent:2022.05-L-714](https://gcr.io/owl-hadoop-cdh/owl-agent:2022.05-L-714)\
docker pull [https://gcr.io/owl-hadoop-cdh/owl-livy:3.2.0-2022.05-L-714](https://gcr.io/owl-hadoop-cdh/owl-livy:3.2.0-2022.05-L-714)\
docker pull [https://gcr.io/owl-hadoop-cdh/owl-web:2022.05-L-714](https://gcr.io/owl-hadoop-cdh/owl-web:2022.05-L-714)\
docker pull [https://gcr.io/owl-hadoop-cdh/spark:3.2.0-2022.05-L-714](https://gcr.io/owl-hadoop-cdh/spark:3.2.0-2022.05-L-714)

## **Description**

Example: [2022.05-L-714](https://gcr.io/owl-hadoop-cdh/owl-agent:2022.05-L-714)

**2022-05**: Release number (Year and Month)\
**L**: Optional Livy package included\
**714** - A unique number appended to each build

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
