---
uid: identityInvitation
---

# Invitation

CRUD operations on Invitation

## Properties

For HTTP requests and responses, the Invitation object has the following properties and JSON-serialized body: 

Property | Type | Descriptions
 --- | --- | ---
string | Id | Unique invitation id.
DateTime | Issued | Invitation issuing timestamp.
DateTime | Expires | Invitation expiration timestamp.
int32 | State | Current state of invitation.
string | TenantId | ID of tenant the invitation belongs to.
Tenant | Tenant | Tenant `Tenant <Tenant>` that owns the invitation.
string | UserId | ID of user whom the invitation was issued to.
User | User | User `User <User>` whom the invitation was issued to.

### Serialized Model

```json
{
  "Id": "Id",
  "Issued": "2019-02-05T19:11:14.7678552-08:00",
  "Expires": "2019-02-05T19:11:14.767859-08:00",
  "State": 0,
  "TenantId": "TenantId",
  "Tenant": {
    "Id": "Id",
    "Alias": "Alias",
    "State": "State",
    "IsCloudConnectCustomer": false
  },
  "UserId": "UserId",
  "User": {
    "Id": "Id",
    "GivenName": "Name",
    "Surname": "Surname",
    "Name": "Name",
    "Email": "user@company.com",
    "ContactEmail": "user@company.com",
    "ContactGivenName": "Name",
    "ContactSurname": "Surname",
    "ExternalUserId": "ExternalUserId",
    "Preferences": "Preferences",
    "Tenant": {
      "Id": "Id",
      "Alias": "Alias",
      "State": "State",
      "IsCloudConnectCustomer": false
    },
    "IdentityProvider": {
      "Id": "Id",
      "DisplayName": "Name",
      "Scheme": "Scheme",
      "UserIdClaimType": "UserIdClaimType"
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
  "ExpiresDateTime": "2019-02-05T19:11:14.7718874-08:00",
  "DeleteExisting": false,
  "SendInvitation": false
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
  "Issued": "2019-02-05T19:11:14.7735675-08:00",
  "Expires": "2019-02-05T19:11:14.77357-08:00",
  "State": 0,
  "TenantId": "TenantId",
  "Tenant": {
    "Id": "Id",
    "Alias": "Alias",
    "State": "State",
    "IsCloudConnectCustomer": false
  },
  "UserId": "UserId",
  "User": {
    "Id": "Id",
    "GivenName": "Name",
    "Surname": "Surname",
    "Name": "Name",
    "Email": "user@company.com",
    "ContactEmail": "user@company.com",
    "ContactGivenName": "Name",
    "ContactSurname": "Surname",
    "ExternalUserId": "ExternalUserId",
    "Preferences": "Preferences",
    "Tenant": {
      "Id": "Id",
      "Alias": "Alias",
      "State": "State",
      "IsCloudConnectCustomer": false
    },
    "IdentityProvider": {
      "Id": "Id",
      "DisplayName": "Name",
      "Scheme": "Scheme",
      "UserIdClaimType": "UserIdClaimType"
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

Internal server error
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
  "Id": "Id",
  "Issued": "2019-02-05T19:11:14.7739804-08:00",
  "Expires": "2019-02-05T19:11:14.7739822-08:00",
  "State": 0,
  "TenantId": "TenantId",
  "Tenant": {
    "Id": "Id",
    "Alias": "Alias",
    "State": "State",
    "IsCloudConnectCustomer": false
  },
  "UserId": "UserId",
  "User": {
    "Id": "Id",
    "GivenName": "Name",
    "Surname": "Surname",
    "Name": "Name",
    "Email": "user@company.com",
    "ContactEmail": "user@company.com",
    "ContactGivenName": "Name",
    "ContactSurname": "Surname",
    "ExternalUserId": "ExternalUserId",
    "Preferences": "Preferences",
    "Tenant": {
      "Id": "Id",
      "Alias": "Alias",
      "State": "State",
      "IsCloudConnectCustomer": false
    },
    "IdentityProvider": {
      "Id": "Id",
      "DisplayName": "Name",
      "Scheme": "Scheme",
      "UserIdClaimType": "UserIdClaimType"
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

Internal server error
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
    "Id": "Id",
    "Issued": "2019-02-05T19:11:14.7745168-08:00",
    "Expires": "2019-02-05T19:11:14.7745189-08:00",
    "State": 0,
    "TenantId": "TenantId",
    "Tenant": {
      "Id": "Id",
      "Alias": "Alias",
      "State": "State",
      "IsCloudConnectCustomer": false
    },
    "UserId": "UserId",
    "User": {
      "Id": "Id",
      "GivenName": "Name",
      "Surname": "Surname",
      "Name": "Name",
      "Email": "user@company.com",
      "ContactEmail": "user@company.com",
      "ContactGivenName": "Name",
      "ContactSurname": "Surname",
      "ExternalUserId": "ExternalUserId",
      "Preferences": "Preferences",
      "Tenant": {
        "Id": "Id",
        "Alias": "Alias",
        "State": "State",
        "IsCloudConnectCustomer": false
      },
      "IdentityProvider": {
        "Id": "Id",
        "DisplayName": "Name",
        "Scheme": "Scheme",
        "UserIdClaimType": "UserIdClaimType"
      }
    }
  },
  {
    "Id": "Id",
    "Issued": "2019-02-05T19:11:14.774575-08:00",
    "Expires": "2019-02-05T19:11:14.774576-08:00",
    "State": 0,
    "TenantId": "TenantId",
    "Tenant": {
      "Id": "Id",
      "Alias": "Alias",
      "State": "State",
      "IsCloudConnectCustomer": false
    },
    "UserId": "UserId",
    "User": {
      "Id": "Id",
      "GivenName": "Name",
      "Surname": "Surname",
      "Name": "Name",
      "Email": "user@company.com",
      "ContactEmail": "user@company.com",
      "ContactGivenName": "Name",
      "ContactSurname": "Surname",
      "ExternalUserId": "ExternalUserId",
      "Preferences": "Preferences",
      "Tenant": {
        "Id": "Id",
        "Alias": "Alias",
        "State": "State",
        "IsCloudConnectCustomer": false
      },
      "IdentityProvider": {
        "Id": "Id",
        "DisplayName": "Name",
        "Scheme": "Scheme",
        "UserIdClaimType": "UserIdClaimType"
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

Internal server error
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
  "ExpiresDateTime": "2019-02-05T19:11:14.7751011-08:00",
  "State": 0,
  "ResendInvitationEmail": false
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
  "Id": "Id",
  "Issued": "2019-02-05T19:11:14.7802746-08:00",
  "Expires": "2019-02-05T19:11:14.7802792-08:00",
  "State": 0,
  "TenantId": "TenantId",
  "Tenant": {
    "Id": "Id",
    "Alias": "Alias",
    "State": "State",
    "IsCloudConnectCustomer": false
  },
  "UserId": "UserId",
  "User": {
    "Id": "Id",
    "GivenName": "Name",
    "Surname": "Surname",
    "Name": "Name",
    "Email": "user@company.com",
    "ContactEmail": "user@company.com",
    "ContactGivenName": "Name",
    "ContactSurname": "Surname",
    "ExternalUserId": "ExternalUserId",
    "Preferences": "Preferences",
    "Tenant": {
      "Id": "Id",
      "Alias": "Alias",
      "State": "State",
      "IsCloudConnectCustomer": false
    },
    "IdentityProvider": {
      "Id": "Id",
      "DisplayName": "Name",
      "Scheme": "Scheme",
      "UserIdClaimType": "UserIdClaimType"
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

Internal server error
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

Internal server error
***

