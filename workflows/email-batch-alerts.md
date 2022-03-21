# Email Batch Alerts

Alert Email functionality allows user to send email to recipients when Alert condition is satisfied for specified dataset. It allows to send email to recipient(s) specified in Alert recipient field on Alert Definition screen. &#x20;

![](../.gitbook/assets/Multiple\_Recipients\_0.png)

User can specify single recipient or multiple recipients. Multiple recipients are specified by Comma(,) AND/OR Semicolon(;)

![](../.gitbook/assets/multiple\_recipient\_2.png)

![](../.gitbook/assets/multiple\_recipient\_3.png)



The Scheduler checks all dataset with condition EMAIL\_SENT is 'false' and batch\_name is not EMPTY i.e. it identifies datasets with alerts which are not sent and alert recipients batch name is not empty. If this condition satisfies it send email to all recipients in batch.

User can also run the DQ jobs manually from Hoot page.

![](<../.gitbook/assets/Screen Shot 2022-03-21 at 1.01.45 PM.png>)
