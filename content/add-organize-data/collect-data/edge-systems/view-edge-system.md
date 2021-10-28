---
uid: ViewEdgeSystem
---

# View and monitor an edge system

View and monitor the health status and configuration information for edge systems, including Edge Data Store and PI Adapters, for a selected namespace. You can filter and sort the list of edge devices, and open a trend displaying diagnostic data for a specific device or component. 

**Note:** An edge system appears on the `Edge Systems` page once it is writing data to OCS.

To view an edge system, complete the following procedure:

1. From the left pane, select **Data Collection** > **Edge Systems**.

1. Verify that the **Edge Systems/Configuration Library** selector is set to **Edge Systems**.

1. **Optional:** To sort by a column in descending order, click on the column header. To sort in ascending order, click again.

1. **Optional:** To filter the edge systems shown based on a specific column, click the filter icon in the column header. 

  **Note:** You can filter for multiple tags using `and` and `or` syntax to refine the filter.

1. Click on a device to see open the right pane that displays information for that device. 

1. Click on the `Details` tab to see the edge system installed on the device and the configured components.

1. Click on the `Configuration` tab to review the configuration details.

1. Click the **View Trend** ![View Trend](images/view-trend-icon.png) to open a trend showing diagnostic data in a new window.

  The level where you click the icon determines what data is included. Click the icon at the top level to see all available diagnostic data for the device. Click the icon at the edge system level to see the diagnostic data available for that edge system. Click the icon at the component level to see the diagnostic data available for that component. 

## Remove an edge system

You can remove edge systems from the list of edge systems in OCS, but the edge system remains on the device. After an edge system is removed from OCS and it is no longer sending data to OCS, you can no longer see or manage it from OCS. If an edge system sends data to OCS after it has been removed from the list of edge systems, it will reappear in the list of edge systems.

Use the following procedure to remove an edge system:

1. In the left pane, select **Data Management** > **Edge Systems**.

1. Verify that the **Edge Systems/Configuration Library** selector is set to **Edge Systems**.

1. Find and click on the edge device to remove.

1. Click **More Options** and select **Remove Edge System**.

1. To confirm removing the selected edge system from the list, click **Remove**. 
