---
uid: identityClient
---

# Client

CRUD operations on Client

## Properties

For HTTP requests and responses, the Client object has the following properties and JSON-serialized body: 

Property | Type | Descriptions
 --- | --- | ---
bool | Enabled | Specifies if client is enabled (defaults to true)
string | ClientId | Unique ID of the client
Secret[] | ClientSecrets | Client secrets - only relevant for flows that require a secret
bool | RequireClientSecret | If set to false, no client secret is needed to request tokens at the token endpoint (defaults to true)
string | ClientName | Client display name (used for logging and consent screen)
string | Description | Client description
string | ClientUri | URI to further information about client (used on consent screen)
string | LogoUri | URI to client logo (used on consent screen)
bool | RequireConsent | Specifies whether a consent screen is required (defaults to true)
bool | AllowRememberConsent | Specifies whether user can choose to store consent decisions (defaults to true)
string[] | AllowedGrantTypes | Specifies the allowed grant types (legal combinations of AuthorizationCode, Implicit, Hybrid, ResourceOwner,
            ClientCredentials).
bool | AllowAccessTokensViaBrowser | Controls whether access tokens are transmitted via the browser for this client (defaults to false).
            This can prevent accidental leakage of access tokens when multiple response types are allowed.
string[] | RedirectUris | Specifies allowed URIs to return tokens or authorization codes to
string[] | PostLogoutRedirectUris | Specifies allowed URIs to redirect to after logout
string | FrontChannelLogoutUri | Specifies logout URI at client for HTTP front-channel based logout.
bool | FrontChannelLogoutSessionRequired | Specifies is the user's session id should be sent to the FrontChannelLogoutUri. Defaults to true.
string | BackChannelLogoutUri | Specifies logout URI at client for HTTP back-channel based logout.
bool | BackChannelLogoutSessionRequired | Specifies is the user's session id should be sent to the BackChannelLogoutUri. Defaults to true.
bool | AllowOfflineAccess | Gets or sets a value indicating whether [allow offline access]. Defaults to false.
string[] | AllowedScopes | Specifies the api scopes that the client is allowed to request. If empty, the client can't access any scope
bool | AlwaysIncludeUserClaimsInIdToken | When requesting both an id token and access token, should the user claims always be added to the id token instead
            of requiring the client to use the user info endpoint.
            Defaults to false.
int32 | IdentityTokenLifetime | Lifetime of identity token in seconds (defaults to 300 seconds / 5 minutes)
int32 | AccessTokenLifetime | Lifetime of access token in seconds (defaults to 3600 seconds / 1 hour)
int32 | AuthorizationCodeLifetime | Lifetime of authorization code in seconds (defaults to 300 seconds / 5 minutes)
int32 | AbsoluteRefreshTokenLifetime | Maximum lifetime of a refresh token in seconds. Defaults to 2592000 seconds / 30 days
int32 | SlidingRefreshTokenLifetime | Sliding lifetime of a refresh token in seconds. Defaults to 1296000 seconds / 15 days
optional: int32 | ConsentLifetime | Lifetime of a user consent in seconds. Defaults to null (no expiration)
TokenUsage | RefreshTokenUsage | ReUse: the refresh token handle will stay the same when refreshing tokens
            OneTime: the refresh token handle will be updated when refreshing tokens
bool | UpdateAccessTokenClaimsOnRefresh | Gets or sets a value indicating whether the access token (and its claims) should be updated on a refresh token
            request.
            Defaults to false.
TokenExpiration | RefreshTokenExpiration | Absolute: the refresh token will expire on a fixed point in time (specified by the AbsoluteRefreshTokenLifetime)
            Sliding: when refreshing the token, the lifetime of the refresh token will be renewed (by the amount specified in
            SlidingRefreshTokenLifetime). The lifetime will not exceed AbsoluteRefreshTokenLifetime.
AccessTokenType | AccessTokenType | Specifies whether the access token is a reference token or a self contained JWT token (defaults to Jwt).
string[] | IdentityProviderRestrictions | Specifies which external IdPs can be used with this client (if list is empty all IdPs are allowed). Defaults to
            empty.
bool | IncludeJwtId | Gets or sets a value indicating whether JWT access tokens should include an identifier. Defaults to false.
Claim[] | Claims | Allows settings claims for the client (will be included in the access token).
bool | AlwaysSendClientClaims | Gets or sets a value indicating whether client claims should be always included in the access tokens - or only for
            client credentials flow.
            Defaults to false
string | ClientClaimsPrefix | Gets or sets a value to prefix it on client claim types. Defaults to client_.
string | PairWiseSubjectSalt | Subject salt to be used.
optional: int32 | UserSsoLifetime | The maximum duration (in seconds) since the last time the user authenticated.
string | UserCodeType | Gets or sets the type of the device flow user code.
int32 | DeviceCodeLifetime | Gets or sets the device code lifetime.
string[] | AllowedCorsOrigins | Gets or sets the allowed CORS origins for JavaScript clients.
string,string[] | Properties | Gets or sets the custom properties for the client.

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
      "Expiration": "2019-02-05T19:11:14.5823992-08:00",
      "Type": "Type"
    },
    {
      "Id": 0,
      "Description": "description",
      "Value": "Value",
      "Expiration": "2019-02-05T19:11:14.5851253-08:00",
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

`GET api/Tenant/{tenantId}/Clients`

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

Number of clients to skip. From query.

```csharp
int32 count [FromQuery] [Optional] [Default = 100]
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
        "Expiration": "2019-02-05T19:11:14.6874061-08:00",
        "Type": "Type"
      },
      {
        "Id": 0,
        "Description": "description",
        "Value": "Value",
        "Expiration": "2019-02-05T19:11:14.6874361-08:00",
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
        "Expiration": "2019-02-05T19:11:14.6877358-08:00",
        "Type": "Type"
      },
      {
        "Id": 0,
        "Description": "description",
        "Value": "Value",
        "Expiration": "2019-02-05T19:11:14.6877662-08:00",
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

`GET api/Tenant/{tenantId}/Clients/{clientId}`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string clientId [FromRoute] [Required] [No-Default]
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
      "Expiration": "2019-02-05T19:11:14.6886929-08:00",
      "Type": "Type"
    },
    {
      "Id": 0,
      "Description": "description",
      "Value": "Value",
      "Expiration": "2019-02-05T19:11:14.6887084-08:00",
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

## `Create Client`

Create a client
            This method is obsolete, please use one of the following instead:
            {tenantId}/Clients/ClientCredential
            {tenantId}/Clients/Implicit
            {tenantId}/Clients/Hybrid

### Request

`POST api/Tenant/{tenantId}/Clients`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
ClientCredentialClientCreateDto clientCredentialClientCreateDto [FromBody] [Required] [No-Default]
```

New `ClientCredentialClientCreateDto <ClientCredentialClientCreateDto>` object

```json
{
  "SecretDescription": "description",
  "SecretExpirationDate": "2019-02-05T19:11:14.7233195-08:00",
  "RoleIds": [
    "String",
    "String"
  ],
  "Name": "Name",
  "Enabled": false,
  "AllowAccessTokensViaBrowser": false,
  "ClientUri": "ClientUri",
  "LogoUri": "LogoUri"
}
```

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `ClientCredentialClientResponseDto`

```json
{
  "Name": "Name",
  "ClientId": "ClientId",
  "ClientSecret": "ClientSecret",
  "SecretExpirationDate": "2019-02-05T19:11:14.7317775-08:00",
  "SecretDescription": "description",
  "SecretId": 0
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

## `Create Client Credential Client`

Create a Client Credential flow `Client <Client>`

### Request

`POST api/Tenant/{tenantId}/Clients/ClientCredential`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
ClientCredentialClientCreateDto clientCredentialClientCreateDto [FromBody] [Required] [No-Default]
```

New `ClientCredentialClientCreateDto <ClientCredentialClientCreateDto>` object

```json
{
  "SecretDescription": "description",
  "SecretExpirationDate": "2019-02-05T19:11:14.7372074-08:00",
  "RoleIds": [
    "String",
    "String"
  ],
  "Name": "Name",
  "Enabled": false,
  "AllowAccessTokensViaBrowser": false,
  "ClientUri": "ClientUri",
  "LogoUri": "LogoUri"
}
```

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `ClientCredentialClientResponseDto`

```json
{
  "Name": "Name",
  "ClientId": "ClientId",
  "ClientSecret": "ClientSecret",
  "SecretExpirationDate": "2019-02-05T19:11:14.7374743-08:00",
  "SecretDescription": "description",
  "SecretId": 0
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

## `Create Implicit Client`

Create an Implicit flow `Client <Client>`

### Request

`POST api/Tenant/{tenantId}/Clients/Implicit`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
ImplicitClientCreateDto implicitClientCreateDto [FromBody] [Required] [No-Default]
```

New `ImplicitClientCreateDto <ImplicitClientCreateDto>` object

```json
{
  "RedirectUris": [
    "String",
    "String"
  ],
  "PostLogoutRedirectUris": [
    "String",
    "String"
  ],
  "AllowedCorsOrigins": [
    "String",
    "String"
  ],
  "Name": "Name",
  "Enabled": false,
  "AllowAccessTokensViaBrowser": false,
  "ClientUri": "ClientUri",
  "LogoUri": "LogoUri"
}
```

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `ImplicitClientResponseDto`

```json
{
  "Name": "Name",
  "ClientId": "ClientId"
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

## `Create Hybrid Client`

Create a Hybrid flow `Client <Client>`

### Request

`POST api/Tenant/{tenantId}/Clients/Hybrid`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
HybridClientCreateDto hybridClientCreateDto [FromBody] [Required] [No-Default]
```

New `HybridClientCreateDto <HybridClientCreateDto>` object

```json
{
  "SecretDescription": "description",
  "SecretExpirationDate": "2019-02-05T19:11:14.7464146-08:00",
  "RedirectUris": [
    "String",
    "String"
  ],
  "PostLogoutRedirectUris": [
    "String",
    "String"
  ],
  "AllowOfflineAccess": false,
  "Name": "Name",
  "Enabled": false,
  "AllowAccessTokensViaBrowser": false,
  "ClientUri": "ClientUri",
  "LogoUri": "LogoUri"
}
```

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `HybridClientResponseDto`

```json
{
  "Name": "Name",
  "ClientId": "ClientId",
  "ClientSecret": "ClientSecret",
  "SecretExpirationDate": "2019-02-05T19:11:14.7520554-08:00",
  "SecretDescription": "description",
  "SecretId": 0,
  "AllowOfflineAccess": false
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

## `Update Client With a Given ID`

Create a client

### Request

`POST api/Tenant/{tenantId}/Clients/{clientId}`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string clientId [FromRoute] [Required] [No-Default]
```

Id of client

```csharp
string secretDescription [FromQuery] [Required] [No-Default]
```

Description of Client secret

```csharp
string secretExpiration [FromQuery] [Required] [No-Default]
```

Expiration of Client secret

```csharp
Client client [FromBody] [Required] [No-Default]
```

New Client object

```json
{
  "Enabled": true,
  "ClientId": "ClientId",
  "ClientSecrets": [
    {
      "Id": 0,
      "Description": "description",
      "Value": "Value",
      "Expiration": "2019-02-05T19:11:14.756844-08:00",
      "Type": "Type"
    },
    {
      "Id": 0,
      "Description": "description",
      "Value": "Value",
      "Expiration": "2019-02-05T19:11:14.7568588-08:00",
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
  "SecretExpirationDate": "2019-02-05T19:11:14.7571815-08:00",
  "RoleIds": [
    "String",
    "String"
  ],
  "Name": "Name",
  "Enabled": false,
  "AllowAccessTokensViaBrowser": false,
  "ClientUri": "ClientUri",
  "LogoUri": "LogoUri"
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

`PUT api/Tenant/{tenantId}/Clients/{clientId}`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string clientId [FromRoute] [Required] [No-Default]
```

Id of client

```csharp
Client client [FromBody] [Required] [No-Default]
```

New Client

```json
{
  "Enabled": true,
  "ClientId": "ClientId",
  "ClientSecrets": [
    {
      "Id": 0,
      "Description": "description",
      "Value": "Value",
      "Expiration": "2019-02-05T19:11:14.7577279-08:00",
      "Type": "Type"
    },
    {
      "Id": 0,
      "Description": "description",
      "Value": "Value",
      "Expiration": "2019-02-05T19:11:14.7577367-08:00",
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
      "Expiration": "2019-02-05T19:11:14.7582491-08:00",
      "Type": "Type"
    },
    {
      "Id": 0,
      "Description": "description",
      "Value": "Value",
      "Expiration": "2019-02-05T19:11:14.7582632-08:00",
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

`DELETE api/Tenant/{tenantId}/Clients/{clientId}`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string clientId [FromRoute] [Required] [No-Default]
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

## `Get Client Secrets`

Get all secrets for a client

### Request

`GET api/Tenant/{tenantId}/Clients/{clientId}/Secrets`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string clientId [FromRoute] [Required] [No-Default]
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
    "Expiration": "2019-02-05T19:11:14.7595242-08:00",
    "Type": "Type"
  },
  {
    "Id": 0,
    "Description": "description",
    "Value": "Value",
    "Expiration": "2019-02-05T19:11:14.759551-08:00",
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

`GET api/Tenant/{tenantId}/Clients/{clientId}/Secrets/{secretId}`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string clientId [FromRoute] [Required] [No-Default]
```

Id of client

```csharp
int32 secretId [FromRoute] [Required] [No-Default]
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
  "Expiration": "2019-02-05T19:11:14.7599294-08:00",
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

`POST api/Tenant/{tenantId}/Clients/{clientId}/Secrets`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string clientId [FromRoute] [Required] [No-Default]
```

Id of client

```csharp
ClientSecretDto clientSecretDto [FromBody] [Required] [No-Default]
```



```json
{
  "Expiration": "2019-02-05T19:11:14.7603754-08:00",
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

 `List[Secret]`

```json
[
  {
    "Id": 0,
    "Description": "description",
    "Value": "Value",
    "Expiration": "2019-02-05T19:11:14.7621833-08:00",
    "Type": "Type"
  },
  {
    "Id": 0,
    "Description": "description",
    "Value": "Value",
    "Expiration": "2019-02-05T19:11:14.7621978-08:00",
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

`PUT api/Tenant/{tenantId}/Clients/{clientId}/Secrets/{secretId}`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string clientId [FromRoute] [Required] [No-Default]
```

Id of client

```csharp
int32 secretId [FromRoute] [Required] [No-Default]
```

secretId

```csharp
ClientSecretDto secretUpdate [FromBody] [Required] [No-Default]
```

secretId

```json
{
  "Expiration": "2019-02-05T19:11:14.7626664-08:00",
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

 `Secret`

```json
{
  "Id": 0,
  "Description": "description",
  "Value": "Value",
  "Expiration": "2019-02-05T19:11:14.7629891-08:00",
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

`DELETE api/Tenant/{tenantId}/Clients/{clientId}/Secrets/{secretId}`

### Parameters

```csharp
string tenantId [FromRoute] [Required] [No-Default]
```

Id of tenant

```csharp
string clientId [FromRoute] [Required] [No-Default]
```

Id of client

```csharp
int32 secretId [FromRoute] [Required] [No-Default]
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
    "Expiration": "2019-02-05T19:11:14.7634925-08:00",
    "Type": "Type"
  },
  {
    "Id": 0,
    "Description": "description",
    "Value": "Value",
    "Expiration": "2019-02-05T19:11:14.7635112-08:00",
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

