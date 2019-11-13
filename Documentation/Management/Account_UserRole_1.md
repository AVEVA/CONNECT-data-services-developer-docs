---
uid: AccountUserRole_1
---

# User Roles (Version 1)

User `Role` s authorize API requests made by users to various OCS features. Users can be assigned more than one `Role`,
but all users have the Account Member role. The following are currently available User `Role` s:
- Account Administrator: Can add, edit, and remove users. Can also edit the permissions of existing users.
- Account Member: Can log in and access the OCS portal.


***

## `Get Roles for User`

Retrieves all `Role` s for the specified user.

### Http

`GET api/v1/Tenants/{tenantId}/Users/{userId}/Roles`


### Parameters

```csharp
[Required]
[FromRoute]
string tenantId
```

The identifier of the account in which the user belongs.
```csharp
[Required]
[FromRoute]
string userId
```

The identifier of the user whose roles will be retrieved.
```csharp
[Optional]
[Default = "0"]
[FromQuery]
INT32 skip
```

Number of `Role` s to ignore.
```csharp
[Optional]
[Default = "100"]
[FromQuery]
INT32 count
```

Number of `Role` s to return.
```csharp
[Optional]
[Default = ""]
[FromRoute]
string query
```

Unsupported parameter.


### Security

Authorized for Account Administrators of the specified account and an Account Member's own `Role` s within the specified account.

### Returns

| Status Code | Return Type | Description | 
 | --- | --- | ---  | 
| 200 | [Role] | Returns a list of `Role` objects belonging to the user with the specified userId. | 
| 400 | Nothing is returned | Could not retrieve `Role` s due to missing or invalid input. | 
| 403 | Nothing is returned | Unauthorized to get `Role` s for the specified user. | 
| 404 | Nothing is returned | User not found in the specified `Tenant`. | 


***

## `Replace User Roles`

Replaces the `Role` s of a user with a new list of roles.

### Http

`PUT api/v1/Tenants/{tenantId}/Users/{userId}/Roles`


### Parameters

```csharp
[Required]
[FromRoute]
string tenantId
```

The identifier for the account in which the user belongs.
```csharp
[Required]
[FromRoute]
string userId
```

The identifier of the user whose roles will be replaced.
```csharp
[Required]
[FromBody]
[Role] roleList
```

A list of `Role` objects to set as the Roles for the specified user.


### Security

Authorized for Account Administrators of the specified account.

### Returns

| Status Code | Return Type | Description | 
 | --- | --- | ---  | 
| 200 | Nothing is returned | Returns the new list of all `Role` objects assigned to the specified user. | 
| 400 | Nothing is returned | Could not replace the `Role` s of the specified user due to missing or invalid input. | 
| 403 | Nothing is returned | Unauthorized to replace the `Role` s of the specified user. | 
| 404 | Nothing is returned | A user with the specified userId was not found. | 
| 405 | Nothing is returned | Method not allowed at this base URL. Try the request again at the Global base URL. | 


***

