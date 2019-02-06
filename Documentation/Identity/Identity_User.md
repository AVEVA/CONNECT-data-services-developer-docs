---
uid: identityUser
---

# User

CRUD operations on User

## Properties

For HTTP requests and responses, the User object has the following properties and JSON-serialized body: 

Property | Type | Descriptions
 --- | --- | ---
string | Id | Unique User ID.
string | GivenName | Given name of user.
string | Surname | Surname of user.
string | Name | Name of user.
string | Email | Email of user.
string | ContactEmail | Preferred contact email to be used.
string | ContactGivenName | Preferred name to be used when contacting user.
string | ContactSurname | Preferred surname to be used when contacting user.
string | ExternalUserId | Provider id for user.
string | Preferences | User preferences.
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
  "Preferences": "Preferences",
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

`GET api/Tenant/{tenantId}/Users`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string query [FromQuery] [Optional] [Default = ""]
```

Query to execute. Currently not supported

```csharp
int32 skip [FromQuery] [Optional] [Default = 0]
```

Number of users to skip

```csharp
int32 count [FromQuery] [Optional] [Default = 100]
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
    "Preferences": "Preferences",
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
    "Preferences": "Preferences",
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

`GET api/Tenant/{tenantId}/Users/Ids`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string[] userIds [FromQuery] [Required] [No-Default]
```

Unordered list of ids for all users to get

```csharp
string query [FromQuery] [Optional] [Default = ""]
```

Query to execute. Currently not supported

```csharp
int32 skip [FromQuery] [Optional] [Default = 0]
```

Number of users to skip

```csharp
int32 count [FromQuery] [Optional] [Default = 100]
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
    "Preferences": "Preferences",
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
    "Preferences": "Preferences",
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
      "Preferences": "Preferences",
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
      "Preferences": "Preferences",
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

`GET api/Tenant/{tenantId}/Users/Status`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string query [FromQuery] [Optional] [Default = ""]
```

Query to execute. Currently not supported

```csharp
int32 skip [FromQuery] [Optional] [Default = 0]
```

Number of users to skip

```csharp
int32 count [FromQuery] [Optional] [Default = 100]
```

Max number of users to return

```csharp
string status [FromQuery] [Optional] [Default = ""]
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
      "Preferences": "Preferences",
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
      "Preferences": "Preferences",
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

`GET api/Tenant/{tenantId}/Users/{userId}`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of Tenant

```csharp
string userId [FromRoute] [Required] [No-Default]
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
  "Preferences": "Preferences",
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

`GET api/Tenant/{tenantId}/Users/{userId}/Status`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string userId [FromRoute] [Required] [No-Default]
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
    "Preferences": "Preferences",
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

`GET api/Tenant/{tenantId}/Users/Status/Ids`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string[] userIds [FromQuery] [Required] [No-Default]
```

Unordered list of ids for all users

```csharp
string query [FromQuery] [Optional] [Default = ""]
```

Query to execute. Currently not supported

```csharp
int32 skip [FromQuery] [Optional] [Default = 0]
```

Number of users to skip

```csharp
int32 count [FromQuery] [Optional] [Default = 100]
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
    "Preferences": "Preferences",
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
    "Preferences": "Preferences",
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
        "Preferences": "Preferences",
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
        "Preferences": "Preferences",
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

`GET api/Tenant/{tenantId}/Users/{userId}/Preferences`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of Tenant

```csharp
string userId [FromRoute] [Required] [No-Default]
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

 `System.String`

```json
string
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

`PUT api/Tenant/{tenantId}/Users/{userId}/Preferences`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of Tenant

```csharp
string userId [FromRoute] [Required] [No-Default]
```

Id of User

```csharp
string preferences [FromQuery] [Required] [No-Default]
```

Preferences

### Security

Allowed for these roles:

- `Account Administrator`
- `Account Member`
- `Cluster Operator`

### Returns

#### 200

Success

##### Type:

 `System.String`

```json
string
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

Creates a `User <User>`

### Request

`POST api/Tenant/{tenantId}/Users`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of Tenant

```csharp
UserCreateDto userCreateDto [FromBody] [Required] [No-Default]
```

User data transfer object

```json
{
  "ContactGivenName": "Name",
  "ContactSurname": "Surname",
  "ContactEmail": "user@company.com",
  "RoleIds": [
    "String",
    "String"
  ],
  "CreateInvitation": false,
  "InvitationExpiresDateTime": "2019-02-05T19:11:14.8141277-08:00"
}
```

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
  "Preferences": "Preferences",
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

Creates a `User <User>` with an Id

### Request

`POST api/Tenant/{tenantId}/Users/{userId}`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of Tenant

```csharp
string userId [FromRoute] [Required] [No-Default]
```

Id of `User <User>`

```csharp
UserCreateDto userCreateDto [FromBody] [Required] [No-Default]
```

User data transfer object

```json
{
  "ContactGivenName": "Name",
  "ContactSurname": "Surname",
  "ContactEmail": "user@company.com",
  "RoleIds": [
    "String",
    "String"
  ],
  "CreateInvitation": false,
  "InvitationExpiresDateTime": "2019-02-05T19:11:14.8201057-08:00"
}
```

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
  "Preferences": "Preferences",
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

`PUT api/Tenant/{tenantId}/Users/{userId}`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string userId [FromRoute] [Required] [No-Default]
```

Id of user

```csharp
UserUpdateDto userUpdateDto [FromBody] [Required] [No-Default]
```

A UserStatusDto object

```json
{
  "ContactGivenName": "Name",
  "ContactSurname": "Surname",
  "ContactEmail": "user@company.com",
  "Preferences": "Preferences",
  "RoleIds": [
    "String",
    "String"
  ]
}
```

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
  "Preferences": "Preferences",
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

`DELETE api/Tenant/{tenantId}/Users/{userId}`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string userId [FromRoute] [Required] [No-Default]
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

`GET api/Tenant/{tenantId}/Users/{userId}/Invitation`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string userId [FromRoute] [Required] [No-Default]
```

Id of user

```csharp
bool includeExpiredInvitations [FromQuery] [Optional] [Default = False]
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
  "Issued": "2019-02-05T19:11:14.8322226-08:00",
  "Expires": "2019-02-05T19:11:14.8322276-08:00",
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
    "Preferences": "Preferences",
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

`GET api/Tenant/{tenantId}/Users/Search`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string identityProviderScheme [FromQuery] [Required] [No-Default]
```

Identity provider scheme

```csharp
string externalUserId [FromQuery] [Required] [No-Default]
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
  "Preferences": "Preferences",
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

