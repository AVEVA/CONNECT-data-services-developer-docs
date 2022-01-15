---
uid: gpUsers
---

# Add a user in AVEVA Data Hub

A user is an identity that has access to a tenant. Roles assigned to a user determine what permissions the user has on resources. 

To invite a user to a tenant, follow these steps:

1. In the left pane, select **Security** > **Users**.

1. In the toolbar, select **Add User**.

1. In the **Contact First Name** and **Contact Last Name** fields, enter a first and last name for the user.  

1. Enter the user's contact email. Ensure that it is correct so the email invitation the user receives is not sent to an unintended recipient.

1. (Optional) On the **Tenant Roles** tab, assign additional roles to the user. By default, the user is assigned the Tenant Member role which cannot be removed. Roles can be modified after the user is added.

1. Select **Invite**. 

   An invitation is sent to the email address specified in the `Contact Email` field. The **Status** column lists the new user as *Pending* until the invitation is accepted. If the invitation expires, the status changes to *Expired*. Once expired, the invitation can be resent.

1. When the user receives the invitation, the user should log in using the identity provider specified. Once the user has logged in, the user status changes to *Active*.
