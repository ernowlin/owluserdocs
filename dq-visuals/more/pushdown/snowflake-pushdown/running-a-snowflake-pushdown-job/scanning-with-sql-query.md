# Scanning with SQL Query

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQCoreComponents/Scanning%20with%20SQL%20Query.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

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
   * Certain AdaptiveRules are enabled by default. You can optionally toggle them on and off.
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
