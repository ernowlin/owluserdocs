# Connectivity to Databricks

### There are three ways to utilize Databricks infrastructure with Collibra Data Quality.

* JDBC (Supported)
* Notebook/SDK (Supported)
* Spark Submit (Not Supported)

## **JDBC (Supported)**

{% hint style="info" %}
**Certification, support and optional packaging is available from 2022.05**
{% endhint %}

### URL

`jdbc:spark://`**`<your-account-here>.`**`cloud.databricks.com:443/default;transportMode=http;ssl=1;httpPath=sql/protocolv1/o/639171477642820/0329-133041-8y8dbmh5;AuthMech=3;UID=token;PWD=`**`<your-token-here>`**

### **Driver**

`com.simba.spark.jdbc.Driver`

### Credentials

`user: token`\
`password: <your-user-generated-token>`

### **Jar**

`SimbaJDBC42.jar`\
`Version:` 2.6.22

Link to [Databricks download](https://databricks.com/spark/jdbc-drivers-download)\
Links to [older versions of Databricks JDBC ](https://www.databricks.com/spark/jdbc-drivers-archive)

## **Notebook (Supported)**

* Pyspark SDK
* Scala SDK
* [Example](https://dq-docs.collibra.com/apis-1/notebook/cdq-+-databricks)

## **Spark Submit (Not Supported)**

* Spark Master URL
* Databricks Jobs API
  * Rest
  * UI
  * [Example](https://dq-docs.collibra.com/apis-1/notebook/cdq-+-databricks/dq-databricks-submit)

{% hint style="info" %}
While these are not officially supported, there is reference architecture and implementation pattern how to do a Databricks Job submission.
{% endhint %}
