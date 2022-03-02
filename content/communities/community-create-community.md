---
uid: community-create-community
---

# Part 1: Create a community

[!include[create-community-intro](includes/create-community-intro.md)]

## Prerequisites

[!include[prereq-administrative-tenant](includes/prereq-administrative-tenant.md)]

## To create a community

To create a community, follow these steps:

1. In the left pane, select **Data Management** > **Communities**.

1. Select **Add Community**.

    The **Create Community** wizard opens to the `Details` page.

1. On the `Details` page, enter a **Name** and **Description**. Then select **Next**.

1. On the `Community Administrators` page, choose the [roles](xref:ccRoles) that are assigned [community administration permissions](xref:ccRoles#community-administrators-preview). Users assigned these roles can perform administration tasks for both their own tenant and the entire community. You can either accept the default roles or add new ones. 
   
    - To add new community administrator roles, select **Add Roles** and then select **Add Role** ![add role](../_icons/plus-thick-alt.svg) for any role that you want to function as community administrator.
    
	- To remove community administrator roles, select **Remove Role** ![remove role](../_icons/remove-object.svg) for the role that you want to remove. 
    
	**Tip:** You can edit the default roles that are listed. For more information, see <xref:communities-manage-default-admins>.

1. After you finish, select **Next**.

1. On the `Community Members` page, add [Community Members](xref:ccRoles#community-member-role-preview), which are users within your tenant that have read access to the community and its data.
    
    To add new Community Members, select **Add Users** and then select **Add User** ![add user](../_icons/plus-thick-alt.svg) for each user that you want to add.

1. After you finish, select **Create**.

The community is created and added to the `Communities` page.

## Next steps

Invite tenants to your community. Continue to <xref:community-invite>.
