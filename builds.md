# Builds

Starting in 2022.04 the builds will follow a new naming convention to designate which optional drivers are packaged.  This is a requirement to only deliver containers with specific jar files.&#x20;

{% hint style="info" %}
**Please note the optional drivers only impact container versions of Collibra Data Quality and does not impact Standalone installation packages.**
{% endhint %}

## **Available Packages**

#### Collibra Data Quality

2022.04-L-303&#x20;

2022.04-AL-302 2022.04-296&#x20;

2022.04-A-295 2022.04-ALL-294&#x20;

2022.04-ABHGCSGCRS-291

#### Spark

3.2.0-2022.04-L-303&#x20;

3.2.0-2022.04-AL-302 1.6 GB&#x20;

3.2.0-2022.04-296&#x20;

3.2.0-2022.04-A-295&#x20;

3.2.0-2022.04-ALL-294&#x20;

3.2.0-2022.04-ABHGCSGCRS-291&#x20;

## **Description**

Example: 2022.04-ABDGCSHLMS-302

2022-4: Release number

302 - It is unique build number appended every

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
