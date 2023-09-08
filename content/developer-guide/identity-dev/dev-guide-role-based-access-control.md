---
uid: accessControl
---

# Role-based access control

Use an Access Control List (ACL) to manage role-based access control to entities such as namespaces and streams. ACLs control user access to entities based on their roles. Each entity has an owner, who has access for all operations regardless of the contents of the ACL. Not all entities support role-based access control.

See [AVEVA Data Hub roles](xref:ccRoles) for details about default system roles.

## Access Control Lists

Access Control Lists (ACLs) contain sets of Access Control Entries (ACEs), which contain the following information:

- TrusteeType: The role for whom access is set.
- AccessType: The access permitted, either allowed or denied.
- AccessRights: The access rights allowed or denied to the Trustee specified.

A user or client that attempts to read, write, delete, or manage access control of an entity assigned an ACL must possess a role that corresponds to a Role Trustee that has `AccessType` set to `Allowed` for the AccessRights corresponding to that operation.

### Collections with ACL endpoints

The following table shows which endpoint collections have an endpoint for access control. For more information on using access control for each supported collection, select the collection link.

| Endpoint Collection | ACL Endpoint |
|--|:--:|
| [Asset store](xref:assets-access-control-list) | &#10004; |
| [Communities](../../api-reference/identity/community-tenant-collection-acls.md)<sup>1</sup> | &#10004; |
| [Data collection](xref:omf-ingress-access-control) | &#10004; |
| [Data views](xref:data-views-access-control) | &#10004; |
| Identity and access management | ✘ |
| Operations | ✘ |
| [Rules: Asset rules](xref:assets-access-control-list) | &#10004; |
| [Rules: Metadata rules](xref:metadata-access-control-list) | &#10004; |
| [Sequential Data Store](xref:sds-access-control-list) | &#10004; |
| [Tenant Management](xref:tenant-root-access-control) | &#10004; |

<sup>1</sup>: The Communities collection contains two different access control endpoints—one for communities and one for community tenants.

### Notes

- If an operation requires more than one access right, then an identity obtains those rights from multiple ACL entries.

- `AccessType.Denied` takes precedence over `AccessType.Allowed`. For example, an identity that has multiple roles, one of which is assigned AccessType.Denied will be forbidden the associated AccessRight, even if another one of their roles is assigned AccessType.Allowed for the same Access Right.
  <!--VTT, 12/14/21: Reworded this bullet per SME request, N. Parakh: For example, an identity that has multiple roles, one of which is assigned AccessType.Denied will be forbidden the associated AccessRight, even if another Role they also have assigned to them is assigned AccessType.Allowed for the same Access Right.-->

- Roles are the only TrusteeType currently supported for AccessControlList ACEs.

- At least one role must be given Manage Permission access.

### Trustee

The following table shows TrusteeTypes and the corresponding TypeIds. Only Role TrusteeType is allowed for AccessControlLists.

| TrusteeType           | TypeId |
|-----------------------|--------|
| User                  | 1      |
| Client                | 2      |
| Role                  | 3      |

The following table shows AccessTypes and the corresponding TypeIds.

| AccessType            | TypeId |
|-----------------------|--------|
| Allowed               | 0      |
| Denied                | 1      |

### Common access rights
The following table shows predefined access rights and their corresponding integer and bitwise information.

| AccessRights          | int  | bitwise |
|-----------------------|------|---------|
| None                  | 0    |   00000 |
| Read                  | 1    |   00001 |
| Write                 | 2    |   00010 |
| Delete                | 4    |   00100 |
| ManageAccessControl   | 8    |   01000 |
| Share                 | 16   |   10000 |
| All                   | 31   |   11111 |

Access rights are determined by the union or summation of one or more individual access rights. For example, `AccessRights: 3` indicates that the `Read (1)` and `Write (2)` access are permitted.

### Sample Access Control List

The following code sample shows the structure and format for an ACL that gives Role 1 `Read` access and Role 2 `All` access, but denies Role 3 `ManageAccessControl` access:

**Body**

Sample body:

```json
{
	"RoleTrusteeAccessControlEntries": [
		{
			"Trustee": {
				"Type": 3,
				"ObjectId": "11111111-1111-1111-1111-111111111111"
			},
			"AccessType": 0,
			"AccessRights": 1
		},
		{
			"Trustee": {
				"Type": 3,
				"ObjectId": "22222222-2222-2222-2222-222222222222"
			},
			"AccessType": 0,
			"AccessRights": 15
		},
		{
			"Trustee": {
				"Type": 3,
				"ObjectId": "33333333-3333-3333-3333-333333333333"
			},
			"AccessType": 1,
			"AccessRights": 8
		}
	],
}
```

## Owner

Set an owner on an entity to grant access for all operations on the entity regardless of the access set in the ACL. Only users and clients are valid owners for entities. Both user and client Trustee types use the `ObjectId` property to specify either the user's ID or client's ID, respectively.

The following code samples shows the format and structure of an owner object.

**User Owner Body**

```json
{
	"Type": 1,
	"TenantId": "55555555-5555-5555-5555-555555555555",
	"ObjectId": "44444444-4444-4444-4444-444444444444"
},
```

**Client Owner Body**

```json
{
	"Type": 2,
	"TenantId": "55555555-5555-5555-5555-555555555555",
	"ObjectId": "66666666-6666-6666-6666-666666666666"
},
```
