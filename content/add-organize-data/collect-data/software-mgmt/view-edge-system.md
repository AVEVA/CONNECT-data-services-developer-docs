---
uid: ViewEdgeSystem
---

# View and monitor a system

View and monitor the health status and configuration information for systems, including Edge Data Store and PI Adapters, for a selected namespace. You can filter and sort the list of edge devices, and open a trend displaying diagnostic data for a specific device or component. 

**Note:** A system appears on the `Edge Data Store & Adapters Systems` page once it is writing health data to AVEVA Data Hub. For information on configuring health endpoints, see the specific system product documentation.

## View a system

To view a system:

1. From the left pane, select **Data Collection** > **Edge Data Store & Adapters**.

1. Verify that the **Systems/Configuration Templates** selector is set to **Systems**.

1. (Optional) To sort by a column in descending order, select the column header. To sort in ascending order, select the header again.

1. (Optional) To filter the systems shown based on a specific column, select the filter icon in the column header. 

  **Note:** Filter for multiple tags using `and` and `or` syntax to refine the filter.

1. (Optional) To search for specific systems, select the **Search for Systems** search bar. The search function provides examples for filtering by criteria such as device name, status, version, and tags. For more information, read [Search in AVEVA Data Hub](xref:Search).

1. To open the right pane that displays information for a device, select the device. 

1. To see the system installed on the device and the configured components, select the **Details** tab.

1. To review the configuration details, select the **Configuration** tab.

1. To open a trend showing diagnostic data in a new window, select the **View Trend** ![View Trend](../../../_icons/default/chart-line-variant.svg) icon.

  The level where you select the icon determines what data is included:

   - To see all available diagnostic data for the device, select the icon at the top level. 

   - To see the diagnostic data available for a specific system, select the icon at the system level. 

   - To see the diagnostic data available for a specific component, select the icon at the component level. 

## Remove an system

You can remove systems from the list in AVEVA Data Hub, but the system remains on the device. After a system is removed from AVEVA Data Hub and it is no longer sending data to AVEVA Data Hub, you can no longer see or manage it from AVEVA Data Hub. If a system sends health data to AVEVA Data Hub after it has been removed from the list, it will reappear in the list of systems.

To remove a system:

1. In the left pane, select **Data Collection** > **Edge Data Store & Adapters**.

1. Verify that the **Systems/Configuration Templates** selector is set to **Systems**.

1. Find and select the edge device to remove.

1. Select **More Options** and select **Remove**.

1. To confirm removing the selected system from the list, select **Remove**. 
