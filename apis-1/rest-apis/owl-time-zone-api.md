---
description: UTC + global DateTime standard
---

# Time Zone API

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQApis/Time%20Zone%20API.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

### Background on common time issues

Controlling dates and times has always been a troublesome topic for global systems. Server clock vs server code such as new Date() which may create a date in the local time zone of the server vs the browser or client's time zone. Moving to the cloud only makes the problem worse when you need to consider the time zone the server might be in and inherit from its system's clock.

### Collibra Data Quality's Solution - Keep it Simple

If everyone worked off of a globally understood format that is not subject to misinterpretation, things would be simpler. Take 03/02/2019, for example. Is this March 2nd or February 3rd? That depends on which country you live in. Collibra DQ only accepts this format: YYYY-MM-DD. Extending this to time would mean YYYY-MM-DD 00:00:00.

### CmdLine Examples

./owlcheck -ds trades -rd "2019-04-01" or -rd "2019-04-01 00:00:00"

### Simple Example

A user running a DQ Check in New York and a user running a DQ Check 3 hours later in California.

| CmdLine Arg    | User Location | TimeZone    | Stored in CDQ (UTC) |
| -------------- | ------------- | ----------- | ------------------- |
| -rd 2019-04-01 | New York      | implied EST | 2019-04-01 04:00:00 |
| -rd 2019-04-01 | California    | implied PST | 2019-04-01 07:00:00 |

These jobs run 3 hours apart, even though they appear to run first thing in the morning to each user. Collibra DQ stores all dates in a common **UTC** format for global consistency.

On the Jobs page, the Start Time and Update Time columns are always based on the server time zone of the DQ Web App, and appear in the YYYY-MM-DD 00:00:00 format.&#x20;

### Web API or URL Example

[http://localhost:9000/dq/hoot?dataset=atmCustomers\&runId=2019-04-01](http://localhost:9000/dq/hoot?dataset=atmCustomers\&runId=2019-04-01) 04:00:00 [http://localhost:9000/dq/hoot?dataset=atmCustomers\&runId=2019-04-01](http://localhost:9000/dq/hoot?dataset=atmCustomers\&runId=2019-04-01) 07:00:00

#### For Convenience if a user prefers seeing and interacting with dates in their local time zone

[http://localhost:9000/dq/hoot?dataset=atmCustomers\&runId=2019-04-01](http://localhost:9000/dq/hoot?dataset=atmCustomers\&runId=2019-04-01) 00:00:00\&tz=EST [http://localhost:9000/dq/hoot?dataset=atmCustomers\&runId=2019-04-01](http://localhost:9000/dq/hoot?dataset=atmCustomers\&runId=2019-04-01) 00:00:00\&tz=PST
