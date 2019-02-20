---
uid: identityClient
---

# Client

APIs for creating, getting, updating, and deleting Clients

## Properties

For HTTP requests and responses, the Client object has the following properties and JSON-serialized body: 

Property | Type | Descriptions
 --- | --- | ---
Enabled | bool | Specifies if client is enabled (defaults to true)
ClientId | string | Unique ID of the client
ClientSecrets | Secret[] | Client secrets - only relevant for flows that require a secret
RequireClientSecret | bool | If set to false, no client secret is needed to request tokens at the token endpoint (defaults to true)
ClientName | string | Client display name (used for logging and consent screen)
Description | string | Client description
ClientUri | string | URI to further information about client (used on consent screen)
LogoUri | string | URI to client logo (used on consent screen)
RequireConsent | bool | Specifies whether a consent screen is required (defaults to true)
AllowRememberConsent | bool | Specifies whether user can choose to store consent decisions (defaults to true)
AllowedGrantTypes | string[] | Specifies the allowed grant types (legal combinations of AuthorizationCode, Implicit, Hybrid, ResourceOwner, ClientCredentials).
AllowAccessTokensViaBrowser | bool | Controls whether access tokens are transmitted via the browser for this client (defaults to false). This can prevent accidental leakage of access tokens when multiple response types are allowed.
RedirectUris | string[] | Specifies allowed URIs to return tokens or authorization codes to
PostLogoutRedirectUris | string[] | Specifies allowed URIs to redirect to after logout
FrontChannelLogoutUri | string | Specifies logout URI at client for HTTP front-channel based logout.
FrontChannelLogoutSessionRequired | bool | Specifies is the user's session id should be sent to the FrontChannelLogoutUri. Defaults to true.
BackChannelLogoutUri | string | Specifies logout URI at client for HTTP back-channel based logout.
BackChannelLogoutSessionRequired | bool | Specifies is the user's session id should be sent to the BackChannelLogoutUri. Defaults to true.
AllowOfflineAccess | bool | Gets or sets a value indicating whether [allow offline access]. Defaults to false.
AllowedScopes | string[] | Specifies the api scopes that the client is allowed to request. If empty, the client can't access any scope
AlwaysIncludeUserClaimsInIdToken | bool | When requesting both an id token and access token, should the user claims always be added to the id token instead of requiring the client to use the user info endpoint. Defaults to false.
IdentityTokenLifetime | int32 | Lifetime of identity token in seconds (defaults to 300 seconds / 5 minutes)
AccessTokenLifetime | int32 | Lifetime of access token in seconds (defaults to 3600 seconds / 1 hour)
AuthorizationCodeLifetime | int32 | Lifetime of authorization code in seconds (defaults to 300 seconds / 5 minutes)
AbsoluteRefreshTokenLifetime | int32 | Maximum lifetime of a refresh token in seconds. Defaults to 2592000 seconds / 30 days
SlidingRefreshTokenLifetime | int32 | Sliding lifetime of a refresh token in seconds. Defaults to 1296000 seconds / 15 days
ConsentLifetime | optional: int32 | Lifetime of a user consent in seconds. Defaults to null (no expiration)
RefreshTokenUsage | TokenUsage | ReUse: the refresh token handle will stay the same when refreshing tokens OneTime: the refresh token handle will be updated when refreshing tokens
UpdateAccessTokenClaimsOnRefresh | bool | Gets or sets a value indicating whether the access token (and its claims) should be updated on a refresh token request. Defaults to false.
RefreshTokenExpiration | TokenExpiration | Absolute: the refresh token will expire on a fixed point in time (specified by the AbsoluteRefreshTokenLifetime) Sliding: when refreshing the token, the lifetime of the refresh token will be renewed (by the amount specified in SlidingRefreshTokenLifetime). The lifetime will not exceed AbsoluteRefreshTokenLifetime.
AccessTokenType | AccessTokenType | Specifies whether the access token is a reference token or a self contained JWT token (defaults to Jwt).
IdentityProviderRestrictions | string[] | Specifies which external IdPs can be used with this client (if list is empty all IdPs are allowed). Defaults to empty.
IncludeJwtId | bool | Gets or sets a value indicating whether JWT access tokens should include an identifier. Defaults to false.
Claims | Claim[] | Allows settings claims for the client (will be included in the access token).
AlwaysSendClientClaims | bool | Gets or sets a value indicating whether client claims should be always included in the access tokens - or only for client credentials flow. Defaults to false
ClientClaimsPrefix | string | Gets or sets a value to prefix it on client claim types. Defaults to client_.
PairWiseSubjectSalt | string | Subject salt to be used.
UserSsoLifetime | optional: int32 | The maximum duration (in seconds) since the last time the user authenticated.
UserCodeType | string | Gets or sets the type of the device flow user code.
DeviceCodeLifetime | int32 | Gets or sets the device code lifetime.
AllowedCorsOrigins | string[] | Gets or sets the allowed CORS origins for JavaScript clients.
Properties | string,string[] | Gets or sets the custom properties for the client.

### Serialized Model

```json
{
  "Enabled": true,
  "ClientId": "ClientId",
  "ClientSecrets": [
    {
      "Id": 0,
      "Description": "description",
      "Value": "Value",
      "Expiration": "2019-02-20T01:57:33.0731668-05:00",
      "Type": "Type"
    },
    {
      "Id": 0,
      "Description": "description",
      "Value": "Value",
      "Expiration": "2019-02-20T01:57:33.0733354-05:00",
      "Type": "Type"
    }
  ],
  "RequireClientSecret": true,
  "ClientName": "Name",
  "Description": "description",
  "ClientUri": "ClientUri",
  "LogoUri": "LogoUri",
  "RequireConsent": true,
  "AllowRememberConsent": true,
  "AllowedGrantTypes": [
    "String",
    "String"
  ],
  "AllowAccessTokensViaBrowser": false,
  "RedirectUris": [
    "String",
    "String"
  ],
  "PostLogoutRedirectUris": [
    "String",
    "String"
  ],
  "FrontChannelLogoutUri": "FrontChannelLogoutUri",
  "FrontChannelLogoutSessionRequired": true,
  "BackChannelLogoutUri": "BackChannelLogoutUri",
  "BackChannelLogoutSessionRequired": true,
  "AllowOfflineAccess": false,
  "AllowedScopes": [
    "String",
    "String"
  ],
  "AlwaysIncludeUserClaimsInIdToken": false,
  "IdentityTokenLifetime": 300,
  "AccessTokenLifetime": 3600,
  "AuthorizationCodeLifetime": 300,
  "AbsoluteRefreshTokenLifetime": 2592000,
  "SlidingRefreshTokenLifetime": 1296000,
  "ConsentLifetime": 0,
  "RefreshTokenUsage": 0,
  "UpdateAccessTokenClaimsOnRefresh": false,
  "RefreshTokenExpiration": 0,
  "AccessTokenType": 0,
  "IdentityProviderRestrictions": [
    "String",
    "String"
  ],
  "IncludeJwtId": false,
  "Claims": [
    {
      "Issuer": "Issuer",
      "OriginalIssuer": "OriginalIssuer",
      "Properties": {
        "String": "String"
      },
      "Subject": {
        "AuthenticationType": null,
        "IsAuthenticated": false,
        "Actor": null,
        "BootstrapContext": null,
        "Claims": [],
        "Label": "Label",
        "Name": null,
        "NameClaimType": "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name",
        "RoleClaimType": "http://schemas.microsoft.com/ws/2008/06/identity/claims/role"
      },
      "Type": "Type",
      "Value": "Value",
      "ValueType": "ValueType"
    },
    {
      "Issuer": "Issuer",
      "OriginalIssuer": "OriginalIssuer",
      "Properties": {
        "String": "String"
      },
      "Subject": {
        "AuthenticationType": null,
        "IsAuthenticated": false,
        "Actor": null,
        "BootstrapContext": null,
        "Claims": [],
        "Label": "Label",
        "Name": null,
        "NameClaimType": "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name",
        "RoleClaimType": "http://schemas.microsoft.com/ws/2008/06/identity/claims/role"
      },
      "Type": "Type",
      "Value": "Value",
      "ValueType": "ValueType"
    }
  ],
  "AlwaysSendClientClaims": false,
  "ClientClaimsPrefix": "ClientClaimsPrefix",
  "PairWiseSubjectSalt": "PairWiseSubjectSalt",
  "UserSsoLifetime": 0,
  "UserCodeType": "UserCodeType",
  "DeviceCodeLifetime": 300,
  "AllowedCorsOrigins": [
    "String",
    "String"
  ],
  "Properties": {
    "String": "String"
  }
}
```

***

## `Get Clients`

Get all clients for a tenant

### Request

`GET api/Tenants/{tenantId}/Client/`

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

 `List[Client]`

```json
[
  {
    "Enabled": true,
    "ClientId": "ClientId",
    "ClientSecrets": [
      {
        "Id": 0,
        "Description": "description",
        "Value": "Value",
        "Expiration": "2019-02-20T01:57:33.1150524-05:00",
        "Type": "Type"
      },
      {
        "Id": 0,
        "Description": "description",
        "Value": "Value",
        "Expiration": "2019-02-20T01:57:33.1150644-05:00",
        "Type": "Type"
      }
    ],
    "RequireClientSecret": true,
    "ClientName": "Name",
    "Description": "description",
    "ClientUri": "ClientUri",
    "LogoUri": "LogoUri",
    "RequireConsent": true,
    "AllowRememberConsent": true,
    "AllowedGrantTypes": [
      "String",
      "String"
    ],
    "AllowAccessTokensViaBrowser": false,
    "RedirectUris": [
      "String",
      "String"
    ],
    "PostLogoutRedirectUris": [
      "String",
      "String"
    ],
    "FrontChannelLogoutUri": "FrontChannelLogoutUri",
    "FrontChannelLogoutSessionRequired": true,
    "BackChannelLogoutUri": "BackChannelLogoutUri",
    "BackChannelLogoutSessionRequired": true,
    "AllowOfflineAccess": false,
    "AllowedScopes": [
      "String",
      "String"
    ],
    "AlwaysIncludeUserClaimsInIdToken": false,
    "IdentityTokenLifetime": 300,
    "AccessTokenLifetime": 3600,
    "AuthorizationCodeLifetime": 300,
    "AbsoluteRefreshTokenLifetime": 2592000,
    "SlidingRefreshTokenLifetime": 1296000,
    "ConsentLifetime": 0,
    "RefreshTokenUsage": 0,
    "UpdateAccessTokenClaimsOnRefresh": false,
    "RefreshTokenExpiration": 0,
    "AccessTokenType": 0,
    "IdentityProviderRestrictions": [
      "String",
      "String"
    ],
    "IncludeJwtId": false,
    "Claims": [
      {
        "Issuer": "Issuer",
        "OriginalIssuer": "OriginalIssuer",
        "Properties": {
          "String": "String"
        },
        "Subject": {
          "AuthenticationType": null,
          "IsAuthenticated": false,
          "Actor": null,
          "BootstrapContext": null,
          "Claims": [],
          "Label": "Label",
          "Name": null,
          "NameClaimType": "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name",
          "RoleClaimType": "http://schemas.microsoft.com/ws/2008/06/identity/claims/role"
        },
        "Type": "Type",
        "Value": "Value",
        "ValueType": "ValueType"
      },
      {
        "Issuer": "Issuer",
        "OriginalIssuer": "OriginalIssuer",
        "Properties": {
          "String": "String"
        },
        "Subject": {
          "AuthenticationType": null,
          "IsAuthenticated": false,
          "Actor": null,
          "BootstrapContext": null,
          "Claims": [],
          "Label": "Label",
          "Name": null,
          "NameClaimType": "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name",
          "RoleClaimType": "http://schemas.microsoft.com/ws/2008/06/identity/claims/role"
        },
        "Type": "Type",
        "Value": "Value",
        "ValueType": "ValueType"
      }
    ],
    "AlwaysSendClientClaims": false,
    "ClientClaimsPrefix": "ClientClaimsPrefix",
    "PairWiseSubjectSalt": "PairWiseSubjectSalt",
    "UserSsoLifetime": 0,
    "UserCodeType": "UserCodeType",
    "DeviceCodeLifetime": 300,
    "AllowedCorsOrigins": [
      "String",
      "String"
    ],
    "Properties": {
      "String": "String"
    }
  },
  {
    "Enabled": true,
    "ClientId": "ClientId",
    "ClientSecrets": [
      {
        "Id": 0,
        "Description": "description",
        "Value": "Value",
        "Expiration": "2019-02-20T01:57:33.1151752-05:00",
        "Type": "Type"
      },
      {
        "Id": 0,
        "Description": "description",
        "Value": "Value",
        "Expiration": "2019-02-20T01:57:33.1151826-05:00",
        "Type": "Type"
      }
    ],
    "RequireClientSecret": true,
    "ClientName": "Name",
    "Description": "description",
    "ClientUri": "ClientUri",
    "LogoUri": "LogoUri",
    "RequireConsent": true,
    "AllowRememberConsent": true,
    "AllowedGrantTypes": [
      "String",
      "String"
    ],
    "AllowAccessTokensViaBrowser": false,
    "RedirectUris": [
      "String",
      "String"
    ],
    "PostLogoutRedirectUris": [
      "String",
      "String"
    ],
    "FrontChannelLogoutUri": "FrontChannelLogoutUri",
    "FrontChannelLogoutSessionRequired": true,
    "BackChannelLogoutUri": "BackChannelLogoutUri",
    "BackChannelLogoutSessionRequired": true,
    "AllowOfflineAccess": false,
    "AllowedScopes": [
      "String",
      "String"
    ],
    "AlwaysIncludeUserClaimsInIdToken": false,
    "IdentityTokenLifetime": 300,
    "AccessTokenLifetime": 3600,
    "AuthorizationCodeLifetime": 300,
    "AbsoluteRefreshTokenLifetime": 2592000,
    "SlidingRefreshTokenLifetime": 1296000,
    "ConsentLifetime": 0,
    "RefreshTokenUsage": 0,
    "UpdateAccessTokenClaimsOnRefresh": false,
    "RefreshTokenExpiration": 0,
    "AccessTokenType": 0,
    "IdentityProviderRestrictions": [
      "String",
      "String"
    ],
    "IncludeJwtId": false,
    "Claims": [
      {
        "Issuer": "Issuer",
        "OriginalIssuer": "OriginalIssuer",
        "Properties": {
          "String": "String"
        },
        "Subject": {
          "AuthenticationType": null,
          "IsAuthenticated": false,
          "Actor": null,
          "BootstrapContext": null,
          "Claims": [],
          "Label": "Label",
          "Name": null,
          "NameClaimType": "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name",
          "RoleClaimType": "http://schemas.microsoft.com/ws/2008/06/identity/claims/role"
        },
        "Type": "Type",
        "Value": "Value",
        "ValueType": "ValueType"
      },
      {
        "Issuer": "Issuer",
        "OriginalIssuer": "OriginalIssuer",
        "Properties": {
          "String": "String"
        },
        "Subject": {
          "AuthenticationType": null,
          "IsAuthenticated": false,
          "Actor": null,
          "BootstrapContext": null,
          "Claims": [],
          "Label": "Label",
          "Name": null,
          "NameClaimType": "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name",
          "RoleClaimType": "http://schemas.microsoft.com/ws/2008/06/identity/claims/role"
        },
        "Type": "Type",
        "Value": "Value",
        "ValueType": "ValueType"
      }
    ],
    "AlwaysSendClientClaims": false,
    "ClientClaimsPrefix": "ClientClaimsPrefix",
    "PairWiseSubjectSalt": "PairWiseSubjectSalt",
    "UserSsoLifetime": 0,
    "UserCodeType": "UserCodeType",
    "DeviceCodeLifetime": 300,
    "AllowedCorsOrigins": [
      "String",
      "String"
    ],
    "Properties": {
      "String": "String"
    }
  }
]
```

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Tenant not found

#### 400

Missing or invalid inputs

#### 500

Internal server error
***

## `Get Client`

Get a client object

### Request

`GET api/Tenants/{tenantId}/Client/{clientId}`

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

 `Client`

```json
{
  "Enabled": true,
  "ClientId": "ClientId",
  "ClientSecrets": [
    {
      "Id": 0,
      "Description": "description",
      "Value": "Value",
      "Expiration": "2019-02-20T01:57:33.1156974-05:00",
      "Type": "Type"
    },
    {
      "Id": 0,
      "Description": "description",
      "Value": "Value",
      "Expiration": "2019-02-20T01:57:33.1157055-05:00",
      "Type": "Type"
    }
  ],
  "RequireClientSecret": true,
  "ClientName": "Name",
  "Description": "description",
  "ClientUri": "ClientUri",
  "LogoUri": "LogoUri",
  "RequireConsent": true,
  "AllowRememberConsent": true,
  "AllowedGrantTypes": [
    "String",
    "String"
  ],
  "AllowAccessTokensViaBrowser": false,
  "RedirectUris": [
    "String",
    "String"
  ],
  "PostLogoutRedirectUris": [
    "String",
    "String"
  ],
  "FrontChannelLogoutUri": "FrontChannelLogoutUri",
  "FrontChannelLogoutSessionRequired": true,
  "BackChannelLogoutUri": "BackChannelLogoutUri",
  "BackChannelLogoutSessionRequired": true,
  "AllowOfflineAccess": false,
  "AllowedScopes": [
    "String",
    "String"
  ],
  "AlwaysIncludeUserClaimsInIdToken": false,
  "IdentityTokenLifetime": 300,
  "AccessTokenLifetime": 3600,
  "AuthorizationCodeLifetime": 300,
  "AbsoluteRefreshTokenLifetime": 2592000,
  "SlidingRefreshTokenLifetime": 1296000,
  "ConsentLifetime": 0,
  "RefreshTokenUsage": 0,
  "UpdateAccessTokenClaimsOnRefresh": false,
  "RefreshTokenExpiration": 0,
  "AccessTokenType": 0,
  "IdentityProviderRestrictions": [
    "String",
    "String"
  ],
  "IncludeJwtId": false,
  "Claims": [
    {
      "Issuer": "Issuer",
      "OriginalIssuer": "OriginalIssuer",
      "Properties": {
        "String": "String"
      },
      "Subject": {
        "AuthenticationType": null,
        "IsAuthenticated": false,
        "Actor": null,
        "BootstrapContext": null,
        "Claims": [],
        "Label": "Label",
        "Name": null,
        "NameClaimType": "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name",
        "RoleClaimType": "http://schemas.microsoft.com/ws/2008/06/identity/claims/role"
      },
      "Type": "Type",
      "Value": "Value",
      "ValueType": "ValueType"
    },
    {
      "Issuer": "Issuer",
      "OriginalIssuer": "OriginalIssuer",
      "Properties": {
        "String": "String"
      },
      "Subject": {
        "AuthenticationType": null,
        "IsAuthenticated": false,
        "Actor": null,
        "BootstrapContext": null,
        "Claims": [],
        "Label": "Label",
        "Name": null,
        "NameClaimType": "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name",
        "RoleClaimType": "http://schemas.microsoft.com/ws/2008/06/identity/claims/role"
      },
      "Type": "Type",
      "Value": "Value",
      "ValueType": "ValueType"
    }
  ],
  "AlwaysSendClientClaims": false,
  "ClientClaimsPrefix": "ClientClaimsPrefix",
  "PairWiseSubjectSalt": "PairWiseSubjectSalt",
  "UserSsoLifetime": 0,
  "UserCodeType": "UserCodeType",
  "DeviceCodeLifetime": 300,
  "AllowedCorsOrigins": [
    "String",
    "String"
  ],
  "Properties": {
    "String": "String"
  }
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

## `Update Client With a Given ID`

Create a client

### Request

`POST api/Tenants/{tenantId}/Client/{clientId}`

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
[Required]
string secretDescription
```

Description of Client secret

```csharp
[FromQuery]
[Required]
string secretExpiration
```

Expiration of Client secret

```csharp
[FromBody]
[Required]
Client client
```

New Client object

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `ClientCredentialClientCreateDto`

```json
{
  "SecretDescription": "description",
  "SecretExpirationDate": "2019-02-20T01:57:33.1161762-05:00",
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

## `Update Client`

Update a client

### Request

`PUT api/Tenants/{tenantId}/Client/{clientId}`

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
Client client
```

New Client

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `Client`

```json
{
  "Enabled": true,
  "ClientId": "ClientId",
  "ClientSecrets": [
    {
      "Id": 0,
      "Description": "description",
      "Value": "Value",
      "Expiration": "2019-02-20T01:57:33.1179443-05:00",
      "Type": "Type"
    },
    {
      "Id": 0,
      "Description": "description",
      "Value": "Value",
      "Expiration": "2019-02-20T01:57:33.1179531-05:00",
      "Type": "Type"
    }
  ],
  "RequireClientSecret": true,
  "ClientName": "Name",
  "Description": "description",
  "ClientUri": "ClientUri",
  "LogoUri": "LogoUri",
  "RequireConsent": true,
  "AllowRememberConsent": true,
  "AllowedGrantTypes": [
    "String",
    "String"
  ],
  "AllowAccessTokensViaBrowser": false,
  "RedirectUris": [
    "String",
    "String"
  ],
  "PostLogoutRedirectUris": [
    "String",
    "String"
  ],
  "FrontChannelLogoutUri": "FrontChannelLogoutUri",
  "FrontChannelLogoutSessionRequired": true,
  "BackChannelLogoutUri": "BackChannelLogoutUri",
  "BackChannelLogoutSessionRequired": true,
  "AllowOfflineAccess": false,
  "AllowedScopes": [
    "String",
    "String"
  ],
  "AlwaysIncludeUserClaimsInIdToken": false,
  "IdentityTokenLifetime": 300,
  "AccessTokenLifetime": 3600,
  "AuthorizationCodeLifetime": 300,
  "AbsoluteRefreshTokenLifetime": 2592000,
  "SlidingRefreshTokenLifetime": 1296000,
  "ConsentLifetime": 0,
  "RefreshTokenUsage": 0,
  "UpdateAccessTokenClaimsOnRefresh": false,
  "RefreshTokenExpiration": 0,
  "AccessTokenType": 0,
  "IdentityProviderRestrictions": [
    "String",
    "String"
  ],
  "IncludeJwtId": false,
  "Claims": [
    {
      "Issuer": "Issuer",
      "OriginalIssuer": "OriginalIssuer",
      "Properties": {
        "String": "String"
      },
      "Subject": {
        "AuthenticationType": null,
        "IsAuthenticated": false,
        "Actor": null,
        "BootstrapContext": null,
        "Claims": [],
        "Label": "Label",
        "Name": null,
        "NameClaimType": "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name",
        "RoleClaimType": "http://schemas.microsoft.com/ws/2008/06/identity/claims/role"
      },
      "Type": "Type",
      "Value": "Value",
      "ValueType": "ValueType"
    },
    {
      "Issuer": "Issuer",
      "OriginalIssuer": "OriginalIssuer",
      "Properties": {
        "String": "String"
      },
      "Subject": {
        "AuthenticationType": null,
        "IsAuthenticated": false,
        "Actor": null,
        "BootstrapContext": null,
        "Claims": [],
        "Label": "Label",
        "Name": null,
        "NameClaimType": "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name",
        "RoleClaimType": "http://schemas.microsoft.com/ws/2008/06/identity/claims/role"
      },
      "Type": "Type",
      "Value": "Value",
      "ValueType": "ValueType"
    }
  ],
  "AlwaysSendClientClaims": false,
  "ClientClaimsPrefix": "ClientClaimsPrefix",
  "PairWiseSubjectSalt": "PairWiseSubjectSalt",
  "UserSsoLifetime": 0,
  "UserCodeType": "UserCodeType",
  "DeviceCodeLifetime": 300,
  "AllowedCorsOrigins": [
    "String",
    "String"
  ],
  "Properties": {
    "String": "String"
  }
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

## `Delete Client`

Delete a client

### Request

`DELETE api/Tenants/{tenantId}/Client/{clientId}`

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

