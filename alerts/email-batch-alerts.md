# Email Batch Alerts

Alert Email functionality allows user to send email to recipients when Alert condition is satisfied for specified dataset.&#x20;

![](../.gitbook/assets/Multiple\_Recipients\_0.png)

On Alert definition screen user can setup an alert with multiple recipients. It helps to have single alert with multiple recipients. It allows user to specify the batch name for the multiple recipients.&#x20;

The user can specify single or multiple recipients. Multiple recipients are specified by Comma(,) AND/OR Semicolon(;) delimiters.

The accepted formats for email are "[name@email.com](mailto:name@email.com)" OR "[name1@email.com](mailto:name1@email.com)[,name2@email.com](mailto:,name2@email.com)" OR "[name1@email.com](mailto:name1@email.com)[;name2@email.com](mailto:,name2@email.com)".

The user can update the batch at any time.&#x20;

![](../.gitbook/assets/multiple\_recipient\_2.png)

![](../.gitbook/assets/multiple\_recipient\_3.png)



After job runs it checks dataset with condition email not sent and batch name not empty. If this condition satisfies it send email to all recipients in the batch.

User can also run the DQ jobs manually from Hoot page.

![](<../.gitbook/assets/Screen Shot 2022-03-21 at 1.01.45 PM.png>)

#### Alert for Batch Schedule

[https://dq-docs.collibra.com/scheduler/schedule-owlchecks](https://dq-docs.collibra.com/scheduler/schedule-owlchecks)
