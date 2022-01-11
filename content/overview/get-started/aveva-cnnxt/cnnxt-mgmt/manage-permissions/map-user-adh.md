---
uid: map-user-adh
---

# Map a user to an AVEVA Data Hub role

You can assign an AVEVA Connect user to an AVEVA Data Hub role. Role assignment determines the actions a user can take in AVEVA Data Hub. There are five built-in roles:

* Tenant Administrator: Administrator with full permissions and has the ability to add and remove users, clients, and secrets.

  **Note:** Do not assign the Tenant Administrator role to general users.

* Tenant Contributor: Has read and write permissions by default.

* Tenant Data Steward: No specific permissions are granted to this role by default.

* Tenant Viewer: No specific permissions are granted to this role by default.

* Tenant Member: Default role assigned to all users or clients. Tenant members are granted read access by default.

Assign an existing AVEVA Connect user to an AVEVA Data Hub role to control what actions the user can perform in AVEVA Data Hub.

1. Open the AVEVA Data Hub portal.

1. From the left pane, select **Security** > **Users**.
 
1. Click **Add User**.
 
1. Enter the user's name email in the contact fields.
 
1. On the **Tenant Roles** tab, select the role(s) you want to assign to the user, then click **Add**.

   **Result:** The user is assigned to the role(s) and listed as active on the `Users` page.
