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

## `GetUsers()`

Returns a list of User objects for a given tenant

### Http 

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

Allowed for these roles: **Account Administrator**, **Cluster Operator**, **Cluster Support**

### Returns

#### 200

Success.. Returns System.Collections.Generic.List`1[OSIsoft.Identity.Common.Models.User]

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

## `GetUsersByIds()`

Returns an ordered list of User objects based on userId for a given tenant or a MultiStatusResponseDto with a list of User objects and a list of errors

### Http 

`GET api/Tenant/{tenantId}/Users/Ids`

### Parameters


```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
[string] userIds [FromQuery] [Required] [No-Default]
```

Unorderd list of ids for all users to get

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

Allowed for these roles: **Account Administrator**, **Cluster Operator**, **Cluster Support**

### Returns

#### 200

Success.. Returns System.Collections.Generic.IList`1[OSIsoft.Identity.Common.Models.User]

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

## `GetUsersStatus()`

Get User status for multiple users, optionally restrict it to only Users of a specific status.

### Http 

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

Allowed for these roles: **Account Administrator**, **Cluster Operator**, **Cluster Support**

### Returns

#### 200

Success.. Returns System.Collections.Generic.List`1[OSIsoft.Identity.Common.Models.UserStatusDto]

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

## `GetUser()`

Returns a User

### Http 

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

Allowed for these roles: **Account Administrator**, **Account Member**, **Cluster Operator**, **Cluster Support**

### Returns

#### 200

Success. Returns OSIsoft.Identity.Common.Models.User

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

## `GetUserStatus()`

Returns user invitation status

### Http 

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

Allowed for these roles: **Account Administrator**, **Account Member**, **Cluster Operator**, **Cluster Support**

### Returns

#### 200

Success. Returns OSIsoft.Identity.Common.Models.UserStatusDto

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

## `GetUserPreferences()`

Returns a user's preferences

### Http 

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

Allowed for these roles: **Account Administrator**, **Account Member**, **Cluster Operator**, **Cluster Support**

### Returns

#### 200

Success. Returns System.String

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

## `UpdateUserPreferences()`

Put a user's preferences

### Http 

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

Allowed for these roles: **Account Administrator**, **Account Member**, **Cluster Operator**

### Returns

#### 200

Success. Returns System.String

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

## `CreateUser()`

Creates a `User <User>`

### Http 

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
  "InvitationExpiresDateTime": "2019-01-25T15:31:27.6465721-08:00"
}
```


### Security

Allowed for these roles: **Account Administrator**, **Cluster Operator**

### Returns

#### 201

Created. Returns OSIsoft.Identity.Common.Models.User

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

## `CreateUserWithId()`

Creates a `User <User>` with an Id

### Http 

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
  "InvitationExpiresDateTime": "2019-01-25T15:31:27.6516152-08:00"
}
```


### Security

Allowed for these roles: **Account Administrator**

### Returns

#### 201

Created. Returns OSIsoft.Identity.Common.Models.User

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

## `UpdateUser()`

Update a user

### Http 

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

Allowed for these roles: **Account Administrator**, **Account Member**

### Returns

#### 200

Updated. Returns OSIsoft.Identity.Common.Models.User

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

## `DeleteUser()`

Delete a user

### Http 

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

Allowed for these roles: **Account Administrator**

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

## `GetUserInvitation()`

Get the invitations for a user

### Http 

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

Allowed for these roles: **Account Administrator**, **Cluster Operator**, **Cluster Support**

### Returns

#### 200

Success. Returns OSIsoft.Identity.Common.Models.Invitation

```json
{
  "Id": "String",
  "Issued": "2019-01-25T15:31:27.6565546-08:00",
  "Expires": "2019-01-25T15:31:27.6565595-08:00",
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

