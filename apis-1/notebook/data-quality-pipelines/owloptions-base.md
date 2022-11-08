---
description: API Documentation for Java Class OwlOptions.
---

# Options (base)

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQApis/Options%20\(base\).htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

The Class properties are laid out in the following format headers to allow Gitbook indexing.

### ClassName field\_name

**field type** | _`default`_\
\_\_Description

## OwlOptions dataset

**String** | \_`StringUtils.Empty` \_\
\_\_Unique string ID for the OwlCheck Dataset. Cannot contain `"."`, `"-"`, `"#"`, `"@"` \\

## Example Code

### Initializing

{% tabs %}
{% tab title="Scala" %}
```scala
import com.owl.common.options.OwlOptions

val opts = new OwlOptions()
```
{% endtab %}

{% tab title="Java" %}
```java
import com.owl.common.options.OwlOptions

OwlOptions opts = new OwlOptions();
```
{% endtab %}
{% endtabs %}
