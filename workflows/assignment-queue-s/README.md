# Assignment Queue(s)

![](../../.gitbook/assets/assignments.gif)

Collibra Data Quality provides observations that usually need review to validate. In many cases, it makes sense to assign the validation to a person that has access to the source data. Assignments can be handled by Collibra internally, or an existing ServiceNow queue when configured.

When reviewing any observation you will notice a column called **Action**

![](<../../.gitbook/assets/image (34).png>)

From the **Action** dropdown, if you choose to validate a finding, you will also have the ability to assign that item to another Collibra user for further investigation

![](<../../.gitbook/assets/image (33).png>)

If you do not choose an assignee (X), it will mark the item as valid, but unassigned: Acknowledged

Your External Queues are where the source of the assignment should be tracked, Collibra Data Quality and ServiceNow are both options. Collibra Data Quality is automatically configured, but you can configure others via the Admin Console and clicking on Assignment Queues.

![](<../../.gitbook/assets/image (32).png>)
