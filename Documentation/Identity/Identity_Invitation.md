---
uid: identityInvitation
---

# Invitation

APIs for creating, getting, updating, and deleting an Invitation

## Properties

For HTTP requests and responses, the InvitationDto object has the following properties and JSON-serialized body: 

Property | Type | Descriptions
 --- | --- | ---
Id | string | Unique Invitation Id.
Issued | DateTime | Invitation issuing timestamp.
Expires | DateTime | Invitation expiration timestamp.
Accepted | optional: DateTime | Invitation accepted timestamp.
State | InvitationStates | Invitation state. Can be None (0), InvitationEmailSent (1), InvitationAccepted (2)
TenantId | string | ID of the Tenant the invitation belongs to.
UserId | Guid | ID of the User whom the invitation was issued to.
IdentityProviderId | optional: Guid | ID of the Identity Provider that must be used to accept the invitation.

### Serialized Model

```json
{
  "Id": "Id",
  "Issued": "2019-04-30T11:14:58.2160523-07:00",
  "Expires": "2019-04-30T11:14:58.2160575-07:00",
  "Accepted": "2019-04-30T11:14:58.2160625-07:00",
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

`GET api/v1-preview/Tenants/{tenantId}/Invitations/{invitationId}`

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

 `InvitationDto`

```json
{
  "Id": "Id",
  "Issued": "2019-04-30T11:14:58.2223665-07:00",
  "Expires": "2019-04-30T11:14:58.2223708-07:00",
  "Accepted": "2019-04-30T11:14:58.2223743-07:00",
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

`GET api/v1-preview/Tenants/{tenantId}/Invitations`

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

 `List[InvitationDto]`

```json
[
  {
    "Id": "Id",
    "Issued": "2019-04-30T11:14:58.2253969-07:00",
    "Expires": "2019-04-30T11:14:58.2254025-07:00",
    "Accepted": "2019-04-30T11:14:58.2254075-07:00",
    "State": 0,
    "TenantId": "00000000-0000-0000-0000-000000000000",
    "UserId": "00000000-0000-0000-0000-000000000000",
    "IdentityProviderId": "00000000-0000-0000-0000-000000000000"
  },
  {
    "Id": "Id",
    "Issued": "2019-04-30T11:14:58.2254297-07:00",
    "Expires": "2019-04-30T11:14:58.2254314-07:00",
    "Accepted": "2019-04-30T11:14:58.2254346-07:00",
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

`PUT api/v1-preview/Tenants/{tenantId}/Invitations/{invitationId}`

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
InvitationCreateOrUpdateDto invitationCreateOrUpdateDto
```

New InvitationUpdateDto object

```json
{
  "ExpiresDateTime": "2019-04-30T11:14:58.2273317-07:00",
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

 `InvitationDto`

```json
{
  "Id": "Id",
  "Issued": "2019-04-30T11:14:58.2308194-07:00",
  "Expires": "2019-04-30T11:14:58.230823-07:00",
  "Accepted": "2019-04-30T11:14:58.2308279-07:00",
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

`DELETE api/v1-preview/Tenants/{tenantId}/Invitations/{invitationId}`

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

`GET api/v1-preview/Tenants/{tenantId}/Users/{userId}/Invitations`

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

 `InvitationDto`

```json
{
  "Id": "Id",
  "Issued": "2019-04-30T11:14:58.2638566-07:00",
  "Expires": "2019-04-30T11:14:58.2638601-07:00",
  "Accepted": "2019-04-30T11:14:58.263864-07:00",
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

`POST api/v1-preview/Tenants/{tenantId}/Users/{userId}/Invitations`

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
InvitationCreateOrUpdateDto invitationCreateOrUpdateDto
```

InvitationCreateDto object

```json
{
  "ExpiresDateTime": "2019-04-30T11:14:58.2648256-07:00",
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

 `InvitationDto`

```json
{
  "Id": "Id",
  "Issued": "2019-04-30T11:14:58.2649045-07:00",
  "Expires": "2019-04-30T11:14:58.2649059-07:00",
  "Accepted": "2019-04-30T11:14:58.2649084-07:00",
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

`PUT api/v1-preview/Tenants/{tenantId}/Users/{userId}/Invitations`

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
InvitationCreateOrUpdateDto invitationCreateOrUpdateDto
```

InvitationCreateDto object

```json
{
  "ExpiresDateTime": "2019-04-30T11:14:58.2669916-07:00",
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

 `InvitationDto`

```json
{
  "Id": "Id",
  "Issued": "2019-04-30T11:14:58.2671028-07:00",
  "Expires": "2019-04-30T11:14:58.2671042-07:00",
  "Accepted": "2019-04-30T11:14:58.2671063-07:00",
  "State": 0,
  "TenantId": "00000000-0000-0000-0000-000000000000",
  "UserId": "00000000-0000-0000-0000-000000000000",
  "IdentityProviderId": "00000000-0000-0000-0000-000000000000"
}
```

#### 201

Created

##### Type:

 `InvitationDto`

```json
{
  "Id": "Id",
  "Issued": "2019-04-30T11:14:58.2671846-07:00",
  "Expires": "2019-04-30T11:14:58.2671857-07:00",
  "Accepted": "2019-04-30T11:14:58.2671878-07:00",
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

