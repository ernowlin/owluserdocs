---
description: Learn how to create CDQ jobs in Databricks notebook.
---

# CDQ + Databricks

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQApis/CDQ%20+%20Databricks.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

### Introduction

This document provides how to guidance to help you to upload and add CDQ jars to a Databricks cluster and to run a CDQ job by invoking CDQ APIs (aka activities).

### Design

![Running CDQ jobs from Scala and Pyspark notebooks.](<../../../.gitbook/assets/3\_DQ\_Compute\_(Databricks)\_to\_Data\_(Delta Lake)\_to\_Control\_Plane.gif>)

### CDQ Environment Setup

In this section, we explain the steps involved in setting up your CDQ environment in Databricks. This is the first step towards invoking CDQ APIs in Databricks.

#### Step 1: Upload CDQ Core jar to Databricks

#### 1. Extract the core jar from owl package zipped file.

The first step is to get the CDQ jar file. Once you have the cdq jar package file, you can get the jars by running the following commands:

`tar -xvf package.tar.gz`\
\`\`**`example`**`: tar -xvf owl-2022.04-RC1-default-package-base.tar.gz`

Running this command instructs tar to extract the files from the zipped file. From the list of the files, you need to upload the owl-core-xxxx-jar-with-dependancies.jar to our Databricks file system which will be explained in the next section.

![Extracting the owl jar files from owl package zipped file.](<../../../.gitbook/assets/Screen Shot 2022-04-19 at 11.33.36 AM.png>)

#### Step 2. Upload the file to Databricks file system using UI

The jars should be manually uploaded in Databricks file system. Below is the quick summary of the steps. You can find more details about upload files in Databricks page: [https://docs.databricks.com/data/databricks-file-system.html](https://docs.databricks.com/data/databricks-file-system.html)\
[https://docs.databricks.com/data/databricks-file-system.html#access-dbfs](https://docs.databricks.com/data/databricks-file-system.html#access-dbfs)

1. Login to your Databricks account.
2. Click ![Data Icon](https://docs.databricks.com/\_images/data-icon.png) **Data** in the sidebar.
3. Click the **DBFS** button at the top of the page.
4. Upload the owl-core-xxxx-jar-with-dependancies.jar to your desired path.

\\

![Upload owl-core-xxxx-jar-with-dependancies.jar to DBFS.](<../../../.gitbook/assets/Screen Shot 2022-04-19 at 11.40.34 AM.png>)

#### Step 3. Install CDQ library in your Databricks cluster

![Install owl-core-xxxx-jar-with-dependancies.jar in your cluster.](<../../../.gitbook/assets/Screen Shot 2022-04-19 at 11.47.46 AM.png>)

Once this step is completed, you can create a workspace and start using CDQ APIs.\
\
\
**Step4. (Optional) Update datasource pool size**\
\*\*\*\*This step is only necessary if you get _PoolExhaustedException_ when you call CDQ APIs.\
To solve the issue you can simply update the connection pool size in the spark environment.\
\
`SPRING_DATASOURCE_POOL_MAX_WAIT=500`\
`SPRING_DATASOURCE_POOL_MAX_SIZE=30`\
`SPRING_DATASOURCE_POOL_INITIAL_SIZE=5`\
`\` Here is the documentation from Databricks about how to set up environment variables: [https://docs.databricks.com/clusters/configure.html#environment-variables](https://docs.databricks.com/clusters/configure.html#environment-variables)

![Add CDQ environment variables to Databricks's cluster](<../../../.gitbook/assets/Screen Shot 2022-05-30 at 3.40.43 PM.png>)

### CDQ Working Example in DataBricks

#### <mark style="color:blue;">Import Collibra DQ Library</mark>

```scala
import org.apache.spark.sql.SparkSession 
import org.apache.spark.sql.functions._ 
import org.apache.spark.sql.types._ 
import scala.collection.JavaConverters._ 
import java.util.Date
import java.time.LocalDate
import java.text.SimpleDateFormat
import spark.implicits._ 
import java.util.{ArrayList, List, UUID}
// CDQ Imports 
import com.owl.core.Owl 
import com.owl.common.options._
import com.owl.common.domain2._
import com.owl.core.util.OwlUtils
spark.catalog.clearCache
```

#### <mark style="color:blue;">Bringing Customer Data From Another Database</mark>

```scala
// Option 1: Bringing Customer Data From A File
val df = (spark.read
  .format("csv").option("header", true).option("delimiter", ",")
  .load("dbfs:/FileStore/nyse.csv")
)


// Option 2: Bringing Customer Data From A Database
val connProps = Map(
"driver" -> "org.postgresql.Driver", 
"user" -> "????", 
"password" -> "????",
"url" -> "jdbc:postgresql://xxx:0000/postgres",
"dbtable" -> "public.example_data") 
//--- Load Spark DataFrame ---//
 val df = spark.read.format("jdbc").options(connProps).load display(df)
display(df) // view your data

```

#### <mark style="color:blue;">Variables to setup CDQ metastore database location</mark>

```scala
val pgHost = "xxxx.amazonaws.com" 
val pgDatabase = "postgres" 
val pgSchema = "public"
val pgUser = "???????" 
val pgPass = "????"
val pgPort = "0000"
```

#### <mark style="color:blue;">Create Collibra DQ Test (Rules) and Detects Breaks</mark>

<mark style="color:orange;">Note: If the rules are already created and assigned to a dataset from UI, calling owlcheck() will automatically execute all the rules associated with the given dataset and there is no need to re-create the rule from notebook.</mark>

```scala
val dataset = "cdq_notebook_db_rules"
var date = "2018-01-11"

// Options
val opt = new OwlOptions()
opt.dataset = dataset
opt.runId = date
opt.host = pgHost
opt.port = pgPort
opt.pgUser = pgUser
opt.pgPassword = pgPass

opt.setDatasetSafeOff(false) // to enable historical overwrite of dataset

// Create a simple rule and assign it to dataset 
val simpleRule = OwlUtils.createRule(opt.dataset)
      simpleRule.setRuleNm("nyse-stocks-symbol")
      simpleRule.setRuleValue("symbol == 'BHK'")
      simpleRule.setRuleType("SQLG")
      simpleRule.setPerc(1.0)
      simpleRule.setPoints(1)
      simpleRule.setIsActive(1)
      simpleRule.setUserNm("admin")
      simpleRule.setPreviewLimit(8)

// Create a rule from generic rules that are created from UI:
val genericRule = OwlUtils.createRule(opt.dataset)
    genericRule.setRuleNm("exchangeRule") // this could be any name
    genericRule.setRuleType("CUSTOM") 
    genericRule.setPoints(1)
    genericRule.setIsActive(1)
    genericRule.setUserNm("admin")
    genericRule.setRuleRepo("exchangeCheckRule"); // Validate the generic rule name 
     //from UI
    genericRule.setRuleValue("EXCH") // COLUMN assosicate with the rule


// Pre Routine 
val cdq = com.owl.core.util.OwlUtils.OwlContext(df, opt)
cdq.removeAllRules(opt.dataset)
.register(opt)
.addRule(simpleRule)

// Scan
cdq.owlCheck()
val results =  cdq.hoot() // returns object Hoot, not a DataFrame
//See Json Results(Option for downstream processing)
println("--------------Results:----------------\n")
println(results) // optional

//Post Routine, See DataFrame Results (Option for downstream processing)
val breaks = cdq.getRuleBreakRows("nyse-stocks-symbol")
println("--------------Breaks:----------------\n")
display(breaks)

// Different Options for handling bad records
val badRecords = breaks.drop("_dataset","_run_id", "_rule_name", "owl_id")
display(badRecords)

val goodRecords = df.except(badRecords)
display(goodRecords)
```

#### <mark style="color:blue;">Write the breaks(bad records) DataFrame to a Parquet file</mark>

```scala
// Remove the file if it exists
dbutils.fs.rm("/tmp/databricks-df-example.parquet", true) 
breaks.write.parquet("/tmp/databricks-df-example.parquet")
```

Below image shows the code snippet and the result in Databricks:

![Create CDQ Test Rules In DataBricks](<../../../.gitbook/assets/Screen Shot 2022-04-20 at 2.18.09 PM (1).png>)

The breaks and the rules can be viewed in CDQ web as well.

![](<../../../.gitbook/assets/Screen Shot 2022-04-20 at 2.12.24 PM.png>)

#### <mark style="color:blue;">Create Collibra DQ Test (Profile)</mark>

```scala
val dataset = "cdq_notebook_nyse_profile"

val runList = List("2018-01-01", "2018-01-02", "2018-01-03", "2018-01-04", "2018-01-05", "2018-01-08", "2018-01-09", "2018-01-10")
for(runId <- runList) {
// Options
val opt = new OwlOptions()
opt.dataset = dataset
opt.host = pgHost
opt.port = pgPort
opt.pgUser = pgUser
opt.pgPassword = pgPass

val profileOpt = new ProfileOpt
profileOpt.on = true
profileOpt.setShape(true)
profileOpt.setShapeSensitivity(5.0)
profileOpt.setShapeMaxPerCol(10)
profileOpt.setShapeMaxColSize(10)
profileOpt.setShapeGranular(true)
profileOpt.behaviorEmptyCheck = true
profileOpt.behaviorMaxValueCheck = true
profileOpt.behaviorMinValueCheck = true
profileOpt.behaviorNullCheck = true
profileOpt.behaviorRowCheck = true
profileOpt.behaviorMeanValueCheck = true
profileOpt.behaviorUniqueCheck = true
profileOpt.behaviorMinSupport = 5 // default is 4
profileOpt.behaviorLookback = 5
options.profile = profileOpt

var date = runId
var df_1 = df.where($"TRADE_DATE"===s"$date")

//Scan
val cdq = OwlUtils.OwlContext(df_1, options)
cdq.register(opt)
cdq.owlCheck()
val profile = cdq.profileDF()
profile.show()
}
```

![CDQ Profile Run In Databricks](<../../../.gitbook/assets/Screen Shot 2022-04-21 at 10.30.21 AM (1).png>)

![The Profile result can be viewed in CDQ Web.](<../../../.gitbook/assets/Screen Shot 2022-04-21 at 10.27.59 AM.png>)

#### <mark style="color:blue;">Create Collibra DQ Test (Dupes)</mark>

```scala
val dataset = "cdq_notebook_db_dupe"
var date = "2018-01-11"

// Options
val opt = new OwlOptions()
opt.dataset = dataset
opt.runId = date
opt.host = pgHost
opt.port = pgPort
opt.pgUser = pgUser
opt.pgPassword = pgPass

opt.dupe.ignoreCase = true
opt.dupe.on = true
opt.dupe.lowerBound = 99
opt.dupe.include = Array("SYMBOL", "TRADE_DATE")

//Scan
val cdq = OwlUtils.OwlContext(df, opt)
cdq.register(opt)
cdq.owlCheck()

val dupesDf = cdq.getDupeRecords
dupesDf.show()
```

![CDQ Dupes Run In Databricks](<../../../.gitbook/assets/Screen Shot 2022-04-21 at 2.43.27 PM.png>)

![Dupes results can be viewed in CDQ Web.](<../../../.gitbook/assets/Screen Shot 2022-04-21 at 2.39.33 PM.png>)

#### <mark style="color:blue;">Create Collibra DQ Test (Outlier)</mark>

```scala
import scala.collection.JavaConverters._
import java.util
import java.util.{ArrayList, List, UUID}

val dataset = "cdq_notebook_db_outlier"
var date = "2018-01-11"

// Options
val opt = new OwlOptions()
opt.dataset = dataset
opt.runId = date
opt.host = pgHost
opt.port = pgPort
opt.pgUser = pgUser
opt.pgPassword = pgPass

opt.dupe.on = false

val dlMulti: util.List[OutlierOpt] = new util.ArrayList[OutlierOpt]
val outlierOpt = new OutlierOpt()
outlierOpt.combine = true
outlierOpt.dateColumn = "trade_date"
outlierOpt.lookback = 4
outlierOpt.key = Array("symbol")
outlierOpt.include = Array("high")
outlierOpt.historyLimit = 10
dlMulti.add(outlierOpt)

opt.setOutliers(dlMulti)

val cdq = OwlUtils.OwlContext(df, opt)
        .register(opt)

cdq.owlCheck
val outliers = cdq.getOutliers()
outliers.show
outliers.select("value")
```

### Known API Limitations

CDQ activities can not be called independently for the time being. owlCheck() function should be called before calling any of the activities. For example to get the profile DataFrame you should call below code snippet:

```
cdq.owlCheck()
cdq.getProfileDF()
```
