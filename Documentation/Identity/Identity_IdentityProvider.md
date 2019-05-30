---
uid: identityIdentityProvider
---

# IdentityProvider

APIs for getting a list of all supported Identity Providers

## Properties

For HTTP requests and responses, the IdentityProvider object has the following properties and JSON-serialized body: 

Property | Type | Required | Descriptions
 --- | --- | --- | ---
Id | Guid | No | Id of an identity provider
DisplayName | string | No | Identity provider display name to use
Scheme | string | No | Specifies the name of the cookie handler that will temporarily store the outcome of the external authentication.
UserIdClaimType | string | No | Type of claim

### Serialized Model

```json
{
  "Id": "00000000-0000-0000-0000-000000000000",
  "DisplayName": "Name",
  "Scheme": "Scheme",
  "UserIdClaimType": "UserIdClaimType"
}
```

***

## `Get Identity Provider`

Returns an IdentityProvider object

### Request

`GET api/v1/IdentityProviders/{identityProviderId}`

### Parameters

```csharp
[Required]
string identityProviderId
```

Id of provider

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `IdentityProvider`

```json
{
  "Id": "00000000-0000-0000-0000-000000000000",
  "DisplayName": "Name",
  "Scheme": "Scheme",
  "UserIdClaimType": "UserIdClaimType"
}
```

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Identity Provider not found

#### 500

Internal server error
***

## `Get Tenant Identity Providers`

Get all identity providers for a tenant

### Request

`GET api/v1/Tenants/{tenantId}/IdentityProviders`

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

Number of providers to skip.

```csharp
[FromQuery]
[Optional]
[Default = 100]
int32 count
```

Max number of providers to return

### Security

Allowed for these roles:

- `Account Administrator`
- `Account Member`

### Returns

#### 200

Success

##### Type:

 `List[IdentityProvider]`

```json
[
  {
    "Id": "00000000-0000-0000-0000-000000000000",
    "DisplayName": "Name",
    "Scheme": "Scheme",
    "UserIdClaimType": "UserIdClaimType"
  },
  {
    "Id": "00000000-0000-0000-0000-000000000000",
    "DisplayName": "Name",
    "Scheme": "Scheme",
    "UserIdClaimType": "UserIdClaimType"
  }
]
```

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Tenant not found

#### 500

Internal server error
***

## `Get Tenant Identity Provider`

Get an identity provider

### Request

`GET api/v1/Tenants/{tenantId}/IdentityProviders/{identityProviderId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
Guid identityProviderId
```

Id of provider

### Security

Allowed for these roles:

- `Account Administrator`
- `Account Member`

### Returns

#### 200

Success

##### Type:

 `IdentityProvider`

```json
{
  "Id": "00000000-0000-0000-0000-000000000000",
  "DisplayName": "Name",
  "Scheme": "Scheme",
  "UserIdClaimType": "UserIdClaimType"
}
```

#### 401

Unauthorized

#### 403

Forbidden

#### 404

IdentityProvider or Tenant not found

#### 500

Internal server error
***

## `Add Identity Provider to Tenant`

Add an existing identity provider to a tenant

### Request

`POST api/v1/Tenants/{tenantId}/IdentityProviders`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[FromBody]
[Required]
IdentityProviderAdd identityProviderAdd
```

Add Identity Provider object

Property | Type | Required | Description 
 --- | --- | --- | ---
IdentityProviderId | Guid | Yes | Identity Provider Id to Add
AzureActiveDirectoryTenant | string | No | Domain Name or Tenant Id of Azure Active Directory
AzureActiveDirectorySendConsent | bool | No | Send consent email for Azure Active Directory.
AzureActiveDirectoryConsentEmail | string | No | Preferred Azure Active Directory consent email for user.
AzureActiveDirectoryConsentGivenName | string | No | Preferred Azure Active Directory consent name for user.
AzureActiveDirectoryConsentSurname | string | No | Preferred Azure Active Directory consent surname for user.



```json
{
  "IdentityProviderId": "00000000-0000-0000-0000-000000000000",
  "AzureActiveDirectoryTenant": "AzureActiveDirectoryTenant",
  "AzureActiveDirectorySendConsent": false,
  "AzureActiveDirectoryConsentEmail": "user@company.com",
  "AzureActiveDirectoryConsentGivenName": "Name",
  "AzureActiveDirectoryConsentSurname": "Surname"
}
```

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 201

Created

##### Type:

 `IdentityProvider`

```json
{
  "Id": "00000000-0000-0000-0000-000000000000",
  "DisplayName": "Name",
  "Scheme": "Scheme",
  "UserIdClaimType": "UserIdClaimType"
}
```

#### 400

Missing or invalid inputs

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Tenant not found

#### 409

Identity Provider already exists in Tenant

#### 500

Internal server error
***

## `Remove Identity Provider From Tenant`

Remove an identity provider from a tenant

### Request

`DELETE api/v1/Tenants/{tenantId}/IdentityProviders/{identityProviderId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
Guid identityProviderId
```

Id of provider

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 204

Removed

#### 401

Unauthorized

#### 403

Forbidden

#### 404

IdentityProvider or Tenant not found

#### 500

Internal server error
***

