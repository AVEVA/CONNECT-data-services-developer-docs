---
uid: start-transfer
---

# Start a data transfer

Once you [Create a data transfer](xref:create-transfer), you can start the transfer. During the transfer, events are sent asynchronously. Historical events are sent first, followed by current events. Data is transferred from on prem to the cloud every 30 seconds or for every 50,000 events, whichever occurs first.

To start a data transfer:

1. (Optional) In the `PI to Data Hub Agents` page, select the PI to Data Hub Agent associated with the data transfer. 

1. (Optional) In the **Manage Agent** tab, expand the `Transfer Overview` section.

1. Select **Start Transfer**, then select **Start**.

   The data transfer begins and transfer status is updated in the `Transfer Overview` section on the **Manage Agent** tab.

   **Note:** The **Manage Agent** tab provides information about the agent associated with the transfer and the transfer progress.

1. In the `Transfer Overview` section, view the transfer status as data is sent to the agent and stream data is created.

   **Note:** The rate at which data transfers varies and depends on the density of data in the source PI Data Archive and/or AF server. See <xref:data-transfer-statuses> for a list of transfer statuses and descriptions. To find out more information about an asset error, agent status, or asset create/update error, select **Logs** above the list of agents to access more information. Possible statuses that appear in the **Current Activity** field may indicate an issue and include Uncategorized Error, PI Point Type Change Detected, and No Valid PI Points In Transfer.   

1. (Optional) To view more information about an agent's status, select **Agent Health Events**.

   **Note:** See [Health Events window](#health-events-window) for more information.  
 
1. (Optional) To see more information about log messages for the transfer, select **Logs**. See <xref:download-tenant-log> for more information. 

1. (Optional) To view transfer progress and metrics for stream and/or asset creation, select the **Transfer Metrics** tab. See [Transfer metrics](#transfer-metrics) for more information. 
    
1. (Optional) To stop a transfer, select **Stop Transfer**, then select **Stop**.

1. (Optional) To remove a transfer, select **Remove Transfer**, select the **Delete Streams and Assets from the cloud** option if applicable, then select **Remove**.

## Health Events window

The `Health Events` window provides information about an agent's activity and current status. Health events are based on log messages. You can sort messages by severity, source, time and message content.

![](../../images/health-evts-window.png)

The following table provides descriptions for the elements of the `Health Events` window.

| Element | Description                                                  |
| ------- | ------------------------------------------------------------ |
| Severity | The severity level of the log message. To filter by a particular severity level (Critical, Error, Warning, Information, Debug or Trace), select the filter icon and select one or more severity levels. |
| Source | The source of an error message. To filter by source (agent, PI point indexing or AF indexing), select the filter icon and select one or more sources. |
| Health Event | The health event that occurred. |
| Timestamp | The date of the event. To filter log messages by a particular date and/or time, select the filter icon, then enter the date and/or time in `Month 00, 000 00:00:00 PM` format. |
| Message | The actual log message. To filter by a word or phrase, select the filter icon, then enter the word or phrase. |
| Clear All Events | Select **Clear All Events** to remove all events from the view. |
| Export | Select **Export** to save a copy of the health event messages to a .csv file. |

## Transfer metrics

The **Transfer Metrics** tab displays details about a transfer's progress by server connection. Metrics for streaming and historical events and the progress of stream and asset creation are shown. 

The following table provides a description of the fields in the **Transfer Metrics** tab.

| Field name | Description   |
| ------------- | ---------- |
| PI Data Archive Server Version | The version of PI Data Archive that is installed on the source server configured to send PI point data via the agent. |
| Last Streaming Read | The date of the latest stream read.|
| Streaming Events Per Second | The average number of streaming events transferred to the PI to Data Hub Agent per second over the last minute. This value is updated every 10 seconds during data transfer.  |
| Historical Events Per Second | The average number of historical events transferred to the PI to Data Hub Agent per second over the last minute. This value is updated every 10 seconds during data transfer. |
| Historical Transfer | Transfer progress for historical data.  |
| Historical Start | The historical start date of the transfer. |
| Historical End | The historical end date of the transfer. |
| Total PI Points In Transfer | Total number of PI points selected for transfer. |
| Total Points Updated | The number of PI Points added to or removed from the transfer configuration. |
| Stream Creation Status | The progress of streams creation during transfer progression.  |
| Total Streams Created | Total number of streams created.  |
| Total Streams Updated | Total number of streams updated with new configuration and metadata. |
| Total Streams Deleted | Total number of deleted streams. |
| Stream Creation Errors  | Total number of errors generated while creation streams. |
| Stream Update Errors | Number of errors generated while updating streams. See the `Transfer Overview` section on the **Manage Agent** tab for error details. |
| Stream Deletion Errors | Number of errors generated during stream deletion. See the `Transfer Overview` section on the **Manage Agent** tab for error details. |
| AF Server Version | The version of Asset Framework (AF) that is installed on the source server configured to send AF element data via the agent.  |
| Total Elements in Transfer | The number of AF elements configured in the transfer. |
| Assets Created Per Second | The number of assets created per second during the transfer. |
| Total Assets Created | The total number of assets created. |
| Assets Updated | The number of assets created or updated during data transfer. |
| Total Assets Deleted | The total number of deleted assets. |
| Asset Create/Update Errors | The number of errors generated during asset creation or updating. |
| Asset Deletion Errors | The number of errors generated during asset deletion. See the `Transfer Overview` section on the **Manage Agent** tab for error details.
