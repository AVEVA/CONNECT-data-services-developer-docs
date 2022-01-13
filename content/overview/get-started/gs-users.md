---
uid: gsUsers
---

# Get started with users

A user is an identity that has access to a tenant. Roles assigned to a user determine what permissions the user has on resources. See the following topics for more information about users:

- [Users](xref:ccUsers)

- [PI Server counterpart](xref:ccUsers#users-pi-server)

- [Users best practices](xref:ccUsers#users-bp)

## Procedure

Follow the procedure to invite a user to your tenant.

1. In the left pane, select **Security** > **Users**.

1. In the toolbar, click **Add User**.

<!--VTT, 12/14/21: There is only one identity provider now - AVEVA Connect. Per N. Parakh, delete all references to identity providers.  This step is no longer valid in UI. "3. If multiple identity providers are enabled in your tenant, you are prompted to select an identity provider. Choose the appropriate identity provider for the user you are adding. After you select an option, you can later switch to a different option."-->

1. Enter a first and last name for the user.  

1. Enter the recipient's email address. The system locates a matching email address to send the invitation to. Ensure that it is correct so that the invitation is not sent to an unintended recipient.

1. Optional: Select the **MyData.Role** role for the user.

    By default, the user is assigned the Tenant Member role which cannot be removed. Roles can be modified after the user is invited.

1. Once the information has been entered, click **Add**. 

    The invitation is sent to the email address specified in the `Email` field. The `Status` column lists the new user as *Pending* until the invitation is accepted. If the invitation expires, the status changes to *Expired*. Once expired, the invitation can be resent.

1. Once the user receives the invitation, they should log in using the identity provider you specified. Once they have logged in, the status of the user changes to `Active`.

## Next step

Continue with [Get started with clients](xref:gsClients).
