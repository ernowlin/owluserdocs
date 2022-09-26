# Coverage Report

## What is a Data Quality Coverage Report

The Coverage Report provides a view that shows DQ coverage across all your technical data sets (for example, schemas, files, tables, and items in the database) via a donut chart, as well as time-series bar charts that show the DQ run level information aggregated by month.

## Steps

To generate a Coverage Report, follow these steps.

1. Log in to the Collibra DQ instance.
2. Click the ![](../../.gitbook/assets/dq-reports-icon.png)Explorer icon in the left navigation pane. \
   The Explorer view opens.
3. In Connections, select one of the databases, for which you want to generate a report and click **Generate Report**.\
   The Coverage Report displays. The report includes a donut chart showing the percentage of all schemas in the database that are running data quality on them and interactive bar charts showing which data sets are running data quality jobs on a monthly basis.
4. To see how many new data quality jobs have been added, click one of the following bar charts (the green color represents new DQ jobs and the gray are the existing jobs):

| View    | Description                                                 |
| ------- | ----------------------------------------------------------- |
| **1m**  | Shows new and existing jobs after one month.                |
| **3m**  | Shows new and existing jobs after three months.             |
| **6m**  | Shows new and existing jobs after six months.               |
| **YTD** | Shows new and existing jobs year-to-date.                   |
| **1y**  | Shows new and existing jobs after one year.                 |
| **All** | Shows new and existing jobs for the entire range of months. |

5\. To generate a Coverage Report for a specific schema, expand the schema and click **Generate**\
&#x20;    **Report**.\
&#x20;   The Coverage Report displays for that schema. You can click into the charts to see specific\
&#x20;    information for DQ coverage for this schema.

In the following screenshot, **`(22/44)`** next to the PUBLIC schema represents 22 out of 44 tables that have DQ jobs running on them and **`(24/24)`** represents 24 out of 44 jobs that have been cataloged, meaning they are registered and have metadata.

![](<../../.gitbook/assets/Screen Shot 2021-04-03 at 7.02.23 PM.png>)
