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

 `List[ClientSecret]`

```json
[
  {
    "Id": 0,
    "Expiration": "2019-05-30T11:29:02.2732158-07:00",
    "Expires": false,
    "Description": "description"
  },
  {
    "Id": 0,
    "Expiration": "2019-05-30T11:29:02.2735937-07:00",
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
  "Expiration": "2019-05-30T11:29:02.2785955-07:00",
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
Expiration | optional: DateTime | No | Expiration date for the client secret
Expires | optional: bool | No | Determines if the secret expires. If this value is set, non null Expiration will be ignored. Defaults to true.
Description | string | No | Description for the client secret



```json
{
  "Expiration": "2019-05-30T11:29:02.2808625-07:00",
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
  "Expiration": "2019-05-30T11:29:02.2866829-07:00",
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
            Only Secret Description and Secret Expiration Date can be updated

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
Expiration | optional: DateTime | No | Expiration date for the client secret
Expires | optional: bool | No | Determines if the secret expires. If this value is set, non null Expiration will be ignored. Defaults to true.
Description | string | No | Description for the client secret



```json
{
  "Expiration": "2019-05-30T11:29:02.2919479-07:00",
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
  "Expiration": "2019-05-30T11:29:02.2920694-07:00",
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

 `List[ClientSecret]`

```json
[
  {
    "Id": 0,
    "Expiration": "2019-05-30T11:29:02.4143088-07:00",
    "Expires": false,
    "Description": "description"
  },
  {
    "Id": 0,
    "Expiration": "2019-05-30T11:29:02.4143307-07:00",
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
  "Expiration": "2019-05-30T11:29:02.4159896-07:00",
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
Expiration | optional: DateTime | No | Expiration date for the client secret
Expires | optional: bool | No | Determines if the secret expires. If this value is set, non null Expiration will be ignored. Defaults to true.
Description | string | No | Description for the client secret



```json
{
  "Expiration": "2019-05-30T11:29:02.4197033-07:00",
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
  "Expiration": "2019-05-30T11:29:02.4198563-07:00",
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
            Only Secret Description and Secret Expiration Date can be updated

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
Expiration | optional: DateTime | No | Expiration date for the client secret
Expires | optional: bool | No | Determines if the secret expires. If this value is set, non null Expiration will be ignored. Defaults to true.
Description | string | No | Description for the client secret



```json
{
  "Expiration": "2019-05-30T11:29:02.4216581-07:00",
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
  "Expiration": "2019-05-30T11:29:02.4217562-07:00",
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

