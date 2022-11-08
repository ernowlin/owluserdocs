---
description: Ideal for rules that apply to more than one data set. Write once, apply many.
---

# Rule Templates

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQCoreComponents/Rule%20Templates.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

![](<../../.gitbook/assets/rule\_template (1).gif>)

Templates are great for regex, format, and compliance checks.

A template rule substitutes the data set and column at runtime. This can save hundreds of redundant rules that do the same thing but on different column names.

Template rules are located in the **Type** dropdown as well as the **Quick Rules** dropdown. The complete list of template rules is located in the Rule Library section. These meant for global rules that are ideal for code sets, compliance checks, and regex checks. These are ideal for checks that apply to many tables.

Rule templates use SQLG (simple) and occasionally SQLF (Freeform) types under the hood. Rule templates appear in the Rule Library once they are created.

See the [rule library section](dq-rule-automation.md) for more details.

{% hint style="info" %}
Customized discovery routines can be run using the [rule library](rule-templates.md#rule-library) together with [data concepts and semantics.](data-concepts-and-semantics.md)
{% endhint %}
