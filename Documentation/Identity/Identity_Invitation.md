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
  "Issued": "2019-04-29T18:26:11.2128847-07:00",
  "Expires": "2019-04-29T18:26:11.2128879-07:00",
  "Accepted": "2019-04-29T18:26:11.2128967-07:00",
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
  "Issued": "2019-04-29T18:26:11.217192-07:00",
  "Expires": "2019-04-29T18:26:11.2171945-07:00",
  "Accepted": "2019-04-29T18:26:11.2171973-07:00",
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
    "Issued": "2019-04-29T18:26:11.2184565-07:00",
    "Expires": "2019-04-29T18:26:11.2184583-07:00",
    "Accepted": "2019-04-29T18:26:11.2184604-07:00",
    "State": 0,
    "TenantId": "00000000-0000-0000-0000-000000000000",
    "UserId": "00000000-0000-0000-0000-000000000000",
    "IdentityProviderId": "00000000-0000-0000-0000-000000000000"
  },
  {
    "Id": "Id",
    "Issued": "2019-04-29T18:26:11.2184717-07:00",
    "Expires": "2019-04-29T18:26:11.2184724-07:00",
    "Accepted": "2019-04-29T18:26:11.2184742-07:00",
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
  "ExpiresDateTime": "2019-04-29T18:26:11.219466-07:00",
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
  "Issued": "2019-04-29T18:26:11.2219636-07:00",
  "Expires": "2019-04-29T18:26:11.2219668-07:00",
  "Accepted": "2019-04-29T18:26:11.2219717-07:00",
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
  "Issued": "2019-04-29T18:26:11.2599425-07:00",
  "Expires": "2019-04-29T18:26:11.2599463-07:00",
  "Accepted": "2019-04-29T18:26:11.2599499-07:00",
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
  "ExpiresDateTime": "2019-04-29T18:26:11.2610822-07:00",
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
  "Issued": "2019-04-29T18:26:11.2611594-07:00",
  "Expires": "2019-04-29T18:26:11.2611608-07:00",
  "Accepted": "2019-04-29T18:26:11.2611629-07:00",
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

## `Update Invitation`

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
  "ExpiresDateTime": "2019-04-29T18:26:11.2633516-07:00",
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
  "Issued": "2019-04-29T18:26:11.2634348-07:00",
  "Expires": "2019-04-29T18:26:11.2634362-07:00",
  "Accepted": "2019-04-29T18:26:11.2634384-07:00",
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
  "Issued": "2019-04-29T18:26:11.2634634-07:00",
  "Expires": "2019-04-29T18:26:11.2634645-07:00",
  "Accepted": "2019-04-29T18:26:11.2634662-07:00",
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

