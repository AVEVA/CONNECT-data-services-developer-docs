---
uid: identityClient
---

# Client

CRUD operations on Client

## Properties

For HTTP requests and responses, the Client object has the following properties and JSON-serialized body: 

```csharp
bool Enabled
```
Specifies if client is enabled (defaults to true)

```csharp
string ClientId
```
Unique ID of the client

```csharp
[Secret] ClientSecrets
```
Client secrets - only relevant for flows that require a secret

```csharp
bool RequireClientSecret
```
If set to false, no client secret is needed to request tokens at the token endpoint (defaults to true)

```csharp
string ClientName
```
Client display name (used for logging and consent screen)

```csharp
string Description
```
Client description

```csharp
string ClientUri
```
URI to further information about client (used on consent screen)

```csharp
string LogoUri
```
URI to client logo (used on consent screen)

```csharp
bool RequireConsent
```
Specifies whether a consent screen is required (defaults to true)

```csharp
bool AllowRememberConsent
```
Specifies whether user can choose to store consent decisions (defaults to true)

```csharp
[string] AllowedGrantTypes
```
Specifies the allowed grant types (legal combinations of AuthorizationCode, Implicit, Hybrid, ResourceOwner,
            ClientCredentials).

```csharp
bool AllowAccessTokensViaBrowser
```
Controls whether access tokens are transmitted via the browser for this client (defaults to false).
            This can prevent accidental leakage of access tokens when multiple response types are allowed.

```csharp
[string] RedirectUris
```
Specifies allowed URIs to return tokens or authorization codes to

```csharp
[string] PostLogoutRedirectUris
```
Specifies allowed URIs to redirect to after logout

```csharp
string FrontChannelLogoutUri
```
Specifies logout URI at client for HTTP front-channel based logout.

```csharp
bool FrontChannelLogoutSessionRequired
```
Specifies is the user's session id should be sent to the FrontChannelLogoutUri. Defaults to true.

```csharp
string BackChannelLogoutUri
```
Specifies logout URI at client for HTTP back-channel based logout.

```csharp
bool BackChannelLogoutSessionRequired
```
Specifies is the user's session id should be sent to the BackChannelLogoutUri. Defaults to true.

```csharp
bool AllowOfflineAccess
```
Gets or sets a value indicating whether [allow offline access]. Defaults to false.

```csharp
[string] AllowedScopes
```
Specifies the api scopes that the client is allowed to request. If empty, the client can't access any scope

```csharp
bool AlwaysIncludeUserClaimsInIdToken
```
When requesting both an id token and access token, should the user claims always be added to the id token instead
            of requiring the client to use the user info endpoint.
            Defaults to false.

```csharp
int32 IdentityTokenLifetime
```
Lifetime of identity token in seconds (defaults to 300 seconds / 5 minutes)

```csharp
int32 AccessTokenLifetime
```
Lifetime of access token in seconds (defaults to 3600 seconds / 1 hour)

```csharp
int32 AuthorizationCodeLifetime
```
Lifetime of authorization code in seconds (defaults to 300 seconds / 5 minutes)

```csharp
int32 AbsoluteRefreshTokenLifetime
```
Maximum lifetime of a refresh token in seconds. Defaults to 2592000 seconds / 30 days

```csharp
int32 SlidingRefreshTokenLifetime
```
Sliding lifetime of a refresh token in seconds. Defaults to 1296000 seconds / 15 days

```csharp
optional: int32 ConsentLifetime
```
Lifetime of a user consent in seconds. Defaults to null (no expiration)

```csharp
TokenUsage RefreshTokenUsage
```
ReUse: the refresh token handle will stay the same when refreshing tokens
            OneTime: the refresh token handle will be updated when refreshing tokens

```csharp
bool UpdateAccessTokenClaimsOnRefresh
```
Gets or sets a value indicating whether the access token (and its claims) should be updated on a refresh token
            request.
            Defaults to false.

```csharp
TokenExpiration RefreshTokenExpiration
```
Absolute: the refresh token will expire on a fixed point in time (specified by the AbsoluteRefreshTokenLifetime)
            Sliding: when refreshing the token, the lifetime of the refresh token will be renewed (by the amount specified in
            SlidingRefreshTokenLifetime). The lifetime will not exceed AbsoluteRefreshTokenLifetime.

```csharp
AccessTokenType AccessTokenType
```
Specifies whether the access token is a reference token or a self contained JWT token (defaults to Jwt).

```csharp
[string] IdentityProviderRestrictions
```
Specifies which external IdPs can be used with this client (if list is empty all IdPs are allowed). Defaults to
            empty.

```csharp
bool IncludeJwtId
```
Gets or sets a value indicating whether JWT access tokens should include an identifier. Defaults to false.

```csharp
[Claim] Claims
```
Allows settings claims for the client (will be included in the access token).

```csharp
bool AlwaysSendClientClaims
```
Gets or sets a value indicating whether client claims should be always included in the access tokens - or only for
            client credentials flow.
            Defaults to false

```csharp
string ClientClaimsPrefix
```
Gets or sets a value to prefix it on client claim types. Defaults to client_.

```csharp
string PairWiseSubjectSalt
```
Subject salt to be used.

```csharp
optional: int32 UserSsoLifetime
```
The maximum duration (in seconds) since the last time the user authenticated.

```csharp
string UserCodeType
```
Gets or sets the type of the device flow user code.

```csharp
int32 DeviceCodeLifetime
```
Gets or sets the device code lifetime.

```csharp
[string] AllowedCorsOrigins
```
Gets or sets the allowed CORS origins for JavaScript clients.

```csharp
[string,string] Properties
```
Gets or sets the custom properties for the client.


```json
{
  "Enabled": true,
  "ClientId": "String",
  "ClientSecrets": [],
  "RequireClientSecret": true,
  "ClientName": "String",
  "Description": "String",
  "ClientUri": "String",
  "LogoUri": "String",
  "RequireConsent": true,
  "AllowRememberConsent": true,
  "AllowedGrantTypes": [
    "string1",
    "string2"
  ],
  "AllowAccessTokensViaBrowser": false,
  "RedirectUris": [
    "string1",
    "string2"
  ],
  "PostLogoutRedirectUris": [
    "string1",
    "string2"
  ],
  "FrontChannelLogoutUri": "String",
  "FrontChannelLogoutSessionRequired": true,
  "BackChannelLogoutUri": "String",
  "BackChannelLogoutSessionRequired": true,
  "AllowOfflineAccess": false,
  "AllowedScopes": [
    "string1",
    "string2"
  ],
  "AlwaysIncludeUserClaimsInIdToken": false,
  "IdentityTokenLifetime": 300,
  "AccessTokenLifetime": 3600,
  "AuthorizationCodeLifetime": 300,
  "AbsoluteRefreshTokenLifetime": 2592000,
  "SlidingRefreshTokenLifetime": 1296000,
  "ConsentLifetime": 3600,
  "RefreshTokenUsage": 0,
  "UpdateAccessTokenClaimsOnRefresh": false,
  "RefreshTokenExpiration": 0,
  "AccessTokenType": 0,
  "IdentityProviderRestrictions": [
    "string1",
    "string2"
  ],
  "IncludeJwtId": false,
  "Claims": [],
  "AlwaysSendClientClaims": false,
  "ClientClaimsPrefix": "String",
  "PairWiseSubjectSalt": "String",
  "UserSsoLifetime": 3600,
  "UserCodeType": "String",
  "DeviceCodeLifetime": 300,
  "AllowedCorsOrigins": [
    "string1",
    "string2"
  ],
  "Properties": {
    "key": "value"
  }
}
```
***

## `GetClients()`

Get all clients for a tenant

### Http 

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

Allowed for these roles: **Account Administrator**, **Cluster Operator**, **Cluster Support**

### Returns

#### 200

Success. Returns System.Collections.Generic.List`1[OSIsoft.Identity.Common.Models.Client]

```json
[
{
  "Enabled": true,
  "ClientId": "String",
  "ClientSecrets": [],
  "RequireClientSecret": true,
  "ClientName": "String",
  "Description": "String",
  "ClientUri": "String",
  "LogoUri": "String",
  "RequireConsent": true,
  "AllowRememberConsent": true,
  "AllowedGrantTypes": [
    "string1",
    "string2"
  ],
  "AllowAccessTokensViaBrowser": false,
  "RedirectUris": [
    "string1",
    "string2"
  ],
  "PostLogoutRedirectUris": [
    "string1",
    "string2"
  ],
  "FrontChannelLogoutUri": "String",
  "FrontChannelLogoutSessionRequired": true,
  "BackChannelLogoutUri": "String",
  "BackChannelLogoutSessionRequired": true,
  "AllowOfflineAccess": false,
  "AllowedScopes": [
    "string1",
    "string2"
  ],
  "AlwaysIncludeUserClaimsInIdToken": false,
  "IdentityTokenLifetime": 300,
  "AccessTokenLifetime": 3600,
  "AuthorizationCodeLifetime": 300,
  "AbsoluteRefreshTokenLifetime": 2592000,
  "SlidingRefreshTokenLifetime": 1296000,
  "ConsentLifetime": 3600,
  "RefreshTokenUsage": 0,
  "UpdateAccessTokenClaimsOnRefresh": false,
  "RefreshTokenExpiration": 0,
  "AccessTokenType": 0,
  "IdentityProviderRestrictions": [
    "string1",
    "string2"
  ],
  "IncludeJwtId": false,
  "Claims": [],
  "AlwaysSendClientClaims": false,
  "ClientClaimsPrefix": "String",
  "PairWiseSubjectSalt": "String",
  "UserSsoLifetime": 3600,
  "UserCodeType": "String",
  "DeviceCodeLifetime": 300,
  "AllowedCorsOrigins": [
    "string1",
    "string2"
  ],
  "Properties": {
    "key": "value"
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

Oops! Something happened, somewhere inside our server, just a while ago

***

## `GetClient()`

Get a client object

### Http 

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

Allowed for these roles: **Account Administrator**, **Cluster Operator**, **Cluster Support**

### Returns

#### 200

Success. Returns OSIsoft.Identity.Common.Models.Client

```json
{
  "Enabled": true,
  "ClientId": "String",
  "ClientSecrets": [],
  "RequireClientSecret": true,
  "ClientName": "String",
  "Description": "String",
  "ClientUri": "String",
  "LogoUri": "String",
  "RequireConsent": true,
  "AllowRememberConsent": true,
  "AllowedGrantTypes": [
    "string1",
    "string2"
  ],
  "AllowAccessTokensViaBrowser": false,
  "RedirectUris": [
    "string1",
    "string2"
  ],
  "PostLogoutRedirectUris": [
    "string1",
    "string2"
  ],
  "FrontChannelLogoutUri": "String",
  "FrontChannelLogoutSessionRequired": true,
  "BackChannelLogoutUri": "String",
  "BackChannelLogoutSessionRequired": true,
  "AllowOfflineAccess": false,
  "AllowedScopes": [
    "string1",
    "string2"
  ],
  "AlwaysIncludeUserClaimsInIdToken": false,
  "IdentityTokenLifetime": 300,
  "AccessTokenLifetime": 3600,
  "AuthorizationCodeLifetime": 300,
  "AbsoluteRefreshTokenLifetime": 2592000,
  "SlidingRefreshTokenLifetime": 1296000,
  "ConsentLifetime": 3600,
  "RefreshTokenUsage": 0,
  "UpdateAccessTokenClaimsOnRefresh": false,
  "RefreshTokenExpiration": 0,
  "AccessTokenType": 0,
  "IdentityProviderRestrictions": [
    "string1",
    "string2"
  ],
  "IncludeJwtId": false,
  "Claims": [],
  "AlwaysSendClientClaims": false,
  "ClientClaimsPrefix": "String",
  "PairWiseSubjectSalt": "String",
  "UserSsoLifetime": 3600,
  "UserCodeType": "String",
  "DeviceCodeLifetime": 300,
  "AllowedCorsOrigins": [
    "string1",
    "string2"
  ],
  "Properties": {
    "key": "value"
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

Oops! Something happened, somewhere inside our server, just a while ago

***

## `CreateClient()`

Create a client
            This method is obsolete, please use one of the following instead:
            {tenantId}/Clients/ClientCredential
            {tenantId}/Clients/Implicit
            {tenantId}/Clients/Hybrid

### Http 

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
  "RoleIds": [
    "string1",
    "string2"
  ],
  "Name": "String",
  "Enabled": true,
  "SecretDescription": "String",
  "SecretExpirationDate": "2019-01-25T15:31:27.5834363-08:00",
  "AllowOfflineAccess": true,
  "AllowAccessTokensViaBrowser": true,
  "ClientUri": "String",
  "LogoUri": "String"
}
```


### Security

Allowed for these roles: **Account Administrator**

### Returns

#### 200

Success. Returns OSIsoft.Identity.Common.Models.ClientResponseDto

```json
{
  "Name": "String",
  "ClientId": "String",
  "ClientSecret": "String",
  "SecretExpirationDate": "2019-01-25T15:31:27.6005036-08:00",
  "SecretDescription": "String",
  "SecretId": 3600
}
```

#### 401

Unauthorized


#### 403

Forbidden


#### 404

Tenant not found


#### 500

Oops! Something happened, somewhere inside our server, just a while ago

***

## `CreateClientCredentialClient()`

Create a Client Credential flow `Client <Client>`

### Http 

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
  "RoleIds": [
    "string1",
    "string2"
  ],
  "Name": "String",
  "Enabled": true,
  "SecretDescription": "String",
  "SecretExpirationDate": "2019-01-25T15:31:27.6051993-08:00",
  "AllowOfflineAccess": true,
  "AllowAccessTokensViaBrowser": true,
  "ClientUri": "String",
  "LogoUri": "String"
}
```


### Security

Allowed for these roles: **Account Administrator**

### Returns

#### 200

Success. Returns OSIsoft.Identity.Common.Models.ClientResponseDto

```json
{
  "Name": "String",
  "ClientId": "String",
  "ClientSecret": "String",
  "SecretExpirationDate": "2019-01-25T15:31:27.605407-08:00",
  "SecretDescription": "String",
  "SecretId": 3600
}
```

#### 401

Unauthorized


#### 403

Forbidden


#### 404

Tenant not found


#### 500

Oops! Something happened, somewhere inside our server, just a while ago

***

## `CreateImplicitClient()`

Create an Implicit flow `Client <Client>`

### Http 

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
    "string1",
    "string2"
  ],
  "PostLogoutRedirectUris": [
    "string1",
    "string2"
  ],
  "AllowedCorsOrigin": [
    "string1",
    "string2"
  ],
  "Name": "String",
  "Enabled": true,
  "SecretDescription": "String",
  "SecretExpirationDate": "2019-01-25T15:31:27.6071458-08:00",
  "AllowOfflineAccess": true,
  "AllowAccessTokensViaBrowser": true,
  "ClientUri": "String",
  "LogoUri": "String"
}
```


### Security

Allowed for these roles: **Account Administrator**

### Returns

#### 200

Success. Returns OSIsoft.Identity.Common.Models.ClientResponseDto

```json
{
  "Name": "String",
  "ClientId": "String",
  "ClientSecret": "String",
  "SecretExpirationDate": "2019-01-25T15:31:27.610992-08:00",
  "SecretDescription": "String",
  "SecretId": 3600
}
```

#### 401

Unauthorized


#### 403

Forbidden


#### 404

Tenant not found


#### 500

Oops! Something happened, somewhere inside our server, just a while ago

***

## `CreateHybridClient()`

Create a Hybrid flow `Client <Client>`

### Http 

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
  "RedirectUris": [
    "string1",
    "string2"
  ],
  "PostLogoutRedirectUris": [
    "string1",
    "string2"
  ],
  "AllowedCorsOrigin": [
    "string1",
    "string2"
  ],
  "Name": "String",
  "Enabled": true,
  "SecretDescription": "String",
  "SecretExpirationDate": "2019-01-25T15:31:27.6130564-08:00",
  "AllowOfflineAccess": true,
  "AllowAccessTokensViaBrowser": true,
  "ClientUri": "String",
  "LogoUri": "String"
}
```


### Security

Allowed for these roles: **Account Administrator**

### Returns

#### 200

Success. Returns OSIsoft.Identity.Common.Models.ClientResponseDto

```json
{
  "Name": "String",
  "ClientId": "String",
  "ClientSecret": "String",
  "SecretExpirationDate": "2019-01-25T15:31:27.6168332-08:00",
  "SecretDescription": "String",
  "SecretId": 3600
}
```

#### 401

Unauthorized


#### 403

Forbidden


#### 404

Tenant not found


#### 500

Oops! Something happened, somewhere inside our server, just a while ago

***

## `CreateClient()`

Create a client

### Http 

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
  "ClientId": "String",
  "ClientSecrets": [],
  "RequireClientSecret": true,
  "ClientName": "String",
  "Description": "String",
  "ClientUri": "String",
  "LogoUri": "String",
  "RequireConsent": true,
  "AllowRememberConsent": true,
  "AllowedGrantTypes": [
    "string1",
    "string2"
  ],
  "AllowAccessTokensViaBrowser": false,
  "RedirectUris": [
    "string1",
    "string2"
  ],
  "PostLogoutRedirectUris": [
    "string1",
    "string2"
  ],
  "FrontChannelLogoutUri": "String",
  "FrontChannelLogoutSessionRequired": true,
  "BackChannelLogoutUri": "String",
  "BackChannelLogoutSessionRequired": true,
  "AllowOfflineAccess": false,
  "AllowedScopes": [
    "string1",
    "string2"
  ],
  "AlwaysIncludeUserClaimsInIdToken": false,
  "IdentityTokenLifetime": 300,
  "AccessTokenLifetime": 3600,
  "AuthorizationCodeLifetime": 300,
  "AbsoluteRefreshTokenLifetime": 2592000,
  "SlidingRefreshTokenLifetime": 1296000,
  "ConsentLifetime": 3600,
  "RefreshTokenUsage": 0,
  "UpdateAccessTokenClaimsOnRefresh": false,
  "RefreshTokenExpiration": 0,
  "AccessTokenType": 0,
  "IdentityProviderRestrictions": [
    "string1",
    "string2"
  ],
  "IncludeJwtId": false,
  "Claims": [],
  "AlwaysSendClientClaims": false,
  "ClientClaimsPrefix": "String",
  "PairWiseSubjectSalt": "String",
  "UserSsoLifetime": 3600,
  "UserCodeType": "String",
  "DeviceCodeLifetime": 300,
  "AllowedCorsOrigins": [
    "string1",
    "string2"
  ],
  "Properties": {
    "key": "value"
  }
}
```


### Security

Allowed for these roles: **Account Administrator**

### Returns

#### 200

Success. Returns OSIsoft.Identity.Common.Models.ClientResponseDto

```json
{
  "Name": "String",
  "ClientId": "String",
  "ClientSecret": "String",
  "SecretExpirationDate": "2019-01-25T15:31:27.6174358-08:00",
  "SecretDescription": "String",
  "SecretId": 3600
}
```

#### 401

Unauthorized


#### 403

Forbidden


#### 404

Client or Tenant not found


#### 500

Oops! Something happened, somewhere inside our server, just a while ago

***

## `UpdateClient()`

Update a client

### Http 

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
  "ClientId": "String",
  "ClientSecrets": [],
  "RequireClientSecret": true,
  "ClientName": "String",
  "Description": "String",
  "ClientUri": "String",
  "LogoUri": "String",
  "RequireConsent": true,
  "AllowRememberConsent": true,
  "AllowedGrantTypes": [
    "string1",
    "string2"
  ],
  "AllowAccessTokensViaBrowser": false,
  "RedirectUris": [
    "string1",
    "string2"
  ],
  "PostLogoutRedirectUris": [
    "string1",
    "string2"
  ],
  "FrontChannelLogoutUri": "String",
  "FrontChannelLogoutSessionRequired": true,
  "BackChannelLogoutUri": "String",
  "BackChannelLogoutSessionRequired": true,
  "AllowOfflineAccess": false,
  "AllowedScopes": [
    "string1",
    "string2"
  ],
  "AlwaysIncludeUserClaimsInIdToken": false,
  "IdentityTokenLifetime": 300,
  "AccessTokenLifetime": 3600,
  "AuthorizationCodeLifetime": 300,
  "AbsoluteRefreshTokenLifetime": 2592000,
  "SlidingRefreshTokenLifetime": 1296000,
  "ConsentLifetime": 3600,
  "RefreshTokenUsage": 0,
  "UpdateAccessTokenClaimsOnRefresh": false,
  "RefreshTokenExpiration": 0,
  "AccessTokenType": 0,
  "IdentityProviderRestrictions": [
    "string1",
    "string2"
  ],
  "IncludeJwtId": false,
  "Claims": [],
  "AlwaysSendClientClaims": false,
  "ClientClaimsPrefix": "String",
  "PairWiseSubjectSalt": "String",
  "UserSsoLifetime": 3600,
  "UserCodeType": "String",
  "DeviceCodeLifetime": 300,
  "AllowedCorsOrigins": [
    "string1",
    "string2"
  ],
  "Properties": {
    "key": "value"
  }
}
```


### Security

Allowed for these roles: **Account Administrator**

### Returns

#### 200

Success. Returns OSIsoft.Identity.Common.Models.Client

```json
{
  "Enabled": true,
  "ClientId": "String",
  "ClientSecrets": [],
  "RequireClientSecret": true,
  "ClientName": "String",
  "Description": "String",
  "ClientUri": "String",
  "LogoUri": "String",
  "RequireConsent": true,
  "AllowRememberConsent": true,
  "AllowedGrantTypes": [
    "string1",
    "string2"
  ],
  "AllowAccessTokensViaBrowser": false,
  "RedirectUris": [
    "string1",
    "string2"
  ],
  "PostLogoutRedirectUris": [
    "string1",
    "string2"
  ],
  "FrontChannelLogoutUri": "String",
  "FrontChannelLogoutSessionRequired": true,
  "BackChannelLogoutUri": "String",
  "BackChannelLogoutSessionRequired": true,
  "AllowOfflineAccess": false,
  "AllowedScopes": [
    "string1",
    "string2"
  ],
  "AlwaysIncludeUserClaimsInIdToken": false,
  "IdentityTokenLifetime": 300,
  "AccessTokenLifetime": 3600,
  "AuthorizationCodeLifetime": 300,
  "AbsoluteRefreshTokenLifetime": 2592000,
  "SlidingRefreshTokenLifetime": 1296000,
  "ConsentLifetime": 3600,
  "RefreshTokenUsage": 0,
  "UpdateAccessTokenClaimsOnRefresh": false,
  "RefreshTokenExpiration": 0,
  "AccessTokenType": 0,
  "IdentityProviderRestrictions": [
    "string1",
    "string2"
  ],
  "IncludeJwtId": false,
  "Claims": [],
  "AlwaysSendClientClaims": false,
  "ClientClaimsPrefix": "String",
  "PairWiseSubjectSalt": "String",
  "UserSsoLifetime": 3600,
  "UserCodeType": "String",
  "DeviceCodeLifetime": 300,
  "AllowedCorsOrigins": [
    "string1",
    "string2"
  ],
  "Properties": {
    "key": "value"
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

Oops! Something happened, somewhere inside our server, just a while ago

***

## `DeleteClient()`

Delete a client

### Http 

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

Allowed for these roles: **Account Administrator**

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

Oops! Something happened, somewhere inside our server, just a while ago

***

## `GetClientSecrets()`

Get all secrets for a client

### Http 

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

Allowed for these roles: **Account Administrator**, **Cluster Operator**, **Cluster Support**

### Returns

#### 200

Success. Returns System.Collections.Generic.List`1[OSIsoft.Identity.Common.Models.Secret]

```json
[
{
  "Id": 0,
  "Description": "String",
  "Value": "String",
  "Expiration": "2019-01-25T15:31:27.6193936-08:00",
  "Type": "String"
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

Oops! Something happened, somewhere inside our server, just a while ago

***

## `GetClientSecret()`

Get a specific client secret

### Http 

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

Allowed for these roles: **Account Administrator**, **Cluster Operator**, **Cluster Support**

### Returns

#### 200

Success. Returns OSIsoft.Identity.Common.Models.Secret

```json
{
  "Id": 0,
  "Description": "String",
  "Value": "String",
  "Expiration": "2019-01-25T15:31:27.621483-08:00",
  "Type": "String"
}
```

#### 401

Unauthorized


#### 403

Forbidden


#### 404

Secret, Client, or Tenant not found


#### 500

Oops! Something happened, somewhere inside our server, just a while ago

***

## `AddClientSecret()`

Add a new secret for a client

### Http 

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
  "Expiration": "2019-01-25T15:31:27.6218635-08:00",
  "Description": "String"
}
```


### Security

Allowed for these roles: **Account Administrator**

### Returns

#### 200

Success. Returns System.Collections.Generic.List`1[OSIsoft.Identity.Common.Models.Secret]

```json
[
{
  "Id": 0,
  "Description": "String",
  "Value": "String",
  "Expiration": "2019-01-25T15:31:27.6230571-08:00",
  "Type": "String"
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

Oops! Something happened, somewhere inside our server, just a while ago

***

## `UpdateClientSecret()`

Update a client secret (Only Secret Description and Secret Expiration Date could be updated)

### Http 

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
  "Expiration": "2019-01-25T15:31:27.6233964-08:00",
  "Description": "String"
}
```


### Security

Allowed for these roles: **Account Administrator**

### Returns

#### 200

Success. Returns OSIsoft.Identity.Common.Models.Secret

```json
{
  "Id": 0,
  "Description": "String",
  "Value": "String",
  "Expiration": "2019-01-25T15:31:27.623571-08:00",
  "Type": "String"
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

Oops! Something happened, somewhere inside our server, just a while ago

***

## `DeleteClientSecret()`

Delete a secret from a client

### Http 

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

Allowed for these roles: **Account Administrator**

### Returns

#### 200

Success. Returns System.Collections.Generic.List`1[OSIsoft.Identity.Common.Models.Secret]

```json
[
{
  "Id": 0,
  "Description": "String",
  "Value": "String",
  "Expiration": "2019-01-25T15:31:27.6240442-08:00",
  "Type": "String"
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

Oops! Something happened, somewhere inside our server, just a while ago

***

