---
uid: AccountClientRole_1
---

# Client Roles (Version 1)

Client `Role` s authorize API requests made by clients to various OCS features. Clients can be assigned more than one
`Role`, but all clients have the Account Member role. The following are currently available Client `Role` s:
- Account Administrator: Can add, edit, and remove data using APIs.
- Account Member: Can read data using most APIs.


***

## `Replace Client Roles`

Replaces the `Role` s of a client with a new list of roles.

### Http

`PUT api/v1/Tenants/{tenantId}/Clients/{clientId}/Roles`


### Parameters

```csharp
[Required]
[FromRoute]
string tenantId
```

The identifier of the account the client belongs to.
```csharp
[Required]
[FromRoute]
string clientId
```

The identifier of the client whose roles will be replaced.
```csharp
[Required]
[FromBody]
[Role] roleList
```

List of `Role` objects to set as the Roles for the specified client.


### Security

`Role` s of a client can only be replaced by an Account Administrator.

### Returns

| Status Code | Return Type | Description | 
 | --- | --- | ---  | 
| 200 | [Role] | Returns a list of all `Role` objects assigned to the user specified by clientId after the replacement operation is complete. | 
| 400 | Nothing is returned | Could not replace `Role` s due to missing or invalid input. | 
| 403 | Nothing is returned | Unauthorized to replace `Role` s of this client. | 
| 404 | Nothing is returned | The client was not found in the specified `Tenant`. | 
| 405 | Nothing is returned | Method not allowed at this base URL. Try the request again at the Global base URL. | 


***

## `Find Client Roles`

Retrieves all `Role` s from a client.

### Http

`GET api/v1/Tenants/{tenantId}/Clients/{clientId}/Roles`


### Parameters

```csharp
[Required]
[FromRoute]
string tenantId
```

The identifier for the account in which the client belongs to.
```csharp
[Required]
[FromRoute]
string clientId
```

The identifier of the client whose `Role` s will be retrieved.
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

`Role` s can be retrieved by an Account Administrator.

### Returns

| Status Code | Return Type | Description | 
 | --- | --- | ---  | 
| 200 | [Role] | Returns a list of `Role` objects belonging to the client with the specified clientId. | 
| 400 | Nothing is returned | Could not retrieve `Role` s from the client due to missing or invalid input. | 
| 403 | Nothing is returned | Unauthorized to retrieve `Role` s from this client. | 
| 404 | Nothing is returned | The client was not found in the specified `Tenant`. | 


***

