---
uid: add-community
---

# Create a community

A community is a space where you and your external partners can share operational data with one another. When you create a community, you are prompted to define:

* A community name and description.

* The user roles that can perform administrative actions within the community.

* The users within your tenant that have read access within the community.

## Prerequisites for community creation

You must be a Tenant Administrator to create a community.

## To create a community

To create a community, follow these steps:

1. In the left pane, select **Data Management** > **Communities**.

1. Select **Add Community**.

    The **Create Community** wizard opens to the `Details` page.

1. On the `Details` page, name and describe the community.

    1. Enter a **Name** and **Description**.
    
    1. Select **Next**.

1. On the `Community Administrators` page, choose the [roles](xref:ccRoles) that are assigned [community administration](xref:ccRoles#community-roles-preview) permissions.

    By default, community administration permissions are assigned to the **Tenant Administrator** role. Optionally, you can add community administration permissions to other roles.

    1. (Optional) Add or remove roles to be assigned community administrator permissions.

        * To add additional roles as community administrator, select **Add Roles** and then select **Add Role** ![add role](../_icons/plus-thick-alt.svg) for any role that you want to function as community administrator.

        * To remove roles that function as community administrator, select **Remove Role** ![remove role](../_icons/remove-object.svg).

    1. Select **Next**.

1. On the `Community Members` page, add [community members](xref:ccRoles#tenant-roles), which are users within your tenant that have read access to the community and its data. 

    **Note:** By default, community administrators do not have community member access rights, so adding community administrators as community members is recommended.

    1. Add or remove users as community members.

        * To add new community members, select **Add Users** and then select **Add User** ![add user](../_icons/plus-thick-alt.svg) for each user that you want to add.

        * To remove community members, select **Remove User** ![remove user](../_icons/remove-object.svg).

    1. Select **Create**.

The community is created and added to the `Communities` page.

## What's next?

Invite tenants to your community. See <xref:community-invite>.
