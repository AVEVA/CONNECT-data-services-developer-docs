---
uid: ccUsers
---

# AVEVA Data Hub users

An AVEVA Data Hub user is an identity that has access to a tenant. Roles assigned to a user determine what permissions the user has on resources. See [AVEVA Data Hub roles](xref:ccRoles) for more information. Users log in to the AVEVA Data Hub portal and are authenticated through AVEVA Connect.

**Note:** Identity resources such as users and clients, are global across AVEVA Data Hub. These resources are not scoped to a particular namespace, but globally scoped across namespaces in AVEVA Data Hub.

Users log in to the AVEVA Data Hub portal through a user account in AVEVA Connect, and users authenticate to custom web applications when using [Hybrid Clients](xref:ccClients#hybrid-client) and [Authorization Code Clients](xref:ccClients#authorization-code-client). Therefore, at least one user should already be added to a tenant when the portal is first accessed.

Some points to note about adding and managing users:

1. Users are added and granted access to AVEVA Data Hub in AVEVA Connect.

2. Make sure the user has been assigned the DataHub Viewer role in AVEVA Connect before sending the invitation to access AVEVA Data Hub. See [Invite users and assign user permissions](xref:invite-users). In AVEVA Data Hub, you can map a user or group to an AVEVA Data Hub role to control what actions they can take.

   **Note:** The AVEVA Data Hub Tenant Member role grants read access to everything in the tenant. If a user should not have read access to some resources, the Tenant Member role can be limited.

3. Any AVEVA Connect user who is assigned to the Administrator role is automatically assigned the Tenant Administrator role in AVEVA Data Hub.

4. Additional AVEVA Connect users can be granted access to an associated AVEVA Data Hub tenant using one of the following methods:

   a. Search for the user in AVEVA Data Hub and then add the user and assign roles. 

   b. Add an AVEVA Connect group to the AVEVA Data Hub tenant, then add that group to AVEVA Data Hub and assign the necessary AVEVA Data Hub roles. Any user that belongs to the AVEVA Connect group is automatically granted access to the AVEVA Data Hub tenant with the associated set of AVEVA Data Hub roles.

**Note:** You must belong to the Tenant Administrator role to add and manage users in a tenant.

## <a name="users-pi-server"></a>PI Server counterpart

A user is comparable to a mapping in Data Archive. For example, in Data Archive a mapping may be added from a Microsoft Windows account to a specified PI identity. The user enters their Windows credentials to authenticate against Data Archive and gets the permissions specified by the PI identity. AVEVA Connect handles authentication for AVEVA Data Hub, and users get their permissions from the roles that are assigned to them.
