---
uid: identityProviders
---

# Identity Providers

An identity provider is a third-party service that stores and authenticates users. You can only add identity providers. Once you have enabled an identity provider for your tenant, it cannot be deactivated for that tenant.<!--AF 3/28/22 Each step section needs a level 2 heading. I would like to see field names if they exist, in the format: "In the **Name** field, enter..." The intro text could use details about consent (if you don't have the details, leave a comment like this so we know to follow up in the future.) -->

## Prerequisite

You must have the role of Tenant Administrator to add and manage the identity provider for your tenant.

To add a new identity provider, follow these steps:

1. In the left pane, select **Security** > **Identity Providers**.

1. Select the identity provider you want to activate from the list of identity providers supported on your tenant.

1. Select **Activate** in the Details tab. A message prompts you to confirm that you want to activate a new identity provider for the tenant.

1. Select **Activate** in the message window.

1. Specify the roles to assign to this new group.

1. If you selected Azure Active Directory, an `Add Identity Provider` window appears where consent is configured.<!--AF 3/28/22 This wording is awkward and it seems like you would need to click something for the window to appear. I might actually combine the following steps into this procedure. -->

To add an identity provider that supports advanced integration, such as Azure Active Directory, you must obtain consent from that account's Administrator:

1. Enter the Azure Active Directory's Tenant ID or Domain Name of that identity provider.

1. Select the **Enable Advanced Integration** checkbox.

1. Enter the Azure Account Administrator's email address.

1. Enter the Azure Account Administrator's name.

1. Select **Request Consent**.

If the identity provider shows a status of `Inactive; Pending Consent`, you must obtain a consent from this identity provider to perform advanced integration with your tenant:

1. Select **Edit Consent**.

1. Enter the Azure Active Directory's Tenant ID or Domain Name.

1. Select the **Enable Advanced Integration** checkbox.

1. Enter the Azure Account Administrator's email address.

1. Enter the Azure Account Administrator's name.

1. Select **Request Consent**.
