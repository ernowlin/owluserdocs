# Assignments Queue

{% hint style="info" %}
We're moving! To improve customer experience, the Collibra Data Quality User Guide is moving to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/Home.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](../../) will remain accessible, but the DQ User Guide will be maintained exclusively in the Documentation Center following the 2022.11 release.&#x20;
{% endhint %}

![](../../.gitbook/assets/assignments.gif)

OwlDQ provides observations that usually need review to validate. In many cases, it makes sense to assign the validation to a person that has access to the source data. Assignments can be handled by Owl internally, or an existing ServiceNow or JIRA queue when configured.

When reviewing any observation you will notice a column called "Action

![](<../../.gitbook/assets/image (73).png>)

From the action dropdown, if you choose to validate a finding, you will also have the ability to assign that item to another Owl user for further investigation

![](<../../.gitbook/assets/image (67).png>)

If you do not choose an assignee (X), it will mark the item as valid, but unassigned: Acknowledged

Your External Queues are where the source of the assignment should be tracked, OWDQ/JIRA/Serive Now are all options. OWLDQ is automatically configured, but you can configure others via the Admin Console and clicking on Assignment Queues.

![](<../../.gitbook/assets/image (2).png>)
