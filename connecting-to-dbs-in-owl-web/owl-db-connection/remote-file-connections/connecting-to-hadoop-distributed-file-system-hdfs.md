# Connecting to Hadoop Distributed File System (HDFS)

## Prerequisites

To configure the HDFS connector, you need:

* Admin privileges in your Collibra Data Quality instance.
* Access to an HDFS cluster.

## Steps

1. In the main menu, hover over the gear icon and click **Connection**.\
   \>>The Connections page opens.
2. Scroll down to the HDFS card.
3. Click the Add button to add a new HDFS connection.\
   \>> The New Remote File Connection (HDFS) modal opens.
4. Enter the values for each property.

| Property          | Description                                                                                                                                                                                   |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Name              | The unique name of your HDFS connector.                                                                                                                                                       |
| Connection URL    | The HDFS URL used for your connection.                                                                                                                                                        |
| Target Agent      | The target agent lets you select an agent for your connection.                                                                                                                                |
| Auth Type         | <p>The method used to authorize your connection.<br></p><p><strong>Note:</strong> If you use an Unsecured Auth Type, no other authorization fields are required. This is not recommended.</p> |
| Principal         | The service principal used to let Collibra Data Quality access your connection.                                                                                                               |
| Keytab            | <p>The keytab used to authorize your connection. <br><br><strong>Note:</strong> Only applicable when you select Keytab as the Auth Type.</p>                                                  |
| TGT               | <p>The Ticket Granting Ticket used to authorize your connection.<br></p><p><strong>Note:</strong> Only applicable when you select TGT Cache as the Auth Type.</p>                             |
| Driver Properties | <p>The configurable driver properties for your connection.<br><br><strong>Note:</strong> This is an optional configuration.</p>                                                               |

5\.  Click **Save** to establish your connection.

## What's next?

Once you save your HDFS connection:

* A confirmation message tells you that your connection is saved and valid.
* You can immediately access your HDFS connection [from Explorer](../../../dq-visuals/more/explorer-2.md).
* Begin [profiling your data](../../../dq-visuals/profile.md).
