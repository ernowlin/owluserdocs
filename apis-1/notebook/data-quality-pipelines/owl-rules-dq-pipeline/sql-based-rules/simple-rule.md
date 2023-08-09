---
description: >-
  Simple rules would be applied to filter a condition on a single column in a
  single table.
---

# Simple rule

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQApis/simple-rule.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

## Example #1

In this example you can see how to create a simple SQL rule, with name **simple\_sql\_rule**.

| Code                                              | Description                                                                                   |
| ------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| rule.setRuleNm("**simple\_sql\_rule**")           | Adding the name of the given rule                                                             |
| rule.setRuleValue("**startDate < '2011-11-01'")** | <p>Setting the simple SQL expression.<br>No <strong>JOIN</strong> allowed between tables!</p> |
| rule.setRuleType("**SQLG**")                      | Setting the rule type                                                                         |

### Code

{% code title="example_simple_sql_rule.scala" %}
```scala
import com.owl.core.Owl
import com.owl.core.util.OwlUtils
import com.owl.common.bll.{RuleBll, RuleTemplateBll}
import com.owl.common.domain2.Rule
import com.owl.common.options.{LoadOpt, OwlOptions}

import org.junit.{Assert, Test}

import org.apache.spark.sql.SparkSession
import org.apache.spark.sql.functions._

val loadOptions = new LoadOpt {
  pghost = "localhost:5432/postgres"
  pguser = "username"
  pgpassword = "password"
}

//----- Init Spark ----- //
def sparkInit(): SparkSession = {
  val sparkSession = SparkSession.builder
    .master("local")
    .appName("test")
    .getOrCreate()

  sparkSession
}

def simpleRuleNotebook(): Unit = {

  // Arrange
  val spark = sparkInit()
  import spark.implicits._

  val headers = "firstName,lastName,startDate"
  val source = Seq(
    ("Thomas", "Martinez", "2010-11-01"),
    ("Harry", "Williams", "2012-05-01"),
    ("Ethan", "Davis", "2009-08-01")
  )
  val arr = headers.split(",")
  val df = source.toDF(arr: _*)

  val opt = new OwlOptions {
    runId = "2019-09-20"
    dataset = "simple_sql_rule_ds"
     load = loadOptions
  }

  val rule = new Rule {
    setDataset(opt.dataset)
    setRuleNm("simple_sql_rule")
    setRuleValue("startDate < '2011-11-01'")
    setRuleType("SQLG")
    setPerc(1.0)
    setPoints(1)
    setIsActive(1)
    setUserNm("admin")
  }

  val cdq = OwlUtils.OwlContext(df, opt)
    .register(opt)
  
  OwlUtils.addRule(rule)

  // Act
  cdq.owlCheck()

  // Assert
  import scala.collection.JavaConversions
  val hootRule = JavaConversions.asScalaBuffer(owl.hoot.rules).find(x => rule.getRuleNm.equals(x.getRuleNm)).orNull

}

// Execute notebook
simpleRuleNotebook()

```
{% endcode %}

### Result

#### via Code

You can do multiple assertion on the result of the OwlCheck process.\
Using **owl.hoot** parameter will provide access to the execution results, in this case for the rule

#### via UI

![Results of notebook execution on UI](<../../../../../.gitbook/assets/image (162).png>)

## Example #2

In this example you can see how to create a simple SQL with rule with **templates**, with name **simple\_sql\_rule\_with\_template**.

#### Steps

1.  Create the rule template, where the template column name should be marked with **$colNm** string.\\

    ```scala
    val ruleTemplate = RuleTemplateBll.createRuleTemplate(
        "not_null_or_empty",
        "Column cannot contain null or empty values", 
        " $colNm is null or $colNm = \'\' or $colNm  = \'null\' "
    )
    ```
2.  Create the Rule instance, where value of **RuleValue** will be used to replace **$colNm** in the template expression.\\

    ```scala
    val rule = OwlUtils.createRule(opt.dataset)
    rule.setRuleNm("is_city_not_null_or_empty")
    rule.setRuleValue("city")
    rule.setRuleType("CUSTOM") // legacy type required to look into rule repo
    rule.setRuleRepo("not_null_or_empty") // custom rule name to pull rule value from rule repo
    rule.setPerc(1.0)
    rule.setPoints(1)
    rule.setIsActive(1)
    rule.setUserNm("admin")
    ```

### Code

```scala
import com.owl.core.Owl
import com.owl.core.util.OwlUtils
import com.owl.common.bll.{RuleBll, RuleTemplateBll}
import com.owl.common.domain2.Rule
import com.owl.common.options.{LoadOpt, OwlOptions}

import org.junit.{Assert, Test}

import org.apache.spark.sql.SparkSession
import org.apache.spark.sql.functions._

val loadOptions = new LoadOpt {
  pghost = "localhost:5432/postgres"
  pguser = "username"
  pgpassword = "password"
}

//----- Init Spark ----- //
def sparkInit(): SparkSession = {
  val sparkSession = SparkSession.builder
    .master("local")
    .appName("test")
    .getOrCreate()

  sparkSession
}

 def simpleRuleWithTemplate(): Unit = {

  // Arrange
  val spark = sparkInit()
  import spark.implicits._

  val headers = "firstName,lastName,city"
  val source = Seq(
    ("Thomas", "Martinez", ""),
    ("Harry", "Williams", null),
    ("Ethan", "Davis", "Los Angeles")
  )
  val arr = headers.split(",")
  val df = source.toDF(arr: _*)

  val opt = new OwlOptions {
    runId = "2019-09-20"
    dataset = "simple_sql_rule_with_template_ds"
    onReadOnly = false
    load = loadOptions
  }
  // create a generic rule
  val ruleRepoName = "not_null_or_empty"
  val ruleRepo = OwlUtils.createRuleTemplate(ruleRepoName, "Column cannot contain null or empty values", "$colNm is null or $colNm = \'\' or $colNm  = \'null\'")
  Util.RuleRepoDaoFactory().delete(ruleRepo)
  val cdq = OwlUtils.OwlContext(df, opt)

  cdq.addRuleTemplate(ruleRepo)
  
  val rule = OwlUtils.createRule(opt.dataset)
  rule.setRuleNm("is_city_not_null_or_empty")
  rule.setRuleValue("city")
  rule.setRuleType("CUSTOM") // legacy type required to look into rule repo
  rule.setRuleRepo("not_null_or_empty") // custom rule name to pull rule value from rule repo
  rule.setPerc(1.0)
  rule.setPoints(1)
  rule.setIsActive(1)
  rule.setUserNm("admin")

  val cdq = OwlUtils.OwlContext(df, opt)
    .register(opt)
  
  cdq.addRule(rule)
  // Act
  owl.owlCheck()

  // Assert
  import scala.collection.JavaConversions
  val hootRule = JavaConversions.asScalaBuffer(owl.hoot.rules).find(x => rule.getRuleNm.equals(x.getRuleNm)).orNull
   println(hootRule.getScore)
}  
  
// Execute notebook
simpleRuleWithTemplate()
```

### Result

#### via UI

![](<../../../../../.gitbook/assets/image (48).png>)
