---
uid: identitySecret
---

# Secret

APIs for creating, getting, updating, and deleting Hybrid Clients


***

## `Get Client Secrets`

This method is obsolete, please use the following instead:
            {tenantId}/ClientCredentialClients/{clientId}/Secrets

### Request

`GET api/v1-preview/Tenants/{tenantId}/Clients/{clientId}/Secret/`

### Parameters

```csharp
[Required]
Guid tenantId
```

Id of tenant

```csharp
[Required]
string clientId
```

Id of client

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

Number of clients to skip. From query.

```csharp
[FromQuery]
[Optional]
[Default = 100]
int32 count
```

Max number of clients to return

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `List[ClientSecretDto]`

```json
[
  {
    "SecretId": "SecretId",
    "Expiration": "2019-03-05T12:43:53.5457636-08:00",
    "Description": "description"
  },
  {
    "SecretId": "SecretId",
    "Expiration": "2019-03-05T12:43:53.5482577-08:00",
    "Description": "description"
  }
]
```

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Client or Tenant not found

#### 500

Internal server error
***

## `Update Client Secret`

This method is obsolete, please use the following instead:
            {tenantId}/ClientCredentialClients/{clientId}/Secrets/{secretId}

### Request

`PUT api/v1-preview/Tenants/{tenantId}/Clients/{clientId}/Secret/{secretId}`

### Parameters

```csharp
[Required]
Guid tenantId
```

Id of tenant

```csharp
[Required]
string clientId
```

Id of client

```csharp
[Required]
string secretId
```

secretId

```csharp
[FromBody]
[Required]
ClientSecretDto secretUpdate
```

secretId

```json
{
  "SecretId": "SecretId",
  "Expiration": "2019-03-05T12:43:53.5582078-08:00",
  "Description": "description"
}
```

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `ClientSecretDto`

```json
{
  "SecretId": "SecretId",
  "Expiration": "2019-03-05T12:43:53.5583418-08:00",
  "Description": "description"
}
```

#### 400

Missing or invalid inputs

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Secret, Client, or Tenant not found

#### 500

Internal server error
***

## `Get Hybrid Client Secrets`

Get all secrets for a Hybrid Client

### Request

`GET api/v1-preview/Tenants/{tenantId}/HybridClients/{clientId}/Secret/`

### Parameters

```csharp
[Required]
Guid tenantId
```

Id of tenant

```csharp
[Required]
string clientId
```

Id of client

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

Number of clients to skip. From query.

```csharp
[FromQuery]
[Optional]
[Default = 100]
int32 count
```

Max number of clients to return

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `List[ClientSecretDto]`

```json
[
  {
    "SecretId": "SecretId",
    "Expiration": "2019-03-05T12:43:53.7920927-08:00",
    "Description": "description"
  },
  {
    "SecretId": "SecretId",
    "Expiration": "2019-03-05T12:43:53.7921111-08:00",
    "Description": "description"
  }
]
```

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Client or Tenant not found

#### 500

Internal server error
***

## `Get Hybrid Client Secret`

Get a specific Hybrid Client Secret

### Request

`GET api/v1-preview/Tenants/{tenantId}/HybridClients/{clientId}/Secret/{secretId}`

### Parameters

```csharp
[Required]
Guid tenantId
```

Id of tenant

```csharp
[Required]
string clientId
```

Id of client

```csharp
[Required]
string secretId
```

Id of secret

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `ClientSecretDto`

```json
{
  "SecretId": "SecretId",
  "Expiration": "2019-03-05T12:43:53.7926788-08:00",
  "Description": "description"
}
```

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Secret, Client, or Tenant not found

#### 500

Internal server error
***

## `Add Hybrid Client Secret`

Add a new secret for a Hybrid Client

### Request

`POST api/v1-preview/Tenants/{tenantId}/HybridClients/{clientId}/Secret/`

### Parameters

```csharp
[Required]
Guid tenantId
```

Id of tenant

```csharp
[Required]
string clientId
```

Id of client

```csharp
[FromBody]
[Required]
ClientSecretCreateOrUpdateDto clientSecretCreateOrUpdateDto
```



```json
{
  "Expiration": "2019-03-05T12:43:53.7931394-08:00",
  "Description": "description"
}
```

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 201

Created

##### Type:

 `ClientSecretResponseDto`

```json
{
  "ClientSecret": "ClientSecret",
  "SecretId": "SecretId",
  "Expiration": "2019-03-05T12:43:53.7946175-08:00",
  "Description": "description"
}
```

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Client or Tenant not found

#### 500

Internal server error
***

## `Update Hybrid Client Secret`

Update a Hybrid Client Secret
            Only Secret Description and Secret Expiration Date can be updated

### Request

`PUT api/v1-preview/Tenants/{tenantId}/HybridClients/{clientId}/Secret/{secretId}`

### Parameters

```csharp
[Required]
Guid tenantId
```

Id of tenant

```csharp
[Required]
string clientId
```

Id of client

```csharp
[Required]
string secretId
```

secretId

```csharp
[FromBody]
[Required]
ClientSecretCreateOrUpdateDto clientSecretCreateOrUpdateDto
```

secretId

```json
{
  "Expiration": "2019-03-05T12:43:53.7968481-08:00",
  "Description": "description"
}
```

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `ClientSecretDto`

```json
{
  "SecretId": "SecretId",
  "Expiration": "2019-03-05T12:43:53.7969186-08:00",
  "Description": "description"
}
```

#### 400

Missing or invalid inputs

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Secret, Client, or Tenant not found

#### 500

Internal server error
***

## `Delete Hybrid Client Secret`

Delete a secret from a Hybrid Client

### Request

`DELETE api/v1-preview/Tenants/{tenantId}/HybridClients/{clientId}/Secret/{secretId}`

### Parameters

```csharp
[Required]
Guid tenantId
```

Id of tenant

```csharp
[Required]
string clientId
```

Id of client

```csharp
[Required]
string secretId
```

Id of secret

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 204

Success

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Secret, Client, or Tenant not found

#### 500

Internal server error
***

## `Get Client Credential Client Secrets`

Get all secrets for a Client Credential Client

### Request

`GET api/v1-preview/Tenants/{tenantId}/ClientCredentialClients/{clientId}/Secret/`

### Parameters

```csharp
[Required]
Guid tenantId
```

Id of tenant

```csharp
[Required]
string clientId
```

Id of client

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

Number of clients to skip. From query.

```csharp
[FromQuery]
[Optional]
[Default = 100]
int32 count
```

Max number of clients to return

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `List[ClientSecretDto]`

```json
[
  {
    "SecretId": "SecretId",
    "Expiration": "2019-03-05T12:43:53.8594384-08:00",
    "Description": "description"
  },
  {
    "SecretId": "SecretId",
    "Expiration": "2019-03-05T12:43:53.8594532-08:00",
    "Description": "description"
  }
]
```

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Client or Tenant not found

#### 500

Internal server error
***

## `Get Client Credential Client Secret`

Get a specific Client Credential Client Secret

### Request

`GET api/v1-preview/Tenants/{tenantId}/ClientCredentialClients/{clientId}/Secret/{secretId}`

### Parameters

```csharp
[Required]
Guid tenantId
```

Id of tenant

```csharp
[Required]
string clientId
```

Id of client

```csharp
[Required]
string secretId
```

Id of secret

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `ClientSecretDto`

```json
{
  "SecretId": "SecretId",
  "Expiration": "2019-03-05T12:43:53.8598704-08:00",
  "Description": "description"
}
```

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Secret, Client, or Tenant not found

#### 500

Internal server error
***

## `Add Client Credential Client Secret`

Add a new secret for a Client Credential Client

### Request

`POST api/v1-preview/Tenants/{tenantId}/ClientCredentialClients/{clientId}/Secret/`

### Parameters

```csharp
[Required]
Guid tenantId
```

Id of tenant

```csharp
[Required]
string clientId
```

Id of client

```csharp
[FromBody]
[Required]
ClientSecretCreateOrUpdateDto clientSecretCreateOrUpdateDto
```



```json
{
  "Expiration": "2019-03-05T12:43:53.8601302-08:00",
  "Description": "description"
}
```

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 201

Created

##### Type:

 `ClientSecretResponseDto`

```json
{
  "ClientSecret": "ClientSecret",
  "SecretId": "SecretId",
  "Expiration": "2019-03-05T12:43:53.8601933-08:00",
  "Description": "description"
}
```

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Client or Tenant not found

#### 500

Internal server error
***

## `Update Client Credential Client Secret`

Update a Client Credential Client Secret
            Only Secret Description and Secret Expiration Date can be updated

### Request

`PUT api/v1-preview/Tenants/{tenantId}/ClientCredentialClients/{clientId}/Secret/{secretId}`

### Parameters

```csharp
[Required]
Guid tenantId
```

Id of tenant

```csharp
[Required]
string clientId
```

Id of client

```csharp
[Required]
string secretId
```

secretId

```csharp
[FromBody]
[Required]
ClientSecretCreateOrUpdateDto clientSecretCreateOrUpdateDto
```

secretId

```json
{
  "Expiration": "2019-03-05T12:43:53.8604588-08:00",
  "Description": "description"
}
```

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `ClientSecretDto`

```json
{
  "SecretId": "SecretId",
  "Expiration": "2019-03-05T12:43:53.8605202-08:00",
  "Description": "description"
}
```

#### 400

Missing or invalid inputs

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Secret, Client, or Tenant not found

#### 500

Internal server error
***

## `Delete Client Credential Client Secret`

Delete a secret from a Client Credential Client

### Request

`DELETE api/v1-preview/Tenants/{tenantId}/ClientCredentialClients/{clientId}/Secret/{secretId}`

### Parameters

```csharp
[Required]
Guid tenantId
```

Id of tenant

```csharp
[Required]
string clientId
```

Id of client

```csharp
[Required]
string secretId
```

Id of secret

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 204

Success

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Secret, Client, or Tenant not found

#### 500

Internal server error
***

