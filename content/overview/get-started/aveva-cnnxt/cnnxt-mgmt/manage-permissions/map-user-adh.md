---
uid: map-user-adh
---

# Map a user to an AVEVA™ Data Hub role

Assign an existing AVEVA™ Connect user to a Data Hub role to control what actions the user can perform in AVEVA™ Data Hub. Role assignment determines the actions a user can take in Data Hub. There are five built-in roles:

* Tenant Administrator - Administrator with full permissions and has the ability to add and remove users, clients, and secrets.

  **Note:** Do not assign the Tenant Administrator role to general users.

* Tenant Contributor - Has read and write permissions by default.

* Tenant Data Steward - No specific permissions are granted to this role by default.

* Tenant Viewer - No specific permissions are granted to this role by default.

* Tenant Member - Default role assigned to all users or clients. Tenant members are granted read access by default.

1. Open the Data Hub portal.

1. From the left pane, select **Security** > **Users**.
 
1. Select **Add User**.
 
1. Enter the user's name email in the contact fields.
 
1. On the **Tenant Roles** tab, select one or more roles to assign to the user, then select **Add**.

  The user is assigned to the roles and listed as active on the `Users` page.
