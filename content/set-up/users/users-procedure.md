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

1. In the left pane, select **Security** > **Users**.

1. In the toolbar, click **Add User**.

<!--12/2/21, VTT: Per SMEs (N. Parkah & A. Woodall) Deleted this step because it only applies to OCS. Old step: 1. If multiple identity providers are enabled in the tenant, you are prompted to select an identity provider. Choose the appropriate identity provider for the user you are adding. You can switch to a different option later.-->

1. Enter a first and last name for the user.  

1. Enter the contact email. A welcome email to access the AVEVA Data Hub tenant will be sent to the user at this address. Ensure that it is correct so that the email is not sent to an unintended recipient.

1. Optional: Enable additional roles for the user. By default, the user is assigned the Tenant Member role which cannot be removed. Roles can be modified after the user is invited.

1. Once the information has been entered, click **Invite**. An welcome email is sent to the email address specified in the `Contact Email` field. The **Status** column lists the new user as *Pending* until the invitation is accepted. If the invitation expires, the status changes to *Expired*. Once expired, the invitation can be resent.

1. Once the user receives the welcome email, they should log in to Data Hub via Connect using the link in the email.

## Related links

- [Tenants Users](xref:identity-tenants-users) API
