---
uid: identityInvitation
---

# Invitation

APIs for creating, getting, updating, and deleting an Invitation

## Properties

For HTTP requests and responses, the Invitation object has the following properties and JSON-serialized body: 

Property | Type | Descriptions
 --- | --- | ---
Id | string | Unique invitation id.
Issued | DateTime | Invitation issuing timestamp.
Expires | DateTime | Invitation expiration timestamp.
State | int32 | Current state of invitation.
TenantId | string | ID of tenant the invitation belongs to.
Tenant | Tenant | Tenant Tenant that owns the invitation.
UserId | string | ID of user whom the invitation was issued to.
User | User | User User whom the invitation was issued to.

### Serialized Model

```json
{
  "Id": "Id",
  "Issued": "2019-02-20T01:57:33.292122-05:00",
  "Expires": "2019-02-20T01:57:33.2921272-05:00",
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

## `Get Invitation`

Get an Invitation using its id in a tenant

### Request

`GET api/Tenants/{tenantId}/Invitation/{invitationId}`

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
  "Issued": "2019-02-20T01:57:33.3071625-05:00",
  "Expires": "2019-02-20T01:57:33.3071675-05:00",
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

`GET api/Tenants/{tenantId}/Invitation/`

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
    "Issued": "2019-02-20T01:57:33.3080691-05:00",
    "Expires": "2019-02-20T01:57:33.3080733-05:00",
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
    "Issued": "2019-02-20T01:57:33.3081558-05:00",
    "Expires": "2019-02-20T01:57:33.3081579-05:00",
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

`PUT api/Tenants/{tenantId}/Invitation/{invitationId}`

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
InvitationUpdateDto invitationUpdateDto
```

New InvitationUpdateDto object

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
  "Issued": "2019-02-20T01:57:33.3088269-05:00",
  "Expires": "2019-02-20T01:57:33.3088301-05:00",
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

`DELETE api/Tenants/{tenantId}/Invitation/{invitationId}`

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

## `Create Invitation`

Create an invitation for a user

### Request

`POST api/Tenants/{tenantId}/User/{userId}/Invitation`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
string userId
```

Id of user

```csharp
[FromBody]
[Required]
InvitationCreateDto invitationCreateDto
```

InvitationCreateDto object

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
  "Issued": "2019-02-20T01:57:33.4030254-05:00",
  "Expires": "2019-02-20T01:57:33.4030318-05:00",
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

