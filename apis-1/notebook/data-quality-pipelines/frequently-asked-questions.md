# FAQs

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQApis/FAQs.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

## How to specify OWL database connection properties

{% tabs %}
{% tab title="OwlOptions" %}
```scala
import com.owl.common.options.OwlOptions

val opt = new OwlOptions()
opt.dataset = "<dataset_name>"
opt.runId = "<date>"  // YYYY-MM-DD
opt.load.pguser = "<db_username>"
opt.load.pgpassword = "<db_password>"
opt.load.pghost = "<ip>:<port>/<database_name>"
```
{% endtab %}

{% tab title="Props" %}
```scala
import com.owl.common.Props

val props = new Props()
props.dataset = "<dataset_name>"
props.runId = "<date>"  // YYYY-MM-DD
props.pguser = "<db_username>"
props.pgpassword = "<db_password>"
props.host = "<ip>:<port>/<database_name>"
```
{% endtab %}
{% endtabs %}
