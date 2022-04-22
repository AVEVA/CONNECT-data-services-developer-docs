---
uid: permissions-management
---

# Permissions management

Within OSIsoft Cloud Services, permissions are applied to user roles per resource. These roles are then applied to users, which determine whether they can access the resource. You can edit permissions that each user role has to the following system resources: 

- Agents
- Asset Rules
- Asset Types
- Assets
- Data Views
- Streams
- Types

## Manage Permissions window

Use the `Manage Permissions` window to apply permissions to each user role for a system resource. This window lists a matrix of roles that have permissions for the resource that you are managing, along with the setting for each individual each permission. Use this matrix to add new roles that have permissions on the resource or update individual permissions.

![Manage permissions](images/manage-permissions-for-namespace.png)

### To add roles

Add roles that have permissions for the resource by selecting **Add Role** > **Add** ![Add](../../_icons/branded/plus.svg).

### To remove roles

Remove newly added roles by selecting **Remove** ![Remove](../../_icons/branded/trash-can.svg). Roles that were added previously cannot be removed because they already have permissions assigned that must be cleared first. For more information, see [To clear permissions for a role](#to-clear-permissions-for-a-role).

### To edit permissions

**Read**, **Write**, **Delete**, **Manage Permissions** permissions can be edited for each user role that has permissions in the namespace. Stream resources include an additional **Share** permission. Mouse over each **Information** ![Information](../../_icons/default/information.svg) icon for more information about each permission.

- To allow a permission, select ![Allow](../../_icons/custom/check-circle.svg) **Allow**.

- To explicitly deny a permission, select ![Deny](../../_icons/custom/cancel.svg) **Deny**. 

    **Note:** When a user is assigned multiple user roles with conflicting permissions, a setting of ![Deny](../../_icons/custom/cancel.svg) **Deny** supersedes a setting of ![Allow](../../_icons/custom/check-circle.svg) **Allow** or undefined (`-`) .

### To clear permissions for a role
    
Clear the permissions applied to a role by selecting **Backspace** ![Backspace](../../_icons/branded/backspace.svg). 

**Notes:**

- Allow Manage Permissions access is required on at least one role.
                          
- Roles that have no permissions assigned are not listed the next time that you manage namespace permissions.

### Modified roles

Roles that are highlighted indicate that one of more of its permissions settings have been modified. Newly added roles are highlighted as well. You can restore the original settings by selecting **Cancel**.
