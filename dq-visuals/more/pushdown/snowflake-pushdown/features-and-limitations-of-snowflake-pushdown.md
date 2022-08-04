# Features and Limitations of Snowflake Pushdown

{% hint style="info" %}
As of 2022.08, Snowflake Pushdown is only available as a private beta for participating customers. Since this is a beta feature, some functionalities may be limited.&#x20;
{% endhint %}

This section describes the features and limitations of using Collibra Data Quality's Snowflake Pushdown capability to run a DQ Job.

{% hint style="warning" %}
To use Snowflake Pushdown, you must be a participant in the private beta. This feature is currently unavailable for non-participants.
{% endhint %}

## Features

The following table shows the features unique to DQ Jobs run using Snowflake Pushdown processing.

| Feature                            | Description                                                                                                                               |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Dynamic date filter                | A togglable option that allows you to filter column data dynamically by runDate ${rd}.                                                    |
| Configurable number of connections | Allows you to set the number of open connections between 1-5 so you can run jobs in parallel and improve the performance of profile jobs. |
| Cancel jobs                        | Unlike Spark compute jobs, you can cancel the SQL queries of Snowflake Pushdown jobs.                                                     |
| No agent                           | Pushdown runs the database engine to execute jobs directly, removing the need for agents. Agent ID = 0.                                   |
| More control over autometrics      | With minimal clicks, you can apply autometrics, such as row count and uniqueness, from the UI.                                            |

## Limitations

Currently, there are some limitations with Snowflake Pushdown since it is in private beta as of 2022.08:

* The cancel jobs feature is currently unavailable, though it will be available in an upcoming release.
* Only DQ Native Rules are supported, though support for Freeform rules is planned in a future release.
* Profile and Rules are supported layers, but Outliers, Patterns, Dupes, Shapes, and Records are not yet supported.&#x20;
* We do not currently support Okta integration, though support for it is planned in a future release.&#x20;

