---
uid: add-community
---

# Part 1: Create a community

The first part of establishing a community is to create it. When you create a community, you are prompted to define a community name and description, the user roles that have administrative permissions within the community, and the users considered Community Members within your tenant.

## Prerequisites

To create a new community, you must be a [Tenant Administrator](xref:ccRoles#tenant-roles).

## To create a community

To create a community, follow these steps:

1. In the left pane, select **Data Management** > **Communities**.

1. Select **Add Community**.

    The **Create Community** wizard opens to the `Details` page.

1. On the `Details` page, enter a **Name** and **Description**. Then select **Next**.

1. On the `Community Administrators` page, choose the [roles](xref:ccRoles) that are assigned [community administration permissions](xref:ccRoles#community-administrators-preview).

    By default, these permissions are assigned to the [Tenant Administrator and Community Administrator](xref:ccRoles#tenant-roles) roles. 
    
    Optionally, you can add these permissions to other roles. Select **Add Roles** and then select **Add Role** ![add role](../_icons/plus-thick-alt.svg) for any role that you want to function as community administrator. 

1. After you finish, select **Next**.

1. On the `Community Members` page, add [Community Members](xref:ccRoles#community-member-role-preview), which are users within your tenant that have read access to the community and its data.

    By default, your user account is added as a Community Member.
    
    To add new Community Members, select **Add Users** and then select **Add User** ![add user](../_icons/plus-thick-alt.svg) for each user that you want to add.

    **Note:** By default, users assigned community administration permissions are not Community Members.

1. After you finish, select **Create**.

The community is created and added to the `Communities` page.

## Next steps

Invite tenants to your community. Continue to <xref:community-invite>.
