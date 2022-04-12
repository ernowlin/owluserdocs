---
description: >-
  This page contains two examples to achieve DQ spark submit to Databricks's
  cluster. Please note that these paths are NOT supported in production and DQ
  does NOT support bug coverages for these flows.
---

# DQ Spark Submit in Databricks

## DQ Spark submit using the UI

### Limitations

There are a few limitation to spark-submit jobs in Databricks listed in this section: [https://docs.databricks.com/jobs.html#create-a-job](https://docs.databricks.com/jobs.html#create-a-job)\
&#x20;Also, spark-submit is only on new clusters from both the UI via Jobs or calling the REST APIs. See Step 4 in: [https://docs.databricks.com/jobs.html#create-a-job](https://docs.databricks.com/jobs.html#create-a-job) where it lists that spark-submit is handled by new clusters only.\


### Steps:

Here are the main steps to create and run a spark submit job from Databricks UI:

1- Grant the DQ's Database access to your Databricks's instance.

2- Upload DQ's jars in DBFS.

3-Setup environment variables for the new cluster.

4- Prepare DQ's Json payload

5-Create and Run the job

6- View the job's result in DQ web.



#### &#x20;Database access

The first step is to make sure the instance of your Databricks has access to your DQ's Metastore Database. This could be archived by setting up security groups.\
The whole subnet should be whitelisted to connect to the database. Here is a link to AWS Databricks documentation the subnet portion of the VPC setup\
[https://docs.databricks.com/administration-guide/cloud-configurations/aws/customer-managed-](https://docs.databricks.com/administration-guide/cloud-configurations/aws/customer-managed-vpc.html#subnets) [vpc.html#subnets](https://docs.databricks.com/administration-guide/cloud-configurations/aws/customer-managed-vpc.html#subnets)\
AWS should have the ability to whitelist a IP address range that would allow the two Databricks subnets where the nodes will be instantiated to connect

#### &#x20;Upload DQ's jars in DBFS

The jars should be manually uploaded in Databricks file system.\


#### Environment variables for the new  cluster :

`SPRING_DATASOURCE_URL=xx`\
`SPRING_DATASOURCE_USERNAME=xx`\
`SPRING_DATASOURCE_DRIVER_CLASS_NAME=xx`\
`LICENSE_KEY=xx`

![Setting up DQ's environment variables for the new cluster.](<../../.gitbook/assets/Screen Shot 2022-04-12 at 10.44.35 AM.png>)

#### Json Payload&#x20;

Once the above steps are done, you can submit a spark submit job with the right DQ's parameters. Payload parameters are from DQ's web run command. You need to manually copy paste the params to prepare a json payload. Here is one sample:&#x20;

```
                     "--class",
                    "com.owl.core.cli.OwlCheck",
                    "dbfs:/FileStore/cdq/owl-core-2022.02-SPARK301-jar-with-dependencies.jar",
                    "-lib",
                    "dbfs:/FileStore/cdq/owl/drivers/postgres",
                    "-q",
                    "select * from public.agent",
                    "-bhlb",
                    "10",
                    "-rd",
                    "2022-03-16",
                    "-driver",
                    "owl.com.org.postgresql.Driver",
                    "-drivermemory",
                    "4g",
                    "-cxn",
                    "metastore",
                    "-h",
                    "owlpostgres.chzid9w0hpyi.us-east-1.rds.amazonaws.com:5432/postgres",
                    "-ds",
                    "public.agent_2",
                    "-deploymode",
                    "cluster",
                    "-owluser",
                    "admin"
                ]
```

#### Run the job

Once the above steps are completed, user can create a spark submit job through Databricks UI. The steps are detailed here: \
[https://docs.databricks.com/jobs.html](https://docs.databricks.com/jobs.html)\
Then user can add the environment variables to the cluster and click run on databticks UI.

![](<../../.gitbook/assets/Screen Shot 2022-04-12 at 10.36.06 AM.png>)

#### Check the result in DQ web:

Once the job is submitted you can login to your DQ's web instance and check the job in the jobs page.&#x20;

## Spark submit by invoking DataBricks's Rest API

There is a Public REST API available for the Jobs API with the latest version being: [https://docs.databricks.com/dev-tools/api/latest/jobs.html](https://docs.databricks.com/dev-tools/api/latest/jobs.html)

### Steps:

1- Authentication

2- Json Payload\


For this flow we need to do the steps 1-4 of the the previous section and then call directly the rest API using postman or any other software.

Below is the sample Json payload:&#x20;

POST /api/2.1/jobs/runs/submit HTTP/1.1\
Host: [dbc-9a4426da-9755.cloud.databricks.com](http://dbc-9a4426da-9755.cloud.databricks.com)\
Content-Type: application/json\
Authorization: Bearer dapid1f92bbd6b4e0c33270acb8a85b51fc7\
Cache-Control: no-cache\
Postman-Token: b3c14bff-05de-e1c1-4098-abd421bb9dc5

`1{ "tasks": [ 2 { 3 "task_key": "CDQ-SparkSubmitCallFinal", 4 "spark_submit_task": { 5 "parameters": [ 6 "--class", 7 "com.owl.core.cli.OwlCheck", 8 "dbfs:/FileStore/cdq/owl-core-2022.02-SPARK301-jar-with-dependencies.jar", 9 "-lib", 10 "dbfs:/FileStore/cdq/owl/drivers/postgres", 11 "-q", 12 "select * from public.agent", 13 "-bhlb", 14 "10", 15 "-rd", 16 "2022-03-16", 17 "-driver", 18 "owl.com.org.postgresql.Driver", 19 "-drivermemory", 20 "4g", 21 "-cxn", 22 "metastore", 23 "-h", 24 "owlpostgres.chzid9w0hpyi.us-east-1.rds.amazonaws.com:5432/postgres", 25 "-ds", 26 "public.agent_2", 27 "-deploymode", 28 "cluster", 29 "-owluser", 30 "admin" 31 ] 32 }, 33 "new_cluster": { 34 "cluster_name": "", 35 "spark_version": "7.3.x-scala2.12", 36 "aws_attributes": { 37 "zone_id": "us-east-1e", 38 "first_on_demand": 1, 39 "availability": "SPOT_WITH_FALLBACK", 40 "spot_bid_price_percent": 100, 41 "ebs_volume_count": 0 42 }, 43 "node_type_id": "i3.xlarge", 44 "spark_env_vars": { 45 "SPRING_DATASOURCE_URL": "jdbc:postgresql://owlpostgres.chzid9w0hpyi.us-east-1.rds.amazonaws.com:5432/postgres", 46 "SPRING_DATASOURCE_PASSWORD":"xxx", 47 "SPRING_DATASOURCE_USERNAME":"xxx", 48 "SPRING_DATASOURCE_DRIVER_CLASS_NAME":"org.postgresql.Driver", 49 "LICENSE_KEY": "ZZZZZZLNJXDQBZN24XKVHYAQ0YCSNK9NSQK1EEN6W1GPABDPDCRAXY:85O62HKN406B6JQTWMUITE2PUZHRURNJZQFSWCMP42O9XWSQ:65536" 50 }, 51 "enable_elastic_disk": false, 52 "num_workers": 8 53 }, 54 "timeout_seconds": 0 55 } 56 ]`\
``

![DQ's Spark submit by invoking databricks rest API.](<../../.gitbook/assets/Screen Shot 2022-04-12 at 11.37.00 AM.png>)
