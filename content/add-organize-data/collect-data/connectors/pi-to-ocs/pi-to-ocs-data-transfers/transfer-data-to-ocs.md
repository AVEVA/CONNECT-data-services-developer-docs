---
uid: transfer-data
---

# Transfer data to AVEVA Data Hub

You initiate a data transfer from the `PI to Data Hub Agents` window. A transfer can consist of PI points and AF elements or AF elements that reference at least one PI point.

PI points can be added to a transfer explicitly using a tag search or implicitly using AF element references. For information, about the difference between implicit and explicit references, see [Explicit versus implicit PI points](#explicit-versus-implicit-pi-points).

**Before you begin:** Download and install the PI to Data Hub Agent. Register your PI Data Archive and AF data sources using the PI to Data Hub Agent Configuration Utility. 

## Create a transfer

Transfer creation consists of the following tasks:

1. Assign a name, description, and optional historical start and end time for data retrieval.

1. Select a level of data privacy to control how much identifying information about an asset is sent with PI point data.

1. Set query criteria and retrieve and add optional AF elements, which reference at least one implicit or explicit PI point, and/or PI point data to the transfer lists.

1. View transfer details.

1. Save the transfer.

1. (Optional) Export a file(s) that contains transfer detail information.

1. Initiate the data transfer and monitor its progress. 

**Note:** If you have configured an AF server, you will not be able to create a transfer until AF indexing is complete. AF indexing status is listed on the **Manage Agent** tab in the `PI to Data Hub Agents` window. The following image shows AF indexing in progress:

![](../../images/af-indexing.png)

## Name the transfer and set data privacy settings 

To name the data transfer: 

1. In the left pane, select **Data Collection** > **PI to Data Hub Agents**.

1. In the `PI to Data Hub Agents` window, select the agent for the data transfer.

1. In the **Manage Agent** tab, select **Create Transfer**.

   The `Transfer Setting` window opens.

   ![](../../images/transfer-settings.png)
   
1. In the **Name** and **Description** fields, enter a name and description for the transfer.

1. (Optional) In the **Historical Start time** fields, enter a historical time context for the data retrieval.

   **Note:** AVEVA Data Hub supports out of order events and stores data in chronological order by timestamp. PI Data Archive 2017 SP2 or higher is required for this feature. Be sure to enter the historical start date and time correctly to ensure all data is included in the transfer. No data before the historical start time will be captured and stored in SDS. See [Overview of data transfers](xref:transfer-data) to learn more about transferring historical data.

1. To set the data privacy level for the transfer, select one of the following **Stream Metadata Replication Policy** settings: 

   * **High** - Sends all intended metadata.
   * **Medium** - Default. Send metadata without logical addresses from the data source.
   * **Low** - Sends no metadata from the data source namespace. Locally configured metadata such as point source and local aliases is allowed (point name, point ID and point source only).
   * **None** - Only the point ID and point name is sent; no metadata is included in the transfer.

   **What PI point attributes are transferred with each Stream Metadata Replication Policy (data privacy) setting?**

    |   | High | Medium | Low | None |
    | ------------- | ----------------- | ----------------- |----------------- | ----------------- |
    | Name | X | X  | X | X |
    | Descriptor | X | X |  
    | EngUnits | X | X |  |  |  |
    | ExDesc | X |  |  |  |
    | InstrumentTag | X  |  |  |  |
    | PointId | X | X | X | X |
    | Pointsource | X | X | X |  |
    | PointType | X | X |  |  |
    | SourceTag | X | X |  |  |
    |Step | X | X |  |  |

1. (Optional) To have streams and assets automatically removed from the transfer when their corresponding PI points and AF elements are removed, select the **Automatically remove Streams and Assets** option. 

1. Select **Ok**.

   The transfer is created and the `Transfer` page opens.

**Note:** To modify the transfer settings, select **Settings** to access the `Transfer Setting` window and modify the name, description, historical start and end times, and data privacy settings as needed.

## Build an AF elements transfer list

After naming the transfer, build an AF elements transfer list by setting query criteria and then selecting AF elements. You can narrow your search by filtering by element name, asset group, attribute name/value, template, and category. A corresponding asset is created for every AF element in your transfer. Static AF element attributes become asset properties. 

To build an AF element:

1. On the `Transfer` page, select the source AF database from the **AF Database** dropdown list.

   ![](../../images/transfer-win.png)

1. (Optional) Select **Root Asset**.

1. (Optional) In the `Select Root Element` window, select the plus buttons to drill down to the root asset in the AF database hierarchy, select a root asset, then choose **Select**. <!-- AF 11/15/21 UGH! I hate "select **Select**". Makes me want to use click. -->

1. (Optional) In the **Element Name** field, enter search criteria to filter by part or all of an AF element name.

   **Note:** If you do not enter filter criteria, the search defaults to `*` or all.  

1. (Optional) In the **Attribute Name** field, enter the attribute name.

1. (Optional) In the **Attribute Value** fields, filter attribute values by specifying the following information:

   **Note:** Custom unit of measurements (UOMs) are not supported. During the transfer of AF element data, AF elements with custom UOMs will not have their corresponding asset's UOM property set.
   
      * In the first field, enter an attribute name.

      * In the second field, use the dropdown list to select an operator (`=`, `<>`, `<`, `>`, `<=`, `>=`, `In`).

      * In the last field, enter an attribute value.

   **Note:** Custom unit of measurements (UOMs) are not supported. During the transfer of AF element data, AF elements with custom UOMs will not have their UOM property set.
   
1. (Optional) To narrow your search by template name, in the **Template** field, select a template from the dropdown list.

1. (Optional) To narrow the search by a specific AF category, in the **Category** field, select a category from the dropdown list.

1. To execute the query and retrieve results, select **Search**.

1. In the `Search Results` list, select each AF element you want added to the transfer.

   A check mark appears next to each selected AF element.

   **Tip:** To select a range of elements, select an element and then hold Shift and select a non-adjacent element. To advance through multiple-paged query results, select the back and forward arrows or enter a page number in the **Page** field.

1. When you are done selecting elements, select **Add AF Elements To Transfer**.
    
   The elements are added to the transfer and listed on the **AF Elements** tab.

1. To add additional elements from other AF databases, repeat these steps. 

**Note:** AF indexing needs to complete before you can view implicit PI points and start the transfer process.

## View AF element details

You can view details about an individual AF element such as related attribute names, values, and data references.

To view AF element details:

1. Select an AF element on the **AF Elements** tab.

1. Select **View Details**.

   The `AF Element Information` pane opens and displays details about AF element attributes. 
   
1. To view the paths of referenced AF elements, select the **Reference AF Elements** tab.
 
1. (Optional) To view health messages for the selected AF element, select the **Health Events** tab. 

1. To view details for another AF element, deselect the currently selected element, and then select a different element in the transfer list.

1. To close the `AF Element Information` pane, select **X** in the upper-right corner of the pane.

## Build a PI points transfer list

You build a PI points transfer list by setting query criteria and then adding the desired PI points. A PI points transfer list may contain both implicit and explicit PI points. See [Explicit vs. implicit PI points](#explicit-versus-implicit-pi-points) for more information.

To build a PI points transfer list:

1. Select the **PI Point Search** tab.


1. To filter the results, do the following:

   | Criteria To Filter By      | Action To Take                                               |
   | -------------------------- | ------------------------------------------------------------ |
   | Common PI point attributes | Enter criteria in any of the following fields:<br /><ul><li>**Name** (alias for tag attribute)</li><li>**Point Source**</li></ul>**Note:** Enter * to retrieve all PI points. |
   | Point descriptions         | Enter criteria in the following fields:<br /><ul><li>**Descriptor** </li><li>**Extended Descriptor**</li></ul> |
   | Engineering units          | Enter criteria in the **Engineering Units** field.           |
   | PI point type            | Select one of the following point types from the **Point Type** dropdown list:<br /><ul><li>`Float32`</li><li>`Float64`</li><li>`Int16`</li><li>`Int32`</li><li>`Digital`</li><li>`Timestamp`</li><li>`String`</li></ul> |
   | Specific location code(s)  | Enter up to five location code values in the **Location Codes** field. |

4. (Optional) To collapse or expand the criteria section, select the **Search Criteria** bar.

5. To execute the query and retrieve matching results, select **Search**.

6. In the **Search Results** area, select each PI point to add to the data transfer.

   A check mark appears next to each selected PI point.

   **Tip:** To select a range of PI points, select a PI point and then hold Shift and select a non-adjacent PI point. To advance through multiple-paged query results, select the back and forward arrows or enter a page number in the **Page** field.

7. When you are done selecting PI points, select **Add PI Points to Transfer**.

   The points are added to the transfer and listed on the **PI Points** tab.

## Explicit versus implicit PI points

PI points added to a transfer are assigned one of the following reference types:

  * Explicit - PI points directly retrieved from a PI Data Archive.

  * Implicit - PI points referenced by AF element attributes that have been retrieved by searching an AF server.

The reference type indicates the PI point's source and how it was retrieved. The reference type for each PI point is listed in the `Reference Type` column on the **PI Points** tab. 

## View PI point details and hide implicit PI points

You can view attribute details for selected PI points in a transfer. Implicit PI points are PI points referenced by AF elements in a transfer. You can hide implicit PI points to temporarily remove them from view on the **PI Points** tab. Hidden implicit PI points are still included in a transfer unless the referencing AF elements are removed from the transfer list. 

To view PI point details:

1. In the `Transfer` pane, select the **PI Points** tab.

1. Select a PI point and select **View Details**.

   The `PI Point Information` pane opens.

1. To view the path of any AF elements that reference the PI point, select the **Source AF Elements** tab.
 
1. (Optional) To view health messages for the selected PI point, select the **Health Events** tab.  

1. (Optional) To hide implicit PI points on the PI points list, turn off the **Show Implicit PI Points** toggle.

   **Note:** Implicit PI points are referenced by AF element attributes and retrieved from an AF server. Hiding implicit PI points does not remove them from a transfer.  

1. (Optional) To show hidden implicit PI points, turn on the **Show Implicit PI Points** toggle.

1. To view another PI point's details, select to select a different PI point in the transfer list.

1. To close the `PI Point Information` pane, select **View Details** or **x**.

## Save a transfer

Before you can transfer data to AVEVA Data Hub, you must save the transfer. To make changes to a transfer, you have to remove the existing transfer and define a new transfer.<!--AF 11/15/21 - I don't like that there is just a single a step for saving the definition. -->
<!--VT, 11/29/21: Ok.-->

To save the transfer:

1. To ensure your data transfer definition is correct and contains all the data you want transferred, review it for accuracy.
 
1. (Optional) Add or remove PI points and/or AF elements as needed. 

1. To save the transfer and return to the PI to Data Hub Agents window, select **Save** in the lower right-hand corner.

## Transfer data to AVEVA Data Hub

Data is ready for transfer after the desired PI points and/or AF elements have been added. During the transfer, events are sent asynchronously. Historical events are sent first, followed by current events. Data is transferred from on prem to the cloud every 30 seconds or for every 50,000 events, whichever occurs first.

**Note:** Modifications to an AF database or Data Archive digital state table during a PI to Data Hub transfer require that you manually stop and restart the transfer to capture all changes. Follow these steps to ensure all data is captured:

1. Stop the transfer.

1. Make modifications to the AF database and/or Data Archive digital state tables.

1. Restart the transfer to pick up these changes.

## Start a data transfer

To start a data transfer:

1. (Optional) In the `PI to Data Hub Agents` window, select the PI to Data Hub Agent associated with the data transfer. 

1. (Optional) In the **Manage Agent** tab, expand the `Transfer Overview` section.

1. Select **Start Transfer**, then select **Start**.

   The data transfer begins and transfer status is updated in the `Transfer Overview` section on the **Manage Agent** tab.

   **Note:** The **Manage Agent** tab provides information about the agent associated with the transfer and the transfer progress.

1. In the `Transfer Overview` section, view the transfer status as data is sent to the agent and stream data is created.

   **Note:** The rate at which data transfers varies and depends on the density of data in the source PI Data Archive and/or AF server. See [Data transfer statuses](xref:data-transfer-statuses) for a list of transfer statuses and descriptions. To find out more information about an asset error, agent status, or asset create/update error, select **Logs** above the list of agents to access more information. Possible statuses that appear in the **Current Activity** field may indicate an issue and include Uncategorized Error, PI Point Type Change Detected, and No Valid PI Points In Transfer.   

1. (Optional) To view more information about an agent's status, select **Agent Health Events**.

   **Note:** See [Overview of the Health Events window](xref:health-evts-window) for more information.  
 
1. (Optional) To see more information about log messages for the transfer, select **Logs**. See [Tenant log messages](xref:download-tenant-log) for more information. 

1. (Optional) To view transfer progress and metrics for stream and/or asset creation, select the **Transfer Metrics** tab. See [Overview of transfer metrics](xref:overview-metrics) for more information. 
    
1. (Optional) To stop a transfer, select **Stop Transfer**, then select **Stop**.

1. (Optional) To remove a transfer, select **Remove Transfer**, then select **Remove**.
 