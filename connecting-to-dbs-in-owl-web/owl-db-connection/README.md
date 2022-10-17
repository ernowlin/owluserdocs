# Adding Connections

{% hint style="info" %}
We're moving! To improve customer experience, the Collibra Data Quality User Guide is moving to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/Home.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](../../) will remain accessible, but the DQ User Guide will be maintained exclusively in the Documentation Center following the 2022.11 release.&#x20;
{% endhint %}

![](<../../.gitbook/assets/connections (1).gif>)

## How to Add DB Connection via UI

We will add a connection named `metastore` that connects to local Postgres server (`localhost:5432/postgres`)

* Login to DQ Web and navigate to Admin Console.

![Fig 1: Home Page](../../.gitbook/assets/DQ-Admin-Console-1.png)

* From the Admin Console, click on the Connections tile.

![Fig 2: Admin Console](../../.gitbook/assets/DQ-Admin-Console-2.png.png)

* Click on Add button in Postgres box to add a Postgres connection

![Fig 3: List of DB Connections](../../.gitbook/assets/DQ-Connection-1.png)

Default Postgres JDBC template connection is shown. This modal is populated with basic values what Postgres connection setting should look like.

![Fig 4: Template Postgres connection creation modal](../../.gitbook/assets/DQ-Connection-2.png)

Replace the Connection URL to point to the Postgres server you want to run DQ Jobs against. In this example, `jdbc:postgresql://localhost:5432/postgres`

Also change Driver Location to the JDBC Driver for Postgres in your installation. Click on the folder icon and click on Postgres driver path. These Driver Directories are default JDBC Drivers provided by DQ installation (usually in `$OWL_BASE/owl/drivers/*`)

![Fig 5: Add new driver or select existing from Driver Directories](../../.gitbook/assets/DQ-Connection-3.png)

Fig 6 is what the new connection setting should look like. Make sure to provide the correct Postgres Username and Password (if using Username/Password for authentication). Press Save to continue. _**This action will attempt to establish a connection.**_

![Fig 6: Connection settings to connect to database named "postgres" in Postgres server "localhost" exposed via port 5432](../../.gitbook/assets/DQ-Connection-4.png)

### Link Connection to Agent

{% hint style="info" %}
Make sure to [Link DB Connection](https://dq-docs.collibra.com/connecting-to-dbs-in-owl-web/owl-db-connection/add-connection-to-agent) to a DQ Agent, if required
{% endhint %}
