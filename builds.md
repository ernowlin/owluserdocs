# Builds

Starting in 2022.04 the builds will follow a new naming convention to designate which optional drivers are packaged.  This is a requirement to only deliver containers with specific jar files.&#x20;

{% hint style="info" %}
**Please note the optional drivers only impact container versions of Collibra Data Quality and does not impact Standalone installation packages.**
{% endhint %}

## **Available Containers**

<details>

<summary><strong>2022.05</strong></summary>

#### Collibra Data Quality

2022.04-L-303&#x20;

#### Spark

3.2.0-2022.04-L-303&#x20;

</details>

<details>

<summary>2022.04</summary>

**Collibra Data Quality**

2022.04-L-303 \
2022.04-AL-302 \
2022.04-296 \
2022.04-A-295 \
2022.04-ALL-294 2\
022.04-ABHGCSGCRS-291

**Spark**

3.2.0-2022.04-L-303 \
****3.2.0-2022.04-AL-302 \
3.2.0-2022.04-296 \
3.2.0-2022.04-A-295 \
3.2.0-2022.04-ALL-294 \
3.2.0-2022.04-ABHGCSGCRS-291

</details>

{% hint style="warning" %}
The default build is considered the secure build with no optional drivers included.
{% endhint %}

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
