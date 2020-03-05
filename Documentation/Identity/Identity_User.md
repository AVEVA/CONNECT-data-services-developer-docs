---
uid: identityUser
---

# User

Users consume resources in a Tenant. They are invited by the Admin of the
            Tenant and should already have an account in one of the configured Identity
            Providers for this Tenant. A User is fully provisioned in OSIsoft Cloud Services
            only after they have accepted the invitation and successfully logged with
            an Identity Provider. OSIsoft Cloud Services does not maintain User credentials, but it delegates
            authentication to the Identity Provider the User logged in with at first. Once
            logged in the User cannot change the Identity Provider it signed up with. A Tenant
            can only have one User with a given email to an Identity Provider. If a User has
            multiple aliases in the same Identity Provider, they will not be able to create
            multiple corresponding OSIsoft Cloud Services users. Users have roles associated with them. These roles
            determine what a User is authorized to do in the Tenant. Roles are assigned to a User
            upon creation and can be modified by an Admin. We allow the change of some User fields
            and the complete deletion of a User.

## Properties

For HTTP requests and responses, the User object has the following properties and JSON-serialized body: 

Property | Type | Description
 --- | --- | ---
Id | Guid | Gets or sets unique User ID.
GivenName | string | Gets or sets given name of user.
Surname | string | Gets or sets surname of user.
Name | string | Gets or sets name of user.
Email | string | Gets or sets email of user.
ContactEmail | string | Gets or sets contact email for user. User will only be contacted through this email.
ContactGivenName | string | Gets or sets preferred contact name for user.
ContactSurname | string | Gets or sets preferred contact surname for user.
ExternalUserId | string | Gets or sets provider id for user. This is the unique ID we get from the Identity Provider.
IdentityProviderId | Guid | Gets or sets Identity Provider Id used to authenticate User. Will be set once the User accepts an invitation. If not specified when sending the invitation to the User, it can be any of the Identity Provider Ids configured for this Tenant.
RoleIds | Guid[] | Gets or sets list of strings of RoleIds.

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

## Authentication

All endpoints referenced in this documentation require authenticated access. Authorization header must be set to the access token you retrieve after a successful authentication request.

`Authorization: Bearer <token>`

Requests made without an access token or an invalid/expired token will fail with a 401 Unauthorized response.
Requests made with an access token which does not have the correct permissions (see security subsection on every endpoint) will fail with a 403 Forbidden.
Read [here](https://github.com/osisoft/OSI-Samples-OCS/tree/master/basic_samples/Authentication) on how to authenticate against OCS with the various clients and receive an access token in response.

## Error Handling

All responses will have an error message in the body. The exceptions are 200 responses and the 401 Unauthorized response. The error message will look as follows:

```json
{
    "OperationId": "1b2af18e-8b27-4f86-93e0-6caa3e59b90c", 
    "Error": "Error message.", 
    "Reason": "Reason that caused error.", 
    "Resolution": "Possible solution for the error." 
}
```

If and when contacting OSIsoft support about this error, please provide the OperationId.

## `Get Users from a Tenant`

Get a list of users from a Tenant. Optionally, get a list of requested users.
            Total number of users in the Tenant set in the Total-Count header.

### Request

`GET api/v1/Tenants/{tenantId}/Users`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[FromQuery]
[Optional]
[Default = ""]
Guid[] id
```

Unordered list of User Ids to get.

```csharp
[FromQuery]
[Optional]
[Default = ""]
string query
```

Query to execute. Currently not supported.

```csharp
[FromQuery]
[Optional]
[Default = 0]
int32 skip
```

Number of users to skip. Ignored if a list of Ids is passed.

```csharp
[FromQuery]
[Optional]
[Default = 100]
int32 count
```

Maximum number of users to return. Ignored if a list of Ids is passed.

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

Partial success.

##### Type:

 `UserMultiStatusResponse`

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

Missing or invalid inputs.

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Tenant not found.

#### 500

Internal server error.
***

## `Get Users' Invitation Status`

Get invitation statuses for multiple users. Optionally
            restrict it only to users of a specific invitation status.
            The User status can be: InvitationAccepted (0),  NoInvitation (1),
            InvitationNotSent (2), InvitationSent (3), InvitationExpired (4).

### Request

`GET api/v1/Tenants/{tenantId}/Users/Status`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[FromQuery]
[Optional]
[Default = ""]
Guid[] id
```

Unordered list of User Ids to get.

```csharp
[FromQuery]
[Optional]
[Default = ""]
string query
```

Query to execute. Currently not supported.

```csharp
[FromQuery]
[Optional]
[Default = 0]
int32 skip
```

Number of users to skip. Ignored if a list of Ids is passed.

```csharp
[FromQuery]
[Optional]
[Default = 100]
int32 count
```

Maximum number of users to return. Ignored if a list of Ids is passed.

```csharp
[FromQuery]
[Optional]
[Default = ""]
string[] status
```

Only return statuses that match these values. Possible User statuses are: InvitationAccepted, NoInvitation, InvitationNotSent, InvitationSent, InvitationExpired.

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

Missing or invalid inputs.

#### 401

Unauthorized.

#### 403

Forbidden.

#### 500

Internal server error.

#### 404

Tenant not found.
***

## `Get User from a Tenant`

Get a User from Tenant.

### Request

`GET api/v1/Tenants/{tenantId}/Users/{userId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
Guid userId
```

Id of User.

### Security

Allowed for these roles:

- `Account Administrator`
- `Account Member`

### Returns

#### 200

Success.

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

Unauthorized.

#### 403

Forbidden.

#### 404

User or Tenant not found.

#### 500

Internal server error.
***

## `Get User's Invitation Status`

Get invitation status for a User. It can be: InvitationAccepted (0),
            NoInvitation (1), InvitationNotSent (2), InvitationSent (3), InvitationExpired (4).

### Request

`GET api/v1/Tenants/{tenantId}/Users/{userId}/Status`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
Guid userId
```

Id of User.

### Security

Allowed for these roles:

- `Account Administrator`
- `Account Member`

### Returns

#### 200

Success.

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

Unauthorized.

#### 403

Forbidden.

#### 404

User or Tenant not found.

#### 500

Internal server error.
***

## `Get User's Preferences`

Get preferences from a User. User preferences can be any valid
            JSON object. A common use case is to store UI preferences for the User.

### Request

`GET api/v1/Tenants/{tenantId}/Users/{userId}/Preferences`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
Guid userId
```

Id of User.

### Security

Allowed for these roles:

- `Account Administrator`
- `Account Member`

### Returns

#### 200

Success.

##### Type:

 `JObject`

```json
{}
```

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

User or Tenant not found.

#### 500

Internal server error.
***

## `Update User's Preferences`

Update preferences for a User.

### Request

`PUT api/v1/Tenants/{tenantId}/Users/{userId}/Preferences`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
Guid userId
```

Id of User.

```csharp
[FromBody]
[Required]
JObject preferences
```

JSON object preferences.

```json
{}
```

### Security

Allowed for these roles:

- `Account Administrator`
- `Account Member`

### Returns

#### 200

Success.

##### Type:

 `JObject`

```json
{}
```

#### 400

Missing preferences.

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

User or Tenant not found.

#### 405

Method not allowed at this base URL. Try the request again at the Global base URL.

#### 500

Internal server error.
***

## `Create User`

Create a User in the Tenant. This endpoint does not create an invitation for the User.
            You will need to create an invitation in the respective endpoint for this User, otherwise
            they will not be able to finish the sign-up process. Users have unique Ids in a Tenant.
            Currently there is a limit of 50000 users per Tenant.
            For Windows Active Directory users, the externalUserId must be specified.

### Request

`POST api/v1/Tenants/{tenantId}/Users`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[FromBody]
[Required]
UserCreateOrUpdate userCreateOrUpdate
```

UserCreateOrUpdate object.

Property | Type | Required | Description 
 --- | --- | --- | ---
Id | Guid | No | Gets or sets user Id for the user. When creating a user, if User ID is not specified, one will be generated.
ExternalUserId | string | No | Gets or sets user ExternalUserId for the user. Must be specified if Identity Provider is Windows Active Directory.
ContactGivenName | string | No | Gets or sets preferred name to be used when contacting user.
ContactSurname | string | No | Gets or sets preferred surname to be used when contacting user.
ContactEmail | string | No | Gets or sets preferred contact email to be used. This does not have to be the same as the user's Identity Provider email.
IdentityProviderId | Guid | No | Gets or sets Identity Provider this user will be required to use to login.  If null, the Identity Provider Id will            be set when creating the Invitation.
RoleIds | Guid[] | No | Gets or sets list of strings of RoleIds.



```json
{
  "Id": "00000000-0000-0000-0000-000000000000",
  "ExternalUserId": "ExternalUserId",
  "ContactGivenName": "Name",
  "ContactSurname": "Surname",
  "ContactEmail": "user@company.com",
  "IdentityProviderId": "00000000-0000-0000-0000-000000000000",
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

Created.

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

Missing or invalid inputs, or the User limit exceeded for Tenant.

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Tenant not found.

#### 405

Method not allowed at this base URL. Try the request again at the Global base URL.

#### 500

Internal server error.
***

## `Update User in a Tenant`

Update a User in a Tenant. The Id of a User cannot be changed.

### Request

`PUT api/v1/Tenants/{tenantId}/Users/{userId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
Guid userId
```

Id of User.

```csharp
[FromBody]
[Required]
UserCreateOrUpdate userCreateOrUpdate
```

UserCreateOrUpdate object. Properties that are not set or are null will not be changed.

Property | Type | Required | Description 
 --- | --- | --- | ---
Id | Guid | No | Gets or sets user Id for the user. When creating a user, if User ID is not specified, one will be generated.
ExternalUserId | string | No | Gets or sets user ExternalUserId for the user. Must be specified if Identity Provider is Windows Active Directory.
ContactGivenName | string | No | Gets or sets preferred name to be used when contacting user.
ContactSurname | string | No | Gets or sets preferred surname to be used when contacting user.
ContactEmail | string | No | Gets or sets preferred contact email to be used. This does not have to be the same as the user's Identity Provider email.
IdentityProviderId | Guid | No | Gets or sets Identity Provider this user will be required to use to login.  If null, the Identity Provider Id will            be set when creating the Invitation.
RoleIds | Guid[] | No | Gets or sets list of strings of RoleIds.



```json
{
  "Id": "00000000-0000-0000-0000-000000000000",
  "ExternalUserId": "ExternalUserId",
  "ContactGivenName": "Name",
  "ContactSurname": "Surname",
  "ContactEmail": "user@company.com",
  "IdentityProviderId": "00000000-0000-0000-0000-000000000000",
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

#### 200

Updated User.

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

Missing or invalid inputs.

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

User or Tenant not found.

#### 405

Method not allowed at this base URL. Try the request again at the Global base URL.

#### 500

Internal server error.
***

## `Delete User in a Tenant`

Delete a User. Admins cannot delete themselves.
            Deleting a User does not invalidate any of the
            existing access tokens, but it prevents this User
            from being able to authenticate in the future.
            Existing access tokens for the User will be valid
            until their expiration date. Refresh tokens on
            behalf of the User will no longer be valid after the
            User has been deleted.

### Request

`DELETE api/v1/Tenants/{tenantId}/Users/{userId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
Guid userId
```

Id of User.

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 204

Deleted.

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

User or Tenant not found.

#### 405

Method not allowed at this base URL. Try the request again at the Global base URL.

#### 500

Internal server error.
***

## `Get Header for User`

Validate that a User exists. This endpoint is identical to the GET
            one, but it does not return an object in the body.

### Request

`HEAD api/v1/Tenants/{tenantId}/Users/{userId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
Guid userId
```

Id of User.

### Security

Allowed for these roles:

- `Account Administrator`
- `Account Member`

### Returns

#### 200

User exists.

##### Type:

 `Void`

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

User does not exist.

#### 500

Internal server error.
***

## `Get Total Count of Users`

Return total number of users in a Tenant. Optionally, check based on a list of requested users.
            The value will be set in the Total-Count header. This endpoint is identical to the GET one but
            it does not return any objects in the body.

### Request

`HEAD api/v1/Tenants/{tenantId}/Users`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[FromQuery]
[Optional]
[Default = ""]
Guid[] id
```

Unordered list of User Ids.

### Security

Allowed for these roles:

- `Account Administrator`
- `Account Member`

### Returns

#### 200

Success.

##### Type:

 `Void`

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

User not found.

#### 500

Internal server error.
***

## `Get Header for User's Preferences`

Validate that there are preferences for a User. This endpoint is identical
            to the GET one but it does not return any objects in the body.

### Request

`HEAD api/v1/Tenants/{tenantId}/Users/{userId}/Preferences`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
Guid userId
```

Id of User.

### Security

Allowed for these roles:

- `Account Administrator`
- `Account Member`

### Returns

#### 200

Success.

##### Type:

 `Void`

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

User or Tenant not found.

#### 500

Internal server error.
***

