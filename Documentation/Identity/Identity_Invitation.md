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
TenantId | Guid | ID of the Tenant the invitation belongs to.
UserId | Guid | ID of the User whom the invitation was issued to.
IdentityProviderId | optional: Guid | ID of the Identity Provider that must be used to accept the invitation.

### Serialized Model

```json
{
  "Id": "Id",
  "Issued": "2019-04-11T17:16:26.3260882-07:00",
  "Expires": "2019-04-11T17:16:26.3260921-07:00",
  "Accepted": "2019-04-11T17:16:26.3260953-07:00",
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
Guid tenantId
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
  "Issued": "2019-04-11T17:16:26.3320979-07:00",
  "Expires": "2019-04-11T17:16:26.3321018-07:00",
  "Accepted": "2019-04-11T17:16:26.3321046-07:00",
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
Guid tenantId
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
    "Issued": "2019-04-11T17:16:26.3339044-07:00",
    "Expires": "2019-04-11T17:16:26.3339079-07:00",
    "Accepted": "2019-04-11T17:16:26.3339108-07:00",
    "State": 0,
    "TenantId": "00000000-0000-0000-0000-000000000000",
    "UserId": "00000000-0000-0000-0000-000000000000",
    "IdentityProviderId": "00000000-0000-0000-0000-000000000000"
  },
  {
    "Id": "Id",
    "Issued": "2019-04-11T17:16:26.3339298-07:00",
    "Expires": "2019-04-11T17:16:26.3339309-07:00",
    "Accepted": "2019-04-11T17:16:26.3339326-07:00",
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
Guid tenantId
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
  "ExpiresDateTime": "2019-04-11T17:16:26.3353508-07:00",
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
  "Issued": "2019-04-11T17:16:26.3394024-07:00",
  "Expires": "2019-04-11T17:16:26.339407-07:00",
  "Accepted": "2019-04-11T17:16:26.3394123-07:00",
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
Guid tenantId
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

