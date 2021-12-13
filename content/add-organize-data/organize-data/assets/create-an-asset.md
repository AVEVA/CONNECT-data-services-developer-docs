---
uid: CreateConfigureAsset
---

# Add an asset

Follow this procedure to create an asset, add and configure its metadata and properties, and select and configure a property whose status will be visible in the card or table view.

To create an asset, follow these steps:

1. In the left pane, select **Visualization** > **Asset Explorer**.

1. From the **Asset/Asset Types** selector, select **Assets**.

1. In the toolbar, select **Add Asset**. 

1. In the `Select Type for New Asset` window, select **None** and select **Continue**.

1. In the right pane, complete the following fields:

   - **Asset** - Enter a name to identify the asset.

   - **Description** - (Optional) Add a description for the asset. 

1. Select the **Metadata** tab.

1. For each metadata to add to the asset, select **Add Metadata** and complete the following fields:

   - **Metadata** - Enter an identifier for the metadata.

   - **Value** - Enter the value for the metadata.

     **Note:** The value must match the selected type. The following date/time format is supported: MM/DD/(YY)YY hh:mm(:ss)

   - **Type** - Select the value type from the dropdown list.

   - **UOM** - If the type is `Integer` or `Double`, select the unit of measure for the value.

1. Select the **Properties** tab. 

1. For each property to add to the asset, select **Add Stream References** and complete the following steps:

   1. In the `Select Streams` window, select the stream and select **Add**..
   
     **Note:** Use the search box to find the stream. You can search on the stream name, description, or the type. Use the asterisk (*)  as a wildcard character.

     The stream reference appears in the right pane. This is the automatically generated user-friendly stream name. You can edit this name.
         
1. Click the scroll bar to display the properties for the stream reference.
   
1. Click **Configure UOMs**. 

1. On the `Configure UOMs` page, make any changes to the property UOMs.

    **Note:** UOMs can be set only on numeric types.

1. When you are done, click **Save**.

    **Note:** Once you click **Save**, any changes are immediately made to the UOMs on the stream, regardless of any other actions you take on this asset. For example, the UOM changes to the stream are not reversed if you click **Cancel** on the **Properties** tab or if you delete the asset.

## Add status tracking to the asset

1. Click the **Status** tab.

2. Click **Add Status Configuration**.

3. In the `Select Property` window, click the property that you want to display status for. Click **Continue**.

    **Note:** Only properties with enumerated states or string values can be selected for the asset status;  therefore, only these properties are displayed. 

    You can only specify one property as the asset's status. 

1. Click the status icons to map the icon for each value.
    
    **Tip:** You can switch to a different property by clicking the ![Change property icon](images/change-property-icon.png) icon.

## Save the asset

1. Click **Save**. 

## Related links

- [Assets](xref:AssetsProperties) Properties
- [Assets API](xref:AssetsAPI)
