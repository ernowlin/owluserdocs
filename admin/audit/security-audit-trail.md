# Security Audit Trail

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQAdmin/Security%20Audit%20Trail.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

Available Data

* User profile updates
* Role updates
* Reference table from metastore
* Dataset deletion requests
* Job schedule attempts

![](<../../.gitbook/assets/image (161).png>)

When administrators modify roles mapped to data sets or data sets mapped to roles, changes are documented automatically in the Audit Trail. This information in the entry log include

* the new and original data sets added or removed during the modification.
* the new and original roles added or removed during the modification.
* a timestamp of when the modification occurs.
* the type of modification.
* username by which the modifications are made.
