---
uid: identityUser
---

# User

APIs for creating, getting, updating, and deleting Users

## Properties

For HTTP requests and responses, the User object has the following properties and JSON-serialized body: 

Property | Type | Descriptions
 --- | --- | ---
Id | string | Unique User ID.
GivenName | string | Given name of user.
Surname | string | Surname of user.
Name | string | Name of user.
Email | string | Email of user.
ContactEmail | string | Preferred contact email to be used.
ContactGivenName | string | Preferred name to be used when contacting user.
ContactSurname | string | Preferred surname to be used when contacting user.
ExternalUserId | string | Provider id for user.
Tenant | Tenant | Tenant the user belongs to.
IdentityProvider | IdentityProvider | Identity provider used to authenticate user.

### Serialized Model

```json
{
  "Id": "Id",
  "GivenName": "Name",
  "Surname": "Surname",
  "Name": "Name",
  "Email": "user@company.com",
  "ContactEmail": "user@company.com",
  "ContactGivenName": "Name",
  "ContactSurname": "Surname",
  "ExternalUserId": "ExternalUserId",
  "Tenant": {
    "Id": "Id",
    "Alias": "Alias",
    "State": "State",
    "IsCloudConnectCustomer": false
  },
  "IdentityProvider": {
    "Id": "Id",
    "DisplayName": "Name",
    "Scheme": "Scheme",
    "UserIdClaimType": "UserIdClaimType"
  }
}
```

***

## `Get Users`

Returns a list of User objects for a given tenant

### Request

`GET api/Tenants/{tenantId}/User/`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[FromQuery]
[Optional]
[Default = ""]
string query
```

Query to execute. Currently not supported

```csharp
[FromQuery]
[Optional]
[Default = 0]
int32 skip
```

Number of users to skip

```csharp
[FromQuery]
[Optional]
[Default = 100]
int32 count
```

Max number of users to return

### Security

Allowed for these roles:

- `Account Administrator`
- `Account Member`
- `Cluster Operator`
- `Cluster Support`

### Returns

#### 200

Success.

##### Type:

 `List[User]`

```json
[
  {
    "Id": "Id",
    "GivenName": "Name",
    "Surname": "Surname",
    "Name": "Name",
    "Email": "user@company.com",
    "ContactEmail": "user@company.com",
    "ContactGivenName": "Name",
    "ContactSurname": "Surname",
    "ExternalUserId": "ExternalUserId",
    "Tenant": {
      "Id": "Id",
      "Alias": "Alias",
      "State": "State",
      "IsCloudConnectCustomer": false
    },
    "IdentityProvider": {
      "Id": "Id",
      "DisplayName": "Name",
      "Scheme": "Scheme",
      "UserIdClaimType": "UserIdClaimType"
    }
  },
  {
    "Id": "Id",
    "GivenName": "Name",
    "Surname": "Surname",
    "Name": "Name",
    "Email": "user@company.com",
    "ContactEmail": "user@company.com",
    "ContactGivenName": "Name",
    "ContactSurname": "Surname",
    "ExternalUserId": "ExternalUserId",
    "Tenant": {
      "Id": "Id",
      "Alias": "Alias",
      "State": "State",
      "IsCloudConnectCustomer": false
    },
    "IdentityProvider": {
      "Id": "Id",
      "DisplayName": "Name",
      "Scheme": "Scheme",
      "UserIdClaimType": "UserIdClaimType"
    }
  }
]
```

#### 400

Missing or invalid inputs

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Tenant not found

#### 500

Internal server error
***

## `Get Users By IDs`

Returns an ordered list of User objects based on userId for a given tenant or a MultiStatusResponseDto with a list of User objects and a list of errors

### Request

`GET api/Tenants/{tenantId}/User/Ids`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[FromQuery]
[Required]
string[] userIds
```

Unordered list of ids for all users to get

```csharp
[FromQuery]
[Optional]
[Default = ""]
string query
```

Query to execute. Currently not supported

```csharp
[FromQuery]
[Optional]
[Default = 0]
int32 skip
```

Number of users to skip

```csharp
[FromQuery]
[Optional]
[Default = 100]
int32 count
```

Max number of users to return

### Security

Allowed for these roles:

- `Account Administrator`
- `Cluster Operator`
- `Cluster Support`

### Returns

#### 200

Success.

##### Type:

 `IList[User]`

```json
[
  {
    "Id": "Id",
    "GivenName": "Name",
    "Surname": "Surname",
    "Name": "Name",
    "Email": "user@company.com",
    "ContactEmail": "user@company.com",
    "ContactGivenName": "Name",
    "ContactSurname": "Surname",
    "ExternalUserId": "ExternalUserId",
    "Tenant": {
      "Id": "Id",
      "Alias": "Alias",
      "State": "State",
      "IsCloudConnectCustomer": false
    },
    "IdentityProvider": {
      "Id": "Id",
      "DisplayName": "Name",
      "Scheme": "Scheme",
      "UserIdClaimType": "UserIdClaimType"
    }
  },
  {
    "Id": "Id",
    "GivenName": "Name",
    "Surname": "Surname",
    "Name": "Name",
    "Email": "user@company.com",
    "ContactEmail": "user@company.com",
    "ContactGivenName": "Name",
    "ContactSurname": "Surname",
    "ExternalUserId": "ExternalUserId",
    "Tenant": {
      "Id": "Id",
      "Alias": "Alias",
      "State": "State",
      "IsCloudConnectCustomer": false
    },
    "IdentityProvider": {
      "Id": "Id",
      "DisplayName": "Name",
      "Scheme": "Scheme",
      "UserIdClaimType": "UserIdClaimType"
    }
  }
]
```

#### 207

Partial success.

##### Type:

 `MultiStatusResponseDto[IList[User]]`

```json
{
  "OperationId": "OperationId",
  "Error": "Error",
  "Reason": "Reason",
  "ChildErrors": [
    {
      "OperationId": "OperationId",
      "Error": "Error",
      "Reason": "Reason",
      "Resolution": "Resolution",
      "StatusCode": 0,
      "ModelId": {
        "String": "String"
      },
      "TenantId": "TenantId"
    },
    {
      "OperationId": "OperationId",
      "Error": "Error",
      "Reason": "Reason",
      "Resolution": "Resolution",
      "StatusCode": 0,
      "ModelId": {
        "String": "String"
      },
      "TenantId": "TenantId"
    }
  ],
  "Data": [
    {
      "Id": "Id",
      "GivenName": "Name",
      "Surname": "Surname",
      "Name": "Name",
      "Email": "user@company.com",
      "ContactEmail": "user@company.com",
      "ContactGivenName": "Name",
      "ContactSurname": "Surname",
      "ExternalUserId": "ExternalUserId",
      "Tenant": {
        "Id": "Id",
        "Alias": "Alias",
        "State": "State",
        "IsCloudConnectCustomer": false
      },
      "IdentityProvider": {
        "Id": "Id",
        "DisplayName": "Name",
        "Scheme": "Scheme",
        "UserIdClaimType": "UserIdClaimType"
      }
    },
    {
      "Id": "Id",
      "GivenName": "Name",
      "Surname": "Surname",
      "Name": "Name",
      "Email": "user@company.com",
      "ContactEmail": "user@company.com",
      "ContactGivenName": "Name",
      "ContactSurname": "Surname",
      "ExternalUserId": "ExternalUserId",
      "Tenant": {
        "Id": "Id",
        "Alias": "Alias",
        "State": "State",
        "IsCloudConnectCustomer": false
      },
      "IdentityProvider": {
        "Id": "Id",
        "DisplayName": "Name",
        "Scheme": "Scheme",
        "UserIdClaimType": "UserIdClaimType"
      }
    }
  ]
}
```

#### 400

Missing or invalid inputs

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Tenant not found

#### 500

Internal server error
***

## `Get Users' Status`

Get User status for multiple users, optionally restrict it to only Users of a specific status.

### Request

`GET api/Tenants/{tenantId}/User/Status`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[FromQuery]
[Optional]
[Default = ""]
string query
```

Query to execute. Currently not supported

```csharp
[FromQuery]
[Optional]
[Default = 0]
int32 skip
```

Number of users to skip

```csharp
[FromQuery]
[Optional]
[Default = 100]
int32 count
```

Max number of users to return

```csharp
[FromQuery]
[Optional]
[Default = ""]
string status
```

Only return statuses that match this value

### Security

Allowed for these roles:

- `Account Administrator`
- `Cluster Operator`
- `Cluster Support`

### Returns

#### 200

Success.

##### Type:

 `List[UserStatusDto]`

```json
[
  {
    "InvitationStatus": 0,
    "User": {
      "Id": "Id",
      "GivenName": "Name",
      "Surname": "Surname",
      "Name": "Name",
      "Email": "user@company.com",
      "ContactEmail": "user@company.com",
      "ContactGivenName": "Name",
      "ContactSurname": "Surname",
      "ExternalUserId": "ExternalUserId",
      "Tenant": {
        "Id": "Id",
        "Alias": "Alias",
        "State": "State",
        "IsCloudConnectCustomer": false
      },
      "IdentityProvider": {
        "Id": "Id",
        "DisplayName": "Name",
        "Scheme": "Scheme",
        "UserIdClaimType": "UserIdClaimType"
      }
    }
  },
  {
    "InvitationStatus": 0,
    "User": {
      "Id": "Id",
      "GivenName": "Name",
      "Surname": "Surname",
      "Name": "Name",
      "Email": "user@company.com",
      "ContactEmail": "user@company.com",
      "ContactGivenName": "Name",
      "ContactSurname": "Surname",
      "ExternalUserId": "ExternalUserId",
      "Tenant": {
        "Id": "Id",
        "Alias": "Alias",
        "State": "State",
        "IsCloudConnectCustomer": false
      },
      "IdentityProvider": {
        "Id": "Id",
        "DisplayName": "Name",
        "Scheme": "Scheme",
        "UserIdClaimType": "UserIdClaimType"
      }
    }
  }
]
```

#### 400

Missing or invalid inputs

#### 401

Unauthorized

#### 403

Forbidden

#### 500

Internal server error

#### 404

Tenant not found
***

## `Get User`

Returns a User

### Request

`GET api/Tenants/{tenantId}/User/{userId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant

```csharp
[Required]
string userId
```

Id of User

### Security

Allowed for these roles:

- `Account Administrator`
- `Account Member`
- `Cluster Operator`
- `Cluster Support`

### Returns

#### 200

Success

##### Type:

 `User`

```json
{
  "Id": "Id",
  "GivenName": "Name",
  "Surname": "Surname",
  "Name": "Name",
  "Email": "user@company.com",
  "ContactEmail": "user@company.com",
  "ContactGivenName": "Name",
  "ContactSurname": "Surname",
  "ExternalUserId": "ExternalUserId",
  "Tenant": {
    "Id": "Id",
    "Alias": "Alias",
    "State": "State",
    "IsCloudConnectCustomer": false
  },
  "IdentityProvider": {
    "Id": "Id",
    "DisplayName": "Name",
    "Scheme": "Scheme",
    "UserIdClaimType": "UserIdClaimType"
  }
}
```

#### 401

Unauthorized

#### 403

Forbidden

#### 404

User or Tenant not found

#### 500

Internal server error
***

## `Get User's Status`

Returns user invitation status

### Request

`GET api/Tenants/{tenantId}/User/{userId}/Status`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
string userId
```

Id of user

### Security

Allowed for these roles:

- `Account Administrator`
- `Account Member`
- `Cluster Operator`
- `Cluster Support`

### Returns

#### 200

Success

##### Type:

 `UserStatusDto`

```json
{
  "InvitationStatus": 0,
  "User": {
    "Id": "Id",
    "GivenName": "Name",
    "Surname": "Surname",
    "Name": "Name",
    "Email": "user@company.com",
    "ContactEmail": "user@company.com",
    "ContactGivenName": "Name",
    "ContactSurname": "Surname",
    "ExternalUserId": "ExternalUserId",
    "Tenant": {
      "Id": "Id",
      "Alias": "Alias",
      "State": "State",
      "IsCloudConnectCustomer": false
    },
    "IdentityProvider": {
      "Id": "Id",
      "DisplayName": "Name",
      "Scheme": "Scheme",
      "UserIdClaimType": "UserIdClaimType"
    }
  }
}
```

#### 401

Unauthorized

#### 403

Forbidden

#### 404

User or Tenant not found

#### 500

Internal server error
***

## `Get Users' Status By IDs`

Returns an ordered list of UserStatusDto objects for a given tenant or a MultiStatusDto response with a list of UserStatusDto objects and a list of errors

### Request

`GET api/Tenants/{tenantId}/User/Status/Ids`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[FromQuery]
[Required]
string[] userIds
```

Unordered list of ids for all users

```csharp
[FromQuery]
[Optional]
[Default = ""]
string query
```

Query to execute. Currently not supported

```csharp
[FromQuery]
[Optional]
[Default = 0]
int32 skip
```

Number of users to skip

```csharp
[FromQuery]
[Optional]
[Default = 100]
int32 count
```

Max number of users to return

### Security

Allowed for these roles:

- `Account Administrator`
- `Cluster Operator`
- `Cluster Support`

### Returns

#### 200

Success.

##### Type:

 `IList[User]`

```json
[
  {
    "Id": "Id",
    "GivenName": "Name",
    "Surname": "Surname",
    "Name": "Name",
    "Email": "user@company.com",
    "ContactEmail": "user@company.com",
    "ContactGivenName": "Name",
    "ContactSurname": "Surname",
    "ExternalUserId": "ExternalUserId",
    "Tenant": {
      "Id": "Id",
      "Alias": "Alias",
      "State": "State",
      "IsCloudConnectCustomer": false
    },
    "IdentityProvider": {
      "Id": "Id",
      "DisplayName": "Name",
      "Scheme": "Scheme",
      "UserIdClaimType": "UserIdClaimType"
    }
  },
  {
    "Id": "Id",
    "GivenName": "Name",
    "Surname": "Surname",
    "Name": "Name",
    "Email": "user@company.com",
    "ContactEmail": "user@company.com",
    "ContactGivenName": "Name",
    "ContactSurname": "Surname",
    "ExternalUserId": "ExternalUserId",
    "Tenant": {
      "Id": "Id",
      "Alias": "Alias",
      "State": "State",
      "IsCloudConnectCustomer": false
    },
    "IdentityProvider": {
      "Id": "Id",
      "DisplayName": "Name",
      "Scheme": "Scheme",
      "UserIdClaimType": "UserIdClaimType"
    }
  }
]
```

#### 207

Partial success.

##### Type:

 `MultiStatusResponseDto[IList[UserStatusDto]]`

```json
{
  "OperationId": "OperationId",
  "Error": "Error",
  "Reason": "Reason",
  "ChildErrors": [
    {
      "OperationId": "OperationId",
      "Error": "Error",
      "Reason": "Reason",
      "Resolution": "Resolution",
      "StatusCode": 0,
      "ModelId": {
        "String": "String"
      },
      "TenantId": "TenantId"
    },
    {
      "OperationId": "OperationId",
      "Error": "Error",
      "Reason": "Reason",
      "Resolution": "Resolution",
      "StatusCode": 0,
      "ModelId": {
        "String": "String"
      },
      "TenantId": "TenantId"
    }
  ],
  "Data": [
    {
      "InvitationStatus": 0,
      "User": {
        "Id": "Id",
        "GivenName": "Name",
        "Surname": "Surname",
        "Name": "Name",
        "Email": "user@company.com",
        "ContactEmail": "user@company.com",
        "ContactGivenName": "Name",
        "ContactSurname": "Surname",
        "ExternalUserId": "ExternalUserId",
        "Tenant": {
          "Id": "Id",
          "Alias": "Alias",
          "State": "State",
          "IsCloudConnectCustomer": false
        },
        "IdentityProvider": {
          "Id": "Id",
          "DisplayName": "Name",
          "Scheme": "Scheme",
          "UserIdClaimType": "UserIdClaimType"
        }
      }
    },
    {
      "InvitationStatus": 0,
      "User": {
        "Id": "Id",
        "GivenName": "Name",
        "Surname": "Surname",
        "Name": "Name",
        "Email": "user@company.com",
        "ContactEmail": "user@company.com",
        "ContactGivenName": "Name",
        "ContactSurname": "Surname",
        "ExternalUserId": "ExternalUserId",
        "Tenant": {
          "Id": "Id",
          "Alias": "Alias",
          "State": "State",
          "IsCloudConnectCustomer": false
        },
        "IdentityProvider": {
          "Id": "Id",
          "DisplayName": "Name",
          "Scheme": "Scheme",
          "UserIdClaimType": "UserIdClaimType"
        }
      }
    }
  ]
}
```

#### 400

Missing or invalid inputs

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Tenant not found

#### 500

Internal server error
***

## `Get User's Preferences`

Returns a user's preferences

### Request

`GET api/Tenants/{tenantId}/User/{userId}/Preferences`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant

```csharp
[Required]
string userId
```

Id of User

### Security

Allowed for these roles:

- `Account Administrator`
- `Account Member`
- `Cluster Operator`
- `Cluster Support`

### Returns

#### 200

Success

##### Type:

 `Newtonsoft.Json.Linq.JObject`

```json
{}
```

#### 401

Unauthorized

#### 403

Forbidden

#### 404

User or Tenant not found

#### 500

Internal server error
***

## `Update User's Preferences`

Put a user's preferences

### Request

`PUT api/Tenants/{tenantId}/User/{userId}/Preferences`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant

```csharp
[Required]
string userId
```

Id of User

```csharp
[FromBody]
[Required]
JObject preferences
```

JSON Preferences

### Security

Allowed for these roles:

- `Account Administrator`
- `Account Member`
- `Cluster Operator`

### Returns

#### 200

Success

##### Type:

 `Newtonsoft.Json.Linq.JObject`

```json
{}
```

#### 400

Missing preferences

#### 401

Unauthorized

#### 403

Forbidden

#### 404

User or Tenant not found

#### 500

Internal server error
***

## `Create User`

Creates a User

### Request

`POST api/Tenants/{tenantId}/User/`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant

```csharp
[FromBody]
[Required]
UserCreateDto userCreateDto
```

User data transfer object

### Security

Allowed for these roles:

- `Account Administrator`
- `Cluster Operator`

### Returns

#### 201

Created

##### Type:

 `User`

```json
{
  "Id": "Id",
  "GivenName": "Name",
  "Surname": "Surname",
  "Name": "Name",
  "Email": "user@company.com",
  "ContactEmail": "user@company.com",
  "ContactGivenName": "Name",
  "ContactSurname": "Surname",
  "ExternalUserId": "ExternalUserId",
  "Tenant": {
    "Id": "Id",
    "Alias": "Alias",
    "State": "State",
    "IsCloudConnectCustomer": false
  },
  "IdentityProvider": {
    "Id": "Id",
    "DisplayName": "Name",
    "Scheme": "Scheme",
    "UserIdClaimType": "UserIdClaimType"
  }
}
```

#### 400

Missing or invalid inputs

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Tenant not found

#### 500

Internal server error
***

## `Create User With ID`

Creates a User with an Id

### Request

`POST api/Tenants/{tenantId}/User/{userId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant

```csharp
[Required]
string userId
```

Id of User

```csharp
[FromBody]
[Required]
UserCreateDto userCreateDto
```

User data transfer object

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 201

Created

##### Type:

 `User`

```json
{
  "Id": "Id",
  "GivenName": "Name",
  "Surname": "Surname",
  "Name": "Name",
  "Email": "user@company.com",
  "ContactEmail": "user@company.com",
  "ContactGivenName": "Name",
  "ContactSurname": "Surname",
  "ExternalUserId": "ExternalUserId",
  "Tenant": {
    "Id": "Id",
    "Alias": "Alias",
    "State": "State",
    "IsCloudConnectCustomer": false
  },
  "IdentityProvider": {
    "Id": "Id",
    "DisplayName": "Name",
    "Scheme": "Scheme",
    "UserIdClaimType": "UserIdClaimType"
  }
}
```

#### 400

Missing or invalid inputs

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Tenant not found

#### 409

Conflict. Client already exists.

#### 500

Internal server error
***

## `Update User`

Update a user

### Request

`PUT api/Tenants/{tenantId}/User/{userId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
string userId
```

Id of user

```csharp
[FromBody]
[Required]
UserUpdateDto userUpdateDto
```

A UserStatusDto object

### Security

Allowed for these roles:

- `Account Administrator`
- `Account Member`

### Returns

#### 200

Updated

##### Type:

 `User`

```json
{
  "Id": "Id",
  "GivenName": "Name",
  "Surname": "Surname",
  "Name": "Name",
  "Email": "user@company.com",
  "ContactEmail": "user@company.com",
  "ContactGivenName": "Name",
  "ContactSurname": "Surname",
  "ExternalUserId": "ExternalUserId",
  "Tenant": {
    "Id": "Id",
    "Alias": "Alias",
    "State": "State",
    "IsCloudConnectCustomer": false
  },
  "IdentityProvider": {
    "Id": "Id",
    "DisplayName": "Name",
    "Scheme": "Scheme",
    "UserIdClaimType": "UserIdClaimType"
  }
}
```

#### 400

Missing or invalid inputs

#### 401

Unauthorized

#### 403

Forbidden

#### 404

User or Tenant not found

#### 500

Internal server error
***

## `Delete User`

Delete a user

### Request

`DELETE api/Tenants/{tenantId}/User/{userId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
string userId
```

Id of user

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 204

Deleted

#### 401

Unauthorized

#### 403

Forbidden

#### 404

User or Tenant not found

#### 500

Internal server error
***

## `Get User's Invitation`

Get the invitations for a user

### Request

`GET api/Tenants/{tenantId}/User/{userId}/Invitation`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
string userId
```

Id of user

```csharp
[FromQuery]
[Optional]
[Default = False]
bool includeExpiredInvitations
```

Specify to return expired invitations

### Security

Allowed for these roles:

- `Account Administrator`
- `Cluster Operator`
- `Cluster Support`

### Returns

#### 200

Success

##### Type:

 `Invitation`

```json
{
  "Id": "Id",
  "Issued": "2019-02-20T01:57:33.4002929-05:00",
  "Expires": "2019-02-20T01:57:33.4002979-05:00",
  "State": 0,
  "TenantId": "TenantId",
  "Tenant": {
    "Id": "Id",
    "Alias": "Alias",
    "State": "State",
    "IsCloudConnectCustomer": false
  },
  "UserId": "UserId",
  "User": {
    "Id": "Id",
    "GivenName": "Name",
    "Surname": "Surname",
    "Name": "Name",
    "Email": "user@company.com",
    "ContactEmail": "user@company.com",
    "ContactGivenName": "Name",
    "ContactSurname": "Surname",
    "ExternalUserId": "ExternalUserId",
    "Tenant": {
      "Id": "Id",
      "Alias": "Alias",
      "State": "State",
      "IsCloudConnectCustomer": false
    },
    "IdentityProvider": {
      "Id": "Id",
      "DisplayName": "Name",
      "Scheme": "Scheme",
      "UserIdClaimType": "UserIdClaimType"
    }
  }
}
```

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Invitation, User, or Tenant not found

#### 500

Internal server error
***

## `Find User By Tenant ID`

Search for an external user in a tenant

### Request

`GET api/Tenants/{tenantId}/User/Search`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[FromQuery]
[Required]
string identityProviderScheme
```

Identity provider scheme

```csharp
[FromQuery]
[Required]
string externalUserId
```

User external Id

### Security

Allowed for these roles:

- `Account Administrator`
- `Cluster Operator`
- `Cluster Support`

### Returns

#### 200

Success

##### Type:

 `User`

```json
{
  "Id": "Id",
  "GivenName": "Name",
  "Surname": "Surname",
  "Name": "Name",
  "Email": "user@company.com",
  "ContactEmail": "user@company.com",
  "ContactGivenName": "Name",
  "ContactSurname": "Surname",
  "ExternalUserId": "ExternalUserId",
  "Tenant": {
    "Id": "Id",
    "Alias": "Alias",
    "State": "State",
    "IsCloudConnectCustomer": false
  },
  "IdentityProvider": {
    "Id": "Id",
    "DisplayName": "Name",
    "Scheme": "Scheme",
    "UserIdClaimType": "UserIdClaimType"
  }
}
```

#### 401

Unauthorized

#### 403

Forbidden

#### 404

User or Tenant not found

#### 500

Internal server error
***

