---
uid: community-manage-shared-streams
---

# Manage shared streams 

Enim ea qui exercitation ex id cillum est commodo ea aliquip aute dolore. Elit fugiat sit reprehenderit adipisicing laboris. Elit eiusmod ullamco nulla proident. Voluptate aliquip dolore voluptate ad.

Irure laborum officia aliqua incididunt nostrud in aliquip officia sit magna irure aliqua. Ut aliqua excepteur qui mollit adipisicing incididunt. Id eu velit ea mollit ea elit qui consequat officia cupidatat amet ipsum dolore occaecat. Anim cillum ipsum officia exercitation fugiat non. Commodo incididunt quis dolor sit do. Aliquip ipsum esse exercitation ullamco deserunt fugiat consectetur ut officia voluptate ex anim aliqua reprehenderit. Enim exercitation adipisicing adipisicing consectetur velit aute qui cillum ea qui ipsum esse.

## Prerequisites

Sit non labore proident esse aliquip duis velit ex consequat irure. Nostrud ex eu id anim enim. Reprehenderit aliquip officia elit aliquip id nulla in eiusmod. Et ex ut magna veniam consequat laboris proident adipisicing nisi. Deserunt laborum enim nulla laboris nostrud Lorem culpa. Ad eiusmod commodo esse deserunt sunt veniam. Velit deserunt sit dolor id aute sint sint esse duis id sint et veniam ullamco.

## Share streams

User with permissions to share a data stream within a community can do so from the Sequential Data Store page. To share streams with other communities, follow these steps:

1. In the left pane, select **Data Management** > **Sequential Data Store**.

1. If it is not already selected, select **Streams** at the upper left.

1. Select each stream that you want to share, and then select **More Options** ![More Options](../_icons/dots-vertical.svg) > **Share Stream**.

    **Tips:** 

    * Use the **Search for streams** field to search for specific streams. Use the wildcard operator (`*`) to return results that start or end with a particular phrase. For more information, see [Search in SDS](xref:sdsSearching).

    * When sharing a large numbers of streams, edit the **Items per page** dropdown to a value that accommodates the number of streams that you want to share.

1. Select one or more community to share your streams with.

1. Select **Select Communities**.

1. From the list of communities, select the communities with which you want to share streams and select **Continue**. 

    **Tip:** Use the **Filter Communities** field to find a specific community.
    
1. To confirm that you want to share the streams with the chosen communities, select **Share**. From the **Share stream** window, select **Confirm**. Then select **Close**.

The chosen streams are shared with the chosen communities. All members of the selected communities are able to read data from the shared streams.

***

## Unshare streams

When you want to stop sharing streams with a community, you can do so from either the `Communities` page or `Sequential Data Store` explorer.

<!-- TODO: draft task-->

### [Communities](#tab/communities)

Adipisicing non id culpa proident est. Id laboris consectetur quis do exercitation anim voluptate. Ad cupidatat officia occaecat adipisicing.

### [Sequential Data Store](#tab/sds)

To stop sharing streams with a community from SDS explorer, follow these steps:

1. In the left pane, select **Data Management** > **Sequential Data Store**.

1. If it is not already selected, select **Streams** at the upper left.

1. Ensure that the **Filter Communities** pane is displayed. Enable it by selecting the **Filter Tenants** ![Filter Tenants](../_icons/filter.svg) icon. 

1. From the **Filter Communities** pane, select one or more community from which to unshare streams.

    **Note:** This pane only lists communities where you are a Community Member.

1. From the list of streams, select one or more to streams unshare. 

1. Select **More Options** ![More Options](../_icons/dots-vertical.svg) > **Unshare Stream**. 

    **Tip:** You can also unshare streams using the **Unshare Streams** buttons available in the right pane.

1. When prompted for confirmation, select **Unshare**.

***
