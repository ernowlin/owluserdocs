# Add Date Column

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQApis/Add%20Date%20Column.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

## Example

```bash
./owlcheck \
-ds "datataset_date_column" \
-rd "2019-07-01" \
-f "/Users/Downloads/csv2/2019010.csv" \
-adddc
```

{% hint style="info" %}
Add date column will use the run date supplied and add a date column named **OWL\_RUN\_ID**
{% endhint %}

```bash
-adddc
```

_This is used when you are using datasets that do not contain a date column or a malformed date string_

### Known Limitations

This feature is only available for files, not for database tables.
