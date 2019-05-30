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
  "Issued": "2019-05-30T11:29:02.5157384-07:00",
  "Expires": "2019-05-30T11:29:02.5157419-07:00",
  "Accepted": "2019-05-30T11:29:02.5157447-07:00",
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
  "Issued": "2019-05-30T11:29:02.5216478-07:00",
  "Expires": "2019-05-30T11:29:02.5216525-07:00",
  "Accepted": "2019-05-30T11:29:02.5216595-07:00",
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
    "Issued": "2019-05-30T11:29:02.5239654-07:00",
    "Expires": "2019-05-30T11:29:02.5239692-07:00",
    "Accepted": "2019-05-30T11:29:02.5239739-07:00",
    "State": 0,
    "TenantId": "00000000-0000-0000-0000-000000000000",
    "UserId": "00000000-0000-0000-0000-000000000000",
    "IdentityProviderId": "00000000-0000-0000-0000-000000000000"
  },
  {
    "Id": "Id",
    "Issued": "2019-05-30T11:29:02.523995-07:00",
    "Expires": "2019-05-30T11:29:02.5239967-07:00",
    "Accepted": "2019-05-30T11:29:02.5239996-07:00",
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
  "ExpiresDateTime": "2019-05-30T11:29:02.5260377-07:00",
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
  "Issued": "2019-05-30T11:29:02.5295716-07:00",
  "Expires": "2019-05-30T11:29:02.5295772-07:00",
  "Accepted": "2019-05-30T11:29:02.5295831-07:00",
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
  "Issued": "2019-05-30T11:29:02.5734101-07:00",
  "Expires": "2019-05-30T11:29:02.573416-07:00",
  "Accepted": "2019-05-30T11:29:02.5734227-07:00",
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
  "ExpiresDateTime": "2019-05-30T11:29:02.5748297-07:00",
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
  "Issued": "2019-05-30T11:29:02.5749278-07:00",
  "Expires": "2019-05-30T11:29:02.5749301-07:00",
  "Accepted": "2019-05-30T11:29:02.5749338-07:00",
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
  "ExpiresDateTime": "2019-05-30T11:29:02.5768757-07:00",
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
  "Issued": "2019-05-30T11:29:02.5770236-07:00",
  "Expires": "2019-05-30T11:29:02.577026-07:00",
  "Accepted": "2019-05-30T11:29:02.5770302-07:00",
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
  "Issued": "2019-05-30T11:29:02.5771215-07:00",
  "Expires": "2019-05-30T11:29:02.5771236-07:00",
  "Accepted": "2019-05-30T11:29:02.5771275-07:00",
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

