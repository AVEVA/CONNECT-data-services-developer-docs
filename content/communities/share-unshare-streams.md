---
uid: ShareStreams
---

# Share and unshare streams

Use these procedures to share or stop sharing streams of data with other communities.

**Note:** To share or unshare a stream, your role must have the Manage Permission privilege for that stream. By default any user who creates a stream has the Manage Permission privilege. To manage permissions for a role, use the **Sequential Data Store > Streams** feature. <!--VT, 7/23/21: Should feature be command?--> 

## Share streams

To perform this procedure you must have already defined streams.

1. On the navigation bar, click **Sequential Data Store**.

1. If necessary, select a namespace at top left.

  ![](images\select-namespace-streams.png "Select a namespace and Streams")

1. If it is not already selected, select **Streams** at top left.

1. Select one or more streams to share.

1. Select **More Options** ![More Options](images\more-options.png "More Options") and select **Share Stream** from the dropdown menu.

  If you select multiple streams, a pane appears for managing streams. You can select **Share Streams** on that pane.

1. Click **Select Communities**.<br>A list of communities appears.

1. Select the communities with which you want to share streams and click **Continue**. If necessary, filter the list of communities by typing in the **Filter Communities** box.

1. Click **Continue**. and then click **Share**. When prompted for confirmation, click **Confirm**.

  All members of the selected communities are able to read data from the shared streams.

## Unshare streams

1. On the `Communities` overview page, find the community where you are sharing streams and click **Details**.

1. On the `Community Details` page, click the **Tenants** tab.

1. Select your own tenant.<br>If you have shared streams, a **Streams** tab appears at right.

1. On the **Streams** tab, select the streams you want to unshare and click **Unshare Streams**. When prompted for confirmation, click **Unshare**.
