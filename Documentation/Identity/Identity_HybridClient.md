---
uid: identityHybridClient
---

# HybridClient

APIs for creating, getting, updating, and deleting Hybrid Clients

## Properties

For HTTP requests and responses, the HybridClient object has the following properties and JSON-serialized body: 

Property | Type | Descriptions
 --- | --- | --- | ---
AllowOfflineAccess | bool | Specifies whether this client can request refresh tokens, by providing the *offline_access* scopes.
AllowAccessTokensViaBrowser | bool | Specifies whether this HybridClient is allowed to receive access tokens via the browser. This is useful to harden flows that allow multiple response types (e.g. by disallowing a hybrid flow client that is supposed to use code *id_token* to add the *token* response type, thus leaking the token to the browser).
RedirectUris | string[] | Specifies the allowed URIs to return tokens or authorization codes to.
PostLogoutRedirectUris | string[] | Specifies allowed URIs to redirect to after logout.
ClientUri | string | URI to a page with information about client (used on consent screen).
LogoUri | string | URI to client logo (used on consent screen).
Id | string | Client ID for this Client
Name | string | Name of Client.
Enabled | bool | Is Client Enabled
Tags | string[] | For OSIsoft internal use only

### Serialized Model

```json
{
  "AllowOfflineAccess": false,
  "AllowAccessTokensViaBrowser": false,
  "RedirectUris": [
    "String",
    "String"
  ],
  "PostLogoutRedirectUris": [
    "String",
    "String"
  ],
  "ClientUri": "ClientUri",
  "LogoUri": "LogoUri",
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

## `Create Hybrid Client`

Create a Hybrid flow Client

### Request

`POST api/v1/Tenants/{tenantId}/HybridClients`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[FromBody]
[Required]
HybridClientCreate hybridClientCreate
```

New HybridClientCreate object

Property | Type | Required | Description 
 --- | --- | --- | ---
SecretDescription | string | No | Description for the initial secret for the client.
SecretExpirationDate | DateTime | No | Expiration date for the initial secret for the client.
AllowOfflineAccess | bool | No | Specifies whether this client can request refresh tokens, by providing the *offline_access* scopes.
AllowAccessTokensViaBrowser | bool | No | Specifies whether this HybridClient is allowed to receive access tokens via the browser.            This is useful to harden flows that allow multiple response types (e.g. by disallowing a hybrid flow            client that is supposed to use code *id_token* to add the *token* response type, thus            leaking the token to the browser).
RedirectUris | string[] | No | Specifies the allowed URIs to return tokens or authorization codes to.
PostLogoutRedirectUris | string[] | No | Specifies allowed URIs to redirect to after logout.
ClientUri | string | No | URI to a page with information about client (used on consent screen).
LogoUri | string | No | URI to client logo (used on consent screen).
Id | string | No | Client ID for this Client
Name | string | Yes | Name of Client.
Enabled | bool | No | Is Client Enabled
Tags | string[] | No | For OSIsoft internal use only



```json
{
  "SecretDescription": "description",
  "SecretExpirationDate": "2019-05-31T14:57:08.5227228-07:00",
  "AllowOfflineAccess": false,
  "AllowAccessTokensViaBrowser": false,
  "RedirectUris": [
    "String",
    "String"
  ],
  "PostLogoutRedirectUris": [
    "String",
    "String"
  ],
  "ClientUri": "ClientUri",
  "LogoUri": "LogoUri",
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

 `ClientResponse`

```json
{
  "Secret": "Secret",
  "Id": 0,
  "Description": "description",
  "ExpirationDate": "2019-05-31T14:57:08.533641-07:00",
  "Client": {
    "AllowOfflineAccess": false,
    "AllowAccessTokensViaBrowser": false,
    "RedirectUris": [
      "String",
      "String"
    ],
    "PostLogoutRedirectUris": [
      "String",
      "String"
    ],
    "ClientUri": "ClientUri",
    "LogoUri": "LogoUri",
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

Client Limit exceeded

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

## `Update Hybrid Client`

Update a Hybrid Client

### Request

`PUT api/v1/Tenants/{tenantId}/HybridClients/{clientId}`

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
HybridClient hybridClient
```

Updated Hybrid Client values

Property | Type | Required | Description 
 --- | --- | --- | ---
AllowOfflineAccess | bool | No | Specifies whether this client can request refresh tokens, by providing the *offline_access* scopes.
AllowAccessTokensViaBrowser | bool | No | Specifies whether this HybridClient is allowed to receive access tokens via the browser.            This is useful to harden flows that allow multiple response types (e.g. by disallowing a hybrid flow            client that is supposed to use code *id_token* to add the *token* response type, thus            leaking the token to the browser).
RedirectUris | string[] | No | Specifies the allowed URIs to return tokens or authorization codes to.
PostLogoutRedirectUris | string[] | No | Specifies allowed URIs to redirect to after logout.
ClientUri | string | No | URI to a page with information about client (used on consent screen).
LogoUri | string | No | URI to client logo (used on consent screen).
Id | string | No | Client ID for this Client. Must be same as the one in the route. Must be the same as the Id in the route.
Name | string | Yes | Name of Client.
Enabled | bool | No | Is Client Enabled
Tags | string[] | No | For OSIsoft internal use only



```json
{
  "AllowOfflineAccess": false,
  "AllowAccessTokensViaBrowser": false,
  "RedirectUris": [
    "String",
    "String"
  ],
  "PostLogoutRedirectUris": [
    "String",
    "String"
  ],
  "ClientUri": "ClientUri",
  "LogoUri": "LogoUri",
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

 `HybridClient`

```json
{
  "AllowOfflineAccess": false,
  "AllowAccessTokensViaBrowser": false,
  "RedirectUris": [
    "String",
    "String"
  ],
  "PostLogoutRedirectUris": [
    "String",
    "String"
  ],
  "ClientUri": "ClientUri",
  "LogoUri": "LogoUri",
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

## `Get Hybrid Client`

Get a Hybrid Client

### Request

`GET api/v1/Tenants/{tenantId}/HybridClients/{clientId}`

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

#### 200

Success

##### Type:

 `HybridClient`

```json
{
  "AllowOfflineAccess": false,
  "AllowAccessTokensViaBrowser": false,
  "RedirectUris": [
    "String",
    "String"
  ],
  "PostLogoutRedirectUris": [
    "String",
    "String"
  ],
  "ClientUri": "ClientUri",
  "LogoUri": "LogoUri",
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

## `Get All Hybrid Clients`

Get all Hybrid Clients

### Request

`GET api/v1/Tenants/{tenantId}/HybridClients`

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

### Returns

#### 200

Success

##### Type:

 `List`

```json
[
  {
    "AllowOfflineAccess": false,
    "AllowAccessTokensViaBrowser": false,
    "RedirectUris": [
      "String",
      "String"
    ],
    "PostLogoutRedirectUris": [
      "String",
      "String"
    ],
    "ClientUri": "ClientUri",
    "LogoUri": "LogoUri",
    "Id": "Id",
    "Name": "Name",
    "Enabled": false,
    "Tags": [
      "String",
      "String"
    ]
  },
  {
    "AllowOfflineAccess": false,
    "AllowAccessTokensViaBrowser": false,
    "RedirectUris": [
      "String",
      "String"
    ],
    "PostLogoutRedirectUris": [
      "String",
      "String"
    ],
    "ClientUri": "ClientUri",
    "LogoUri": "LogoUri",
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

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Tenant not found

#### 500

Internal server error
***

## `Delete Hybrid Client`

Delete an Hybrid Client

### Request

`DELETE api/v1/Tenants/{tenantId}/HybridClients/{clientId}`

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

