---
uid: add-community
---

# Create a community

A community is a space where you and your external partners can share operational data with one another. When you create a community, you are prompted to define a community name and description, the user roles that can perform administrative actions within the community, and the users considered community members within your tenant.

To create a community, follow these steps:

1. In the left pane, select **Data Management** > **Communities**.

1. Select **Add Community**.

    The **Create Community** wizard opens to the `Details` page.

1. On the `Details` page, enter a **Name** and **Description**. Then select **Next**.

1. On the `Community Administrators` page, choose the [roles](xref:ccRoles) that are assigned community administration permissions.

    By default, [community administration](xref:ccRoles#community-roles-preview) permissions are assigned to the [Tenant Administrator and Community Administrator](xref:ccRoles#tenant-roles) roles. 
    
    Optionally, you can add community administration permissions to other roles. Select **Add Roles** and then select **Add Role** ![add role](../_icons/plus-thick-alt.svg) for any role that you want to function as community administrator. 

    After you finish, select **Next**.

1. On the `Community Members` page, add [Community Members](xref:ccRoles#tenant-roles), which are users within your tenant that have read access to the community and its data.

    To add new Community Members, select **Add Users** and then select **Add User** ![add user](../_icons/plus-thick-alt.svg) for each user that you want to add.

    **Note:** By default, users assigned [community administration](xref:ccRoles#community-administreators-preview) permissions are not Community Members.

    After you finish, select **Create**.

The community is created and added to the `Communities` page.

## What's next?

Invite tenants to your community. See <xref:community-invite>.
