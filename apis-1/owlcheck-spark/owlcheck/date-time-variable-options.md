# Date Time Variable Options

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQApis/Date%20Time%20Variable%20Options.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

**Benefit**: Enhanced query and file date templating and variable options. This allows easier scheduling and programmatic templating for common date variables.

| Key      | Function                                                                                 |
| -------- | ---------------------------------------------------------------------------------------- |
| ${rd}    | replaces with -rd values in CMD, e.g. 2021-09-01                                         |
| ${rdEnd} | replaces with -rdEnd values in CMD                                                       |
| ${yyyy}  | replaces with 4 digit year portion of -rd values in CMD, e.g. 2021                       |
| ${yy}    | replaces with 2 digit year portion of -rd values in CMD, e.g. 21                         |
| ${M}     | replaces with 1 digit month portion of -rd values in CMD                                 |
| ${MM}    | replaces with 2 digit month portion of -rd values in CMD                                 |
| ${MMM}   | replaces with 3 letter month name portion of -rd values in CMD, e.g. Jan, Jul, Dec       |
| ${MMMMM} | replaces with long month name portion of -rd values in CMD, e.g. January, July, December |
| ${d}     | replaces with 1 digit day portion of -rd values in CMD                                   |
| ${dd}    | replaces with 2 digit day portion of -rd values in CMD                                   |
| ${HH}    | replaces with 2 digit hour portion of -rd values in CMD                                  |
| ${KK}    | replaces with 1 digit hour portion of -rd values in CMD                                  |
| ${mm}    | replaces with 2 digit minute portion of -rd values in CMD                                |
| ${ss}    | replaces with 2 digit second portion of -rd values in CMD                                |
