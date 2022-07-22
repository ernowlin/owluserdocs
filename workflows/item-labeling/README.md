---
description: Quickly click findings to trigger retraining
---

# Item Labeling

![](../../.gitbook/assets/item\_label.gif)

## Action labeling options

The following action labels instruct Collibra on how to handle a finding:

| Action     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Validate   | <p>Instructs Collibra to either assign a finding to a specific user for review, which then appears in the <a href="../assignments-queue/">Assignments Queue</a>, or acknowledge without an assignee that the finding is a valid observation. <br><br><strong>Note:</strong> Validating a finding does not improve your score.</p>                                                                                                                                                                                                                |
| Invalidate | <p>Instructs Collibra to ignore a finding and allow the value to pass. There are two invalidation options: Save and Save &#x26; Retrain.<br><br><strong>Save:</strong> Allows you to mark a finding as invalidated.<br><strong>Save &#x26; Retrain:</strong> Allows you to invalidate a finding and any previously saved invalidated findings (if any). <br><br><strong>Note:</strong> When you have many findings to invalidate, it may be best to use the Save option to invalidate them at the same time once all findings are reviewed. </p> |
| Resolve    | Instructs Collibra to mark the finding as an observation and prevents it from appearing in future runs. Resolving a finding does not immediately affect data quality scores.                                                                                                                                                                                                                                                                                                                                                                     |

## Available actions by feature

| Feature   | Available actions             |
| --------- | ----------------------------- |
| Behaviors | Validate, Resolve             |
| Rules     | Validate, Resolve             |
| Outliers  | Validate, Invalidate, Resolve |
| Pattern   | Validate, Invalidate, Resolve |
| Source    | Validate, Invalidate, Resolve |
| Record    | Validate, Resolve             |
| Dupes     | Validate, Invalidate, Resolve |

{% hint style="warning" %}
**Note:** Some findings are ineligible for all labeling options. For example, you can only apply Validate and Resolve labels to findings that result from Rules.&#x20;
{% endhint %}

## Validating a finding

When you apply a validate label to a finding, you can assign it to another DQ user to review. This marks the finding for future runs and sends it to the internal [Assignments Queue](../assignments-queue/). You can also configure DQ to send assignments to an external queue, [such as ServiceNow](../assignments-queue/external-assignment.md).

## Invalidating a finding

Sometimes the findings page flags issues with your data set that DQ discovers during a job run, but maybe you want DQ to ignore certain flagged issues. The invalidate label allows you to do that. After you add a descriptive annotation of your action, you can then select either Save or Save & Retrain.&#x20;

### Save

If you have a large number of findings that DQ has flagged, and you want to invalidate all of them at once instead of clicking through one at a time, select Save for all of the findings you would like to bulk invalidate. On your last finding, select Save & Retrain. All previously saved invalidated findings are removed and DQ retrains your data set.&#x20;

### Save & Retrain

When you Save & Retrain your data set, any previously deducted points from a flagged finding are restored and reflected in your overall data quality score. If you do not have many findings to invalidate, you can Save & Retrain individually instead of in bulk.&#x20;

## Resolving a finding

Some features, such as Behavior and Rules, only permit Validate and Resolve actions. When you cannot Validate a finding but you want to apply a label, select Resolve. The Resolve label prevents a finding from appearing in future runs of your data set, and does not immediately affect your data quality score when applied.&#x20;

## Recalling labeled findings

To modify a previously labeled finding, you can always access them through the Labels tab. Here you can edit an annotation or delete a label entirely. If you delete a label, it returns to the findings page, unlabeled. From there you can again choose to Validate, Invalidate, or Resolve it.&#x20;

To closely analyze when a finding has received a label, who has applied it, and more, see also the [Audit Trail](../../admin/audit/dataset-audit-trail.md).

