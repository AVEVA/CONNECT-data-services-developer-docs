---
uid: CreateAssetFromAssetType
---

# Add an asset based on an asset type

For more information on asset types, see [Asset types](xref:AssetTypes).

To create an asset based on an asset type, follow these steps:

1. In the left pane, select **Visualization** > **Asset Explorer**.

1. From the **Asset/Asset Types** selector, select **Assets**.

1. In the toolbar, select **Add Asset**. 

1. In the `Select Type for New Asset` window, select the type and select **Continue**.

1. In the right pane, complete the following fields:

   - **Asset** - Enter a name to identify the asset.

   - **Asset Type** - Displays the asset type on which this asset is based.

   - **Description** - (Optional) Add a description for the asset. 

1. Select the **Metadata** tab. 

1. Edit the values for any of the metadata.

    **Note:** You can only edit the values. The metadata are derived from the asset type, as indicated by the **T** and, therefore, you cannot add or delete metadata or change the type.

1. Select the **Properties** tab.

1. Select the caret ![](images/caret.png) icon to reveal the stream reference configuration details. 

1. To open the `Select Stream` window, select **Choose a Stream**.

1. Select the stream from the list of streams.

     **Note:** Only streams of the type specified for the stream reference are displayed. You can search the stream name, ID, or description. You can use the asterisk (*) as a wildcard.

1. Select **Add**.

1. Select **Configure UOMs**. 

1. On the `Configure UOMs` page, make any changes to the property UOMs.

    **Note:** UOMs can be set only on numeric types.

1. When you are done, select **Save**.

     **Note:** Once you select **Save**, any changes are immediately made to the UOMs on the stream, regardless of any other actions you take on this asset. For example, the UOM changes to the stream are not reversed if you select **Cancel** on the **Properties** tab or if you delete the asset.

1. To save the asset, select **Save**.

## Related links

- [Assets](xref:AssetsProperties) Properties
- [Asset Types API](xref:AssetTypesAPI)
