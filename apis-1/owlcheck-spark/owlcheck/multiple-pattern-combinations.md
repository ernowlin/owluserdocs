---
description: Run more than one relationship through pattern matching
---

# Multiple Pattern Relationships

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQApis/Multiple%20Pattern%20Relationships.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

## Example

```bash
./owlcheck \
-ds "fpg_multiple" \
-rd "2018-10-04" \

-cxn "postgres" \
-lib   "/opt/owl/drivers/postgres/" \
-q "select * from public.fpg_accounts where d_date = '2018-10-04'" \

-fpgon \
-fpgdc "d_date" \
-fpglb "4" \
-fpgmulti "id,ssn_num=first_name,email|id,ssn_num=first_name,gender|id,ssn_num=last_name" 
```

{% hint style="info" %}
Instead of -fpgkey and -fpgcol

key1=cols1|keys2=cols2

Enter multiple key=cols combinations separated by a pipe
{% endhint %}

```bash
-fpgmulti "id,ssn_num=first_name,email|id,ssn_num=first_name,gender"
```
