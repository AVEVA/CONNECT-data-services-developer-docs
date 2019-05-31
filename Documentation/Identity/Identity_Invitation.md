---
uid: identityInvitation
---

# Invitation

APIs for creating, getting, updating, and deleting an Invitation

## Properties

For HTTP requests and responses, the Invitation object has the following properties and JSON-serialized body: 

Property | Type | Descriptions
 --- | --- | --- | ---
Id | string | Unique Invitation Id.
Issued | DateTime | Invitation issuing timestamp.
Expires | DateTime | Invitation expiration timestamp.
Accepted | DateTime | Invitation accepted timestamp.
State | InvitationStates | Invitation state. Can be None (0), InvitationEmailSent (1), InvitationAccepted (2)
TenantId | string | ID of the Tenant the invitation belongs to.
UserId | Guid | ID of the User whom the invitation was issued to.
IdentityProviderId | Guid | ID of the Identity Provider that must be used to accept the invitation.

### Serialized Model

```json
{
  "Id": "Id",
  "Issued": "2019-05-31T14:57:08.818742-07:00",
  "Expires": "2019-05-31T14:57:08.8187457-07:00",
  "Accepted": "2019-05-31T14:57:08.8187487-07:00",
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
  "Issued": "2019-05-31T14:57:08.8230985-07:00",
  "Expires": "2019-05-31T14:57:08.8231026-07:00",
  "Accepted": "2019-05-31T14:57:08.823106-07:00",
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

 `List`

```json
[
  {
    "Id": "Id",
    "Issued": "2019-05-31T14:57:08.8247538-07:00",
    "Expires": "2019-05-31T14:57:08.8247586-07:00",
    "Accepted": "2019-05-31T14:57:08.8247617-07:00",
    "State": 0,
    "TenantId": "00000000-0000-0000-0000-000000000000",
    "UserId": "00000000-0000-0000-0000-000000000000",
    "IdentityProviderId": "00000000-0000-0000-0000-000000000000"
  },
  {
    "Id": "Id",
    "Issued": "2019-05-31T14:57:08.8247759-07:00",
    "Expires": "2019-05-31T14:57:08.8247768-07:00",
    "Accepted": "2019-05-31T14:57:08.8247784-07:00",
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
ExpiresDateTime | DateTime | No | Invitation expiration date. Must be in the future.
State | InvitationStates | No | Set the state of invitation.
SendInvitation | bool | No | Send the invitation. Default is true.
IdentityProviderId | Guid | No | Identity Provider to use for accepting this invitation. Null implies invitation can be accepted using any            configured Identity Provider.



```json
{
  "ExpiresDateTime": "2019-05-31T14:57:08.8271583-07:00",
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
  "Issued": "2019-05-31T14:57:08.829861-07:00",
  "Expires": "2019-05-31T14:57:08.8298663-07:00",
  "Accepted": "2019-05-31T14:57:08.8298719-07:00",
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
  "Issued": "2019-05-31T14:57:08.8742373-07:00",
  "Expires": "2019-05-31T14:57:08.8742414-07:00",
  "Accepted": "2019-05-31T14:57:08.874277-07:00",
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
ExpiresDateTime | DateTime | No | Invitation expiration date. Must be within 2 months in the future.
State | InvitationStates | No | Set the state of invitation.
SendInvitation | bool | No | Send the invitation. Default is true.
IdentityProviderId | Guid | No | Identity Provider to use for accepting this invitation. Null implies invitation can be accepted using any            configured Identity Provider.



```json
{
  "ExpiresDateTime": "2019-05-31T14:57:08.8763743-07:00",
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
  "Issued": "2019-05-31T14:57:08.8765326-07:00",
  "Expires": "2019-05-31T14:57:08.8765354-07:00",
  "Accepted": "2019-05-31T14:57:08.8765399-07:00",
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
ExpiresDateTime | DateTime | No | Invitation expiration date. Must be within 2 months in the future.
State | InvitationStates | No | Set the state of invitation.
SendInvitation | bool | No | Send the invitation. Default is true.
IdentityProviderId | Guid | No | Identity Provider to use for accepting this invitation. Null implies invitation can be accepted using any            configured Identity Provider.



```json
{
  "ExpiresDateTime": "2019-05-31T14:57:08.8782746-07:00",
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
  "Issued": "2019-05-31T14:57:08.8784046-07:00",
  "Expires": "2019-05-31T14:57:08.8784072-07:00",
  "Accepted": "2019-05-31T14:57:08.8784113-07:00",
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
  "Issued": "2019-05-31T14:57:08.8784625-07:00",
  "Expires": "2019-05-31T14:57:08.8784643-07:00",
  "Accepted": "2019-05-31T14:57:08.878468-07:00",
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

