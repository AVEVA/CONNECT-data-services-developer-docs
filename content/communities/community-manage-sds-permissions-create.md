---
uid: community-manage-sds-permissions-create
---

# Part 3: Enable stream sharing permissions

To share data into a Community and provide access to this data for external tenants, a user with the **Share** permission on one or more streams must share the stream into a Community that they have read access to. By default, OCS has a [Tenant Data Steward](xref:ccRoles#tenant-roles) role that is intended for users in the tenant to share resources with other external tenants using Communities. However, the Tenant Data Steward role is not assigned Share privileges on streams by default. Therefore a Tenant Administrator or another user assigned **Manage Permissions** on the streams must first grant the Tenant Data Steward role (or another other roles) the **Share** privilege on streams before they can be shared by users within that role. 

## Prerequisites

You must be assigned the [Tenant Administrator](xref:ccRoles#tenant-roles) role or another role assigned **Manage Permsissions** on one or more streams.

## To enable stream sharing permissions

1. From the left pane, select **Data Management** > **Sequential Data Store**.

1. Select one or more streams that you want to allow sharing on.

1. Select **More options** ![More options icon](../../../_icons/dots-vertical.svg) > **Manage Permissions**.

1. From **Select Role**, choose the role whose permissions you want to modify. Using the **Tenant Data Steward** role is recommended, but you can use any role.

1. Select the **Allow** checkbox for the **Share** access type.

1. Select **Save**.

If you want to configure different roles to allow different data stewards to share different sets of data, you can accomplish this by not using the default Tenant Data Steward role and instead create as many roles as you need to manage this within your organization. Then repeat the steps above to grant the share permission for those roles on the specific sets of streams/data that each role will manage. For instructions on how to allow stream sharing, see [Manage permissions](xref:manage-streams#manage-permissions).
