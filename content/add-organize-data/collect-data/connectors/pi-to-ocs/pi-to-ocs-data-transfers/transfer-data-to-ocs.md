---
uid: create-transfer
---

# Create a data transfer

You create a data transfer from the `PI to Data Hub Agents` page. A transfer can consist of PI points and AF elements or AF elements that reference at least one PI point. AF elements reference PI points via AF attributes that have a PI point data reference.

PI points can be added to a transfer explicitly using a tag search or implicitly using AF element references. For information about the difference between implicit and explicit references, see [Explicit versus implicit PI points](#explicit-versus-implicit-pi-points).

**Before you begin:** Download and install the PI to Data Hub Agent. Register your Data Archive and AF data sources using the PI to Data Hub Agent Configuration Utility.

Transfer creation consists of the following tasks:

1. Name the transfer and set data privacy settings. Assign a name, description, and optional historical start time for data retrieval.

1. Select Stream Metadata Replication Policy (High, Medium, Low, or None) to control which PI point attributes the transfer stores as metadata in SDS streams. This policy provides a level of data privacy in cases where sensitive information is stored in PI point attributes that you do not want replicated to the cloud.

1. Build an AF elements transfer list. For agents with AF server configured, search for AF elements to add to the transfer. Add AF elements to the transfer. PI points referenced by AF elements will be implicitly added to the transfer. Points added to the transfer in this manner are referred to as Implicit PI points.

1. Build a PI points transfer list. Instead of or in addition to adding AF elements, you can search for PI points explicitly and add these to the transfer. Points added to the transfer in this manner are referred to as Explicit PI points.

1. View transfer details.

1. Save the transfer. Before you can save a transfer, at least one Implicit or Explicit PI point must be added to the transfer and the Implicit or Explicit PI points must correspond to the same Data Archive.

**Note:** If you have configured an AF server, you will not be able to create a transfer until AF indexing is complete. AF indexing status is listed on the **Manage Agent** tab in the `PI to Data Hub Agents` page. The following image shows AF indexing in progress:

![Manage Agent tab displaying successful AF Server and PI Points indexing](../../images/af-indexing.png)

## Name the transfer and set data privacy settings

To name the data transfer:

1. In the left pane, select **Data Collection** > **PI to Data Hub Agents**.

1. In the `PI to Data Hub Agents` page, select the agent for the data transfer.

1. In the **Manage Agent** tab, select **Create Transfer**.

   The `Transfer Settings` window opens.

   ![Transfer Settings window displaying default options](../../images/transfer-settings.png)

1. In the **Name** and **Description** fields, enter a name and description for the transfer.

1. (Optional) In the **Historical Start Time** field, enter a historical time context for the data retrieval. Be sure to enter the historical start date and time correctly to ensure all data is included in the transfer. No data before the historical start time will be captured and stored in SDS. See <xref:lp-transfer> to learn more about transferring historical data.

   **Note:** The PI to Data Hub Agent supports transferring out-of-order events written to Data Archive.

1. To set the data privacy level for the transfer, select the **Stream Metadata Replication Policy**. In this context, metadata refers to PI point attributes transferred as SDS stream metadata.

   - **High**: Sends all supported PI point attributes as metadata.
   - **Medium**: Default. Sends metadata without logical addresses from the data source.
   - **Low**: Sends no metadata from the data source namespace. Locally configured metadata such as point source and local aliases is allowed (point name, point ID and point source only).
   - **None**: Sends only the point ID and point name; no metadata is included in the transfer.

   **PI point attributes transferred with each Stream Metadata Replication Policy (data privacy) setting**

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
    | Step | X | X |  |  |

1. (Optional) To have streams and assets automatically removed from the transfer when their corresponding PI points and AF elements are removed, select the **Automatically delete Streams and Assets from the cloud** option.

1. Select **Ok**.

   The transfer is created and the `Transfer` page opens.

**Note:** To modify the transfer settings, select **Settings** to access the `Transfer Settings` window and modify the name, description, historical start time, and data privacy settings as needed.

## Build an AF elements transfer list

After naming the transfer, build an AF elements transfer list by setting query criteria and then selecting AF elements. You can narrow your search by filtering by element name, root element, attribute name/value, template, and category. A corresponding asset is created for every AF element in your transfer. Static AF element attributes become asset metadata.

1. On the `Transfer` page, select the source AF database from the **AF Database** dropdown list.

   ![Transfer page with AF Database selected](../../images/transfer-win.png)

1. (Optional) Select **Root Element**.

1. (Optional) In the `Select Root Element` window, select the plus buttons to drill down to the root element in the AF database hierarchy, select a root element, then choose **Select**.

1. (Optional) In the **Element Name** field, enter search criteria to filter by part or an entire AF element name.

   **Note:** If you do not enter filter criteria, the search defaults to `*` or all.

1. (Optional) In the **Attribute Name** field, enter the attribute name.

1. (Optional) In the **Attribute Value** fields, filter attribute values by specifying the following information:

   **Note:** Custom units of measure (UOMs) are not supported. During the transfer of AF element data, AF elements with custom UOMs will not have their corresponding asset's UOM property set.

   - In the first field, enter an attribute name.

   - In the second field, use the dropdown list to select an operator (`=`, `<>`, `<`, `>`, `<=`, `>=`, `In`).

   - In the last field, enter an attribute value.

   **Note:** Custom units of measure (UOMs) are not supported. During the transfer of AF element data, AF elements with custom UOMs will not have their UOM property set.

1. (Optional) To narrow your search by template name, in the **Template** field, select a template from the dropdown list.

1. (Optional) To narrow the search by a specific AF category, in the **Category** field, select a category from the dropdown list.

1. To execute the query and retrieve results, select **Search**.

   When dealing with large data sets, a search query can take a significant amount of time. Select **Cancel** to stop the query if necessary.

1. In the `Search Results` list, select each AF element you want added to the transfer.

   A check mark appears next to each selected AF element.

   **Tip:** To select a range of elements, select an element, hold the Shift key, and select a non-adjacent element. To advance through multiple-paged query results, select the back and forward arrows or enter a page number in the **Page** field.

1. When you are done selecting elements, select **Add AF Elements To Transfer**.

   The elements are added to the transfer and listed on the **AF Elements** tab.

1. To add additional elements from other AF databases, repeat these steps.

**Note:** AF indexing must complete before you can view implicit PI points and start the transfer process.

## View AF element details

You can view details about an individual AF element such as related attribute names, values, and data references.

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

1. (Optional) To collapse or expand the criteria section, select the **Search Criteria** bar.

1. To execute the query and retrieve matching results, select **Search**.

   When dealing with large data sets, a search query can take a significant amount of time. Select **Cancel** to stop the query if necessary.

1. In the **Search Results** area, select each PI point to add to the data transfer.

   A check mark appears next to each selected PI point.

   **Tip:** To select a range of PI points, select a PI point and then hold Shift and select a non-adjacent PI point. To advance through multiple-paged query results, select the back and forward arrows or enter a page number in the **Page** field.

1. When you are done selecting PI points, select **Add PI Points to Transfer**.

   The points are added to the transfer and listed on the **PI Points** tab.

## Explicit versus implicit PI points

PI points added to a transfer are assigned one of the following reference types:

- Explicit - PI points directly retrieved from a Data Archive.

- Implicit - PI points referenced by AF element attributes that have been retrieved by searching an AF server.

The reference type for each PI point is listed in the `Reference Type` column on the **PI Points** tab.

## View PI point details and hide implicit PI points

You can view attribute details for selected PI points in a transfer. Implicit PI points are PI points referenced only by AF elements in a transfer. You can hide implicit PI points to temporarily remove them from view on the **PI Points** tab. Hidden implicit PI points are still included in a transfer unless the referencing AF elements are removed from the transfer list.

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

Before you can transfer data to AVEVA Data Hub, you must save the transfer.

1. To ensure your data transfer definition is correct and contains all the data you want transferred, review it for accuracy.

1. (Optional) Add or remove PI points and/or AF elements as needed.

1. To save the transfer and return to the `PI to Data Hub Agents` page, select **Save** in the lower right-hand corner.

   **Note:** In order to save the transfer, it must include at least one valid PI point.
