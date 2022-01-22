---
uid: community-invite
---

# Invite a tenant to a community

Invite business partners to join a community so they can share data. 

**Note:** The business partner must already belong to a tenant in OSIsoft Cloud Services (OCS).

Two different users must perform the following procedure to invite and add a tenant to a community:

- One user, the "inviter," invites another tenant. To be an inviter, you must be a Community Administrator.

- Another user, the "invitee," accepts the invitation on behalf of their tenant. To be an invitee, you must be a Tenant Administrator of a separate tenant that does not already belong to the community.

**Invite process**

![Invite process](images/invite-process.drawio.svg)

## Step 1: Inviter sends invite

To send an invite to a community, follow these steps:

1. In the left pane, select **Data Management** > **Communities**.

1. Find the community you want to share and select **Details**.

1. On the **Tenants** tab, select **Invite Tenant**.

1. Enter the email address of the administrator of the tenant you would like to invite and select **Send**.

  An email is sent to the invitee.

## Step 2: Invitee accepts invite

After you send an invitation to another tenant, wait for the tenant administrator to accept the email invitation.

**Tip:** Share <xref:community-accept-invite> with the invited tenant administrator for additional instruction.

## Step 3: Inviter confirms invite

To confirm an invite, follow these steps:

1. Follow the instructions in the email.

1. Log into the tenant that owns the community you are sharing.

1. In the left pane, select **Data Management** > **Communities**.

1. On the `Communities` overview page, find the community to which you have invited another tenant and select **Details**.

1. On the `Community Details` page, select the **Invitations** tab.

1. Select an invitation with a status of **Invitation Accepted**.

1. On the `Invitation Details` pane, select **Confirm Tenant**. When prompted for confirmation, select **Confirm Tenant** again.

  The invitee's tenant is now part of the community.