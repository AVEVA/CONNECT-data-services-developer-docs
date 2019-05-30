---
uid: identityInvitation
---

# Invitation

APIs for creating, getting, updating, and deleting an Invitation

## Properties

For HTTP requests and responses, the Invitation object has the following properties and JSON-serialized body: 

Property | Type | Required | Descriptions
 --- | --- | --- | ---
Id | string | Yes | Unique Invitation Id.
Issued | DateTime | Yes | Invitation issuing timestamp.
Expires | DateTime | Yes | Invitation expiration timestamp.
Accepted | optional: DateTime | No | Invitation accepted timestamp.
State | InvitationStates | Yes | Invitation state. Can be None (0), InvitationEmailSent (1), InvitationAccepted (2)
TenantId | string | Yes | ID of the Tenant the invitation belongs to.
UserId | Guid | Yes | ID of the User whom the invitation was issued to.
IdentityProviderId | optional: Guid | No | ID of the Identity Provider that must be used to accept the invitation.

### Serialized Model

```json
{
  "Id": "Id",
  "Issued": "2019-05-30T10:23:28.2540564-07:00",
  "Expires": "2019-05-30T10:23:28.2540625-07:00",
  "Accepted": "2019-05-30T10:23:28.2540676-07:00",
  "State": 0,
  "TenantId": "00000000-0000-0000-0000-000000000000",
  "UserId": "00000000-0000-0000-0000-000000000000",
  "IdentityProviderId": "00000000-0000-0000-0000-000000000000"
}
```

***

## `Get Invitation`

Get an Invitation using its id in a tenant

### Request

`GET api/v1/Tenants/{tenantId}/Invitations/{invitationId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
string invitationId
```

Id of invitation

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `Invitation`

```json
{
  "Id": "Id",
  "Issued": "2019-05-30T10:23:28.2606158-07:00",
  "Expires": "2019-05-30T10:23:28.260621-07:00",
  "Accepted": "2019-05-30T10:23:28.2606359-07:00",
  "State": 0,
  "TenantId": "00000000-0000-0000-0000-000000000000",
  "UserId": "00000000-0000-0000-0000-000000000000",
  "IdentityProviderId": "00000000-0000-0000-0000-000000000000"
}
```

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Invitation or Tenant not found

#### 500

Internal server error
***

## `Get Invitations`

Get all invitations for a tenant

### Request

`GET api/v1/Tenants/{tenantId}/Invitations`

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

Number of invitations to skip

```csharp
[FromQuery]
[Optional]
[Default = 100]
int32 count
```

Max number of invitations to return

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

### Returns

#### 200

Success

##### Type:

 `List[Invitation]`

```json
[
  {
    "Id": "Id",
    "Issued": "2019-05-30T10:23:28.2629257-07:00",
    "Expires": "2019-05-30T10:23:28.2629314-07:00",
    "Accepted": "2019-05-30T10:23:28.2629369-07:00",
    "State": 0,
    "TenantId": "00000000-0000-0000-0000-000000000000",
    "UserId": "00000000-0000-0000-0000-000000000000",
    "IdentityProviderId": "00000000-0000-0000-0000-000000000000"
  },
  {
    "Id": "Id",
    "Issued": "2019-05-30T10:23:28.2629644-07:00",
    "Expires": "2019-05-30T10:23:28.2629661-07:00",
    "Accepted": "2019-05-30T10:23:28.2629692-07:00",
    "State": 0,
    "TenantId": "00000000-0000-0000-0000-000000000000",
    "UserId": "00000000-0000-0000-0000-000000000000",
    "IdentityProviderId": "00000000-0000-0000-0000-000000000000"
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

## `Update Invitation`

Update an invitation

### Request

`PUT api/v1/Tenants/{tenantId}/Invitations/{invitationId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
string invitationId
```

Id of invitation

```csharp
[FromBody]
[Required]
InvitationCreateOrUpdate invitationCreateOrUpdate
```

New InvitationCreateOrUpdate object

Property | Type | Required | Description 
 --- | --- | --- | ---
ExpiresDateTime | optional: DateTime | No | Invitation expiration date. Must be in the future.
State | optional: InvitationStates | No | Set the state of invitation.
SendInvitation | optional: bool | No | Send the invitation. Default is true.
IdentityProviderId | optional: Guid | No | Identity Provider to use for accepting this invitation. Null implies invitation can be accepted using any            configured Identity Provider.



```json
{
  "ExpiresDateTime": "2019-05-30T10:23:28.265126-07:00",
  "State": 0,
  "SendInvitation": false,
  "IdentityProviderId": "00000000-0000-0000-0000-000000000000"
}
```

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `Invitation`

```json
{
  "Id": "Id",
  "Issued": "2019-05-30T10:23:28.2681685-07:00",
  "Expires": "2019-05-30T10:23:28.2681733-07:00",
  "Accepted": "2019-05-30T10:23:28.2681785-07:00",
  "State": 0,
  "TenantId": "00000000-0000-0000-0000-000000000000",
  "UserId": "00000000-0000-0000-0000-000000000000",
  "IdentityProviderId": "00000000-0000-0000-0000-000000000000"
}
```

#### 400

Missing or invalid inputs

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Invitation or Tenant not found

#### 500

Internal server error
***

## `Delete Invitation`

Delete an invitation

### Request

`DELETE api/v1/Tenants/{tenantId}/Invitations/{invitationId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
string invitationId
```

Id of invitation

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

Invitation or Tenant not found

#### 500

Internal server error
***

## `Get User's Invitation`

Get the invitations for a user

### Request

`GET api/v1/Tenants/{tenantId}/Users/{userId}/Invitation`

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

#### 200

Success

##### Type:

 `Invitation`

```json
{
  "Id": "Id",
  "Issued": "2019-05-30T10:23:28.3166374-07:00",
  "Expires": "2019-05-30T10:23:28.3166432-07:00",
  "Accepted": "2019-05-30T10:23:28.31665-07:00",
  "State": 0,
  "TenantId": "00000000-0000-0000-0000-000000000000",
  "UserId": "00000000-0000-0000-0000-000000000000",
  "IdentityProviderId": "00000000-0000-0000-0000-000000000000"
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

## `Create Invitation`

Create an invitation for a user. Should use when no other invitation exists for the user.

### Request

`POST api/v1/Tenants/{tenantId}/Users/{userId}/Invitation`

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
InvitationCreateOrUpdate invitationCreateOrUpdate
```

InvitationCreateOrUpdate object

Property | Type | Required | Description 
 --- | --- | --- | ---
ExpiresDateTime | optional: DateTime | No | Invitation expiration date. Must be in the future.
State | optional: InvitationStates | No | Set the state of invitation.
SendInvitation | optional: bool | No | Send the invitation. Default is true.
IdentityProviderId | optional: Guid | No | Identity Provider to use for accepting this invitation. Null implies invitation can be accepted using any            configured Identity Provider.



```json
{
  "ExpiresDateTime": "2019-05-30T10:23:28.3187293-07:00",
  "State": 0,
  "SendInvitation": false,
  "IdentityProviderId": "00000000-0000-0000-0000-000000000000"
}
```

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 201

Created

##### Type:

 `Invitation`

```json
{
  "Id": "Id",
  "Issued": "2019-05-30T10:23:28.3188831-07:00",
  "Expires": "2019-05-30T10:23:28.318886-07:00",
  "Accepted": "2019-05-30T10:23:28.3188902-07:00",
  "State": 0,
  "TenantId": "00000000-0000-0000-0000-000000000000",
  "UserId": "00000000-0000-0000-0000-000000000000",
  "IdentityProviderId": "00000000-0000-0000-0000-000000000000"
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

#### 409

Invitation already exists

#### 500

Internal server error
***

## `Create or Update Invitation`

Create or update an invitation for a user

### Request

`PUT api/v1/Tenants/{tenantId}/Users/{userId}/Invitation`

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
InvitationCreateOrUpdate invitationCreateOrUpdate
```

InvitationCreateOrUpdate object

Property | Type | Required | Description 
 --- | --- | --- | ---
ExpiresDateTime | optional: DateTime | No | Invitation expiration date. Must be in the future.
State | optional: InvitationStates | No | Set the state of invitation.
SendInvitation | optional: bool | No | Send the invitation. Default is true.
IdentityProviderId | optional: Guid | No | Identity Provider to use for accepting this invitation. Null implies invitation can be accepted using any            configured Identity Provider.



```json
{
  "ExpiresDateTime": "2019-05-30T10:23:28.3206494-07:00",
  "State": 0,
  "SendInvitation": false,
  "IdentityProviderId": "00000000-0000-0000-0000-000000000000"
}
```

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Updated

##### Type:

 `Invitation`

```json
{
  "Id": "Id",
  "Issued": "2019-05-30T10:23:28.3207466-07:00",
  "Expires": "2019-05-30T10:23:28.3207483-07:00",
  "Accepted": "2019-05-30T10:23:28.3207508-07:00",
  "State": 0,
  "TenantId": "00000000-0000-0000-0000-000000000000",
  "UserId": "00000000-0000-0000-0000-000000000000",
  "IdentityProviderId": "00000000-0000-0000-0000-000000000000"
}
```

#### 201

Created

##### Type:

 `Invitation`

```json
{
  "Id": "Id",
  "Issued": "2019-05-30T10:23:28.3207809-07:00",
  "Expires": "2019-05-30T10:23:28.320782-07:00",
  "Accepted": "2019-05-30T10:23:28.320784-07:00",
  "State": 0,
  "TenantId": "00000000-0000-0000-0000-000000000000",
  "UserId": "00000000-0000-0000-0000-000000000000",
  "IdentityProviderId": "00000000-0000-0000-0000-000000000000"
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

## `Delete Invitation`

Delete an invitation for a user

### Request

`DELETE api/v1/Tenants/{tenantId}/Users/{userId}/Invitation`

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

Invitation or Tenant not found

#### 500

Internal server error
***

