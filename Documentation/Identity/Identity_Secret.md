---
uid: identitySecret
---

# Secret

APIs for creating, getting, updating, and deleting Hybrid Clients

## Properties

For HTTP requests and responses, the Secret object has the following properties and JSON-serialized body: 

Property | Type | Descriptions
 --- | --- | ---
Id | int32 | Gets the Id for the secret. Note: This is currently an auto-incremented integer
Description | string | Gets or sets the description.
Value | string | Gets or sets the value.
Expiration | optional: DateTime | Gets or sets the expiration.
Type | string | Gets or sets the type of the client secret.

### Serialized Model

```json
{
  "Id": 0,
  "Description": "description",
  "Value": "Value",
  "Expiration": "2019-02-20T01:57:33.1368262-05:00",
  "Type": "Type"
}
```

***

## `Get Client Secrets`

Get all secrets for a client

### Request

`GET api/Tenants/{tenantId}/Clients/{clientId}/Secret/`

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

### Security

Allowed for these roles:

- `Account Administrator`
- `Cluster Operator`
- `Cluster Support`

### Returns

#### 200

Success

##### Type:

 `List[Secret]`

```json
[
  {
    "Id": 0,
    "Description": "description",
    "Value": "Value",
    "Expiration": "2019-02-20T01:57:33.1374782-05:00",
    "Type": "Type"
  },
  {
    "Id": 0,
    "Description": "description",
    "Value": "Value",
    "Expiration": "2019-02-20T01:57:33.1374951-05:00",
    "Type": "Type"
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

## `Get Client Secret`

Get a specific client secret

### Request

`GET api/Tenants/{tenantId}/Clients/{clientId}/Secret/{secretId}`

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
- `Cluster Operator`
- `Cluster Support`

### Returns

#### 200

Success

##### Type:

 `Secret`

```json
{
  "Id": 0,
  "Description": "description",
  "Value": "Value",
  "Expiration": "2019-02-20T01:57:33.1380568-05:00",
  "Type": "Type"
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

## `Add Client Secret`

Add a new secret for a client

### Request

`POST api/Tenants/{tenantId}/Clients/{clientId}/Secret/`

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
ClientSecretDto clientSecretDto
```



### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 201

Created

##### Type:

 `List[Secret]`

```json
[
  {
    "Id": 0,
    "Description": "description",
    "Value": "Value",
    "Expiration": "2019-02-20T01:57:33.1385802-05:00",
    "Type": "Type"
  },
  {
    "Id": 0,
    "Description": "description",
    "Value": "Value",
    "Expiration": "2019-02-20T01:57:33.1385943-05:00",
    "Type": "Type"
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

Update a client secret (Only Secret Description and Secret Expiration Date could be updated)

### Request

`PUT api/Tenants/{tenantId}/Clients/{clientId}/Secret/{secretId}`

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
ClientSecretDto secretUpdate
```

secretId

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `Secret`

```json
{
  "Id": 0,
  "Description": "description",
  "Value": "Value",
  "Expiration": "2019-02-20T01:57:33.1391229-05:00",
  "Type": "Type"
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

## `Delete Client Secret`

Delete a secret from a client

### Request

`DELETE api/Tenants/{tenantId}/Clients/{clientId}/Secret/{secretId}`

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

 `List[Secret]`

```json
[
  {
    "Id": 0,
    "Description": "description",
    "Value": "Value",
    "Expiration": "2019-02-20T01:57:33.139657-05:00",
    "Type": "Type"
  },
  {
    "Id": 0,
    "Description": "description",
    "Value": "Value",
    "Expiration": "2019-02-20T01:57:33.1396704-05:00",
    "Type": "Type"
  }
]
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

