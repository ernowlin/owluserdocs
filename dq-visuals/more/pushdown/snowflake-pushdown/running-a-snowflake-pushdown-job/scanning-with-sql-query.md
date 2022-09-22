# Scanning with SQL Query

{% hint style="info" %}
As of 2022.08, Snowflake Pushdown is only available as a private beta for participating customers. Since this is a beta feature, some capabilities may be limited.&#x20;
{% endhint %}

The SQL Query option lets you write and compile a query manually for an advanced scan of your table.&#x20;

## Prerequisites

You have an [active Snowflake connection](../../../../../connecting-to-dbs-in-owl-web/supported-drivers/connectivity-to-snowflake.md) and [Pushdown enabled](../../../../../connecting-to-dbs-in-owl-web/supported-drivers/connectivity-to-snowflake.md).

## Steps

1. From Explorer, select your Snowflake connection with the ![](../../../../../.gitbook/assets/dq-pushdown-icon.png) icon next to it.\
   **Note:** For the ![](../../../../../.gitbook/assets/dq-pushdown-icon.png) icon to be visible, you need to enable Pushdown when you establish your Snowflake connection.
2. Select your schema.
3. Click Create DQ Job.\
   \>> The Job creator page opens.
4. Select **SQL Query**.\
   \>> The SQL view opens.
5. Write and compile a SQL query.\
   **Note:** To switch to Standard view and return to the [Partial Scan](running-a-partial-scan.md) workflow, select the three-dots menu icon and select **Standard view**. Any changes made to your SQL query are lost when you switch between views.
6. Click **Next**. \
   Alternatively, you can also click **Add layers** from the left workflow menu.\
   \>> The Add layers view appears.
7. Optionally add layers or toggle default settings.&#x20;
   * Certain Autometrics are enabled by default. You can optionally toggle them on and off.
   * Shapes are enabled by default. You can optionally toggle them on and off, and configure more advanced options by selecting the Manual checkbox.&#x20;
8. Click **Next**.\
   \>> The Review page opens.
9. Review your DQ scan.&#x20;
10. Select **Run**.\
    \>> A dialog appears and tracks the status of your Snowflake Pushdown job.

{% hint style="info" %}
**Note:** More advanced layers beyond basic profile jobs will soon be available to customers participating in the private beta.
{% endhint %}

### What's next?

After scanning with SQL Query, go to the Jobs page to [view the results](../../../../profile.md#view-the-results).
