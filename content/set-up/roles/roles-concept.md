---
uid: ccRoles
---

# Roles

Administrators use roles to manage access to assets, resources, and services. They can then assign these roles to identities, which include users, groups, and client-credentials clients. When an identity tries to access a resource, OCS checks the assigned roles against the permissions on the resource to determine their access level.

Assigning a role to a user or client does not determine access. For any resource, you set access on the resource for specific roles, rather than for specific users or clients. Manage access using Manage Permissions for the given resource. For each role, you set access to the following access types: Read, Write, Delete, and Manage Permissions.

## Role types

OSIsoft Cloud Services includes three different types of roles, which determine the scope of the access rights assigned to a user:

- [Tenant roles](#tenant-roles)

- [Tenant custom roles](#tenant-custom-roles)

- [Community roles](#community-roles-preview)

### Tenant roles

Tenant roles are default roles that assign access rights to users within the scope of your tenant. These default roles cannot be removed from the tenant. Tenant roles assign a default permissions for each access right in the system. 

There are five default tenant roles. The following table lists the default permission for each tenant role. 

| Role | Read | Write | Delete | Manage Permissions | Notes |
|--|--|--|--|--|--|--|
| Tenant Administrator | &#10004; | &#10004; | &#10004; | &#10004; | This is the highest privilege role, with the ability to create new and remove existing users, clients, and secrets. Do not assign this role to clients. |
| Tenant Contributor | &#10004; | &#10004; |  |  |
| Tenant Member | &#10004; |  |  |  | This role is automatically assigned to all users or clients. |
| Tenant Viewer |  |  |  |  | This role has no specific permissions by default. |
| Tenant Data Steward |  |  |  |  | This role has no specific permissions by default. |

### Tenant Custom roles 

You can create custom tenant roles when the default tenant roles do not meet your organizational use cases. You can assign these custom roles a custom set of access rights and permissions. By default, added roles do not have any specific permissions. 

You must have the Tenant Administrator role to add and manage roles in a tenant.

### Community roles (Preview)

Community roles define the access that user has within the scope of a [community](xref:communities), regardless of whether that community is owned by your tenant or a partner tenant.

There is a single community role: Community Member. The following table lists its default access rights within a community.

| Role | Read | Write | Delete | Manage Permissions|
|--|--|--|--|--|--|
| Community Member | &#10004; |  |  |  |  |

#### How are communities administered?

When a tenant administrator creates or joins a new community, they are prompted to assign new community administration access rights to one or more existing tenant roles. You can assign these permissions to either a default tenant role or a custom tenant role. All users assigned the updated role will have administrative access rights within the community for their tenant.  

## <a name="roles-pi-server"></a>PI Server counterpart

Roles are comparable to PI identities in PI Data Archive or identities in PI AF server. An administrator grants permissions to roles instead of directly to individual users or clients. This is similar to how PI Server uses identities to assign permissions for a set of users or clients.

## <a name="roles-bp"></a>Roles best practices

Consider the following best practices when you create and assign roles:

- Consider whether the read access granted by the Tenant Member role is acceptable for all users and clients in your tenant. Specifically, if you plan to invite users from outside your organization, you may want to limit their read access. One way to do this is to create a custom role for external users so that their permissions can be explicitly managed.
 
- When using PI to OCS, ensure write access to stream and asset collections. The PI to OCS Agent has write permission to the streams collection in OCS. By default, the Tenant Contributor role provides write permission to the automatically generated PIToOcs Agent Client User. Write permission to this collection is required to enable stream creation.

- Use caution when granting the Tenant Administrator role. Make sure to assign a different role to users and clients who should not manage permissions. Avoid assigning the Tenant Administrator role to client-credentials clients.

- Ensure that the roles assigned to client-credentials clients only grant the minimum set of permissions required by the application that uses these clients. This minimizes the potential damage in the event a client secret is compromised or a problem arises with the application.

- Use caution when denying permissions because this supersedes any allowed access to a role. For example, if a user is allowed write access through one role but is denied write access through another role, the user will not have write access. Because all users and clients are assigned the Tenant Member role, you cannot deny permissions to the Tenant Member role. Doing so would deny the given permission to every user in the tenant.
