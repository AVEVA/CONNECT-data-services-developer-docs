---
uid: map-group-adh
---

# Map a group to an AVEVA™ Data Hub role

As an administrator, you can assign an existing AVEVA™ Connect group to a Data Hub role. There are five built-in roles which cannot be removed from a tenant:

* Tenant Administrator: Administrator with full permissions by default. This is the highest privilege role, with the ability to create new and remove existing users, clients and secrets.

  **Note:** Do not assign the Tenant Administrator role to general users.

* Tenant Contributor: Has read and write permissions by default.

* Tenant Data Steward: No specific permissions are granted to this role by default.

* Tenant Viewer: No specific permissions are granted to this role by default.

* Tenant Member: Default role assigned to all users or clients. Tenant members are granted read access by default.

Assign an existing AVEVA™ Connect group to a Data Hub role to control what actions users assigned to this group can take in AVEVA™ Data Hub.

1. Open the Data Hub portal.

1. From the left pane, select **Security** > **Groups**.
 
1. Click **Add Group**.
 
1. In the **Name** text box, enter the name or first few characters of the AVEVA Connect group name, then press Enter.

   **Result:** The group appears in the **Name** field.
 
1. Assign a role, or multiple roles, to the group to control the actions members can take in the Data Hub portal, then click **Add**. 
