---
description: >-
  The Batch Alerts functionality allow you to setup a single alert with multiple
  recipients. Click the Alerts icon in the left navigation pane and then click
  Alert Definitions.
---

# Email Batch Alerts

![](../.gitbook/assets/Multiple\_Recipients\_0.png)

In the Batch Name field, specify a batch name for the multiple recipients. Multiple recipients are specified by comma (,) AND/OR semicolon (;) delimiters.

{% hint style="info" %}
You can specify either single or multiple recipients.
{% endhint %}

The accepted formats for email are "[name@email.com](mailto:name@email.com)" OR "[name1@email.com](mailto:name1@email.com)[,name2@email.com](mailto:,name2@email.com)" OR "[name1@email.com](mailto:name1@email.com)[;name2@email.com](mailto:,name2@email.com)".

You can update the batch at any time.

![](../.gitbook/assets/multiple\_recipient\_2.png)

![](../.gitbook/assets/multiple\_recipient\_3.png)

After a job runs, it checks the data set with condition email not sent and batch name not empty. If this condition is met, an email is sent to all recipients in the batch.

You can also run the DQ jobs manually from **DQ Job** tab.

![](<../.gitbook/assets/Screen Shot 2022-03-21 at 1.01.45 PM.png>)

#### Alert for Batch Schedule

[https://dq-docs.collibra.com/scheduler/schedule-owlchecks](https://dq-docs.collibra.com/scheduler/schedule-owlchecks)
