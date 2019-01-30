---
uid: identityUser
---

# User

CRUD operations on User

## Properties

For HTTP requests and responses, the User object has the following properties and JSON-serialized body: 

```csharp
string Id
```
Unique User ID.

```csharp
string GivenName
```
Given name of user.

```csharp
string Surname
```
Surname of user.

```csharp
string Name
```
Name of user.

```csharp
string Email
```
Email of user.

```csharp
string ContactEmail
```
Preferred contact email to be used.

```csharp
string ContactGivenName
```
Preferred name to be used when contacting user.

```csharp
string ContactSurname
```
Preferred surname to be used when contacting user.

```csharp
string ExternalUserId
```
Provider id for user.

```csharp
string Preferences
```
User preferences.

```csharp
Tenant Tenant
```
Tenant the user belongs to.

```csharp
IdentityProvider IdentityProvider
```
Identity provider used to authenticate user.

### Serialized Model

```json
{
  "Id": "String",
  "GivenName": "String",
  "Surname": "String",
  "Name": "String",
  "Email": "String",
  "ContactEmail": "String",
  "ContactGivenName": "String",
  "ContactSurname": "String",
  "ExternalUserId": "String",
  "Preferences": "String",
  "Tenant": {
    "Id": "String",
    "Alias": "String",
    "State": "String",
    "IsCloudConnectCustomer": false
  },
  "IdentityProvider": {
    "Id": "String",
    "DisplayName": "String",
    "Scheme": "String",
    "UserIdClaimType": "String"
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
  "Id": "String",
  "GivenName": "String",
  "Surname": "String",
  "Name": "String",
  "Email": "String",
  "ContactEmail": "String",
  "ContactGivenName": "String",
  "ContactSurname": "String",
  "ExternalUserId": "String",
  "Preferences": "String",
  "Tenant": {
    "Id": "String",
    "Alias": "String",
    "State": "String",
    "IsCloudConnectCustomer": false
  },
  "IdentityProvider": {
    "Id": "String",
    "DisplayName": "String",
    "Scheme": "String",
    "UserIdClaimType": "String"
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

Oops! Something happened, somewhere inside our server, just a while ago
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
  "Id": "String",
  "GivenName": "String",
  "Surname": "String",
  "Name": "String",
  "Email": "String",
  "ContactEmail": "String",
  "ContactGivenName": "String",
  "ContactSurname": "String",
  "ExternalUserId": "String",
  "Preferences": "String",
  "Tenant": {
    "Id": "String",
    "Alias": "String",
    "State": "String",
    "IsCloudConnectCustomer": false
  },
  "IdentityProvider": {
    "Id": "String",
    "DisplayName": "String",
    "Scheme": "String",
    "UserIdClaimType": "String"
  }
}
]
```

#### 207

Partial success.

##### Type:

 `MultiStatusResponseDto[IList[User]]`

```json
[
[
{
  "Id": "String",
  "GivenName": "String",
  "Surname": "String",
  "Name": "String",
  "Email": "String",
  "ContactEmail": "String",
  "ContactGivenName": "String",
  "ContactSurname": "String",
  "ExternalUserId": "String",
  "Preferences": "String",
  "Tenant": {
    "Id": "String",
    "Alias": "String",
    "State": "String",
    "IsCloudConnectCustomer": false
  },
  "IdentityProvider": {
    "Id": "String",
    "DisplayName": "String",
    "Scheme": "String",
    "UserIdClaimType": "String"
  }
}
]
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

Oops! Something happened, somewhere inside our server, just a while ago
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
    "Id": "String",
    "GivenName": "String",
    "Surname": "String",
    "Name": "String",
    "Email": "String",
    "ContactEmail": "String",
    "ContactGivenName": "String",
    "ContactSurname": "String",
    "ExternalUserId": "String",
    "Preferences": "String",
    "Tenant": {
      "Id": "String",
      "Alias": "String",
      "State": "String",
      "IsCloudConnectCustomer": false
    },
    "IdentityProvider": {
      "Id": "String",
      "DisplayName": "String",
      "Scheme": "String",
      "UserIdClaimType": "String"
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

Oops! Something happened, somewhere inside our server, just a while ago

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
  "Id": "String",
  "GivenName": "String",
  "Surname": "String",
  "Name": "String",
  "Email": "String",
  "ContactEmail": "String",
  "ContactGivenName": "String",
  "ContactSurname": "String",
  "ExternalUserId": "String",
  "Preferences": "String",
  "Tenant": {
    "Id": "String",
    "Alias": "String",
    "State": "String",
    "IsCloudConnectCustomer": false
  },
  "IdentityProvider": {
    "Id": "String",
    "DisplayName": "String",
    "Scheme": "String",
    "UserIdClaimType": "String"
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

Oops! Something happened, somewhere inside our server, just a while ago
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
    "Id": "String",
    "GivenName": "String",
    "Surname": "String",
    "Name": "String",
    "Email": "String",
    "ContactEmail": "String",
    "ContactGivenName": "String",
    "ContactSurname": "String",
    "ExternalUserId": "String",
    "Preferences": "String",
    "Tenant": {
      "Id": "String",
      "Alias": "String",
      "State": "String",
      "IsCloudConnectCustomer": false
    },
    "IdentityProvider": {
      "Id": "String",
      "DisplayName": "String",
      "Scheme": "String",
      "UserIdClaimType": "String"
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

Oops! Something happened, somewhere inside our server, just a while ago
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
  "Id": "String",
  "GivenName": "String",
  "Surname": "String",
  "Name": "String",
  "Email": "String",
  "ContactEmail": "String",
  "ContactGivenName": "String",
  "ContactSurname": "String",
  "ExternalUserId": "String",
  "Preferences": "String",
  "Tenant": {
    "Id": "String",
    "Alias": "String",
    "State": "String",
    "IsCloudConnectCustomer": false
  },
  "IdentityProvider": {
    "Id": "String",
    "DisplayName": "String",
    "Scheme": "String",
    "UserIdClaimType": "String"
  }
}
]
```

#### 207

Partial success.

##### Type:

 `MultiStatusResponseDto[IList[UserStatusDto]]`

```json
[
[
{
  "InvitationStatus": 0,
  "User": {
    "Id": "String",
    "GivenName": "String",
    "Surname": "String",
    "Name": "String",
    "Email": "String",
    "ContactEmail": "String",
    "ContactGivenName": "String",
    "ContactSurname": "String",
    "ExternalUserId": "String",
    "Preferences": "String",
    "Tenant": {
      "Id": "String",
      "Alias": "String",
      "State": "String",
      "IsCloudConnectCustomer": false
    },
    "IdentityProvider": {
      "Id": "String",
      "DisplayName": "String",
      "Scheme": "String",
      "UserIdClaimType": "String"
    }
  }
}
]
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

Oops! Something happened, somewhere inside our server, just a while ago
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

Oops! Something happened, somewhere inside our server, just a while ago
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

Oops! Something happened, somewhere inside our server, just a while ago
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
  "ContactGivenName": "String",
  "ContactSurname": "String",
  "ContactEmail": "String",
  "RoleIds": [
    "string1",
    "string2"
  ],
  "CreateInvitation": true,
  "InvitationExpiresDateTime": "2019-01-29T15:18:37.4576005-08:00"
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
  "Id": "String",
  "GivenName": "String",
  "Surname": "String",
  "Name": "String",
  "Email": "String",
  "ContactEmail": "String",
  "ContactGivenName": "String",
  "ContactSurname": "String",
  "ExternalUserId": "String",
  "Preferences": "String",
  "Tenant": {
    "Id": "String",
    "Alias": "String",
    "State": "String",
    "IsCloudConnectCustomer": false
  },
  "IdentityProvider": {
    "Id": "String",
    "DisplayName": "String",
    "Scheme": "String",
    "UserIdClaimType": "String"
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

Oops! Something happened, somewhere inside our server, just a while ago
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
  "ContactGivenName": "String",
  "ContactSurname": "String",
  "ContactEmail": "String",
  "RoleIds": [
    "string1",
    "string2"
  ],
  "CreateInvitation": true,
  "InvitationExpiresDateTime": "2019-01-29T15:18:37.4629233-08:00"
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
  "Id": "String",
  "GivenName": "String",
  "Surname": "String",
  "Name": "String",
  "Email": "String",
  "ContactEmail": "String",
  "ContactGivenName": "String",
  "ContactSurname": "String",
  "ExternalUserId": "String",
  "Preferences": "String",
  "Tenant": {
    "Id": "String",
    "Alias": "String",
    "State": "String",
    "IsCloudConnectCustomer": false
  },
  "IdentityProvider": {
    "Id": "String",
    "DisplayName": "String",
    "Scheme": "String",
    "UserIdClaimType": "String"
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

Oops! Something happened, somewhere inside our server, just a while ago
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
  "ContactGivenName": "String",
  "ContactSurname": "String",
  "ContactEmail": "String",
  "Preferences": "String",
  "RoleIds": [
    "string1",
    "string2"
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
  "Id": "String",
  "GivenName": "String",
  "Surname": "String",
  "Name": "String",
  "Email": "String",
  "ContactEmail": "String",
  "ContactGivenName": "String",
  "ContactSurname": "String",
  "ExternalUserId": "String",
  "Preferences": "String",
  "Tenant": {
    "Id": "String",
    "Alias": "String",
    "State": "String",
    "IsCloudConnectCustomer": false
  },
  "IdentityProvider": {
    "Id": "String",
    "DisplayName": "String",
    "Scheme": "String",
    "UserIdClaimType": "String"
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

Oops! Something happened, somewhere inside our server, just a while ago
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

Oops! Something happened, somewhere inside our server, just a while ago
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
  "Id": "String",
  "Issued": "2019-01-29T15:18:37.4691001-08:00",
  "Expires": "2019-01-29T15:18:37.4691047-08:00",
  "State": 0,
  "TenantId": "String",
  "Tenant": {
    "Id": "String",
    "Alias": "String",
    "State": "String",
    "IsCloudConnectCustomer": false
  },
  "UserId": "String",
  "User": {
    "Id": "String",
    "GivenName": "String",
    "Surname": "String",
    "Name": "String",
    "Email": "String",
    "ContactEmail": "String",
    "ContactGivenName": "String",
    "ContactSurname": "String",
    "ExternalUserId": "String",
    "Preferences": "String",
    "Tenant": {
      "Id": "String",
      "Alias": "String",
      "State": "String",
      "IsCloudConnectCustomer": false
    },
    "IdentityProvider": {
      "Id": "String",
      "DisplayName": "String",
      "Scheme": "String",
      "UserIdClaimType": "String"
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

Oops! Something happened, somewhere inside our server, just a while ago
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
  "Id": "String",
  "GivenName": "String",
  "Surname": "String",
  "Name": "String",
  "Email": "String",
  "ContactEmail": "String",
  "ContactGivenName": "String",
  "ContactSurname": "String",
  "ExternalUserId": "String",
  "Preferences": "String",
  "Tenant": {
    "Id": "String",
    "Alias": "String",
    "State": "String",
    "IsCloudConnectCustomer": false
  },
  "IdentityProvider": {
    "Id": "String",
    "DisplayName": "String",
    "Scheme": "String",
    "UserIdClaimType": "String"
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

Oops! Something happened, somewhere inside our server, just a while ago
***

