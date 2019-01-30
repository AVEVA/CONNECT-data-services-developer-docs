---
uid: identityIdentityProvider
---

# IdentityProvider

APIs for CRUD operations on identity providers

## Properties

For HTTP requests and responses, the IdentityProvider object has the following properties and JSON-serialized body: 

```csharp
string Id
```
Id of an identity provider

```csharp
string DisplayName
```
Identity provider display name to use

```csharp
string Scheme
```
Specifies the name of the cookie handler that will temporarily store the outcome of the external authentication.

```csharp
string UserIdClaimType
```
Type of claim

### Serialized Model

```json
{
  "Id": "String",
  "DisplayName": "String",
  "Scheme": "String",
  "UserIdClaimType": "String"
}
```

***

## `Get Identity Provider`

Returns an IdentityProvider object

### Request

`GET api/IdentityProvider/{identityProviderId}`

### Parameters

```csharp
string identityProviderId [FromRoute] [Required] [No-Default]
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
  "Id": "String",
  "DisplayName": "String",
  "Scheme": "String",
  "UserIdClaimType": "String"
}
```

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Identity Provider not found

#### 500

Oops! Something happened, somewhere inside our server, just a while ago
***

## `Get Identity Provider By Scheme`

Returns a list of IdentityProvider objects that follow a scheme

### Request

`GET api/IdentityProvider/schemes/{scheme}`

### Parameters

```csharp
string scheme [FromRoute] [Required] [No-Default]
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
  "Id": "String",
  "DisplayName": "String",
  "Scheme": "String",
  "UserIdClaimType": "String"
}
```

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Identity Provider not found

#### 500

Oops! Something happened, somewhere inside our server, just a while ago
***

## `Get Identity Providers`

Returns a list of IdentityProvider objects

### Request

`GET api/IdentityProvider/`

### Parameters

```csharp
string query [FromQuery] [Optional] [Default = ""]
```

Query to execute. Currently not supported

```csharp
int32 skip [FromQuery] [Optional] [Default = 0]
```

Number of providers to skip.

```csharp
int32 count [FromQuery] [Optional] [Default = 100]
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
  "Id": "String",
  "DisplayName": "String",
  "Scheme": "String",
  "UserIdClaimType": "String"
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

Oops! Something happened, somewhere inside our server, just a while ago
***

## `Get Tenant Identity Providers`

Get all identity providers for a tenant

### Request

`GET api/Tenant/{tenantId}/IdentityProviders`

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

Number of providers to skip.

```csharp
int32 count [FromQuery] [Optional] [Default = 100]
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
  "Id": "String",
  "DisplayName": "String",
  "Scheme": "String",
  "UserIdClaimType": "String"
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

Oops! Something happened, somewhere inside our server, just a while ago
***

## `Get Tenant Identity Provider`

Get an identity provider

### Request

`GET api/Tenant/{tenantId}/IdentityProviders/{identityProviderId}`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string identityProviderId [FromRoute] [Required] [No-Default]
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
  "Id": "String",
  "DisplayName": "String",
  "Scheme": "String",
  "UserIdClaimType": "String"
}
```

#### 401

Unauthorized

#### 403

Forbidden

#### 404

IdentityProvider or Tenant not found

#### 500

Oops! Something happened, somewhere inside our server, just a while ago
***

## `Add Identity Provider to Tenant`

Add an existing identity provider to a tenant

### Request

`POST api/Tenant/{tenantId}/IdentityProviders`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string identityProviderId [FromQuery] [Required] [No-Default]
```

Id of provider

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 204

Added

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

## `Remove Identity Provider From Tenant`

Remove an identity provider from a tenant

### Request

`DELETE api/Tenant/{tenantId}/IdentityProviders/{identityProviderId}`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string identityProviderId [FromRoute] [Required] [No-Default]
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

Oops! Something happened, somewhere inside our server, just a while ago
***

