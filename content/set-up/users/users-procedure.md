---
uid: gpUsers
---

# Add a user in AVEVA Data Hub

An AVEVA Data Hub user is an identity that has access to a tenant. Roles assigned to a user determine what permissions the user has on resources. See the following topics for more information about users:

- [Users](xref:ccUsers)
- [PI Server counterpart](xref:ccUsers#users-pi-server)
- [Users best practices](xref:ccUsers#users-bp)

## Procedure

Follow the procedure to invite a user to your tenant.

<!--12/2/21, VTT: Per SMEs (N. Parkah & A. Woodall) Removed this step because it only applies to OCS. Old step: 1. If multiple identity providers are enabled in the tenant, you are prompted to select an identity provider. Choose the appropriate identity provider for the user you are adding. You can switch to a different option later.--> 

1. In the left pane, select **Security** > **Users**.

1. In the toolbar, select **Add User**.

1. In the **Contact First Name** and **Contact Last Name** fields, enter a first and last name for the user.  

1. Enter the user's contact email. Ensure that it is correct so the email invitation the user receives is not sent to an unintended recipient.

1. (Optional) On the **Tenant Roles** tab, assign additional roles to the user. By default, the user is assigned the Tenant Member role which cannot be removed. Roles can be modified after the user is added.

1. Click **Add**.
 
   The user is added to the list of AVEVA Data Hub users and assigned to the selected roles.

## Related links

- [Tenants Users](xref:identity-tenants-users) API
