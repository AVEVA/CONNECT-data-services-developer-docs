---
uid: identityInvitation
---

# Invitation

CRUD operations on Invitation

## Properties

For HTTP requests and responses, the Invitation object has the following properties and JSON-serialized body: 

```csharp
string Id
```
Unique invitation id.

```csharp
DateTime Issued
```
Invitation issuing timestamp.

```csharp
DateTime Expires
```
Invitation expiration timestamp.

```csharp
int32 State
```
Current state of invitation.

```csharp
string TenantId
```
ID of tenant the invitation belongs to.

```csharp
Tenant Tenant
```
Tenant `Tenant <Tenant>` that owns the invitation.

```csharp
string UserId
```
ID of user whom the invitation was issued to.

```csharp
User User
```
User `User <User>` whom the invitation was issued to.

### Serialized Model

```json
{
  "Id": "String",
  "Issued": "2019-01-29T15:18:37.4389538-08:00",
  "Expires": "2019-01-29T15:18:37.4389574-08:00",
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

***

## `Create Invitation`

Create an invitation for a user

### Request

`POST api/Tenant/{tenantId}/Users/{userId}/Invitation`

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
InvitationCreateDto invitationCreateDto [FromBody] [Required] [No-Default]
```

InvitationCreateDto object

```json
{
  "ExpiresDateTime": "2019-01-29T15:18:37.4430474-08:00",
  "DeleteExisting": true,
  "SendInvitation": true
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
  "Id": "String",
  "Issued": "2019-01-29T15:18:37.4453016-08:00",
  "Expires": "2019-01-29T15:18:37.4453058-08:00",
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

Oops! Something happened, somewhere inside our server, just a while ago
***

## `Get Invitation`

Get an Invitation using its id in a tenant

### Request

`GET api/Tenant/{tenantId}/Invitations/{invitationId}`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string invitationId [FromRoute] [Required] [No-Default]
```

Id of invitation

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
  "Issued": "2019-01-29T15:18:37.4458637-08:00",
  "Expires": "2019-01-29T15:18:37.4458669-08:00",
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

Invitation or Tenant not found

#### 500

Oops! Something happened, somewhere inside our server, just a while ago
***

## `Get Invitations`

Get all invitations for a tenant

### Request

`GET api/Tenant/{tenantId}/Invitations`

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

Number of invitations to skip

```csharp
int32 count [FromQuery] [Optional] [Default = 100]
```

Max number of invitations to return

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

 `List[Invitation]`

```json
[
{
  "Id": "String",
  "Issued": "2019-01-29T15:18:37.4465545-08:00",
  "Expires": "2019-01-29T15:18:37.4465573-08:00",
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

## `Update Invitation`

Update an invitation

### Request

`PUT api/Tenant/{tenantId}/Invitations/{invitationId}`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string invitationId [FromRoute] [Required] [No-Default]
```

Id of invitation

```csharp
InvitationUpdateDto invitationUpdateDto [FromBody] [Required] [No-Default]
```

New InvitationUpdateDto object

```json
{
  "ExpiresDateTime": "2019-01-29T15:18:37.4471032-08:00",
  "State": 0,
  "ResendInvitationEmail": true
}
```

### Security

Allowed for these roles:

- `Account Administrator`
- `Cluster Support`
- `Cluster Operator`

### Returns

#### 200

Success

##### Type:

 `Invitation`

```json
{
  "Id": "String",
  "Issued": "2019-01-29T15:18:37.4492369-08:00",
  "Expires": "2019-01-29T15:18:37.4492393-08:00",
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

Invitation or Tenant not found

#### 500

Oops! Something happened, somewhere inside our server, just a while ago
***

## `Delete Invitation`

Delete an invitation

### Request

`DELETE api/Tenant/{tenantId}/Invitations/{invitationId}`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string invitationId [FromRoute] [Required] [No-Default]
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

Oops! Something happened, somewhere inside our server, just a while ago
***

