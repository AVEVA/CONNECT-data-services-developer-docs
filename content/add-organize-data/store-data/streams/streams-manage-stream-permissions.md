---
uid: streams-manage-stream-permissions
---

# Manage stream permissions

If you are assigned the **Manage Permissions** access right, then you can configure stream permissions for other user roles in your tenant. You can granularly assign individual stream permissions to each user role in your tenant.

## Prerequisites

To manage data stream permissions, your user role must be assigned the **Manage Permissions** access right.

## Manage permissions for streams

To manage permissions for a single data stream, complete the following steps:

1. From the left pane, select **Data Management** > **Sequential Data Store**.

1. Select one or more stream that you want to manage permissions for.

1. Select **Manage Permissions**.

    **Tip:** If you are only managing permissions for a single stream, select **More options** ![More options icon](../../../_icons/default/dots-vertical.svg) > **Manage Permissions** instead.

1. Use the `Manage Permissions` to edit stream permissions for each user role. For more information, see [Manage Permissions for Streams window](#manage-permissions-for-streams-window).

1. Select **Save**.

## Manage default permissions for new streams

You can edit the default user roles and permissions added to stream when it is created. Editing these default roles and permissions speeds up creation of new data streams by minimizing permission edits.

1. From the left pane, select **Data Management** > **Sequential Data Store**.

1. Select **More options** ![More options icon](../../../_icons/default/dots-vertical.svg) > **Manage Default Permissions**.

1. Use the `Manage Default Permissions` window to edit default edit stream permissions.

1. (Optional) To update all existing data streams within the namespace with your selected default settings, select **Apply to all existing streams in the Namespace**.

	**Warning!** Use of this option applies your updated permission settings to *all* streams in the namespace using a patch operation. Use this option with care, as it will overwrite existing permission settings.

1. Select **Save**.

## Manage Permissions for Streams window

Regardless of what context you are editing stream permissions, all edits are performed using the **Manage Permissions for Streams** dialog. This dialog lists a matrix of roles that have permissions for the selected streams, along with the setting for each individual each permission. Use this matrix to add new roles that have permissions for the streams or update individual permissions.

![Manage permissions](../../../communities/images/manage-permissions-for-streams.png)

<details>
	<summary><strong>To add roles</strong></summary>
    <p>Add roles that have permissions for the selected streams by selecting <strong>Add Role</strong> > <strong>Plus</strong> <img src="../../../_icons/branded/plus.svg"/>.</p>
</details>
<details>
	<summary><strong>To edit permissions for a role</strong></summary>
    <p>Read, write, delete, manage permissions, and share permissions can be edited for each user role that has permissions on the stream. Mouse over the <strong>Information</strong> <img src="../../../_icons/branded/information.svg"/> icon for more information about each permission. Permission that have a default value of `-` are equivalent to a setting of <img src="../../../_icons/custom/cancel.svg"/> <strong>Deny</strong>.</p>
    <ul>
        <li><p>To allow a permission, select <img src="../../../_icons/custom/check-circle.svg"/> <strong>Allow</strong>.</p></li>
        <li><p>To explicitly deny a permission, select <img src="../../../_icons/custom/cancel.svg"/> <strong>Deny</strong>.</p></li>
    </ul>
    <p>Roles that are highlighted indicate a *dirty* state—one of more of its permissions settings have been modified. You can restore the original settings by selecting <strong>Cancel</strong>.
</p>
</details>
<details>
	<summary><strong>To clear settings for a role</strong></summary>
    <p>Clear the permissions applied to a role by selecting <strong>Backspace</strong> <img src="../../../_icons/branded/backspace.svg"/>.</p>
</details>
<details>
	<summary><strong>To remove roles</strong></summary>
    <p>Remove roles that have permissions for the selected streams by first clearing the permissions settings for the role and then selecting the <strong>Delete</strong> <img src="../../../_icons/branded/trash-can.svg"> icon to completely remove the role from the streams.</p>
</details>
