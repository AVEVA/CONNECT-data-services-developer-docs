---
uid: identityIdentityProvider
---

# IdentityProvider

APIs for CRUD operations on identity providers

## Properties

For HTTP requests and responses, the IdentityProvider object has the following properties and JSON-serialized body: 

Property | Type | Descriptions
 --- | --- | ---
Id | string | Id of an identity provider
DisplayName | string | Identity provider display name to use
Scheme | string | Specifies the name of the cookie handler that will temporarily store the outcome of the external authentication.
UserIdClaimType | string | Type of claim

### Serialized Model

```json
{
  "Id": "Id",
  "DisplayName": "Name",
  "Scheme": "Scheme",
  "UserIdClaimType": "UserIdClaimType"
}
```

***

## `Get Identity Provider`

Returns an IdentityProvider object

### Request

`GET api/IdentityProvider/{identityProviderId}`

### Parameters

```csharp
[Required]
string identityProviderId
```

Id of provider

### Security

Allowed for these roles:

- `Account Administrator`
- `Cluster Operator`
- `Cluster Support`

### Returns

#### 200

Success

##### Type:

 `IdentityProvider`

```json
{
  "Id": "Id",
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

## `Get Identity Provider By Scheme`

Returns a list of IdentityProvider objects that follow a scheme

### Request

`GET api/IdentityProvider/schemes/{scheme}`

### Parameters

```csharp
[Required]
string scheme
```

Scheme name

### Security

Allowed for these roles:

- `Cluster Operator`

### Returns

#### 200

Success

##### Type:

 `IdentityProvider`

```json
{
  "Id": "Id",
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

## `Get Identity Providers`

Returns a list of IdentityProvider objects

### Request

`GET api/IdentityProvider/`

### Parameters

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

- `Cluster Operator`

### Returns

#### 200

Success

##### Type:

 `List[IdentityProvider]`

```json
[
  {
    "Id": "Id",
    "DisplayName": "Name",
    "Scheme": "Scheme",
    "UserIdClaimType": "UserIdClaimType"
  },
  {
    "Id": "Id",
    "DisplayName": "Name",
    "Scheme": "Scheme",
    "UserIdClaimType": "UserIdClaimType"
  }
]
```

#### 400

Missing or invalid inputs

#### 401

Unauthorized

#### 403

Forbidden

#### 500

Internal server error
***

## `Get Tenant Identity Providers`

Get all identity providers for a tenant

### Request

`GET api/Tenants/{tenantId}/IdentityProvider/`

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
- `Cluster Operator`
- `Cluster Support`

### Returns

#### 200

Success

##### Type:

 `List[IdentityProvider]`

```json
[
  {
    "Id": "Id",
    "DisplayName": "Name",
    "Scheme": "Scheme",
    "UserIdClaimType": "UserIdClaimType"
  },
  {
    "Id": "Id",
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

`GET api/Tenants/{tenantId}/IdentityProvider/{identityProviderId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
string identityProviderId
```

Id of provider

### Security

Allowed for these roles:

- `Account Administrator`
- `Cluster Operator`
- `Cluster Support`

### Returns

#### 200

Success

##### Type:

 `IdentityProvider`

```json
{
  "Id": "Id",
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

`POST api/Tenants/{tenantId}/IdentityProvider/{identityProviderId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
string identityProviderId
```

Id of provider

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
  "Id": "Id",
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

#### 500

Internal server error
***

## `Remove Identity Provider From Tenant`

Remove an identity provider from a tenant

### Request

`DELETE api/Tenants/{tenantId}/IdentityProvider/{identityProviderId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
string identityProviderId
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

