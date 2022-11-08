---
description: Simple check for individual columns
---

# Data type based rules

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQApis/Data%20type%20based%20rules.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

## Rule types

### Empty check

**Rule type: EMPTYCHECK**\
**Description:** Checking whether the target column has empty values or not

### Null check

**Rule type: NULLCHECK**\
**Description:** Checking whether the target column has _NULL_ values or not

### Date check

**Rule type: DATECHECK**\
**Description:** Checking whether the target column has **only** DATE values or not

### Integer check

**Rule type: INTCHECK**\
**Description:** Checking whether the target column has **only** INTEGER values or not

### Double check

**Rule type: DOUBLECHECK**\
**Description:** Checking whether the target column has **only** DOUBLE values or not

### String check

**Rule type: STRINGCHECK**\
**Description:** Checking whether the target column has **only** STRING values or not.

### Mixed datatype check

**Rule type: DATATYPECHECK**\
**Description:** ---

## Syntax

* **\<rule\_type>** - Fixed key to the rule type
* **\<column\_name>** - Column to apply the rule
* **\<rule\_name>** - Custom name of the rule

```scala
opt.dataset = "example_ds"

val rule = RuleBll.createRule(opt.dataset)
rule.setRuleNm("<rule_name>")
rule.setRuleValue("<column_name>")
rule.setRuleType("<rule_type>")
rule.setPerc(1.0)
rule.setPoints(1)
rule.setIsActive(1)
rule.setUserNm("admin")
```
