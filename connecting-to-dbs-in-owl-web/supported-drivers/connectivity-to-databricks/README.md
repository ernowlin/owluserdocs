# Connectivity to Databricks

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DBConnection/Connectivity%20to%20Databricks.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

### There are three ways to utilize Databricks infrastructure with Collibra Data Quality.

* JDBC (Supported)
* Notebook/SDK (Supported)
* Spark Submit (Not Supported)

## **JDBC (Supported)**

{% hint style="info" %}
**Certification, support and optional packaging is available from 2022.05**
{% endhint %}

### URL

jdbc:databricks://**`<your-account-here>.`**.cloud.databricks.com:443/default;transportMode=http;ssl=1;httpPath=sql/protocolv1/o/3633393438801721/0915-195703-sh82m595;AuthMech=3;UID=token;PWD=**`<your-token-here>`**

### **Driver**

com.databricks.client.jdbc.Driver

### Credentials

`user: token`\
`password: <your-user-generated-token>`

### **Jar**

[https://databricks-bi-artifacts.s3.us-east-2.amazonaws.com/simbaspark-drivers/jdbc/2.6.27/DatabricksJDBC42-2.6.27.1048.zip](https://databricks-bi-artifacts.s3.us-east-2.amazonaws.com/simbaspark-drivers/jdbc/2.6.27/DatabricksJDBC42-2.6.27.1048.zip)\
`Version:` 2.6.27

Link to [Databricks download](https://databricks.com/spark/jdbc-drivers-download)\
Link to [older versions of Databricks JDBC ](https://www.databricks.com/spark/jdbc-drivers-archive)

## **Notebook (Supported)**

* Pyspark SDK
* Scala SDK
* [Example](https://dq-docs.collibra.com/apis-1/notebook/cdq-+-databricks)

Databricks no longer supports Run time 6.5 and 10.3. Therefore, CDQ Profile 2.45 is not runnable on Databricks.&#x20;

[https://docs.databricks.com/release-notes/runtime/10.3ml.html](https://docs.databricks.com/release-notes/runtime/10.3ml.html)

The following table shows the latest supported versions of CDQ Profiles and their matching Databricks Run times. (last updated: September 2022)\


<figure><img src="../../../.gitbook/assets/Screen Shot 2022-08-29 at 3.54.00 PM.png" alt=""><figcaption></figcaption></figure>

## **Spark Submit (Not Supported)**

* Spark Master URL
* Databricks Jobs API
  * Rest
  * UI
  * [Example](https://dq-docs.collibra.com/apis-1/notebook/cdq-+-databricks/dq-databricks-submit)

{% hint style="info" %}
While these are not officially supported, there is reference architecture and implementation pattern how to do a Databricks Job submission.
{% endhint %}
