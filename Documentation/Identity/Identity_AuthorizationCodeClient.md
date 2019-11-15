---
uid: identityAuthorizationCodeClient
---

# AuthorizationCodeClient

Authorization Code clients are used in Javascript/Browser (SPA) based applications or native
            mobile applications with the presence of a User.
            These clients are issued an ID. You can read more about these clients
            [here](https://github.com/osisoft/OSI-Samples-OCS/tree/master/basic_samples/Authentication#authorization-code-flow-with-pkce).
            Authorization Code clients are not issued secrets or refresh tokens.

## Properties

For HTTP requests and responses, the AuthorizationCodeClient object has the following properties and JSON-serialized body: 

Property | Type | Description
 --- | --- | ---
AllowedCorsOrigins | string[] | Gets or sets the values used by the default CORS policy service implementations to build a CORS policy for JavaScript clients.
RedirectUris | string[] | Gets or sets the allowed URIs to which return tokens or authorization codes can be returned. Wildcards are ignored. URIs must match exactly what you are redirecting to after login. If URIs do not match, the authentication process will fail with a bad_client error. Maximum 10 per client.
PostLogoutRedirectUris | string[] | Gets or sets allowed URIs to redirect to after logout. Wildcards are ignored. URIs must match exactly what you are redirecting to after logout. Maximum 10 for client.
ClientUri | string | Gets or sets URI to a page with information about client (used on consent screen).
LogoUri | string | Gets or sets URI to client logo (used on consent screen).
Id | string | Gets or sets client ID for this client. This ID should be a GUID.
Name | string | Gets or sets name of Client.
Enabled | bool | Gets or sets whether client is enabled. Client can be used for authentication if set to true. Client cannot be used for authentication if set to false.
AccessTokenLifetime | int32 | Gets or sets lifetime of access token issued for this client after authentication. Minimum 60 seconds. Maximum 3600 seconds. Defaults to 3600 seconds.
Tags | string[] | Gets or sets for OSIsoft internal use only.

### Serialized Model

```json
{
  "AllowedCorsOrigins": [
    "String",
    "String"
  ],
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
  "AccessTokenLifetime": 0,
  "Tags": [
    "String",
    "String"
  ]
}
```

***

## Authentication

All endpoints referenced in this documentation require authenticated access. Authorization header must be set to the access token you retrieve after a successful authentication request.

`Authorization: Bearer <token>`

Requests made without an access token or an invalid/expired token will fail with a 401 Unauthorized response.
Requests made with an access token which does not have the correct permissions (see security subsection on every endpoint) will fail with a 403 Forbidden.
Read [here](https://github.com/osisoft/OSI-Samples-OCS/tree/master/basic_samples/Authentication) on how to authenticate against OCS with the various clients and receive an access token in response.

## Error Handling

All responses will have an error message in the body. The exceptions are 200 responses and the 401 Unauthorized response. The error message will look as follows:

```json
{
    "OperationId": "1b2af18e-8b27-4f86-93e0-6caa3e59b90c", 
    "Error": "Error message.", 
    "Reason": "Reason that caused error.", 
    "Resolution": "Possible solution for the error." 
}
```

If and when contacting OSIsoft support about this error, please provide the OperationId.

## `Create an Authorization Code Client`

Create an Authorization Code flow Client. No Secret will be generated for this
            Client.

### Request

`POST api/v1/Tenants/{tenantId}/AuthorizationCodeClients`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[FromBody]
[Required]
AuthorizationCodeClient authorizationCodeClient
```

New AuthorizationCodeClient object.

Property | Type | Required | Description 
 --- | --- | --- | ---
AllowedCorsOrigins | string[] | No | Gets or sets the values used by the default CORS policy service implementations to build a            CORS policy for JavaScript clients.
RedirectUris | string[] | No | Gets or sets the allowed URIs to which return tokens or authorization codes can be returned.            Wildcards are ignored. URIs must match exactly what you are redirecting to            after login. If URIs do not match, the authentication process will fail            with a bad_client error.            Maximum 10 per client.
PostLogoutRedirectUris | string[] | No | Gets or sets allowed URIs to redirect to after logout. Wildcards are ignored.            URIs must match exactly what you are redirecting to after logout.            Maximum 10 for client.
ClientUri | string | No | Gets or sets URI to a page with information about client (used on consent screen).
LogoUri | string | No | Gets or sets URI to client logo (used on consent screen).
Id | string | No | Gets or sets client ID for this client. This ID should be a GUID.
Name | string | Yes | Gets or sets name of Client.
Enabled | bool | No | Gets or sets whether client is enabled. Client can be used for authentication            if set to true. Client cannot be used for authentication if set to false.
AccessTokenLifetime | int32 | No | Gets or sets lifetime of access token issued for this client after authentication.            Minimum 60 seconds. Maximum 3600 seconds. Defaults to 3600 seconds.
Tags | string[] | No | Gets or sets for OSIsoft internal use only.



```json
{
  "AllowedCorsOrigins": [
    "String",
    "String"
  ],
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
  "AccessTokenLifetime": 0,
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

Created.

##### Type:

 `AuthorizationCodeClient`

```json
{
  "AllowedCorsOrigins": [
    "String",
    "String"
  ],
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
  "AccessTokenLifetime": 0,
  "Tags": [
    "String",
    "String"
  ]
}
```

#### 400

Missing or invalid inputs, or Client limit exceeded.

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Tenant not found.

#### 405

Method not allowed at this base URL. Try the request again at the Global base URL.

#### 409

Client Id already exists.

#### 500

Internal server error.
***

## `Update an Authorization Code Client`

Update an Authorization Code Client. It can take up to one hour
            for update to manifest in the authentication process.

### Request

`PUT api/v1/Tenants/{tenantId}/AuthorizationCodeClients/{clientId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
string clientId
```

Id of Client.

```csharp
[FromBody]
[Required]
AuthorizationCodeClient authorizationCodeClient
```

Updated Authorization Code Client values. Properties that are not set or are null will not be changed.

Property | Type | Required | Description 
 --- | --- | --- | ---
AllowedCorsOrigins | string[] | No | Gets or sets the values used by the default CORS policy service implementations to build a            CORS policy for JavaScript clients.
RedirectUris | string[] | No | Gets or sets the allowed URIs to which return tokens or authorization codes can be returned.            Wildcards are ignored. URIs must match exactly what you are redirecting to            after login. If URIs do not match, the authentication process will fail            with a bad_client error.            Maximum 10 per client.
PostLogoutRedirectUris | string[] | No | Gets or sets allowed URIs to redirect to after logout. Wildcards are ignored.            URIs must match exactly what you are redirecting to after logout.            Maximum 10 for client.
ClientUri | string | No | Gets or sets URI to a page with information about client (used on consent screen).
LogoUri | string | No | Gets or sets URI to client logo (used on consent screen).
Id | string | No | Gets or sets client ID for this client. This ID should be a GUID.
Name | string | Yes | Gets or sets name of Client.
Enabled | bool | No | Gets or sets whether client is enabled. Client can be used for authentication            if set to true. Client cannot be used for authentication if set to false.
AccessTokenLifetime | int32 | No | Gets or sets lifetime of access token issued for this client after authentication.            Minimum 60 seconds. Maximum 3600 seconds. Defaults to 3600 seconds.
Tags | string[] | No | Gets or sets for OSIsoft internal use only.



```json
{
  "AllowedCorsOrigins": [
    "String",
    "String"
  ],
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
  "AccessTokenLifetime": 0,
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

Success.

##### Type:

 `AuthorizationCodeClient`

```json
{
  "AllowedCorsOrigins": [
    "String",
    "String"
  ],
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
  "AccessTokenLifetime": 0,
  "Tags": [
    "String",
    "String"
  ]
}
```

#### 401

Unauthorized.

#### 403

Forbidden.

#### 400

Missing or invalid inputs.

#### 404

Client or Tenant not found.

#### 405

Method not allowed at this base URL. Try the request again at the Global base URL.

#### 500

Internal server error.
***

## `Get an Authorization Code Client from Tenant`

Get an Authorization Code Client from Tenant.

### Request

`GET api/v1/Tenants/{tenantId}/AuthorizationCodeClients/{clientId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
string clientId
```

Id of Client.

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success.

##### Type:

 `AuthorizationCodeClient`

```json
{
  "AllowedCorsOrigins": [
    "String",
    "String"
  ],
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
  "AccessTokenLifetime": 0,
  "Tags": [
    "String",
    "String"
  ]
}
```

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Client or Tenant not found.

#### 500

Internal server error.
***

## `Get All Authorization Code Clients from Tenant`

Get all Authorization Code clients from a Tenant.
            Optionally, get a list of requested clients. Total number
            of clients in the Tenant set in the Total-Count header.

### Request

`GET api/v1/Tenants/{tenantId}/AuthorizationCodeClients`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[FromQuery]
[Optional]
[Default = ""]
string[] id
```

Unordered list of ids for all clients to get. Empty or whitespace Ids will be ignored.

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

Query to execute. Currently not supported.

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

Maximum number of clients to return.

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success.

##### Type:

 `List`

```json
[
  {
    "AllowedCorsOrigins": [
      "String",
      "String"
    ],
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
    "AccessTokenLifetime": 0,
    "Tags": [
      "String",
      "String"
    ]
  },
  {
    "AllowedCorsOrigins": [
      "String",
      "String"
    ],
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
    "AccessTokenLifetime": 0,
    "Tags": [
      "String",
      "String"
    ]
  }
]
```

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Tenant not found.

#### 500

Internal server error.
***

## `Get Total Count Authorization Code Clients from Tenant`

Return total number of Authorization Code clients in a Tenant.
            Optionally, check based on a list of requested clients. The
            value will be set in the Total-Count header. This endpoint
            is identical to the GET one but it does not return any objects
            in the body.

### Request

`HEAD api/v1/Tenants/{tenantId}/AuthorizationCodeClients`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[FromQuery]
[Optional]
[Default = ""]
string[] id
```

Unordered list of ids for all clients to get. Empty or whitespace Ids will be ignored.

```csharp
[FromQuery]
[Optional]
[Default = ""]
string[] tag
```

Only count Clients that have these tags.

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success.

##### Type:

 `Void`

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Client or Tenant not found.

#### 500

Internal server error.
***

## `Delete an Authorization Code Client`

Delete an Authorization Code Client. It can take up to one hour
            for deletion to manifest in the authentication process. Access
            tokens issued to this client will be valid until their expiration.

### Request

`DELETE api/v1/Tenants/{tenantId}/AuthorizationCodeClients/{clientId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
string clientId
```

Id of Client.

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 204

Deleted.

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Client or Tenant not found.

#### 405

Method not allowed at this base URL. Try the request again at the Global base URL.

#### 500

Internal server error.
***

## `Get Header for Authorization Code Client`

Validate that an Authorization Code Client exists in Tenant.

### Request

`HEAD api/v1/Tenants/{tenantId}/AuthorizationCodeClients/{clientId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
string clientId
```

Id of Client.

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success.

##### Type:

 `ClientCredentialClient`

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Client or Tenant not found.

#### 500

Internal server error.
***

