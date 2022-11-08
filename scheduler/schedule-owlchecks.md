# Schedule a Job

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/Scheduler/Schedule%20a%20Job.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

After you successfully run a job, you can schedule that job to run automatically. You can do this by updating the template (if needed) and clicking the schedule icon on the Findings page. To change the template, you can use the -rd variable: ${rd} in your query to set dynamic dates or date ranges for your scheduled job.

![](../.gitbook/assets/schedule.gif)

![](<../.gitbook/assets/image (154).png>)

![](<../.gitbook/assets/Screen Shot 2020-07-27 at 8.32.20 PM.png>)

Here you can choose the Agent to run the job, the frequency (daily/monthly/quarterly) and the time of day:

![](<../.gitbook/assets/Screen Shot 2020-07-27 at 8.28.09 PM.png>)

If your monthly or quarterly jobs are loaded after the month or quarter has ended, you can schedule the job for the day when the data has loaded but set the offset to the proper run date required for charting/reporting.

![](<../.gitbook/assets/Screen Shot 2020-07-27 at 8.30.57 PM.png>)

When the Schedule Status is set to Active and your job is scheduled to run automatically, a green indicator appears next to the Schedule icon. A red indicator means that the Scheduler is inactive and your job is not scheduled to run automatically.&#x20;

{% hint style="success" %}
After you toggle the Schedule Status and click Save from the Scheduler modal, refresh the page for your settings to update.
{% endhint %}

## Leverage external schedulers

For more details on how to leverage an external scheduler, check out [this section](https://dq-docs.collibra.com/apis-1/owlcheck-spark/owlcheck/owlcheck-cron). We support Cron / Autosys / Control M / Oozie.
