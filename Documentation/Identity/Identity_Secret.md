---
uid: identitySecret
---

# Secret

APIs for creating, getting, updating, and deleting Hybrid Client Secrets


***

## `Get Hybrid Client Secrets`

Get all secrets for a Hybrid Client

### Request

`GET api/v1/Tenants/{tenantId}/HybridClients/{clientId}/Secrets`

### Parameters

```csharp
[Required]
string tenantId
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

Number of secrets to skip. From query.

```csharp
[FromQuery]
[Optional]
[Default = 100]
int32 count
```

Max number of secrets to return

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `List[ClientSecret]`

```json
[
  {
    "Id": 0,
    "Expiration": "2019-05-31T14:57:08.5721303-07:00",
    "Expires": false,
    "Description": "description"
  },
  {
    "Id": 0,
    "Expiration": "2019-05-31T14:57:08.5724552-07:00",
    "Expires": false,
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

`GET api/v1/Tenants/{tenantId}/HybridClients/{clientId}/Secrets/{secretId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
string clientId
```

Id of client

```csharp
[Required]
int32 secretId
```

Id of secret

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `ClientSecret`

```json
{
  "Id": 0,
  "Expiration": "2019-05-31T14:57:08.5763045-07:00",
  "Expires": false,
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

`POST api/v1/Tenants/{tenantId}/HybridClients/{clientId}/Secrets`

### Parameters

```csharp
[Required]
string tenantId
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
ClientSecretCreateOrUpdate clientSecretCreateOrUpdate
```



Property | Type | Required | Description 
 --- | --- | --- | ---
Expiration | DateTime | No | Expiration date for the client secret. If not provided the secret will never expire.
Expires | bool | No | Determines if the secret expires. If this value is set, non null Expiration will be ignored. Defaults to true.
Description | string | No | Description for the client secret



```json
{
  "Expiration": "2019-05-31T14:57:08.577856-07:00",
  "Expires": false,
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

 `ClientSecretResponse`

```json
{
  "Secret": "Secret",
  "Id": 0,
  "Expiration": "2019-05-31T14:57:08.5795202-07:00",
  "Expires": false,
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

### Request

`PUT api/v1/Tenants/{tenantId}/HybridClients/{clientId}/Secrets/{secretId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
string clientId
```

Id of client

```csharp
[Required]
int32 secretId
```

secretId

```csharp
[FromBody]
[Required]
ClientSecretCreateOrUpdate clientSecretCreateOrUpdate
```

secretId

Property | Type | Required | Description 
 --- | --- | --- | ---
Expiration | DateTime | No | Expiration date for the client secret. If not provided the secret will never expire.
Expires | bool | No | Determines if the secret expires. If this value is set, non null Expiration will be ignored. Defaults to true.
Description | string | No | Description for the client secret



```json
{
  "Expiration": "2019-05-31T14:57:08.5829853-07:00",
  "Expires": false,
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

 `ClientSecret`

```json
{
  "Id": 0,
  "Expiration": "2019-05-31T14:57:08.5830795-07:00",
  "Expires": false,
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

`DELETE api/v1/Tenants/{tenantId}/HybridClients/{clientId}/Secrets/{secretId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
string clientId
```

Id of client

```csharp
[Required]
int32 secretId
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

`GET api/v1/Tenants/{tenantId}/ClientCredentialClients/{clientId}/Secrets`

### Parameters

```csharp
[Required]
string tenantId
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

Number of secrets to skip. From query.

```csharp
[FromQuery]
[Optional]
[Default = 100]
int32 count
```

Max number of secrets to return

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `List[ClientSecret]`

```json
[
  {
    "Id": 0,
    "Expiration": "2019-05-31T14:57:08.6890608-07:00",
    "Expires": false,
    "Description": "description"
  },
  {
    "Id": 0,
    "Expiration": "2019-05-31T14:57:08.6890792-07:00",
    "Expires": false,
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

`GET api/v1/Tenants/{tenantId}/ClientCredentialClients/{clientId}/Secrets/{secretId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
string clientId
```

Id of client

```csharp
[Required]
int32 secretId
```

Id of secret

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `ClientSecret`

```json
{
  "Id": 0,
  "Expiration": "2019-05-31T14:57:08.6906466-07:00",
  "Expires": false,
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

`POST api/v1/Tenants/{tenantId}/ClientCredentialClients/{clientId}/Secrets`

### Parameters

```csharp
[Required]
string tenantId
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
ClientSecretCreateOrUpdate clientSecretCreateOrUpdate
```



Property | Type | Required | Description 
 --- | --- | --- | ---
Expiration | DateTime | No | Expiration date for the client secret.  If not provided the secret will never expire.
Expires | bool | No | Determines if the secret expires. If this value is set, non null Expiration will be ignored. Defaults to true.
Description | string | No | Description for the client secret



```json
{
  "Expiration": "2019-05-31T14:57:08.6923968-07:00",
  "Expires": false,
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

 `ClientSecretResponse`

```json
{
  "Secret": "Secret",
  "Id": 0,
  "Expiration": "2019-05-31T14:57:08.692539-07:00",
  "Expires": false,
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

### Request

`PUT api/v1/Tenants/{tenantId}/ClientCredentialClients/{clientId}/Secrets/{secretId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
string clientId
```

Id of client

```csharp
[Required]
int32 secretId
```

secretId

```csharp
[FromBody]
[Required]
ClientSecretCreateOrUpdate clientSecretCreateOrUpdate
```

secretId

Property | Type | Required | Description 
 --- | --- | --- | ---
Expiration | DateTime | No | Expiration date for the client secret. If not provided the secret will never expire.
Expires | bool | No | Determines if the secret expires. If this value is set, non null Expiration will be ignored. Defaults to true.
Description | string | No | Description for the client secret



```json
{
  "Expiration": "2019-05-31T14:57:08.6970108-07:00",
  "Expires": false,
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

 `ClientSecret`

```json
{
  "Id": 0,
  "Expiration": "2019-05-31T14:57:08.6971447-07:00",
  "Expires": false,
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

`DELETE api/v1/Tenants/{tenantId}/ClientCredentialClients/{clientId}/Secrets/{secretId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[Required]
string clientId
```

Id of client

```csharp
[Required]
int32 secretId
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

