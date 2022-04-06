---
uid: gpUsers
---

# Add a user in AVEVA Data Hub

A user is an identity that has access to a tenant. Roles assigned to a user determine what permissions the user has on resources. 

## Prerequisite

You must have the role of Tenant Administrator to add and manage users.

## Procedure

To add a user to a tenant, follow these steps:

1. In the left pane, select **Security** > **Users**.

1. In the toolbar, select **Add User**.

1. In the **Contact First Name** and **Contact Last Name** fields, enter a first and last name for the user.  

1. In the **User Email** field, enter the first few characters of the user's contact email and then select the correct email address from the dropdown list.

   **Note**: The user must exist in AVEVA Connect before being added within AVEVA Data Hub.

1. (Optional) On the **Tenant Roles** tab, assign additional roles to the user. By default, the user is assigned the Tenant Member role which cannot be removed. Roles can be modified after the user is added.

1. Select **Add**. 

   A welcome email is sent to the email address specified in the `Contact Email` field.
