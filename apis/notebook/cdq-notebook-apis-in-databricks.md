# CDQ Notebook APIs in Databricks

### &#x20;Introduction

In this page we demonstrate the detailed steps to upload and add CDQ jars to a Databricks cluster and to run a CDQ job by invoking CDQ APIs.

### CDQ  Environment Setup&#x20;

In this section, we explain the steps to create a CDQ workspace in Databricks and to invoke different CDQ APIs for basic CDQ activities.

#### Step 1: Upload CDQ Core jar to Databricks

#### 1. Extract the core jar from owl package zipped file.

The first step is to get the CDQ jar file. Once you have the cdq jar package file, you can get the jars by running the following commands:&#x20;

`tar -xvf package.tar.gz`\
``**`example`**`: tar -xvf owl-2022.04-RC1-default-package-base.tar.gz`

Running this command instructs tar to extract the files from the zipped file. From the list of the files, you need to upload the owl-core-xxxx-jar-with-dependancies.jar to our Databricks file system which will be explained in the next section.

![Extracting the owl jar files from owl package zipped file.](<../../.gitbook/assets/Screen Shot 2022-04-19 at 11.33.36 AM.png>)

#### 2. Upload the file to Databricks file system using UI 

The jars should be manually uploaded in Databricks file system. Below is the quick summary of the steps. You can find more details about upload files in Databricks page:  [https://docs.databricks.com/data/databricks-file-system.html](https://docs.databricks.com/data/databricks-file-system.html)\
[https://docs.databricks.com/data/databricks-file-system.html#access-dbfs](https://docs.databricks.com/data/databricks-file-system.html#access-dbfs)

1. Login to your Databricks account.
2. Click ![Data Icon](https://docs.databricks.com/\_images/data-icon.png) **Data** in the sidebar.
3. Click the **DBFS** button at the top of the page.
4. Upload the owl-core-xxxx-jar-with-dependancies.jar to your desired path.

\


![Upload owl-core-xxxx-jar-with-dependancies.jar to DBFS.](<../../.gitbook/assets/Screen Shot 2022-04-19 at 11.40.34 AM.png>)

#### 3. Install CDQ library in your Databricks cluster



![Install owl-core-xxxx-jar-with-dependancies.jar in your cluster.](<../../.gitbook/assets/Screen Shot 2022-04-19 at 11.47.46 AM.png>)

Once this step is completed, you can create a workspace and start using CDQ APIs.\
\


### Working Example in DataBricks

#### <mark style="color:blue;">Import Collibra DQ Library</mark>

<mark style="color:orange;">`import org.apache.spark.sql.SparkSession`</mark> \ <mark style="color:orange;">`import scala.collection.JavaConverters._`</mark>\ <mark style="color:orange;">`import java.util.Date`</mark> \ <mark style="color:orange;">`import java.time.LocalDate`</mark> \ <mark style="color:orange;">`import java.text.SimpleDateFormat`</mark> \ <mark style="color:orange;">`import spark.implicits._`</mark>

<mark style="color:green;">`// Imports`</mark> \ <mark style="color:green;">``</mark><mark style="color:orange;">`import com.owl.core.Owl`</mark> \ <mark style="color:orange;">`import com.owl.common.options._`</mark>\ <mark style="color:orange;">`import com.owl.common.domain2._`</mark> \ <mark style="color:orange;">`import com.owl.core.util.OwlUtils`</mark>

<mark style="color:green;">`// Variables`</mark>\ <mark style="color:green;">``</mark>` `<mark style="color:orange;">``</mark> \ <mark style="color:orange;">`val pgHost = "xxx.amazonaws.com:xxx/postgres"`</mark>\ <mark style="color:orange;">`var pgDatabase = "postgres"`</mark>\ <mark style="color:orange;">`val pgSchema = "finance"`</mark> \ <mark style="color:orange;">`val pgUser = "xxxx"`</mark> \ <mark style="color:orange;">`val pgPass = "xxxx"`</mark>\ <mark style="color:orange;">`val pgPort = "xxxx/postgres?currentSchema=finance"`</mark>

<mark style="color:orange;">`spark.catalog.clearCache`</mark>&#x20;

#### <mark style="color:blue;">Bringing In Customer Data (From Another Database)</mark>

<mark style="color:orange;">`val connProps = Map ( "driver" -> "org.postgresql.Driver",`</mark> \ <mark style="color:orange;">`"user" -> "xx",`</mark> \ <mark style="color:orange;">`"password" -> "xxxx",`</mark>\ <mark style="color:orange;">`"url" -> "jdbc:postgresql://xxx:xxx/postgres",`</mark>\ <mark style="color:orange;">`"dbtable" -> "public.example_data" )`</mark>&#x20;

<mark style="color:green;">`//--- Load Spark DataFrame ---//`</mark>

&#x20;<mark style="color:orange;">`val df = spark.read.format("jdbc").options(connProps).load display(df)`</mark>\ <mark style="color:orange;">`display(df)`</mark>` `<mark style="color:green;">`// view your data`</mark>

#### <mark style="color:blue;">Create Collibra DQ Test</mark>

<mark style="color:green;">//Create a new OwlOptions object so we can assign properties</mark>

<mark style="color:green;"></mark>

<mark style="color:green;">//Set OwlOptions values to the metastore</mark>

<mark style="color:green;"></mark>

#### <mark style="color:blue;">Detects Breaks</mark>

#### <mark style="color:blue;">Cleanse the bad records</mark>

<mark style="color:blue;"></mark>
