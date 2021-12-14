---
uid: ccUsers
---

# AVEVA Data Hub users

An AVEVA Data Hub user is an identity that has access to a tenant. Roles assigned to a user determine what permissions the user has on resources. See [AVEVA Data Hub roles](xref:ccRoles) for more information. Users log in to the AVEVA Data Hub portal and are authenticated through AVEVA Connect.

Note: Identity resources such as users and clients, are global across AVEVA Data Hub. These resources are not scoped to a particular namespace, but globally scoped across namespaces in Data Hub.

Users log in to the AVEVA Data Hub portal through a user account in Connect, and users authenticate to custom web applications when using [Hybrid Clients](xref:ccClients#hybrid-client) and [Authorization Code Clients](xref:ccClients#authorization-code-client). Therefore, at least one user should already be added to a tenant when the portal is first accessed.

Some points to note about adding and managing users:

(1) Users are added and granted access to Data Hub in AVEVA Connect.

(2) Make sure the user has been assigned to the correct role in AVEVA Connect before sending the invitation to access Data Hub. See [Invite users and assign user permissions](xref:invite-users). In Data Hub, you can map a user or group to a Data Hub role to control what actions they can take.

   **Note:** The Data Hub Tenant Member role grants read access to everything in the tenant. If a user should not have read access to some resources, the Tenant Member role can be limited.

(3) Any AVEVA Connect user who is assigned to the Administrator role will automatically be assigned to the Tenant Administrator role in Data Hub.

(4) Additional Connect users can be granted access to an associated Data Hub tenant using one of the following methods:

  (a) Search for the user in Data Hub and then add the user and assign roles. 

  (b) Add an AVEVA Connect group to the Data Hub tenant and then assign that AVEVA Connect group to the desired Data Hub roles. Any AVEVA Connect User that belongs to the Connect group will now be automatically granted access to the Data Hub tenant with the associated set of Data Hub roles.

**Note:** You must belong to the Tenant Administrator role to add and manage users in a tenant.

## <a name="users-pi-server"></a>PI Server counterpart

A user is comparable to a mapping in PI Data Archive. For example, in PI Data Archive a mapping may be added from a Microsoft Windows account to a specified PI identity. The user uses their Windows credentials to authenticate against PI Data Archive and gets the permissions specified by the PI identity. A user uses Azure Active Directory, Microsoft accounts, or Google credentials to authenticate against AVEVA&trade; Data Hub, and users get their permissions from the roles that are assigned to them.
