---
description: >-
  The purpose of this page is to demonstrate DQ spark submit to Databticks
  cluster.
---

# DQ-Databricks Submit

### DQ Spark submit using the UI

#### Limitations

There are a few limitation to spark-submit jobs in Databricks listed in this section: [https://docs.databricks.com/jobs.html#create-a-job](https://docs.databricks.com/jobs.html#create-a-job)\
&#x20;Also, spark-submit is only on new clusters from both the UI via Jobs or calling the REST APIs. See Step 4 in: [https://docs.databricks.com/jobs.html#create-a-job](https://docs.databricks.com/jobs.html#create-a-job) where it lists that spark-submit is handled by new clusters only.\


Please note that these are only examples to demonstrate how to achieve DQ spark submit to Databricks's cluster. These paths are NOT supported in production and DQ team does NOT support any bug coverages or professional services or customer questions for these flows.&#x20;

#### Steps:

Here are the main steps to create and run a spark submit job from Databricks UI:

1- Grant the DQ's Database access to your Databricks's instance.

2- Upload DQ's jars in DBFS.

3-Setup environment variables for the new cluster.

4- Prepare DQ's Json payload.

5-Create and Run the job.

6- View the job's result in DQ web.



#### &#x20;Database access

The first step is to make sure  your Databricks instance has access to your DQ's Database. The whole subnet should be whitelisted to connect to the database. Here is a link to AWS Databricks documentation the subnet portion of the VPC setup\
[https://docs.databricks.com/administration-guide/cloud-configurations/aws/customer-managed-](https://docs.databricks.com/administration-guide/cloud-configurations/aws/customer-managed-vpc.html#subnets) [vpc.html#subnets](https://docs.databricks.com/administration-guide/cloud-configurations/aws/customer-managed-vpc.html#subnets)\
AWS should have the ability to whitelist a IP address range that would allow the two Databricks subnets where the nodes will be instantiated to connect

#### &#x20;Upload DQ's jars in DBFS

The jars should be manually uploaded in Databricks file system. The steps can be found on Databricks website.\


#### Environment variables for the new  cluster :

`These environment variables should be set on the new cluster.`&#x20;

`SPRING_DATASOURCE_URL=xx`\
`SPRING_DATASOURCE_USERNAME=xx`\
`SPRING_DATASOURCE_DRIVER_CLASS_NAME=xx`\
`LICENSE_KEY=xx // This is DQ's license key`

![Setting up DQ's environment variables for the new cluster.](<../../.gitbook/assets/Screen Shot 2022-04-12 at 10.44.35 AM.png>)

#### Json Payload&#x20;

Once the above steps are completed, you can submit a spark submit job with DQ's parameters. Payload parameters can be get from DQ's web Run command. You need to manually copy paste the params to prepare a json payload. Here is one sample:&#x20;

```
                     "--class",
                    "com.owl.core.cli.OwlCheck",
                    "dbfs:/FileStore/cdq/owl-core-2022.02-SPARK301-jar-with-dependencies.jar",
                    "-lib",
                    "dbfs:/FileStore/cdq/owl/drivers/postgres",
                    "-q",
                    "select * from xx.xxx",
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
                    "xxxx.xxxxxx.amazonaws.com:xxxx/postgres",
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

![Create a job in Databricks UI](<../../.gitbook/assets/Screen Shot 2022-04-12 at 10.36.06 AM.png>)

#### Check the result in DQ web:

Once the job is submitted you can login to your DQ's web instance and check the job in the jobs page.&#x20;

### Spark submit by invoking Databricks's Rest API

There are Public REST APIS available for the Jobs API with the latest version being: [https://docs.databricks.com/dev-tools/api/latest/jobs.html](https://docs.databricks.com/dev-tools/api/latest/jobs.html)

For this path we need to do the steps 1-4 of the the previous section and then call directly the rest API using postman or any other tool. So the two new steps are as below:

#### Steps:

1- Json Payload

2- Authentication

#### &#x20;Json payload&#x20;

Below is the sample Json payload:&#x20;

`POST /api/2.1/jobs/runs/submit HTTP/1.1`\
`Host:` [`xxxxxx.cloud.databricks.com`](http://dbc-9a4426da-9755.cloud.databricks.com)``\
`Content-Type: application/json`\
`Authorization: Bearer`` `~~`xxxxxxxxxxxxx`~~\
`Cache-Control: no-cache`\
`Postman-Token: xxxxxxxx`

<mark style="color:orange;">{</mark> <mark style="color:orange;"></mark><mark style="color:orange;">`"tasks": [ { "task_key": "CDQ-SparkSubmitCallFinal", "spark_submit_task": { "parameters": [ "--class", "com.owl.core.cli.OwlCheck", "dbfs:/FileStore/cdq/owl-core-2022.02-SPARK301-jar-with-dependencies.jar", "-lib", "dbfs:/FileStore/cdq/owl/drivers/postgres", "-q", "select * from public.agent", "-bhlb", "10", "-rd", "2022-03-16", "-driver", "owl.com.org.postgresql.Driver", "-drivermemory", "4g", "-cxn", "metastore", "-h", "xxxs.amazonaws.com:xxx/postgres", "-ds", "public.agent_2", "-deploymode", "cluster", "-owluser", "admin" ] }, "new_cluster": { "cluster_name": "", "spark_version": "7.3.x-scala2.12", "aws_attributes": { "zone_id": "us-east-1e", "first_on_demand": 1, "availability": "SPOT_WITH_FALLBACK", "spot_bid_price_percent": 100, "ebs_volume_count": 0 }, "node_type_id": "i3.xlarge", "spark_env_vars": { "SPRING_DATASOURCE_URL": "jdbc:postgresql://xxx-xx-xxs.amazonaws.com:xx/postgres", "SPRING_DATASOURCE_PASSWORD":"xxx", "SPRING_DATASOURCE_USERNAME":"xxx", "SPRING_DATASOURCE_DRIVER_CLASS_NAME":"org.postgresql.Driver", "LICENSE_KEY": "xxxx" }, "enable_elastic_disk": false, "num_workers": 8 }, "timeout_seconds": 0 } ] }`</mark>\ <mark style="color:orange;">``</mark>

![Authentication setup for Databricks Rest API](<../../.gitbook/assets/Screen Shot 2022-04-12 at 10.17.00 AM (1).png>)

#### View the job's result in DQ web

Like the previous section, the result of job run can be viewed in DQ's web.\


![DQ job submitted from Databricks API](https://lh5.googleusercontent.com/KJb5BNxvXE0I-Un7SFsTP3PkwptnKs2jG2GyeWKFyh7iYJilNOSgC0qP6pA\_NNWhisKpnQ-9R6e2M08MDW1-9gQhO4crWhdhLKO30Oppb0jCJBCPHb5KWsDFJG5pu26Ns7bYdaFl)
