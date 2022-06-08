# Rule Preview

### Set a Preview Limit

Rule Previews allow you to set Preview Limits by the row, enabling you to drill in to your data even further. Limits can be set to any positive number. 6 is default.

{% hint style="success" %}
Best practice is to apply a limit of 1000 or less. Increasing the limit above 1000 should only be done if your Postgres has sufficient CPU and memory.&#x20;
{% endhint %}

Set a preview limit

1. Create a new **DQ Job** and navigate to the **Rule Builder** page.
2. Select your dataset and click the **Search** button.
3. Select a rule type from the **Select a type** button.&#x20;
4. Create your SQL rule in the **Expr** field and enter a unique name for your rule in the **Name** field.
5. Enter an even number in **Preview Limit (Rows)**.
6. Click **Save**.
7. Run the **DQ Job** to execute the rules assigned to the dataset.&#x20;

{% hint style="info" %}
Note: Freeform and Simple rule are the only two rule types supported at this time.
{% endhint %}

![](../../.gitbook/assets/create\_rule.gif)

### View and Export Results

Another key feature of Rule Previews is that you have the ability to easily export the details of your drill-in.&#x20;

View and export your results

1. Click the + icon in the **Rule Name** column to expand the table to view your results.&#x20;
2. Click **Export with Details** to download the break records to your local machine.&#x20;

![](../../.gitbook/assets/see\_rule\_results.gif)

{% hint style="success" %}
Rule preview is currently available for Freeform and Simple rules.
{% endhint %}
