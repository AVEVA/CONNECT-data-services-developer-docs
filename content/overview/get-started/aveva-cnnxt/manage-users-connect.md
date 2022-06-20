---
uid: ManageUsersConnect
---

# Manage users and permissions

User and permission management occurs in both AVEVA Connect and AVEVA Data Hub. You begin in AVEVA Connect by creating groups, assigning roles, and adding users. These tasks require Account Administrator privileges in AVEVA Connect. Once these tasks are complete, you can add and then map existing users or groups to AVEVA Data Hub roles.

An overview of the process is outlined below.

1. [Create groups](xref:create-group) in AVEVA Connect.

   - The User group is built-in and applies to all users by default.
   - Add additional groups if you wish to control individual access to folders (namespaces in AVEVA Data Hub), or for use within AVEVA Data Hub to control permissions.

1. [Assign roles to groups](xref:assign-roles-groups) in AVEVA Connect.

   - The DataHub Viewer role allows the user to see the namespace tile in AVEVA Connect and access AVEVA Data Hub for that namespace.
   - Only the DataHub Viewer role is applicable to AVEVA Data Hub. For information on other roles in AVEVA Connect see [View Role Assignments](https://help.connect.aveva.com/#/home/885637/10/11).
   - When the AVEVA Data Hub service is activated for a folder, it automatically adds the DataHub Viewer role for that folder to the User group. You can remove the role from the User group if you do not wish all of your users to have access to that namespace.

1. [Add users](xref:invite-users) in AVEVA Connect.

   - Adding users can be done individually, or you can prepare and import a spreadsheet. See [Import Users in Bulk](https://help.connect.aveva.com/#/home/885599/10/11).
   - You can assign groups to users when they are created, or add them later.

1. [Add the groups](xref:Groups) you created in AVEVA Connect to AVEVA Data Hub and assign roles to them.

1. [Add the users](xref:gpUsers) to AVEVA Data Hub.

   - The AVEVA Data Hub roles assigned to a user's group apply to the user automatically.
   - Other roles can be added individually.
   - By default the Account Administrator in AVEVA Connect will have the Tenant Administrator role in AVEVA Data Hub.