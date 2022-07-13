---
uid: ManageUsersConnect
---

# Manage users and permissions

User and permission management occurs in both AVEVA Connect and AVEVA Data Hub. You begin in AVEVA Connect by creating groups, assigning roles, and adding users. These tasks require Account Administrator privileges in AVEVA Connect. Once these tasks are complete, you can add and then map existing users or groups to AVEVA Data Hub roles.

An overview of the process is outlined below with links to the specific procedures.

1. <xref:create-group> in AVEVA Connect.

   - The User group is built-in.

   - Add additional groups if you want to control individual access to folders (namespaces in AVEVA Data Hub), or for use within AVEVA Data Hub to control permissions.

1. <xref:assign-roles-groups> in AVEVA Connect.

   - The DataHub Viewer role allows the user to see the namespace tile in AVEVA Connect and access AVEVA Data Hub for that namespace. By itself, this role does not grant any access to resources within AVEVA Data Hub.

   - Only the DataHub Viewer role is applicable to AVEVA Data Hub. For information on other roles in AVEVA Connect, see [View Role Assignments](https://help.connect.aveva.com/#/home/885637/10/11).

   - When the AVEVA Data Hub service is activated for a folder, it automatically adds the DataHub Viewer role for that folder to the User group. You can remove the role from the User group if you do not want all of your users to have access to that namespace.

1. <xref:invite-users> in AVEVA Connect.

   - You can add users individually, or you can prepare and import a spreadsheet. See [Import Users in Bulk](https://help.connect.aveva.com/#/home/885599/10/11).

   - You can assign groups to users when they are created, or assign them later.

1. <xref:AddGroup> and assign roles to it.

   - For information about the roles in AVEVA Data Hub, see <xref:ccRoles>.

1. <xref:gpUsers>.

   - If the user was assigned a group in AVEVA Connect, and that group has been added to AVEVA Data Hub with roles assigned to it, those roles apply to the user automatically.

   - Other roles can be added individually.

   - By default the Account Administrator in AVEVA Connect will have the Tenant Administrator role in AVEVA Data Hub.

## Example

Linda is an Account Administrator for her organization in AVEVA Connect. She wants to add Karl to the EU Mining Operations namespace in AVEVA Data Hub with Tenant Member Access, and Luis to the same namespace with Tenant Contributor Access.

For Karl, all Linda has to do is add a user for him in AVEVA Connect that is part of the User group, then add that user in AVEVA Data Hub. Because the DataHub Viewer role is added by default to the User group in AVEVA Connect, and the Tenant Member role is assigned by default in AVEVA Data Hub, nothing more needs to be done.

For Luis, Linda could follow the same process and manually add the Tenant Contributor role when adding Luis as a user in AVEVA Data Hub. However, she decides to handle the role assignment at a group level so any future changes can be applied to multiple users simultaneously. She creates a group in AVEVA Connect called Contributor, then adds that group in AVEVA Data Hub and assigns it the role of Tenant Contributor. Linda adds a user for Luis in AVEVA Connect that belongs to the group Contributor. She then adds a user for him in AVEVA Data Hub. Because he belongs to the Contributor group, AVEVA Data Hub assigns the Tenant Contributor role to him automatically.
