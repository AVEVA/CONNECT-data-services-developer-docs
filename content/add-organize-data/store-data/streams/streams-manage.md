---
uid: manage-streams
---
# Manage streams

The Sequential Data Store gives you capabilities to manage stored streams. The capabilities function the same if you are working in the context of a namespace or a community.

## Manage permissions

For a role to perform any actions on a stream, you must grant that role permissions for the stream. For any stream, you can assign the following permissions to a role:

- Read
- Write
- Delete
- Manage Permissions
- Share

1. From the left pane, select **Data Management** > **Sequential Data Store**.

1. Select one or more streams.

1. Select **More options** ![More options icon](../../../_icons/dots-vertical.svg) > **Manage Permissions**.

1. In the `Manage Permissions` window, from **Select Role**, choose the role whose permissions you want to modify.

1. Select the permissions to grant to the selected role, and then select **Save**.

## Add tags or metadata

Tags and metadata allow you to associate additional information with a stream. For example, tags can denote special attributes for a stream. Metadata consists of keys and their associated values.

1. From the left pane, select **Data Management** > **Sequential Data Store**.

1. Select a stream.

1. Select **More options** ![More options icon](../../../_icons/dots-vertical.svg) > **Edit Stream**.

   A tab opens to allow you to modify the metadata and tags for the stream.

1. Add metadata.

   - Select the **Metadata** tab, and then select **Add Metadata**. In the `Metadata Key` box, enter the name of the key and in the `Metadata Value` box, enter a value for that key.

   - To remove a metadata, select the **X** beside the row to be deleted.

1. Add tags.

   - Select the **Tags** tab, if it is not already selected. In the `New Tag` box, enter the name of the tag, and then select the plus sign (**+**).
   
   - To remove a tag, select the **X** beside the tag name.

## Share streams

You can share streams with other tenants from the **Sequential Data Store** page. Choose the streams that you want to share and the communities that you want to share them with. 

To share streams with other communities, follow these steps:

1. In the left pane, select **Data Management** > **Sequential Data Store**.

1. If it is not already selected, select **Streams** at the upper left.

1. Select each stream that you want to share, and then select **More Options** ![More Options](../../../_icons/dots-vertical.svg) > **Share Stream**.

    **Tips:** 

    * Use the **Search for streams** field to search for specific streams. Use the wildcard operator (`*`) to return results that start or end with a particular phrase. For more information, see [Search in SDS](xref:sdsSearching).

    * When sharing a large numbers of streams, edit the **Items per page** dropdown to a value that accommodates the number of streams that you want to share.

1. Select one or more community to share your streams with.

1. Select **Select Communities**.

1. From the list of communities, select the communities with which you want to share streams and select **Continue**. 

    **Tip:** Use the **Filter Communities** field to find a specific community.
    
1. To confirm that you want to share the streams with the chosen communities, select **Share**. From the **Share stream** window, select **Confirm**. Then select **Close**.

The chosen streams are shared with the chosen communities. All members of the selected communities are able to read data from the shared streams.

## Unshare streams

To stop sharing streams with a community, follow these steps:

1. In the left pane, select **Data Management** > **Sequential Data Store**.

1. If it is not already selected, select **Streams** at the upper left.

1. Ensure that the **Filter Communities** pane is displayed. Enable it by selecting the **Filter Tenants** ![Filter Tenants](../../../_icons/filter.svg) icon. 

1. From the **Filter Communities** pane, select one or more community from which to unshare streams.

    **Note:** This pane only lists communities where you are a Community Member.

1. From the list of streams, select one or more to streams unshare. 

1. Select **More Options** ![More Options](../../../_icons/dots-vertical.svg) > **Unshare Stream**. 

    **Tip:** You can also unshare streams using the **Unshare Streams** buttons available in the right pane.

1. When prompted for confirmation, select **Unshare**.

## Remove streams

When you remove a stream, you are deleting it.

1. From the left pane, select **Data Management** > **Sequential Data Store**.

1. Select one or more streams.

1. Select **More options** ![More options icon](../../../_icons/dots-vertical.svg) > **Remove Stream**.

1. In the confirmation window, select **Remove** to confirm the deletion.
