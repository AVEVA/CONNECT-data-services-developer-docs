---
uid: ShareStreams
---

# Share and unshare streams

Use these procedures to share or stop sharing streams of data with other communities. To share streams, they must already be defined.

**Note:** To share or unshare a stream, your role must have the Manage Permission privilege for that stream. By default any user who creates a stream has the Manage Permission privilege. To manage permissions for a role, use the **Sequential Data Store** > **Streams** feature.

## Share streams

To share streams with other communities, follow these steps:

1. In the left pane, select **Data Management** > **Sequential Data Store**.

1. If it is not already selected, select **Streams** at the upper left.

1. Select one or more streams to share.

    To search for a particular stream, enter a search term in the **Search for streams** field. If necessary, use a wildcard operator "*" to return results that start or end with a particular phrase. For more information, see [Search in SDS](xref:sdsSearching).

1. Select the **More Options** icon ![More Options](images\more-options.png "More Options"), then select **Share Stream** from the dropdown list.

    If you selected multiple streams in the previous step, a pane appears for managing streams. You can select **Share Streams** on that pane.

1. Select **Select Communities**.

1. From the list of communities, select the communities with which you want to share streams and select **Continue**. If necessary, filter the list of communities by typing in the **Filter Communities** filter.

1. Select **Continue**, and then select **Share**. When prompted for confirmation, select **Confirm**.

    All members of the selected communities are able to read data from the shared streams.

## Unshare streams from Community Details

To stop sharing streams, follow these steps:

1. In the left pane, select **Data Management** > **Communities**.

1. Find the community where you are sharing streams and select **Details**.

1. On the `Community Details` page, select the **Tenants** tab.

1. Select your own tenant.

    If you have shared streams, a **Streams** tab appears at right.

1. On the **Streams** tab, select the streams you want to stop sharing, then select **Unshare Streams**. When prompted for confirmation, select **Unshare**.

## Unshare streams from the Sequential Data Store

In addition to unsharing streams, the Sequential Data Store provides many capabilities for managing streams. For more information, see [Manage streams](xref:manage-streams).

To stop sharing streams, follow these steps:

1. In the left pane, select **Data Management** > **Sequential Data Store**.

1. Use the toggle switches to filter streams by namespace or community.

   ![Toggle switches](images\namespace-communities-switches.png)

1. From the list, select a namespace or a community.

    To search for a particular stream, enter a search term in the **Search for streams** text box. If necessary, use a wildcard operator "*" to return results that start or end with a particular phrase. For more information, see [Search in SDS](xref:sdsSearching).

1. From the list of streams, select one or more to stop sharing.

1. Select the **More Options** icon ![More Options](images\more-options.png "More Options"), and then select **Unshare Stream** from the dropdown list.

    If you selected multiple streams in the previous step, a pane appears for managing streams. You can select **Unshare Streams** on that pane.

1. When prompted for confirmation, select **Unshare**.
