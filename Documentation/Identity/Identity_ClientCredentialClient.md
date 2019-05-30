---
uid: identityClientCredentialClient
---

# ClientCredentialClient

APIs for creating, getting, updating, and deleting Client Credential Clients

## Properties

For HTTP requests and responses, the ClientCredentialClient object has the following properties and JSON-serialized body: 

Property | Type | Required | Descriptions
 --- | --- | --- | ---
RoleIds | Guid[] | No | List of Roles to be assigned to this client.
Id | string | No | Client ID for this Client
Name | string | Yes | Name of Client.
Enabled | optional: bool | No | Is Client Enabled
Tags | string[] | No | For OSIsoft internal use only

### Serialized Model

```json
{
  "RoleIds": [
    "00000000-0000-0000-0000-000000000000",
    "00000000-0000-0000-0000-000000000000"
  ],
  "Id": "Id",
  "Name": "Name",
  "Enabled": false,
  "Tags": [
    "String",
    "String"
  ]
}
```

***

## `Create Client Credential Client`

Create a Client Credential flow Client

### Request

`POST api/v1/Tenants/{tenantId}/ClientCredentialClients`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[FromBody]
[Required]
ClientCredentialClientCreate clientCredentialClientCreate
```

New ClientCredentialClientCreate object

Property | Type | Required | Description 
 --- | --- | --- | ---
SecretDescription | string | No | Description for the initial secret for the client.
SecretExpirationDate | optional: DateTime | No | Expiration date for the initial secret for the client.
RoleIds | Guid[] | No | List of Roles to be assigned to this client.
Id | string | No | Client ID for this Client
Name | string | Yes | Name of Client.
Enabled | optional: bool | No | Is Client Enabled
Tags | string[] | No | For OSIsoft internal use only



```json
{
  "SecretDescription": "description",
  "SecretExpirationDate": "2019-05-30T10:23:28.0754159-07:00",
  "RoleIds": [
    "00000000-0000-0000-0000-000000000000",
    "00000000-0000-0000-0000-000000000000"
  ],
  "Id": "Id",
  "Name": "Name",
  "Enabled": false,
  "Tags": [
    "String",
    "String"
  ]
}
```

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 201

Created

##### Type:

 `ClientResponse[ClientCredentialClient]`

```json
{
  "Secret": "Secret",
  "Id": 0,
  "Description": "description",
  "ExpirationDate": "2019-05-30T10:23:28.0786212-07:00",
  "Client": {
    "RoleIds": [
      "00000000-0000-0000-0000-000000000000",
      "00000000-0000-0000-0000-000000000000"
    ],
    "Id": "Id",
    "Name": "Name",
    "Enabled": false,
    "Tags": [
      "String",
      "String"
    ]
  }
}
```

#### 400

Missing or invalid inputs, or Client limit exceeded.

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Tenant not found

#### 409

Client Id already exists

#### 500

Internal server error
***

## `Update Client Credential Client`

Update a Client Credential Client

### Request

`PUT api/v1/Tenants/{tenantId}/ClientCredentialClients/{clientId}`

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
ClientCredentialClient updatedClientCredentialClient
```

Updated Client Credential Client values

Property | Type | Required | Description 
 --- | --- | --- | ---
RoleIds | Guid[] | No | List of Roles to be assigned to this client.
Id | string | No | Client ID for this Client
Name | string | Yes | Name of Client.
Enabled | optional: bool | No | Is Client Enabled
Tags | string[] | No | For OSIsoft internal use only



```json
{
  "RoleIds": [
    "00000000-0000-0000-0000-000000000000",
    "00000000-0000-0000-0000-000000000000"
  ],
  "Id": "Id",
  "Name": "Name",
  "Enabled": false,
  "Tags": [
    "String",
    "String"
  ]
}
```

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `ClientCredentialClient`

```json
{
  "RoleIds": [
    "00000000-0000-0000-0000-000000000000",
    "00000000-0000-0000-0000-000000000000"
  ],
  "Id": "Id",
  "Name": "Name",
  "Enabled": false,
  "Tags": [
    "String",
    "String"
  ]
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

`GET api/v1/Tenants/{tenantId}/ClientCredentialClients/{clientId}`

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
- `Account Member`

### Returns

#### 200

Success

##### Type:

 `ClientCredentialClient`

```json
{
  "RoleIds": [
    "00000000-0000-0000-0000-000000000000",
    "00000000-0000-0000-0000-000000000000"
  ],
  "Id": "Id",
  "Name": "Name",
  "Enabled": false,
  "Tags": [
    "String",
    "String"
  ]
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

`GET api/v1/Tenants/{tenantId}/ClientCredentialClients`

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
string[] tag
```

Only return Clients that have these tags.

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
- `Account Member`

### Returns

#### 200

Success

##### Type:

 `List[ClientCredentialClient]`

```json
[
  {
    "RoleIds": [
      "00000000-0000-0000-0000-000000000000",
      "00000000-0000-0000-0000-000000000000"
    ],
    "Id": "Id",
    "Name": "Name",
    "Enabled": false,
    "Tags": [
      "String",
      "String"
    ]
  },
  {
    "RoleIds": [
      "00000000-0000-0000-0000-000000000000",
      "00000000-0000-0000-0000-000000000000"
    ],
    "Id": "Id",
    "Name": "Name",
    "Enabled": false,
    "Tags": [
      "String",
      "String"
    ]
  }
]
```

#### 207

Partial success.

##### Type:

 `MultiStatusResponse[ClientCredentialClient]`

```json
{
  "OperationId": "OperationId",
  "Error": "Error",
  "Reason": "Reason",
  "ChildErrors": [
    {
      "StatusCode": 0,
      "ModelId": "ModelId",
      "OperationId": "OperationId",
      "Error": "Error",
      "Reason": "Reason",
      "Resolution": "Resolution"
    },
    {
      "StatusCode": 0,
      "ModelId": "ModelId",
      "OperationId": "OperationId",
      "Error": "Error",
      "Reason": "Reason",
      "Resolution": "Resolution"
    }
  ],
  "Data": [
    {
      "RoleIds": [
        "00000000-0000-0000-0000-000000000000",
        "00000000-0000-0000-0000-000000000000"
      ],
      "Id": "Id",
      "Name": "Name",
      "Enabled": false,
      "Tags": [
        "String",
        "String"
      ]
    },
    {
      "RoleIds": [
        "00000000-0000-0000-0000-000000000000",
        "00000000-0000-0000-0000-000000000000"
      ],
      "Id": "Id",
      "Name": "Name",
      "Enabled": false,
      "Tags": [
        "String",
        "String"
      ]
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

`DELETE api/v1/Tenants/{tenantId}/ClientCredentialClients/{clientId}`

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

## `Create Client Credential Client`

Create a Client Credential flow Client

### Request

`POST api/v1/Tenants/{tenantId}/ClientCredentialClients`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[FromBody]
[Required]
ClientCredentialClientCreate clientCredentialClientCreate
```

New ClientCredentialClientCreate object

Property | Type | Required | Description 
 --- | --- | --- | ---
SecretDescription | string | No | 
SecretExpirationDate | optional: DateTime | No | 
RoleIds | Guid[] | No | 
ClientId | string | No | 
Id | string | No | 
Name | string | Yes | 
Enabled | optional: bool | No | 
Tags | string[] | No | 



```json
{
  "SecretDescription": "description",
  "SecretExpirationDate": "2019-05-30T10:23:28.0979619-07:00",
  "RoleIds": [
    "00000000-0000-0000-0000-000000000000",
    "00000000-0000-0000-0000-000000000000"
  ],
  "ClientId": "ClientId",
  "Id": "Id",
  "Name": "Name",
  "Enabled": false,
  "Tags": [
    "String",
    "String"
  ]
}
```

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 201

Created

##### Type:

 `VPreview.ClientCredentialClientResponse`

```json
{
  "ClientSecret": "ClientSecret",
  "SecretId": "SecretId",
  "SecretDescription": "description",
  "SecretExpirationDate": "2019-05-30T10:23:28.1019375-07:00",
  "RoleIds": [
    "00000000-0000-0000-0000-000000000000",
    "00000000-0000-0000-0000-000000000000"
  ],
  "ClientId": "ClientId",
  "Id": "Id",
  "Name": "Name",
  "Enabled": false,
  "Tags": [
    "String",
    "String"
  ]
}
```

#### 400

Missing or invalid inputs, or Client limit exceeded.

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Tenant not found

#### 409

Client Id already exists

#### 500

Internal server error
***

