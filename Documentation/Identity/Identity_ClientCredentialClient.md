---
uid: identityClientCredentialClient
---

# ClientCredentialClient

APIs for creating, getting, updating, and deleting Client Credential Clients

## Properties

For HTTP requests and responses, the ClientCredentialClientDto object has the following properties and JSON-serialized body: 

Property | Type | Descriptions
 --- | --- | ---
RoleIds | string[] | List of Roles to be assigned to this client.
ClientId | string | Client ID for this Client
Name | string | Name of Client.
Enabled | optional: bool | Is Client Enabled

### Serialized Model

```json
{
  "RoleIds": [
    "String",
    "String"
  ],
  "ClientId": "ClientId",
  "Name": "Name",
  "Enabled": false
}
```

***

## `Create Client Credential Client`

Create a Client Credential flow Client

### Request

`POST api/Tenants/{tenantId}/ClientCredentialClient/`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[FromBody]
[Required]
ClientCredentialClientCreateDto clientCredentialClientCreateDto
```

New ClientCredentialClientCreateDto object

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 201

Created

##### Type:

 `ClientCredentialClientResponseDto`

```json
{
  "ClientSecret": "ClientSecret",
  "SecretId": 0,
  "SecretDescription": "description",
  "SecretExpirationDate": "2019-02-20T01:57:32.9770889-05:00",
  "RoleIds": [
    "String",
    "String"
  ],
  "ClientId": "ClientId",
  "Name": "Name",
  "Enabled": false
}
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

## `Update Client Credential Client`

Update a Client Credential Client

### Request

`PUT api/Tenants/{tenantId}/ClientCredentialClient/{clientId}`

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
ClientCredentialClientDto updatedClientCredentialClientDto
```

Updated Client Credential Client values

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `ClientCredentialClientDto`

```json
{
  "RoleIds": [
    "String",
    "String"
  ],
  "ClientId": "ClientId",
  "Name": "Name",
  "Enabled": false
}
```

#### 401

Unauthorized

#### 403

Forbidden

#### 400

Missing or invalid inputs

#### 404

Client or Tenant not found

#### 500

Internal server error
***

## `Get Client Credential Client`

Get a Client Credential Client

### Request

`GET api/Tenants/{tenantId}/ClientCredentialClient/{clientId}`

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

 `ClientCredentialClientDto`

```json
{
  "RoleIds": [
    "String",
    "String"
  ],
  "ClientId": "ClientId",
  "Name": "Name",
  "Enabled": false
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

## `Get All Client Credential Clients`

Get all Client Credential Clients

### Request

`GET api/Tenants/{tenantId}/ClientCredentialClient/`

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
- `Cluster Operator`
- `Cluster Support`

### Returns

#### 200

Success

##### Type:

 `List[ClientCredentialClientDto]`

```json
[
  {
    "RoleIds": [
      "String",
      "String"
    ],
    "ClientId": "ClientId",
    "Name": "Name",
    "Enabled": false
  },
  {
    "RoleIds": [
      "String",
      "String"
    ],
    "ClientId": "ClientId",
    "Name": "Name",
    "Enabled": false
  }
]
```

#### 207

Partial success.

##### Type:

 `MultiStatusResponseDto[IList[ClientCredentialClientDto]]`

```json
{
  "OperationId": "OperationId",
  "Error": "Error",
  "Reason": "Reason",
  "ChildErrors": [
    {
      "OperationId": "OperationId",
      "Error": "Error",
      "Reason": "Reason",
      "Resolution": "Resolution",
      "StatusCode": 0,
      "ModelId": {
        "String": "String"
      },
      "TenantId": "TenantId"
    },
    {
      "OperationId": "OperationId",
      "Error": "Error",
      "Reason": "Reason",
      "Resolution": "Resolution",
      "StatusCode": 0,
      "ModelId": {
        "String": "String"
      },
      "TenantId": "TenantId"
    }
  ],
  "Data": [
    {
      "RoleIds": [
        "String",
        "String"
      ],
      "ClientId": "ClientId",
      "Name": "Name",
      "Enabled": false
    },
    {
      "RoleIds": [
        "String",
        "String"
      ],
      "ClientId": "ClientId",
      "Name": "Name",
      "Enabled": false
    }
  ]
}
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

## `Delete Client Credential Client`

Delete a Client Credential Client

### Request

`DELETE api/Tenants/{tenantId}/ClientCredentialClient/{clientId}`

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

### Returns

#### 204

Deleted

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Client or Tenant not found

#### 500

Internal server error
***

