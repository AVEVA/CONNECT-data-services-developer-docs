---
uid: map-group-adh
---

# Map a group to an AVEVA Data Hub role

Assign an existing AVEVA Connect group to a Data Hub role to control what actions users assigned to this group can take in AVEVA Data Hub. There are six built-in tenant roles which cannot be removed:

* Tenant Administrator - Administrator with full permissions and has the ability to add and remove users, clients, and secrets.

  **Note:** Do not assign the Tenant Administrator role to general users.

* Community Administrator - A role with full administrative rights. These rights include all the privileges of a Community Moderator plus the ability to delete a community, invite and confirm tenant invitations, and remove tenants from the community. See Community roles for more information.

* Tenant Contributor - Has read and write permissions by default.

* Tenant Data Steward - No specific permissions are granted to this role by default.

* Tenant Viewer - No specific permissions are granted to this role by default.

* Tenant Member - Default role assigned to all users or clients. Tenant members are granted read access by default.

To assign an existing AVEVA Connect group to a Data Hub role, follow these steps:

1. Open the AVEVA Data Hub portal.

1. From the left pane, select **Security** > **Groups**.
 
1. Select **Add Group**.
 
1. In the **Name** field, enter the name or first few characters of the AVEVA Connect group name, then press Enter.

  The group appears in the **Name** field.
 
1. Assign a role, or multiple roles, to the group to control the actions members can take in the AVEVA Data Hub portal, then select **Add**. 
