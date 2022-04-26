---
uid: streams-manage-stream-permissions
---

# Manage permissions for streams

If you are assigned the **Manage Permissions** access right, then you can configure stream permissions for other user roles in your tenant. You can granularly assign individual stream permissions to each user role.

## Prerequisites

To manage data stream permissions, you must be assigned the **Manage Permissions** access right.

## To manage permissions for streams

When managing permissions for streams, you can either edit them one at a time or in bulk.

### [Single stream](#tab/tabid-1)

When editing permissions for a single stream, each user role that has permissions assigned are pre-populated in the window that opens.

1. From the left pane, select **Data Management** > **Sequential Data Store**.

1. Select a single stream that you want to manage permissions for.

1. Select **More options** ![More options icon](../../../_icons/default/dots-vertical.svg) > **Manage Permissions**.  

    The `Manage Permissions for Stream` window opens. Because you are editing permissions for a single stream, all user roles that have permissions on the stream are displayed along with their settings.

    **Stream with pre-populated user roles and permissions**
    ![Manage Permissions for Stream](../images/manage-stream-permissions-single-stream.png)

1. Use the `Manage Permissions for Stream` window to:

    - (Optional) Add user roles that have permissions on the stream.
    - Edit stream permissions for each user role.

    For more information, see [Manage Permissions window](xref:permissions-management#manage-permissions-window).

1. When you are finished editing permissions, select **Save**.

### [Multiple streams](#tab/tabid-2)

When editing permissions for multiple streams, no user roles or permission settings are pre-populated in the window because the permissions for each stream are unique. Therefore you must add each user role that you want to have permissions on the stream before editing each permission setting.

1. From the left pane, select **Data Management** > **Sequential Data Store**.

1. Select one or more streams that you want to manage permissions for.

1. Select **Manage Permissions**.

    The `Manage Permissions for Selected Streams` window opens. Because you are editing permissions for multiple streams, no user roles or settings are listed, as the permission settings for each stream are different.
    
    **Streams without pre-populated user roles and permissions**
    ![Manage Permissions for Selected Streams](../images/manage-stream-permissions-bulk.png)

1. Use the `Manage Permissions` window to:

    - Add user roles that have permissions on the stream.
    - Edit stream permissions for each user role.

    For more information, see [Manage Permissions window](xref:permissions-management#manage-permissions-window).

1. When you are finished editing permissions, select **Save**.

    **Note:** This action overwrites any previous permission settings applied to the affected user roles.

***

## To manage default permissions for new streams

You can edit the default user roles and permissions added to a stream when it is created.

1. From the left pane, select **Data Management** > **Sequential Data Store**.

1. Select **More options** ![More options icon](../../../_icons/default/dots-vertical.svg) > **Manage Default Permissions**.

1. Use the `Manage Default Permissions` window to edit default user roles and stream permissions. For more information, see [Manage Permissions window](xref:permissions-management#manage-permissions-window).

1. (Optional) To update all existing data streams within the namespace with your selected default settings, select **Apply to all existing streams in the Namespace**.

	**Warning!** Use of this option applies updated permission settings to *all* streams in the namespace. Use this option with care, as it overwrites existing permission settings.

1. When you are finished editing permissions, select **Save**.
