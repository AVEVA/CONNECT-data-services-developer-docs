---
uid: community-view-shared-streams
---

# View shared streams 

After a community has been established, you can view which data streams in your tenant have been shared into a community. You can view which data streams are shared in one of two ways: from the `Communities` page or from SDS explorer. Your access to view information depends upon your assigned user roles and permissions.

## To view shared streams

You can view shared streams from both the `Communities` page and SDS explorer. Select one of the tabs for more information on how to view which data streams are shared.

## [Communities](#tab/communities)

From the `Communities` page **Tenants** tab, you can view which data streams each tenant has shared with the community.

1. From the left panel, select **Data Management** > **Communities**.

1. Browse to the applicable community and select **Details**.
    
1. From the **Tenants** tab, select a tenant to view which streams that it is sharing with the community.

    Details for the community open in the right pane.

1. From the right pane, select the **Streams** tab.

    **Tips:**

        - To view shared streams and their details in the **Sequential Data Store** explorer,  select the **Launch** icon ![launch icon](../_icons/launch.svg).

        - If you are viewing your own tenant and you have sharing permissions for the stream, you can unshare them in this context by selecting a stream and choosing **Unshare Stream**.
    
    ![Tenant shared streams](images/communities-shared-streams.png)

The **Streams** tab lists each data stream that the tenant is sharing with the community. 

## [Sequential Data Store](#tab/sds)

When working from SDS explorer, you can view which data streams your tenant is sharing either by stream or by community. Additionally, you can also view which streams are shared into the community by other tenants.

### View your shared streams by community

1. From the left panel, select **Data Management** > **Sequential Data Store**.

1. (Optional) Toggle the **Filter Communities** panel by clicking the **Filter** icon ![filter icon](../_icons/filter.svg) and select a community to filter for.

    Filtering the page by communities displays only streams that are shared within the selected communities.
    
    ![Filter communities](images/filter-pane.png)

Additional details about the stream display in each tab of the right panel, including **Details**, **Metadata and Tags**, and **Sharing**. The **Sharing** tab lists each community the stream is shared with.

### View the communities that a stream is shared to

### View stream shared by other tenants

***
