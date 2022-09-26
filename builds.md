# Builds

Builds follow a naming convention to indicate which [optional](builds.md#optional-drivers) drivers are packaged.

{% hint style="info" %}
**Please note the optional drivers only impact container versions of Collibra Data Quality and does not impact Standalone installation packages.**
{% endhint %}

### **Available Containers**

<details>

<summary>2022.09</summary>

**Collibra Data Quality**

* 2022.09-ADGCSILM-1386
* 2022-09-ABDGCSILM-1387
* 2022.09-ABDGCSHILM-1388
* 2022.09-1390

**Spark**

* 3.2.2-2022.09-ADGCSILM-1386
* 3.2.2-2022.09-ABDGCSILM-1387
* 3.2.2-2022.09-ABDGCSHILM-1388
* 3.2.2-2022.09-1390

</details>

<details>

<summary>2022.08</summary>

**Collibra Data Quality**

* 2022.08-L-1132
* 2022.08-AHM-1133
* 2022.08-H-1134
* 2022.08-HM-1135
* 2022.08-D-1136
* 2022.08-AL-1137
* 2022.08-AD-1138
* 2022.08-ABGCSHMS-1139
* 2022.08-AGCSHLM-1140
* 2022.08-M-1141
* 2022.08-GCSL-1142
* 2022.08-ADH-1143

**Spark**

* 3.2.0-2022.08-L-1132
* 3.2.0-2022.08-AHM-1133
* 3.2.0-2022.08-H-1134
* 3.2.0-2022.08-HM-1135
* 3.2.0-2022.08-D-1136
* 3.2.0-2022.08-AL-1137
* 3.2.0-2022.08-AD-1138
* 3.2.0-2022.08-ABGCSHMS-1139
* 3.2.0-2022.08-AGCSHLM-1140
* 3.2.0-2022.08-M-1141
* 3.2.0-2022.08-GCSL-1142
* 3.2.0-2022.08-ADH-1143

</details>

<details>

<summary>2022.07</summary>

#### Collibra Data Quality

* 2022.07-L-939

<!---->

* 2022.07-AHM-940

<!---->

* 2022.07-H-941

<!---->

* 2022.07-HM-942

<!---->

* 2022.07-D-943

<!---->

* 2022.07-AL-944

<!---->

* 2022.07-AD-945

<!---->

* 2022.07-ABGCSHMS-947

<!---->

* 2022.07-M-946

#### Spark

* 3.2.0-2022.07-L-939

<!---->

* 3.2.0-2022.07-AHM-940

<!---->

* 3.2.0-2022.07-H-946

<!---->

* 3.2.0-2022.07-HM-942

<!---->

* 3.2.0-2022.07-D-943

<!---->

* 3.2.0-2022.07-AL-944

<!---->

* 3.2.0-2022.07-AD-945

<!---->

* 3.2.0-2022.07-ABGCSHMS-947

<!---->

* 3.2.0-2022.07-M-946

</details>

<details>

<summary>2022.06</summary>

**Collibra Data Quality**

* 2022.06-L-819
* 2022.06-AHM-820
* 2022.06-H-821
* 2022.06-HM-822
* 2022.06-D-823
* 2022.06-AL-824
* 2022.06-AD-825
* 2022.06-ABGCSHMS-826
* 2022.06-M-830

**Spark**

* 3.2.0-2022.06-L-819
* 3.2.0-2022.06-AHM-820
* 3.2.0-2022.06-H-821
* 3.2.0-2022.06-HM-822
* 3.2.0-2022.06-D-823
* 3.2.0-2022.06-AL-824
* 3.2.0-2022.06-AD-825
* 3.2.0-2022.06-ABGCSHMS-826
* 3.2.0-2022.06-M-830

</details>

<details>

<summary><strong>2022.05</strong></summary>

**Collibra Data Quality**

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

**Spark**

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

* 2022.04-L-303
* 2022.04-AL-302
* 2022.04-296
* 2022.04-A-295
* 2022.04-ALL-294 2
* 022.04-ABHGCSGCRS-291

**Spark**

* 3.2.0-2022.04-L-303
* 3.2.0-2022.04-AL-302
* 3.2.0-2022.04-296
* 3.2.0-2022.04-A-295
* 3.2.0-2022.04-ALL-294
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

## **Default Drivers**

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
