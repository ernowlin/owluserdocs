# Spark-shell Sample

`./bin/spark-shell --jars /opt/owl/bin/owl-core-trunk-jar-with-dependencies.jar,/opt/owl/drivers/postgres/postgresql-42.2.5.jar --deploy-mode client --master local[*]`

Import lib’s, if you get a dependency error, please import a second time.

`import com.owl.core.util.{OwlUtils, Util}`

`import com.owl.common.domain2.OwlCheckQ`

`import com.owl.common.options._`

Set up connection parameters to the database we want to scan if you don’t already have a dataframe

`val`` `_`url`_` ``= "jdbc:postgresql://xxx.xxx.xxx.xxx:xxxx/db?currentSchema=schema"`\
`val`` `_`connProps`_` ``=`` `_`Map`_`(`\
&#x20; `"driver" -> "org.postgresql.Driver",`\
&#x20; `"user" -> "user",`\
&#x20; `"password" -> "pwd",`\
&#x20; `"url" ->`` `_`url`_`,`\
&#x20; `"dbtable" -> "db.table"`\
`)`

Create a new OwlOptions object so we can assign properties

`val opt = new OwlOptions()`

Set up variables for ease of re-use

`val dataset = "nyse_notebook_test_final"`

`val runId = "2017-12-18"`

`var date = runId`

`var query = s"""select * from <table> where <date_col> = '`**`$`**`date' """`

`val pgDatabase = "dev"`\
`val pgSchema = "public"`

Set OwlOptions values to the metastore

`opt.`_`dataset`_` ``= dataset`\
`opt.`_`runId`_` ``= runId`\
`opt.`_`host`_` ``= "xxx.xxx.xxx.xxx"`\
`opt.`_`pgUser`_` ``= "xxxxx"`\
`opt.`_`pgPassword`_` ``= "xxxxx"`\
`opt.`_`port`_` ``= s"5432/`**`$`**`pgDatabase?currentSchema=`**`$`**`pgSchema"`

Create a connection, build the dataframe, register and run

With inline processing you will already have a dataframe so you can skip down to setting the OwlContext

`val conn =`` `_`connProps`_` ``+ ("dbtable" -> s"(`**`$`**`query)`` `**`$`**`dataset")`\
`val df =`` `_`spark`_`.read.format("jdbc").options(conn).load`

`val owl = OwlUtils.`_`OwlContext`_`(df, opt)`\
`owl.register(opt)`\
`owl.owlCheck`
