---
description: >-
  Collibra Data Quality Summary reports provide information about your data sets
  rolled up in high level summaries. These reports include the Weekly Summary
  Report and Data Quality Checks Report.
---

# Summary Reports

## What is the Weekly Summary Report?

When you operate a large data lake or several large data environments, it's helpful to have a way to report across different dimensions at an executive summary level. You may want to know the health or coverage per line of business, department or tenet, or per database.&#x20;

The Collibra Data Quality Weekly Summary Report automatically aggregates a simple series of the high level trends for each data set, which allows you to see the DQ scores and trends, as well as row counts and passing runs in a weekly report. You can copy, export, and print this report to an Excel or CSV file format.

{% hint style="info" %}
As of the 2022.08 release, PDF is no longer a supported file format for exporting reports.
{% endhint %}

<figure><img src="../../.gitbook/assets/dq-weekly-summary-report.png" alt=""><figcaption></figcaption></figure>

## Steps

To generate a Weekly Summary report, follow these steps.

1. Log in to your Collibra DQ instance.
2. Click the ![](../../.gitbook/assets/dq-reports-icon.png) icon in the left navigation pane. \
   \>> The Reports page opens.
3. Select the **Data Summary** tile.\
   \>> The Weekly Summary report displays.

The following table describes the report columns.

| Column          | Description                                                                                                                            | Column |   |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------- | ------ | - |
| Dataset         | The data sets scanned over one week.                                                                                                   |        |   |
| Score           | The average data quality score of a data set over one week.                                                                            |        |   |
| Score Trend     | <p>A line graph representation of data quality scores over one week. <br>Hover over the blue dots to see the score trend.</p>          |        |   |
| Rows            | The total number of rows of a particular data set scanned over one week.                                                               |        |   |
| Rows Trend      | <p>A line graph representation of row count over one week.<br>Hover over the blue dots to see the rows trend.</p>                      |        |   |
| Pass/Fail       | Total number of DQ scans with a passing score (>75%) over one week.                                                                    |        |   |
| Passing Trend   | <p>A histogram of DQ scans that passed (blue) or failed (red) over one week.<br>Hover over the blue dots to see the passing trend.</p> |        |   |
| Table/File Name | The name of the table or file in use.                                                                                                  |        |   |

4\. Toggle the ![](<../../.gitbook/assets/dq-sort-icon (1).png>) icon at the top of the column to sort the data that displays in the columns in\
&#x20;    ascending or descending order.

5\. Filter the report results by entering information in the search bar. For example, if you \
&#x20;   enter a number in the search field, any report result that includes that number displays.

6\. Click **Copy**, **Excel**, **CSV**, or **Print** at the top right of the columns to copy, export, and print the\
&#x20;   report.

7\. Navigate the pages of your report by clicking the **Previous** and **Next** pagination buttons, \
&#x20;   located at the bottom of the columns.

## What is the Data Quality Checks Report?

The Data Quality Checks Report provides a number of automatic checks of your data sets that are continually updated, based on observation and learning. This report includes the type of check performed and the check value and break value per data set. There is also a summary report that rolls up the number of automatic DQ checks done.

{% hint style="info" %}
As of the 2022.08 release, PDF is no longer a supported file format for exporting reports.
{% endhint %}

<figure><img src="../../.gitbook/assets/dq-data-quality-checks-report.png" alt=""><figcaption></figcaption></figure>

## Steps

To see the Data Quality Checks report, follow these steps.

1. Login into the Collibra DQ instance.
2. Click the ![](../../.gitbook/assets/dq-reports-icon.png) icon in the left navigation pane. \
   \>> The Reports page opens.
3. Select the **DQ Check Summary** tile.\
   \>> The Data Quality Checks report displays. \
   This report includes a summary of the number of checks that Collibra DQ automatically ran at the top of the report and the details, which are described in the following table.

| Column      | Description                                                                                             |
| ----------- | ------------------------------------------------------------------------------------------------------- |
| Data Set    | The name of the data set.                                                                               |
| Check Type  | The type of check that DQ ran.                                                                          |
| Check Value | The value associated with this check.                                                                   |
| Break Value | The number of points associated with a rule break, which are then subtracted from a data quality score. |

4\. Toggle the ![](<../../.gitbook/assets/dq-sort-icon (1).png>)icon at the top of the column to sort the data that displays in the columns in\
&#x20;    ascending or descending order.

5\. Filter the report results by entering information in the search bar. For example, if you \
&#x20;   enter a number in the search field, any report result that includes that number displays.

6\. Navigate the pages of your report by clicking the **Previous** and **Next** pagination buttons, \
&#x20;   located at the bottom of the columns.
