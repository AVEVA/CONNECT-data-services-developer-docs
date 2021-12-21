---
uid: ccRoles
---

# AVEVA Data Hub roles

Data Hub roles are used to manage access to assets, resources, and services. Roles are assigned to identities, which includes users, groups, and client-credentials clients. When an identity tries to access a resource, AVEVA&trade; Data Hub checks the assigned roles against the permissions on the resource to determine their access level.

There are six built-in Data Hub roles that cannot be removed from a tenant:

- Tenant Administrator - Administrator with full permissions by default. This is the highest privilege role, with the ability to create new and remove existing users, clients and secrets. Any AVEVA Connect user who is assigned to the Administrator role will automatically be assigned to the Tenant Administrator role in AVEVA Data Hub.

  **Note:** Do not assign the Tenant Administrator role to client-credential clients. This role can be assigned via the Tenant Management API.

- Community Administrator - A role with full administrative rights. These rights include all the privileges of a Community Moderator plus the ability to delete a community, invite and confirm tenant invitations, and remove tenants from the community. See [Community roles](xref:communityroles) for more information.

- Tenant Contributor - Granted read and write permissions by default.

- Tenant Data Steward - No specific permissions are granted to this role by default.

- Tenant Viewer - No specific permissions are granted to this role by default.

- Tenant Member - This role cannot be removed and is assigned to all users or clients. Tenant members are granted read access by default.

You can add custom roles to further control access. By default, custom roles do not have any specific permissions. You must have the Tenant Administrator role to add and manage roles for a tenant. 

Access to resources is a combination of 1) the roles assigned to a user and group, and 2) the permissions set on the resources. For any resource, you set access on the resource for specific roles, rather than on specific users or clients. Access is managed for resources in the Manage Permissions dialog box. <!--VTT, 12/14/21: Need to link to new procedure on managing permissions via the Manage Permissions dialog box when it's published.-->   

## <a name="roles-pi-server"></a>PI Server counterpart

Roles are comparable to PI identities in PI Data Archive or identities in PI AF server. Permissions are granted to roles instead of directly to individual users or clients. This is similar to how identities in PI Server are used to assign permissions for a set of users or clients.

## <a name="roles-bp"></a>Roles best practices

The following best practices are recommended when you create and assign roles:

- Consider whether the read access granted by the Tenant Member role is acceptable for all users and clients in your tenant. Specifically, if you plan to invite users from outside your organization, you may want to limit their read access. One way to do this is to create a custom role for external users so that their permissions can be explicitly managed.

- Use caution when granting the Tenant Administrator role. Make sure to assign a different role to users and clients who should not manage permissions. Avoid assigning the Tenant Administrator role to client-credentials clients.

- Ensure that the roles assigned to client-credentials clients only grant the minimum set of permissions required by the application that uses these clients. This minimizes the potential damage in the event a client secret is compromised or a problem arises with the application.

- Use caution when denying permissions because this supersedes any allowed access to a role. For example, if a user is allowed write access through one role but is denied write access through another role, the user will not have write access. Because all users and clients are assigned the Tenant Member role, you cannot deny permissions to the Tenant Member role. Doing so would deny the given permission to every user in the tenant.
