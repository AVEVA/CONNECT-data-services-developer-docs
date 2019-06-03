---
uid: identityUser
---

# User

APIs for creating, getting, updating, and deleting Users

## Properties

For HTTP requests and responses, the User object has the following properties and JSON-serialized body: 

Property | Type | Description
 --- | --- | ---
Id | Guid | Unique User ID.
GivenName | string | Given name of user.
Surname | string | Surname of user.
Name | string | Name of user.
Email | string | Email of user.
ContactEmail | string | Preferred contact email for user.
ContactGivenName | string | Preferred contact name for user.
ContactSurname | string | Preferred contact surname for user.
ExternalUserId | string | Provider id for user.
IdentityProviderId | Guid | Identity Provider Id used to authenticate user.
RoleIds | Guid[] | List of strings of RoleIds.

### Serialized Model

```json
{
  "Id": "00000000-0000-0000-0000-000000000000",
  "GivenName": "Name",
  "Surname": "Surname",
  "Name": "Name",
  "Email": "user@company.com",
  "ContactEmail": "user@company.com",
  "ContactGivenName": "Name",
  "ContactSurname": "Surname",
  "ExternalUserId": "ExternalUserId",
  "IdentityProviderId": "00000000-0000-0000-0000-000000000000",
  "RoleIds": [
    "00000000-0000-0000-0000-000000000000",
    "00000000-0000-0000-0000-000000000000"
  ]
}
```

***

## `Get Users`

Returns a list of User objects for a given tenant

### Request

`GET api/v1/Tenants/{tenantId}/Users`

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

### Returns

#### 200

Success.

##### Type:

 `List`

```json
[
  {
    "Id": "00000000-0000-0000-0000-000000000000",
    "GivenName": "Name",
    "Surname": "Surname",
    "Name": "Name",
    "Email": "user@company.com",
    "ContactEmail": "user@company.com",
    "ContactGivenName": "Name",
    "ContactSurname": "Surname",
    "ExternalUserId": "ExternalUserId",
    "IdentityProviderId": "00000000-0000-0000-0000-000000000000",
    "RoleIds": [
      "00000000-0000-0000-0000-000000000000",
      "00000000-0000-0000-0000-000000000000"
    ]
  },
  {
    "Id": "00000000-0000-0000-0000-000000000000",
    "GivenName": "Name",
    "Surname": "Surname",
    "Name": "Name",
    "Email": "user@company.com",
    "ContactEmail": "user@company.com",
    "ContactGivenName": "Name",
    "ContactSurname": "Surname",
    "ExternalUserId": "ExternalUserId",
    "IdentityProviderId": "00000000-0000-0000-0000-000000000000",
    "RoleIds": [
      "00000000-0000-0000-0000-000000000000",
      "00000000-0000-0000-0000-000000000000"
    ]
  }
]
```

#### 207



##### Type:

 `MultiStatusResponse`

```json
{
  "OperationId": "OperationId",
  "Error": "Error",
  "Reason": "Reason",
  "ChildErrors": [
    {
      "StatusCode": 0,
      "ModelId": "ModelId",
      "OperationId": "OperationId",
      "Error": "Error",
      "Reason": "Reason",
      "Resolution": "Resolution"
    },
    {
      "StatusCode": 0,
      "ModelId": "ModelId",
      "OperationId": "OperationId",
      "Error": "Error",
      "Reason": "Reason",
      "Resolution": "Resolution"
    }
  ],
  "Data": [
    {
      "Id": "00000000-0000-0000-0000-000000000000",
      "GivenName": "Name",
      "Surname": "Surname",
      "Name": "Name",
      "Email": "user@company.com",
      "ContactEmail": "user@company.com",
      "ContactGivenName": "Name",
      "ContactSurname": "Surname",
      "ExternalUserId": "ExternalUserId",
      "IdentityProviderId": "00000000-0000-0000-0000-000000000000",
      "RoleIds": [
        "00000000-0000-0000-0000-000000000000",
        "00000000-0000-0000-0000-000000000000"
      ]
    },
    {
      "Id": "00000000-0000-0000-0000-000000000000",
      "GivenName": "Name",
      "Surname": "Surname",
      "Name": "Name",
      "Email": "user@company.com",
      "ContactEmail": "user@company.com",
      "ContactGivenName": "Name",
      "ContactSurname": "Surname",
      "ExternalUserId": "ExternalUserId",
      "IdentityProviderId": "00000000-0000-0000-0000-000000000000",
      "RoleIds": [
        "00000000-0000-0000-0000-000000000000",
        "00000000-0000-0000-0000-000000000000"
      ]
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

`GET api/v1/Tenants/{tenantId}/Users/Status`

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

### Returns

#### 200

Success.

##### Type:

 `List`

```json
[
  {
    "InvitationStatus": 0,
    "User": {
      "Id": "00000000-0000-0000-0000-000000000000",
      "GivenName": "Name",
      "Surname": "Surname",
      "Name": "Name",
      "Email": "user@company.com",
      "ContactEmail": "user@company.com",
      "ContactGivenName": "Name",
      "ContactSurname": "Surname",
      "ExternalUserId": "ExternalUserId",
      "IdentityProviderId": "00000000-0000-0000-0000-000000000000",
      "RoleIds": [
        "00000000-0000-0000-0000-000000000000",
        "00000000-0000-0000-0000-000000000000"
      ]
    }
  },
  {
    "InvitationStatus": 0,
    "User": {
      "Id": "00000000-0000-0000-0000-000000000000",
      "GivenName": "Name",
      "Surname": "Surname",
      "Name": "Name",
      "Email": "user@company.com",
      "ContactEmail": "user@company.com",
      "ContactGivenName": "Name",
      "ContactSurname": "Surname",
      "ExternalUserId": "ExternalUserId",
      "IdentityProviderId": "00000000-0000-0000-0000-000000000000",
      "RoleIds": [
        "00000000-0000-0000-0000-000000000000",
        "00000000-0000-0000-0000-000000000000"
      ]
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

`GET api/v1/Tenants/{tenantId}/Users/{userId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant

```csharp
[Required]
Guid userId
```

Id of User

### Security

Allowed for these roles:

- `Account Administrator`
- `Account Member`

### Returns

#### 200

Success

##### Type:

 `User`

```json
{
  "Id": "00000000-0000-0000-0000-000000000000",
  "GivenName": "Name",
  "Surname": "Surname",
  "Name": "Name",
  "Email": "user@company.com",
  "ContactEmail": "user@company.com",
  "ContactGivenName": "Name",
  "ContactSurname": "Surname",
  "ExternalUserId": "ExternalUserId",
  "IdentityProviderId": "00000000-0000-0000-0000-000000000000",
  "RoleIds": [
    "00000000-0000-0000-0000-000000000000",
    "00000000-0000-0000-0000-000000000000"
  ]
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

`GET api/v1/Tenants/{tenantId}/Users/{userId}/Status`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
Guid userId
```

Id of user

### Security

Allowed for these roles:

- `Account Administrator`
- `Account Member`

### Returns

#### 200

Success

##### Type:

 `UserStatus`

```json
{
  "InvitationStatus": 0,
  "User": {
    "Id": "00000000-0000-0000-0000-000000000000",
    "GivenName": "Name",
    "Surname": "Surname",
    "Name": "Name",
    "Email": "user@company.com",
    "ContactEmail": "user@company.com",
    "ContactGivenName": "Name",
    "ContactSurname": "Surname",
    "ExternalUserId": "ExternalUserId",
    "IdentityProviderId": "00000000-0000-0000-0000-000000000000",
    "RoleIds": [
      "00000000-0000-0000-0000-000000000000",
      "00000000-0000-0000-0000-000000000000"
    ]
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

## `Get User's Preferences`

Returns a user's preferences

### Request

`GET api/v1/Tenants/{tenantId}/Users/{userId}/Preferences`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant

```csharp
[Required]
Guid userId
```

Id of User

### Security

Allowed for these roles:

- `Account Administrator`
- `Account Member`

### Returns

#### 200

Success

##### Type:

 `JObject`

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

`PUT api/v1/Tenants/{tenantId}/Users/{userId}/Preferences`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant

```csharp
[Required]
Guid userId
```

Id of User

```csharp
[FromBody]
[Required]
JObject preferences
```

JSON Preferences

```json
{}
```

### Security

Allowed for these roles:

- `Account Administrator`
- `Account Member`

### Returns

#### 200

Success

##### Type:

 `JObject`

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

`POST api/v1/Tenants/{tenantId}/Users`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant

```csharp
[FromBody]
[Required]
UserCreateOrUpdate userCreateOrUpdate
```

User values to use during creating

Property | Type | Required | Description 
 --- | --- | --- | ---
Id | Guid | No | User Id for the user. When creating a user, if User ID is not specified, one will be generated.
ContactGivenName | string | Yes | Preferred name to be used when contacting user.
ContactSurname | string | Yes | Preferred surname to be used when contacting user.
ContactEmail | string | Yes | Preferred contact email to be used.
RoleIds | Guid[] | Yes | List of strings of RoleIds. At least one role must be provided.



```json
{
  "Id": "00000000-0000-0000-0000-000000000000",
  "ContactGivenName": "Name",
  "ContactSurname": "Surname",
  "ContactEmail": "user@company.com",
  "RoleIds": [
    "00000000-0000-0000-0000-000000000000",
    "00000000-0000-0000-0000-000000000000"
  ]
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
  "Id": "00000000-0000-0000-0000-000000000000",
  "GivenName": "Name",
  "Surname": "Surname",
  "Name": "Name",
  "Email": "user@company.com",
  "ContactEmail": "user@company.com",
  "ContactGivenName": "Name",
  "ContactSurname": "Surname",
  "ExternalUserId": "ExternalUserId",
  "IdentityProviderId": "00000000-0000-0000-0000-000000000000",
  "RoleIds": [
    "00000000-0000-0000-0000-000000000000",
    "00000000-0000-0000-0000-000000000000"
  ]
}
```

#### 400

Missing or invalid inputs, or User limit exceeded

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Tenant not found

#### 500

Internal server error
***

## `Update User`

Create or Update a User

### Request

`PUT api/v1/Tenants/{tenantId}/Users/{userId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
Guid userId
```

Id of user

```csharp
[FromBody]
[Required]
UserCreateOrUpdate userCreateOrUpdate
```

A UserStatus object

Property | Type | Required | Description 
 --- | --- | --- | ---
Id | Guid | No | User Id for the user. When creating a user. Must be the same as the one in the route.
ContactGivenName | string | No | Preferred name to be used when contacting user.
ContactSurname | string | No | Preferred surname to be used when contacting user.
ContactEmail | string | No | Preferred contact email to be used.
RoleIds | Guid[] | No | List of strings of RoleIds.



```json
{
  "Id": "00000000-0000-0000-0000-000000000000",
  "ContactGivenName": "Name",
  "ContactSurname": "Surname",
  "ContactEmail": "user@company.com",
  "RoleIds": [
    "00000000-0000-0000-0000-000000000000",
    "00000000-0000-0000-0000-000000000000"
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
  "Id": "00000000-0000-0000-0000-000000000000",
  "GivenName": "Name",
  "Surname": "Surname",
  "Name": "Name",
  "Email": "user@company.com",
  "ContactEmail": "user@company.com",
  "ContactGivenName": "Name",
  "ContactSurname": "Surname",
  "ExternalUserId": "ExternalUserId",
  "IdentityProviderId": "00000000-0000-0000-0000-000000000000",
  "RoleIds": [
    "00000000-0000-0000-0000-000000000000",
    "00000000-0000-0000-0000-000000000000"
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

User or Tenant not found

#### 500

Internal server error
***

## `Delete User`

Delete a user

### Request

`DELETE api/v1/Tenants/{tenantId}/Users/{userId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
Guid userId
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

