---
uid: gsUsers
---

# Get started with users

A user is an identity that has access to a tenant. Roles assigned to a user determine what permissions the user has on resources. For more information about users, see [Users](xref:ccUsers).

To invite a user to your tenant:

1. In the left pane, select **Security** > **Users**.

1. In the toolbar, select **Add User**.

    <!--VTT, 12/14/21: There is only one identity provider now - AVEVA Connect. Per N. Parakh, delete all references to identity providers.  This step is no longer valid in UI. "3. If multiple identity providers are enabled in your tenant, you are prompted to select an identity provider. Choose the appropriate identity provider for the user you are adding. After you select an option, you can later switch to a different option."-->

1. In the **Contact First Name** and **Contact Last Name** fields, enter a first and last name for the user.  

1. In the **User Email** field, enter the first few characters of the user's contact email and then select the correct email address from the dropdown list.

   **Note**: The user must exist in AVEVA Connect before being added within AVEVA Data Hub.

1. (Optional) On the **Tenant Roles** tab, assign additional roles to the user. By default, the user is assigned the Tenant Member role which cannot be removed. Roles can be modified after the user is added.

1. Select **Add**. 

   A welcome email is sent to the email address specified in the `Contact Email` field.

## Next step

Continue with [Get started with clients](xref:gsClients).