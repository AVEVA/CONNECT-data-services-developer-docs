---
uid: transfer-data
---

# Transfer data to OCS

You initiate a data transfer from the `PI to OCS Agents` window. A transfer can contain a combination of PI points and AF elements or just PI points or AF elements. The transfer of PI System data to OCS consists of the following procedures:

1. [Create a transfer](#create-a-transfer)

2. [Build an AF elements transfer list](#build-an-af-elements-transfer-list)

3. [View AF element details](#view-af-element-details)
4. [Build a PI points transfer list](#build-a-pi-points-transfer-list)
5. [View PI point details](#view-pi-point-details)

6. [Save a transfer](#save-a-transfer)

7. [Initiate a data transfer](#initiate-a-data-transfer)

To learn about PI point reference types, see [Overview of explicit vs. implicit PI points](#overview-of-explicit-vs.-implicit-pi-points).

#### Before you start

Download and install the PI to OCS Agent. Register your PI Data Archive and AF data sources using the PI to OCS Agent Configuration Utility. 

### Create a transfer

The transfer creation process consists of these steps:

1. Assign a name, description, and optional historical start and end time for data retrieval.
2. Set the level of data privacy protection to control how much identifying information about an asset is sent with PI point data.
3. Set query criteria and retrieve and add desired AF elements and PI point data to your transfer list.
4. Save your transfer.
5. Optional: Export a file(s) that contains transfer detail information.
6. Initiate and monitor the transfer of data from PI to OCS. 

### Procedure 

1. Sign in to the [OCS portal](https://cloud.osisoft.com).

2. Click the menu ![](..\..\images\waffle-button.png) icon, then click **Data Collection > PI to OCS Agents**.

4. In the `PI to OCS Agents` window, select the agent for the data transfer.

5. In the `Details` pane, click **Create Transfer**.

   **Result:** The **Transfer Setting** dialog box opens.
   ![](..\..\images\transfer-settings.png)
5. Enter a name and description for the transfer.

6. Optional: In the **Historical Start time** fields, enter a historical time context for the data retrieval.

   **NOTE:** OCS supports out of order events and stores data in chronological order by timestamp. PI Data Archive 2017 SP2 or higher is required for this feature. Be sure to enter the historical start date and time correctly to ensure all data is included in the transfer. No data before the historical start time will be captured and stored in SDS.  See [Overview of data transfers](https://docs.osisoft.com/bundle/ocs/page/add-organize-data/collect-data/connectors/pi-to-ocs/pi-to-ocs-data-transfers/overview-data-transfers.html) to learn more about transferring historical data.

7. Select the level of data privacy for the transfer by selecting one of the following **Stream Metadata Replication Policy** settings:

   * **High**: Send all identifying information about an asset with the PI point.
   * **Medium (default)**: Send metadata without logical addresses from the data source.
   * **Low**: Does not send any metadata. Locally configured metadata such as point source and local aliases can be sent in the transfer.
   * **None**: No sensitive data is included in the transfer.

8. Click **Ok**.

   **Result:** The transfer is created and the `Transfer` page opens.
   ![](..\..\images\transfer-win.png)
9. Optional: Click the **Settings** button to open the **Transfer Setting** dialog box and modify transfer settings (name, description, historical start and end times, and data privacy settings).

## Build an AF elements transfer list

You build an AF elements transfer by setting query criteria and then selecting AF elements.  You can narrow your search by filtering by element name, asset group, attribute name/value, template, and category. 

1. Select your agent in the **PI to OCS Agents** list, then click the **Add** button.

   **Result:** The `AF Element Search` pane opens.
   ![](..\..\images\af-element-search-tab.png)
2. Click the **AF Database** down arrow, then select the source AF database for your query.
3. Optional: Click the **Root Asset** button, then select a root asset to narrow your search by a specific asset group.
#### To filter by element name:
4. Optional: In the **Element Name** text box, enter search criteria to filter by part or all of an AF element name.
#### To filter by attribute name and/or value:
5. Optional: In the **Attribute Name** text box, enter the attribute name.
6. Optional: In the **Attribute Value** fields, filter by attribute value by specifying the following information:
      * In the first text box, enter an attribute name.
      * Click the operator down arrow, then select an operator (=, <>, <, >, =<, =>, In).
      * In the last text box, enter an attribute value.
#### To filter by AF template or category:
7. Optional: Click the **Template** down arrow to narrow your search by template name.
8. Optional: Click the **Category** down arrow to narrow the search by a specific category.
#### To retrieve and select query results:
9. Click **Search** to execute the query and retrieve matching results.

   **Result:** Query results are displayed in the **Search Results** list.
10. Scroll through the query results and click on each AF elements you want in the transfer.

      **Result:** A checkmark appears next to each AF element.
      
      **Tip:** To select a range of elements, click an element and then scroll to and [SHIFT+Click] a non-adjacent element.
11. To advance through multiple-paged query results, click the back and forward arrows or enter a page number in the **Page** text box.
12. Repeat step 10 until you have finished selecting elements.
13. When you are done selecting elements, click **Add AF Elements To Transfer**.

    **Result:**  The elements are added to the transfer in the `AF Elements` tab.
14. Click **Save** to add and save your selection to the transfer.

**Note:** You can continue adding AF elements after adding and saving a selection. AF Indexing needs to complete before you can view implicit PI points and start the transfer process.

## View AF element details

You can view details about individual AF element such as related attributes and the element path. You can also view the path of any referenced AF elements.

1. In the `Transfer` pane, click the **AF Elements** tab.

2. In the transfer list, select an AF element.

3. Click the **View Details** button.

   **Result:** The **AF Element Information** pane opens.
4. Click the **Reference AF Elements** tab.

   **Result:** If defined, the path(s) of any referenced AF element is listed. 
5. To view details for another AF element, click to deselect the currently selected element, then select a different element in the transfer list.
6. Repeat step 4-5 as needed.
7. Click the **View Details** button or **x** to close the **AF Element Information** pane.

## Build a PI points transfer list
You build a PI points transfer list by setting query criteria and then selecting the desired PI points. A PI points transfer list may contain both implicit and explicit PI points. See [Overview of explicit vs. implicit PI points](#overview-of-explicit-vs.-implicit-pi-points) for more information.

1. Click the **PI Point** **Search** tab.
   ![](..\..\images\pi-pt-search-tab.png)
2. Click the **Add** button.

   **Result:** The `Search` pane opens.
3. Define your search query:

   | Type Of Search Criteria    | Action To Take                                               |
   | -------------------------- | ------------------------------------------------------------ |
   | Common PI point attributes | Enter search criteria in any of the following fields:<br /><ul><li>**Name** (alias for tag attribute)</li><li>**Point Source**</li></ul><br /><br />**Note:** Enter * to retrieve all PI points. |
   | Point descriptions         | Enter search criteria in the following fields:<br /><ul><li>**Descriptor** </li><li>**Extended Descriptor**</li></ul> |
   | Engineering units          | Enter search criteria in the **Engineering Units** field.           |
   | A PI point type            | Select one of the following point types from the **Point Type** drop-down list:<br /><ul><li>**Float32** </li><li>**Float64**</li><li>**Int16**</li><li>**Int32**</li><li>**Digital**</li><li>**Timestamp**</li><li>**String**</li></ul> |
   | Specific location code(s)  | Enter up to five location code values (1-9) in the **Location Codes** field. |

4. Optional: Click the **Search Criteria** bar to collapse or expand the criteria section.
5. Click **Search** to execute the query and retrieve matching results.
6. Scroll through the **Search Results** list box and click each PI point you want added to the data transfer.

   **Result:** A checkmark appears next to each selected PI point.

   **Tip:** To select a range of PI points, click a PI point and then scroll to and [SHIFT+Click] a non-adjacent PI point. 
7. To advance through multiple-paged query results, click the back and forward arrows OR enter a page number in the **Page** text box.
8. Repeat step 6 until you have finished selecting PI points.
9. When you are done selecting PI points, click the **Add PI Points to Transfer** button.

   **Result:**  The points are added to the transfer and appear on the `PI Points` tab.


## Overview of explicit vs. implicit PI points

PI points added to a transfer are assigned one of two reference types:

* Explicit
* Implicit

The reference type indicates the PI point source and how it was retrieved. The reference type appears next to a PI point in the Reference Type column on the **PI Points** tab.

The explicit reference type is assigned to PI points directly retrieved from a PI Data Archive.  The implicit reference type is assigned to PI points that are referenced by AF element attributes and retrieved by searching an AF server.

## Hide implicit PI points

Implicit PI points are PI points referenced by AF elements in a transfer. You can hide implicit PI points to temporarily remove them from view in a transfer list.  Hidden implicit PI points are still included in a transfer unless the referencing AF elements are removed from the transfer list. 

1. On the **Transfer** page, click the **Show Implicit PI Points** toggle button to hide and temporarily remove implicit PI points from the PI points list.

   **Note:** Implicit PI points are referenced by AF element attributes and retrieved from an AF server. Hiding implicit PI points does not remove them from a transfer.  
2. **Optional:** Click the **Show Implicit PI Points** toggle button again to unhide and list any implicit PI points.

## View PI point details

You can view attribute details for selected PI points in a transfer, and also hide/show implicit PI points on the `Transfer` pane.

1. Optional: In the `Transfer` pane, click the **PI Points** tab.
2. Select a PI point.
3. At the top right of the `Transfer` window, click the **View Details** button.

   **Result:** The **PI Point Information** pane opens.
4. Click the **Source AF Elements** tab to view any AF elements that reference the PI point. 
5. To view another PI point's details, click to deselect the currently selected PI point, then select a different PI point in the transfer list.
6. Repeat steps 4-5 as needed.
7. Click the **View Details** button or **x** to close the **PI Point Information** pane.

## Save a transfer

Before you can transfer data to OCS, you must save the transfer to retain your PI point and/or AF element selections.

1. In the `Transfer` pane, click **Save**.

   **Result:** The transfer is saved and you are returned to the `PI to OCS Agents` window.

## Overview of the Details pane

The `Details` pane provides information about the agent associated with the transfer, the saved transfer, and a transfer's data sources.  As shown in the screen capture below, the sections in the `Details` pane can be expanded and collapsed using the chevron arrows (![](../../images/chevrons.png)):  
![](../../images/details-pane2.png)

| Numbered section | Description                                                  |
| ---------------- | ------------------------------------------------------------ |
| **1**            | `Agent Overview:` Lists the agent description (if any), namespace, status, version, and date and time of last connection. |
| **2**            | `Transfer Overview:` Displays transfer details and progress. Also contains buttons to view, remove or stop a transfer. |
| **3**            | `Data Source:` Displays details about the data source server(s) and version(s), as well as the streaming status of a data transfer. It also lists how much historical data has been transferred for a given time period.  If an AF server has been added, details about the AF server and transferred elements is shown under the listed  AF server data source (![](..\..\images\af-data-icon.png)) icon. <br /><br />Under the PI Data Archive data source (![](..\..\images\pda-source-icon.png)) icon, both the Streaming and Historical Events Per Second fields list the number of events successfully transferred over to OCS.  Historical data is the number of incoming events per second that come from a backlog of events for the PI points associated with the transfer, and are not able to be transferred as “real-time” events. Streaming events represent the number of current, real-time events transferred into OCS. |

## Initiate a data transfer

Data is ready for transfer to OCS after the desired PI points and/or AF elements have been added to a transfer.  During the transfer, events are sent asynchronously. Historical events are sent first, followed by current events.

### Before you start

In the `PI to OCS Agents` window, select the PI to OCS Agent that contains the data you want to transfer.

###  Procedure

1. Optional: In the `Details` pane, click the `Transfer Overview` down chevron arrow to expand this section.

   **Result:** The `Transfer Overview` section expands.
2. Click the **Start Transfer** button, then click **Start**.

   **Result:** The transfer process begins and information about the transfer is updated in the `Details` pane.
3. In the `Details` pane, expand the `Data Source` section to view the status of a transfer as data is sent to OCS.

   **Note:** The rate at which data is transferred varies and depends on the density of data in the source PI Data Archive and/or AF server. See [Data transfer statuses](xref:data-transfer-statuses) for a list of transfer statuses and descriptions. 
4. Optional: To stop a transfer, click **Stop Transfer**, then click **Stop**.
5. Optional: To remove a transfer, click **Remove Transfer**, then click **Remove**.