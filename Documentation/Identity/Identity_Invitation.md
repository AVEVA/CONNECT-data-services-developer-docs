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


```json
{
  "Id": "String",
  "Issued": "2019-01-25T15:31:27.6290964-08:00",
  "Expires": "2019-01-25T15:31:27.629101-08:00",
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

## `GetInvitation()`

Get an Invitation using its id in a tenant

### Http 

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

Allowed for these roles: **Account Administrator**, **Cluster Operator**, **Cluster Support**

### Returns

#### 200

Success. Returns OSIsoft.Identity.Common.Models.Invitation

```json
{
  "Id": "String",
  "Issued": "2019-01-25T15:31:27.6338799-08:00",
  "Expires": "2019-01-25T15:31:27.6338842-08:00",
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

## `GetInvitations()`

Get all invitations for a tenant

### Http 

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

Allowed for these roles: **Account Administrator**, **Cluster Operator**, **Cluster Support**

### Returns

#### 200

Success. Returns System.Collections.Generic.List`1[OSIsoft.Identity.Common.Models.Invitation]

```json
[
{
  "Id": "String",
  "Issued": "2019-01-25T15:31:27.6344432-08:00",
  "Expires": "2019-01-25T15:31:27.6344456-08:00",
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

## `UpdateInvitation()`

Update an invitation

### Http 

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
  "ExpiresDateTime": "2019-01-25T15:31:27.6347732-08:00",
  "State": 0
}
```


### Security

Allowed for these roles: **Account Administrator**

### Returns

#### 200

Success. Returns OSIsoft.Identity.Common.Models.Invitation

```json
{
  "Id": "String",
  "Issued": "2019-01-25T15:31:27.6368418-08:00",
  "Expires": "2019-01-25T15:31:27.6368457-08:00",
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

## `DeleteInvitation()`

Delete an invitation

### Http 

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

Allowed for these roles: **Account Administrator**

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

## `CreateInvitation()`

Create an invitation for a user

### Http 

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
  "ExpiresDateTime": "2019-01-25T15:31:27.657196-08:00",
  "DeleteExisting": true,
  "SendInvitation": true
}
```


### Security

Allowed for these roles: **Account Administrator**

### Returns

#### 201

Created. Returns OSIsoft.Identity.Common.Models.Invitation

```json
{
  "Id": "String",
  "Issued": "2019-01-25T15:31:27.6592092-08:00",
  "Expires": "2019-01-25T15:31:27.6592135-08:00",
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

