---
uid: community-accept-invite
---

# Part 1: Accept community invitation

When another tenant invites you to a community, you receive an email invitation that you can use to join. 

**Note:** Invitations are valid for 14 days before they expire. If you do not accept the invitation within that time, or you do not receive an invitation email, you must request a new invitation from the owning tenant.

To accept an invitation, follow these steps:

<!-- We should add more information here about what it means to accept an invitation. If I'm an admin, I'm immediately wondering what this exposes from a security perspective -->

1. Open and review the email invitation from OSIsoft Cloud Services.

1. Select the **VIEW COMMUNITY INVITE** link.

1. If prompted, enter the tenant ID or tenant alias for your tenant and select **Continue**.

  **Important!** If you have multiple tenants, verify that you are logging into the correct tenant.

1. If prompted, log in to OSIsoft Cloud Services.

  A page opens and displays that your tenant will join the community that issued the invitation.

1. Select **Join**.

  Your tenant does not officially join the until the inviting tenant confirms the invitation.

1. On the `Community Administrators` page, choose the [roles](xref:ccRoles) that are assigned [community administration permissions](xref:ccRoles#community-administrators-preview).

  By default, these permissions are assigned to the [Tenant Administrator and Community Administrator](xref:ccRoles#tenant-roles) roles. 
    
  Optionally, you can add these permissions to other roles. Select **Add Roles** and then select **Add Role** ![add role](../_icons/plus-thick-alt.svg) for any role that you want to function as community administrator. 

1. After you finish, select **Next**.

1. On the `Community Members` page, add [Community Members](xref:ccRoles#community-member-role-preview), which are users within your tenant that have read access to the community and its data.

  To add new Community Members, select **Add Users** and then select **Add User** ![add user](../_icons/plus-thick-alt.svg) for each user that you want to add.

  **Note:** By default, users assigned community administration permissions are not Community Members.

The tenant that invited you to the community is updated that you accepted their invitation. Wait for them to confirm the invitation. When the inviting tenant confirms, you receive an email that your tenant now has access to the community.

## Next steps

Edit permissions for data streams to allow tenant data stewards to share them with the community. Continue to <xref:community-manage-sds-permissions-join>.
