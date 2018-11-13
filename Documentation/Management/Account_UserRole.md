---
uid: AccountUserRole
---

# UserRole

APIs to manage user roles.

## Properties

For HTTP requests and responses, the UserRole object has the following properties and JSON-serialized body: 

| Property | Type | Description | 
 | --- | --- | ---  | 
| UserId | string | User Id. | 
| RoleId | string | Role Id. | 


```json
{
	"UserId": "userid",
	"RoleId": "roleid"
}
```
***

## `GetRolesForUser()`

Retrieves all roles for the specified user.

### Http

`GET api/Tenants/{tenantId}/Users/{userId}/Roles`

### Parameters

`string tenantId`:	The identifier for the account in which the user belongs

`string userId`:	The identifier of the <see cref="!:User" /> whose roles will be retrieved

`string skip`:	Number of `Roles` to ignore

`string count`:	Number of `Roles` to be returned

`string query`:	Unsupported parameter



### Security

Allowed by Account Member and Account Administrator [Roles](xref:AccountRole)

### Returns

An array of `Role` objects belonging to the user with the specified userId.

***
## `AddAccountRoleToUser()`

Adds an account role to the specified user.

### Http

`PUT api/Tenants/{tenantId}/Users/{userId}/Roles/{roleId}`

### Parameters

`string tenantId`:	The identifier for the account in which the user belongs

`string userId`:	The identifier of the <see cref="!:User" /> who will be given the role

`string roleId`:	The identifier of the role to add to the <see cref="!:User" />



### Security

Allowed by Account Administrator [Role](xref:AccountRole)

### Returns

The `Role` with the specified roleId

***
## `RemoveRoleFromUser()`

Removes a role from a user.

### Http

`DELETE api/Tenants/{tenantId}/Users/{userId}/Roles/{roleId}`

### Parameters

`string tenantId`:	The identifier for the account in which the user belongs

`string userId`:	The identifier of the <see cref="!:User" /> whose role will be removed

`string roleId`:	The identifier of the role to remove from the <see cref="!:User" />



### Security

Allowed by Account Administrator [Role](xref:AccountRole)

### Returns

Nothing is returned

***
## `ReplaceUserRoles()`

Replace the roles of a user with a new list of roles.

### Http

`PUT api/Tenants/{tenantId}/Users/{userId}/Roles`

### Parameters

`string tenantId`:	The identifier for the account in which the user belongs

`string userId`:	The identifier of the <see cref="!:User" /> whose roles will be replaced

`[Role] newRoles`:	From the body. An array of `Role` objects to set as the Roles for the specified user



### Security

Allowed by Account Administrator and Community Lead [Roles](xref:AccountRole)

### Returns

An array of all `Role` objects assigned to the user specified by userId after the replacement operation is complete

***
