---
uid: identityClaimTypeName
---

# ClaimTypeName

An Identity Provider Claim Type Name is the field or type name in a claim
            that will be used to match to a value when creating an Identity Provider Claim.


***

## Authentication

All endpoints referenced in this documentation require authenticated access. Authorization header must be set to the access token you retrieve after a successful authentication request.

`Authorization: Bearer <token>`

Requests made without an access token or an invalid/expired token will fail with a 401 Unauthorized response.
Requests made with an access token which does not have the correct permissions (see security subsection on every endpoint) will fail with a 403 Forbidden.
Read [here](https://github.com/osisoft/OSI-Samples-OCS/tree/master/basic_samples/Authentication) on how to authenticate against OCS with the various clients and receive an access token in response.

## Error Handling

All responses will have an error message in the body. The exceptions are 200 responses and the 401 Unauthorized response. The error message will look as follows:

```json
{
    "OperationId": "1b2af18e-8b27-4f86-93e0-6caa3e59b90c", 
    "Error": "Error message.", 
    "Reason": "Reason that caused error.", 
    "Resolution": "Possible solution for the error." 
}
```

If and when contacting OSIsoft support about this error, please provide the OperationId.

## `Get All Identity Provider Claim Type Names`

Get all Identity Provider Claim Type Names for an Identity Provider on a Tenant.

### Request

`GET api/v1/Tenants/{tenantId}/IdentityProviders/{identityProviderId}/ClaimTypeNames`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
Guid identityProviderId
```

Id of Identity Provider.

```csharp
[FromQuery]
[Optional]
[Default = ""]
string query
```

Query to execute. Currently not supported.

```csharp
[FromQuery]
[Optional]
[Default = 0]
int32 skip
```

Number of Identity Providers to skip.

```csharp
[FromQuery]
[Optional]
[Default = 100]
int32 count
```

Maximum number of Identity Providers to return.

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success.

##### Type:

 `List`

```json
[
  {
    "Id": "00000000-0000-0000-0000-000000000000",
    "TypeName": "Name",
    "IdentityProviderId": "00000000-0000-0000-0000-000000000000"
  },
  {
    "Id": "00000000-0000-0000-0000-000000000000",
    "TypeName": "Name",
    "IdentityProviderId": "00000000-0000-0000-0000-000000000000"
  }
]
```

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Tenant or Identity Provider not found.

#### 500

Internal server error.
***

## `Get All Identity Provider Claim Type Names Header`

Get Header for all Identity Provider Claims Type Names for an Identity Provider on a Tenant.

### Request

`HEAD api/v1/Tenants/{tenantId}/IdentityProviders/{identityProviderId}/ClaimTypeNames`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
Guid identityProviderId
```

Id of Identity Provider.

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success.

##### Type:

 `Void`

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Tenant or Identity Provider not found.

#### 500

Internal server error.
***

## `Get Identity Provider Claim Type Name`

Get an Identity Provider Claim Type Name from an Identity Provider on a Tenant.

### Request

`GET api/v1/Tenants/{tenantId}/IdentityProviders/{identityProviderId}/ClaimTypeNames/{identityProviderClaimTypeNameId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
Guid identityProviderId
```

Id of Identity Provider.

```csharp
[Required]
Guid identityProviderClaimTypeNameId
```

Id of Identity Provider Claim Type Name.

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success.

##### Type:

 `IdentityProviderClaim`

```json
{
  "Id": "00000000-0000-0000-0000-000000000000",
  "TypeName": "Name",
  "Value": "Value",
  "RoleIds": [
    "00000000-0000-0000-0000-000000000000",
    "00000000-0000-0000-0000-000000000000"
  ]
}
```

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Tenant, Identity Provider, or Identity Provider Claim Type Name not found.

#### 500

Internal server error.
***

## `Get Identity Provider Claim Type Name Header`

Get an Identity Provider Claim Type Name Header from an Identity Provider on a Tenant.

### Request

`HEAD api/v1/Tenants/{tenantId}/IdentityProviders/{identityProviderId}/ClaimTypeNames/{identityProviderClaimTypeNameId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
Guid identityProviderId
```

Id of Identity Provider.

```csharp
[Required]
Guid identityProviderClaimTypeNameId
```

Id of Identity Provider Claim Type Name.

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success.

##### Type:

 `Void`

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Tenant, Identity Provider, or Identity Provider Claim Type Name not found.

#### 500

Internal server error.
***

