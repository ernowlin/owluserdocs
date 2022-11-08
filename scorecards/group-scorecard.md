# Page View

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQScorecards/Page%20View.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

![](../.gitbook/assets/page\_view.gif)

## Visually and logically group datasets together to create a heat-map of blindspots.

Similarly to job control and build frameworks like Jenkins, we always want to know the health of our datasets. Did it recently fail? Does it commonly fail on Mondays? What is the aggregate or composite score for multiple datasets? Owl allows you to define scheduled health checks that depend on the success/failure status of any number of datasets. This protects the downstream process consumers from pulling erroneous data into their models.

![](../.gitbook/assets/owl-group-scorecard.png)
