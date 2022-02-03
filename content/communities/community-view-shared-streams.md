---
uid: community-view-shared-streams
---

# View shared streams 

After a community has been established, any member within that community can view which data streams are shared within the community. You can view which data streams are shared one of two ways: from the **Community details** page or from the **Sequential Data Store** page.

## Prerequisites to view shared streams

You must have the [Community Member](xref:ccRoles#community-member-role-preview) role for the community that you want to view stream data.

## To view shared streams from Community details

You can view data streams shared within a community by browsing to its **Community Details** page, choosing a community, and viewing its **Streams** tab.

1. From the left panel, select **Data Management** > **Communities**.

    The **Communities** page opens, listing a card for each community.

1. Browse to the community that you want to shared streams for and click **Details**.

    The **Community details** page opens for the community. 
    
1. From the **Tenants** tab, select the community tenant that you want to view data for.

    Details for the community open in the right pane.

1. From the right pane, select the **Streams** tab.

    ![Tenant shared streams](images/communities-shared-streams.png)

The **Streams** tab lists each data stream that the tenant is sharing with the community. To view shared streams and their details in the **Sequential Data Store** explorer, select a stream and then select the **Launch** icon ![launch icon](../_icons/launch.svg). 

## To view shared streams from Sequential Data Store

When viewing the **Sequential Data Store** page, each stream lists whether it is shared within a community. Additionally, you can use the **Filter Communities** panel to filter for streams shared within one or more community.

1. From the left panel, select **Data Management** > **Sequential Data Store**.

1. (Optional) Toggle the **Filter Communities** panel by clicking the **Filter** icon ![filter icon](../_icons/filter.svg) and select a community to filter for.

    Filtering the page by communities displays only streams that are shared within the selected communities.
    
    ![Filter communities](images/filter-pane.png)

Additional details about the stream display in each tab of the right panel, including **Details**, **Metadata and Tags**, and **Sharing**. The **Sharing** tab lists each community the stream is shared with.
