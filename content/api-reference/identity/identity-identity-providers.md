---
title: identity/identity-identity-providers v20210426.5
language_tabs: []
toc_footers: []
includes: []
search: true
code_clipboard: true
highlight_theme: darkula
headingLevel: 2
generator: osisoft.widdershins v1.0.7

---

# Identity Providers
An identity provider provides authentication services and maintains credentials for users that have been provisioned in OCS. Each tenant can have one or more identity providers. Each user is either assigned one of the available identity providers in the tenant or chooses one in the Home Realm Discovery page when accepting the invitation. A user can only log in with the same identity provider they signed up with.

## `List Identity Providers`

<a id="opIdIdentityProviders_List Identity Providers"></a>

Returns a list of identity provider objects.

### Request
```text 
GET /api/v1/IdentityProviders
?query={query}&skip={skip}&count={count}
```

#### Parameters

`[optional] string query`
<br/>(not supported) Search string identifier<br/><br/>`[optional] integer skip`
<br/>Number of identity providers to skip<br/><br/>`[optional] integer count`
<br/>Maximum number of identity providers to return.<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[IdentityProvider](#schemaidentityprovider)[]|Identity providers found|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

#### Example response body
> 200 Response

```json
[
  {
    "Id": "string",
    "DisplayName": "string",
    "Scheme": "string",
    "UserIdClaimType": "string",
    "ClientId": "string",
    "IsConfigured": true,
    "Capabilities": {
      "User": {},
      "Group": {}
    }
  }
]
```

### Authorization

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `Get Header for Identity Providers`

<a id="opIdIdentityProviders_Get Header for Identity Providers"></a>

Get the total number of identity providers.

### Request
```text 
HEAD /api/v1/IdentityProviders
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Headers for identity providers found.|
|401|None|Unauthorized|
|403|None|Forbidden|
|404|None|Tenant not found|
|500|None|Internal server error|

### Authorization

Allowed for these roles: 
<ul>
<li>Tenant Administrator</li>
</ul>

---

## `Get Identity Provider`

<a id="opIdIdentityProviders_Get Identity Provider"></a>

Returns an IdentityProvider object.

### Request
```text 
GET /api/v1/IdentityProviders/{identityProviderId}
```

#### Parameters

`string identityProviderId`
<br/>Identity provider unique identifier<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[IdentityProvider](#schemaidentityprovider)|Identity provider specified|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|404|[ErrorResponse](#schemaerrorresponse)|Identity provider not found|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

#### Example response body
> 200 Response

```json
{
  "Id": "string",
  "DisplayName": "string",
  "Scheme": "string",
  "UserIdClaimType": "string",
  "ClientId": "string",
  "IsConfigured": true,
  "Capabilities": {
    "User": {
      "SignIn": null,
      "Invitation": null,
      "Search": null
    },
    "Group": {
      "Authorize": null,
      "Search": null
    }
  }
}
```

### Authorization

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `Get Identity Provider based on Id`

<a id="opIdIdentityProviders_Get Identity Provider based on Id"></a>

Validates that a identity provider exists

### Request
```text 
HEAD /api/v1/IdentityProviders/{identityProviderId}
```

#### Parameters

`string identityProviderId`
<br/>Identity provider unique identifier<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Identity provider found|
|401|None|Unauthorized|
|403|None|Forbidden|
|404|None|Identity provider or tenant not found|
|500|None|Internal server error|

### Authorization

Allowed for these roles: 
<ul>
<li>Tenant Administrator</li>
</ul>

---

## `Get Identity Provider by Scheme`

<a id="opIdIdentityProviders_Get Identity Provider by Scheme"></a>

Returns a list of identity provider objects that follow a scheme.

### Request
```text 
GET /api/v1/IdentityProviders/schemes/{scheme}
```

#### Parameters

`string scheme`
<br/>Scheme name (for example, AAD or Google).<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[IdentityProvider](#schemaidentityprovider)|Identity provider specified|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|404|[ErrorResponse](#schemaerrorresponse)|Identity provider not found|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

#### Example response body
> 200 Response

```json
{
  "Id": "string",
  "DisplayName": "string",
  "Scheme": "string",
  "UserIdClaimType": "string",
  "ClientId": "string",
  "IsConfigured": true,
  "Capabilities": {
    "User": {
      "SignIn": null,
      "Invitation": null,
      "Search": null
    },
    "Group": {
      "Authorize": null,
      "Search": null
    }
  }
}
```

### Authorization

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `Get Identity Provider Based on Scheme`

<a id="opIdIdentityProviders_Get Identity Provider Based on Scheme"></a>

Validates that a scheme exists

### Request
```text 
HEAD /api/v1/IdentityProviders/schemes/{scheme}
```

#### Parameters

`string scheme`
<br/>Scheme name (for example, AAD or Google).<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Identity provider found|
|401|None|Unauthorized|
|403|None|Forbidden|
|404|None|Identity provider not found|
|500|None|Internal server error|

### Authorization

Allowed for these roles: 
<ul>
<li>Tenant Administrator</li>
</ul>

---

## `List all Identity Providers from Tenant`

<a id="opIdIdentityProviders_List all Identity Providers from Tenant"></a>

Gets all identity providers from a tenant.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/IdentityProviders
?query={query}&skip={skip}&count={count}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/>
`[optional] string query`
<br/>(not supported) Search string identifier<br/><br/>`[optional] integer skip`
<br/>Number of identity providers to skip<br/><br/>`[optional] integer count`
<br/>Maximum number of identity providers to return.<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[IdentityProvider](#schemaidentityprovider)[]|Identity providers found|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|404|[ErrorResponse](#schemaerrorresponse)|Tenant not found|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

#### Example response body
> 200 Response

```json
[
  {
    "Id": "string",
    "DisplayName": "string",
    "Scheme": "string",
    "UserIdClaimType": "string",
    "ClientId": "string",
    "IsConfigured": true,
    "Capabilities": {
      "User": {},
      "Group": {}
    }
  }
]
```

### Authorization

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `Get Total Count of Identity Providers`

<a id="opIdIdentityProviders_Get Total Count of Identity Providers"></a>

Returns the total number of identity providers in a tenant. The value will be set in the Total-Count header. This endpoint is identical to the GET one but it does not return any objects in the body.

### Request
```text 
HEAD /api/v1/Tenants/{tenantId}/IdentityProviders
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Identity provider headers for tenant|
|401|None|Unauthorized|
|403|None|Forbidden|
|404|None|Tenant not found|
|500|None|Internal server error|

### Authorization

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `Add Identity Provider to Tenant`

<a id="opIdIdentityProviders_Add Identity Provider to Tenant"></a>

Adds an existing identity provider to a tenant. This identity provider will be available in the Home Realm Discovery Page for users to log in or sign up.

### Request
```text 
POST /api/v1/Tenants/{tenantId}/IdentityProviders
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/>

### Request Body

IdentityProviderAdd object<br/>

```json
{
  "AzureActiveDirectoryConsentEmail": "user@example.com",
  "AzureActiveDirectoryConsentGivenName": "string",
  "AzureActiveDirectoryConsentSurname": "string",
  "AzureActiveDirectoryTenant": "string",
  "AzureActiveDirectoryConsentTypes": "string",
  "IdentityProviderId": "string",
  "AzureActiveDirectorySendConsent": true
}
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|201|[IdentityProvider](#schemaidentityprovider)|Identity provider created|
|302|None|Found|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|404|[ErrorResponse](#schemaerrorresponse)|Tenant not found|
|408|[ErrorResponse](#schemaerrorresponse)|Operation timed out|
|409|[ErrorResponse](#schemaerrorresponse)|Identity provider already exists in tenant|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

#### Example response body
> 201 Response

```json
{
  "Id": "string",
  "DisplayName": "string",
  "Scheme": "string",
  "UserIdClaimType": "string",
  "ClientId": "string",
  "IsConfigured": true,
  "Capabilities": {
    "User": {
      "SignIn": null,
      "Invitation": null,
      "Search": null
    },
    "Group": {
      "Authorize": null,
      "Search": null
    }
  }
}
```

### Authorization

Allowed for these roles: 
<ul>
<li>Tenant Administrator</li>
</ul>

---

## `Get Identity Provider from Tenant`

<a id="opIdIdentityProviders_Get Identity Provider from Tenant"></a>

Gets an identity provider from a tenant.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/IdentityProviders/{identityProviderId}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/>`string identityProviderId`
<br/>Identity provider unique identifier<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[IdentityProvider](#schemaidentityprovider)|Identity provider specified|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|404|[ErrorResponse](#schemaerrorresponse)|Identity provider or tenant not found|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

#### Example response body
> 200 Response

```json
{
  "Id": "string",
  "DisplayName": "string",
  "Scheme": "string",
  "UserIdClaimType": "string",
  "ClientId": "string",
  "IsConfigured": true,
  "Capabilities": {
    "User": {
      "SignIn": null,
      "Invitation": null,
      "Search": null
    },
    "Group": {
      "Authorize": null,
      "Search": null
    }
  }
}
```

### Authorization

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `Get Header for Identity Provider`

<a id="opIdIdentityProviders_Get Header for Identity Provider"></a>

Validates that a identity provider exists in the tenant. This endpoint is identical to the GET one but it does not return any objects in the body.

### Request
```text 
HEAD /api/v1/Tenants/{tenantId}/IdentityProviders/{identityProviderId}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/>`string identityProviderId`
<br/>Identity provider unique identifier<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Header for identity provider|
|401|None|Unauthorized|
|403|None|Forbidden|
|404|None|Identity provider or tenant not found|
|500|None|Internal server error|

### Authorization

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `Remove Identity Provider From Tenant`

<a id="opIdIdentityProviders_Remove Identity Provider From Tenant"></a>

Removes an identity provider from a tenant. Users provisioned with this identity provider will remain in the tenant, but will not be able to authenticate. An administrator cannot remove the identity provider they are signed in with.

### Request
```text 
DELETE /api/v1/Tenants/{tenantId}/IdentityProviders/{identityProviderId}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/>`string identityProviderId`
<br/>Identity provider unique identifier<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|204|None|No content|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|404|[ErrorResponse](#schemaerrorresponse)|Identity provider or tenant not found.|
|408|[ErrorResponse](#schemaerrorresponse)|Operation timed out|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

#### Example response body
> 401 Response

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "property1": null,
  "property2": null
}
```

### Authorization

Allowed for these roles: 
<ul>
<li>Tenant Administrator</li>
</ul>

---

## `Get an Identity Provider Consent from a Tenant`

<a id="opIdIdentityProviders_Get an Identity Provider Consent from a Tenant"></a>

Gets the consent information for an identity provider for a tenant. The ConsentState property, if returned, determines whether an identity provider consents to sharing access to its directory with the OCS tenant. For example, the expected ConsentState's for AAD include (Pending_)SignIn and (Pending_)ReadAllUsersGroups.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/IdentityProviders/{identityProviderId}/Consent
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/>`string identityProviderId`
<br/>Identity provider unique identifier to check for consent<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[IdentityProviderConsent](#schemaidentityproviderconsent)|Identity provider consent.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|404|[ErrorResponse](#schemaerrorresponse)|Identity provider or tenant not found.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

#### Example response body
> 200 Response

```json
{
  "Scheme": "string",
  "property1": null,
  "property2": null
}
```

### Authorization

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `Get Header for Identity Provider Consent`

<a id="opIdIdentityProviders_Get Header for Identity Provider Consent"></a>

Validates that a identity provider consent exists in the tenant. This endpoint is identical to the GET one but it does not return any objects in the body.

### Request
```text 
HEAD /api/v1/Tenants/{tenantId}/IdentityProviders/{identityProviderId}/Consent
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/>`string identityProviderId`
<br/>Identity provider unique identifier to check for consent<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Ok if the identity provider consent exists|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|404|[ErrorResponse](#schemaerrorresponse)|Identity provider or tenant not found|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

#### Example response body
> 401 Response

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "property1": null,
  "property2": null
}
```

### Authorization

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `Update Identity Provider Consent of a Tenant`

<a id="opIdIdentityProviders_Update Identity Provider Consent of a Tenant"></a>

Updates the identity provider consent of a tenant. Currently only supports AAD. The consent grants User.Read.All and GroupMember.Read.All permissions to the OCS tenant.

### Request
```text 
POST /api/v1/Tenants/{tenantId}/IdentityProviders/{identityProviderId}/Consent
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/>`string identityProviderId`
<br/>Identity provider unique identifier to activate consent<br/><br/>

### Request Body

Identity provider consent<br/>

```json
{
  "Scheme": "string",
  "property1": null,
  "property2": null
}
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[IdentityProviderConsent](#schemaidentityproviderconsent)|Identity provider consent|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|404|[ErrorResponse](#schemaerrorresponse)|Tenant not found|
|408|[ErrorResponse](#schemaerrorresponse)|Operation timed out|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

#### Example response body
> 200 Response

```json
{
  "Scheme": "string",
  "property1": null,
  "property2": null
}
```

### Authorization

Allowed for these roles: 
<ul>
<li>Tenant Administrator</li>
</ul>

---

## `Get a List of all Groups on an Identity Provider`

<a id="opIdIdentityProviders_Get a List of all Groups on an Identity Provider"></a>

Gets a list of groups that matches the query string on an identity provider that supports Advanced Integration, such as AAD. The prerequisite is that the identity provider must have already consented to sharing access to its directory with the OCS tenant. The consent grants User.Read.All and GroupMember.Read.All permissions to the OCS tenant.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/IdentityProviders/{identityProviderId}/groups
?query={query}&count={count}&skipToken={skipToken}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/>`string identityProviderId`
<br/>Identity provider unique identifier<br/><br/>`string query`
<br/>Start of user name or email to search for.<br/><br/>
`[optional] integer count`
<br/>Maximum number of groups to return.<br/><br/>`[optional] string skipToken`
<br/>An encoded string that identifies the set of groups that was not returned. For example, if you specify a count of the first 5 groups matching your query, the skipToken identifies the 6th group.<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[IdentityProviderResultsOfIdentityProviderGroup](#schemaidentityproviderresultsofidentityprovidergroup)|List of groups found|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|404|[ErrorResponse](#schemaerrorresponse)|Identity provider or tenant not found.|
|408|[ErrorResponse](#schemaerrorresponse)|Operation timed out|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

#### Example response body
> 200 Response

```json
{
  "Results": [
    {
      "Id": "string",
      "Name": "string",
      "Email": "user@example.com",
      "IsClusterManagementAllowed": true
    }
  ],
  "SkipToken": "string"
}
```

### Authorization

Allowed for these roles: 
<ul>
<li>Tenant Administrator</li>
</ul>

---

## `Get Identity Provider Groups`

<a id="opIdIdentityProviders_Get Identity Provider Groups"></a>

Gets the groups based on the Ids. Currently, AAD provider is the only provider that supports this endpoint.

### Request
```text 
POST /api/v1/Tenants/{tenantId}/IdentityProviders/{identityProviderId}/Groups
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/>`string identityProviderId`
<br/>Identity provider unique identifier<br/><br/>

### Request Body

Group unique identifier list.<br/>

```json
[
  "string"
]
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[IdentityProviderResultsOfIdentityProviderGroup](#schemaidentityproviderresultsofidentityprovidergroup)|List of groups|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|404|[ErrorResponse](#schemaerrorresponse)|Tenant not found|
|408|[ErrorResponse](#schemaerrorresponse)|Operation timed out|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

#### Example response body
> 200 Response

```json
{
  "Results": [
    {
      "Id": "string",
      "Name": "string",
      "Email": "user@example.com",
      "IsClusterManagementAllowed": true
    }
  ],
  "SkipToken": "string"
}
```

### Authorization

Allowed for these roles: 
<ul>
<li>Tenant Administrator</li>
</ul>

---

## `Get a List of All Users Belonging to Group on an Identity Provider`

<a id="opIdIdentityProviders_Get a List of All Users Belonging to Group on an Identity Provider"></a>

Gets a list of all users belonging to a specific group on an identity provider that supports Advanced Integration, such as AAD. The prerequisite is that the identity provider must have already consented to sharing access to its directory with the OCS tenant.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/IdentityProviders/{identityProviderId}/groups/{groupId}/members
?count={count}&skipToken={skipToken}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/>`string identityProviderId`
<br/>Identity provider unique identifier<br/><br/>`string groupId`
<br/>Group unique identifier<br/><br/>
`[optional] integer count`
<br/>Maximum number of users to return<br/><br/>`[optional] string skipToken`
<br/>An encoded string that identifies the set of users that was not returned. For example, if you request a count of the first 50 users matching your query, the skipToken identifies the 51st user.<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[IdentityProviderMembers](#schemaidentityprovidermembers)|List of members|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|404|[ErrorResponse](#schemaerrorresponse)|Identity provider or tenant not found.|
|408|[ErrorResponse](#schemaerrorresponse)|Operation timed out|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

#### Example response body
> 200 Response

```json
{
  "Users": [
    {
      "Id": "string",
      "GivenName": "string",
      "Surname": "string",
      "Name": "string",
      "Email": "user@example.com"
    }
  ],
  "Groups": [
    {
      "Id": "string",
      "Name": "string",
      "Email": "user@example.com",
      "IsClusterManagementAllowed": true
    }
  ],
  "SkipToken": "string"
}
```

### Authorization

Allowed for these roles: 
<ul>
<li>Tenant Administrator</li>
</ul>

---

## `Get a List of All Users on an Identity Provider`

<a id="opIdIdentityProviders_Get a List of All Users on an Identity Provider"></a>

Gets a list of users that matches the query string on an identity provider that supports Advanced Integration, such as AAD. The prerequisite is that the identity provider must have already consented to sharing access to its directory with the OCS tenant.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/IdentityProviders/{identityProviderId}/users
?query={query}&count={count}&skipToken={skipToken}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/>`string identityProviderId`
<br/>Identity provider unique identifier<br/><br/>`string query`
<br/>Start of user name or email to search for.<br/><br/>
`[optional] integer count`
<br/>Maximum number of users to returns.<br/><br/>`[optional] string skipToken`
<br/>An encoded string that identifies the set of users that was not returned. For example, if you specify a count of the first 50 users matching your query, the skipToken identifies the 51st user.<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[IdentityProviderResultsOfIdentityProviderUser](#schemaidentityproviderresultsofidentityprovideruser)|List of users found|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|404|[ErrorResponse](#schemaerrorresponse)|Identity provider or tenant not found.|
|408|[ErrorResponse](#schemaerrorresponse)|Operation timed out|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

#### Example response body
> 200 Response

```json
{
  "Results": [
    {
      "Id": "string",
      "GivenName": "string",
      "Surname": "string",
      "Name": "string",
      "Email": "user@example.com"
    }
  ],
  "SkipToken": "string"
}
```

### Authorization

Allowed for these roles: 
<ul>
<li>Tenant Administrator</li>
</ul>

---

## `Get a List of All Groups that a User Belongs to on an Identity Provider`

<a id="opIdIdentityProviders_Get a List of All Groups that a User Belongs to on an Identity Provider"></a>

Gets a list of all groups that the specified user belongs to on an identity provider that supports Advanced Integration, such as AAD. The prerequisite is that the identity provider must have already consented to sharing access to its directory with the OCS tenant. The consent grants User.Read.All and GroupMember.Read.All permissions to the OCS tenant.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/IdentityProviders/{identityProviderId}/Users/{userId}/Groups
?skip={skip}&count={count}&timeout={timeout}&skipToken={skipToken}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/>`string identityProviderId`
<br/>Identity provider unique identifier<br/><br/>`string userId`
<br/>User unique identifier<br/><br/>
`[optional] integer skip`
<br/>Indexes into a result set<br/><br/>`[optional] integer count`
<br/>Maximum number of groups to return<br/><br/>`[optional] integer timeout`
<br/>The maximum time to allow for searching groups before returning the groups.<br/><br/>`[optional] string skipToken`
<br/>An encoded string that identifies the set of groups that was not returned. For example, if you request a count of the first 3 groups matching your query, the skipToken identifies the 4th user.<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[IdentityProviderResultsOfIdentityProviderGroup](#schemaidentityproviderresultsofidentityprovidergroup)|List of groups user is a member of|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|404|[ErrorResponse](#schemaerrorresponse)|Identity provider or tenant not found.|
|408|[ErrorResponse](#schemaerrorresponse)|Operation timed out|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

#### Example response body
> 200 Response

```json
{
  "Results": [
    {
      "Id": "string",
      "Name": "string",
      "Email": "user@example.com",
      "IsClusterManagementAllowed": true
    }
  ],
  "SkipToken": "string"
}
```

### Authorization

Allowed for these roles: 
<ul>
<li>Tenant Administrator</li>
</ul>

---
# Definitions

## IdentityProvider

<a id="schemaidentityprovider"></a>
<a id="schema_IdentityProvider"></a>
<a id="tocSidentityprovider"></a>
<a id="tocsidentityprovider"></a>

The IdentityProvider object

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|guid|false|false|Identity provider unique identifier|
|DisplayName|string|false|true|Identity provider display name to use|
|Scheme|string|false|true|Name of the cookie handler that will temporarily store the outcome of the external authentication|
|UserIdClaimType|string|false|true|Type of claim|
|ClientId|string|false|true|Client Id of the identity provider|
|IsConfigured|boolean|false|false|Whether the identity provider has been configured|
|Capabilities|[IdentityProviderCapabilities](#schemaidentityprovidercapabilities)|false|true|Capabilities of the identity provider|

```json
{
  "Id": "string",
  "DisplayName": "string",
  "Scheme": "string",
  "UserIdClaimType": "string",
  "ClientId": "string",
  "IsConfigured": true,
  "Capabilities": {
    "User": {
      "SignIn": null,
      "Invitation": null,
      "Search": null
    },
    "Group": {
      "Authorize": null,
      "Search": null
    }
  }
}

```

---

## IdentityProviderCapabilities

<a id="schemaidentityprovidercapabilities"></a>
<a id="schema_IdentityProviderCapabilities"></a>
<a id="tocSidentityprovidercapabilities"></a>
<a id="tocsidentityprovidercapabilities"></a>

The model for the capabilities of an identity provider

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|User|[IdentityProviderUserCapabilites](#schemaidentityproviderusercapabilites)|false|true|User-level capabilities|
|Group|[IdentityProviderGroupCapabilites](#schemaidentityprovidergroupcapabilites)|false|true|Group-level capabilities|

```json
{
  "User": {
    "SignIn": true,
    "Invitation": true,
    "Search": true
  },
  "Group": {
    "Authorize": true,
    "Search": true
  }
}

```

---

## IdentityProviderUserCapabilites

<a id="schemaidentityproviderusercapabilites"></a>
<a id="schema_IdentityProviderUserCapabilites"></a>
<a id="tocSidentityproviderusercapabilites"></a>
<a id="tocsidentityproviderusercapabilites"></a>

User-level capabilities of an identity provider

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|SignIn|boolean|false|false|Value indicating whether user log in is supported|
|Invitation|boolean|false|false|Value indicating whether authorization via the invitation flow is supported|
|Search|boolean|false|false|Value indicating whether user search is supported|

```json
{
  "SignIn": true,
  "Invitation": true,
  "Search": true
}

```

---

## IdentityProviderGroupCapabilites

<a id="schemaidentityprovidergroupcapabilites"></a>
<a id="schema_IdentityProviderGroupCapabilites"></a>
<a id="tocSidentityprovidergroupcapabilites"></a>
<a id="tocsidentityprovidergroupcapabilites"></a>

The model for the group level capabilities of an identity provider

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Authorize|boolean|false|false|Value indicating whether authorization via groups is supported|
|Search|boolean|false|false|Value indicating whether group search is supported|

```json
{
  "Authorize": true,
  "Search": true
}

```

---

## ErrorResponse

<a id="schemaerrorresponse"></a>
<a id="schema_ErrorResponse"></a>
<a id="tocSerrorresponse"></a>
<a id="tocserrorresponse"></a>

Object returned whenever there is an error TODO: Remove this internal model and re-adopt public model when moving to System.Text.Json in WI 202168.

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|true|false|Gets or sets operationId of action that caused the Error.|
|Error|string|true|false|Gets or sets error description.|
|Reason|string|true|false|Gets or sets reason for the Error.|
|Resolution|string|true|false|Gets or sets what can be done to resolve the Error.|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "property1": null,
  "property2": null
}

```

---

## IdentityProviderConsent

<a id="schemaidentityproviderconsent"></a>
<a id="schema_IdentityProviderConsent"></a>
<a id="tocSidentityproviderconsent"></a>
<a id="tocsidentityproviderconsent"></a>

The model for an identity provider consent in identity storage. TODO: Remove this internal model and re-adopt public model when moving to System.Text.Json in WI 202168.

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Scheme|string|false|true|Scheme of the identity provider.|

```json
{
  "Scheme": "string",
  "property1": null,
  "property2": null
}

```

---

## IdentityProviderAdd

<a id="schemaidentityprovideradd"></a>
<a id="schema_IdentityProviderAdd"></a>
<a id="tocSidentityprovideradd"></a>
<a id="tocsidentityprovideradd"></a>

Object for adding an identity provider.

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|AzureActiveDirectoryConsentEmail|email|false|true|Email address to send consent.|
|AzureActiveDirectoryConsentGivenName|string|false|true|Preferred name to use in the consent email.|
|AzureActiveDirectoryConsentSurname|string|false|true|Preferred surname to use in the consent email.|
|AzureActiveDirectoryTenant|string|false|true|AAD tenant domain name (for example, mydomain.onmicrosoft.com).|
|AzureActiveDirectoryConsentTypes|string|false|true|Semicolon delimited AAD consent types. Can be "SignIn" or "SignIn;ReadAllUsersGroups".|
|IdentityProviderId|guid|false|false|Identity provider unique identifier.|
|AzureActiveDirectorySendConsent|boolean|false|false|Whether to send consent email for AAD.|

```json
{
  "AzureActiveDirectoryConsentEmail": "user@example.com",
  "AzureActiveDirectoryConsentGivenName": "string",
  "AzureActiveDirectoryConsentSurname": "string",
  "AzureActiveDirectoryTenant": "string",
  "AzureActiveDirectoryConsentTypes": "string",
  "IdentityProviderId": "string",
  "AzureActiveDirectorySendConsent": true
}

```

---

## IdentityProviderResultsOfIdentityProviderUser

<a id="schemaidentityproviderresultsofidentityprovideruser"></a>
<a id="schema_IdentityProviderResultsOfIdentityProviderUser"></a>
<a id="tocSidentityproviderresultsofidentityprovideruser"></a>
<a id="tocsidentityproviderresultsofidentityprovideruser"></a>

Result object for Identity Provider access users/groups.

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Results|[[IdentityProviderUser](#schemaidentityprovideruser)]|false|false|List of users/groups.|
|SkipToken|string|false|true|Skip token for paging.|

```json
{
  "Results": [
    {
      "Id": "string",
      "GivenName": "string",
      "Surname": "string",
      "Name": "string",
      "Email": "user@example.com"
    }
  ],
  "SkipToken": "string"
}

```

---

## IdentityProviderUser

<a id="schemaidentityprovideruser"></a>
<a id="schema_IdentityProviderUser"></a>
<a id="tocSidentityprovideruser"></a>
<a id="tocsidentityprovideruser"></a>

Base class for identity provider access user.

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|false|User unique identifier.|
|GivenName|string|false|true|Given name of the user.|
|Surname|string|false|true|Surname of the user.|
|Name|string|false|true|Name of the user.|
|Email|email|false|true|Email of the user.|

```json
{
  "Id": "string",
  "GivenName": "string",
  "Surname": "string",
  "Name": "string",
  "Email": "user@example.com"
}

```

---

## IdentityProviderResultsOfIdentityProviderGroup

<a id="schemaidentityproviderresultsofidentityprovidergroup"></a>
<a id="schema_IdentityProviderResultsOfIdentityProviderGroup"></a>
<a id="tocSidentityproviderresultsofidentityprovidergroup"></a>
<a id="tocsidentityproviderresultsofidentityprovidergroup"></a>

Result object for Identity Provider access users/groups.

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Results|[[IdentityProviderGroup](#schemaidentityprovidergroup)]|false|false|List of users/groups.|
|SkipToken|string|false|true|Skip token for paging.|

```json
{
  "Results": [
    {
      "Id": "string",
      "Name": "string",
      "Email": "user@example.com",
      "IsClusterManagementAllowed": true
    }
  ],
  "SkipToken": "string"
}

```

---

## IdentityProviderGroup

<a id="schemaidentityprovidergroup"></a>
<a id="schema_IdentityProviderGroup"></a>
<a id="tocSidentityprovidergroup"></a>
<a id="tocsidentityprovidergroup"></a>

Base class for identity provider access group.

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|false|Object unique identifier of the IdentityProviderGroup.|
|Name|string|false|true|Group name of the IdentityProviderGroup.|
|Email|email|false|true|Email address of the IdentityProviderGroup.|
|IsClusterManagementAllowed|boolean|false|true|Value indicating whether group can manage cluster roles.|

```json
{
  "Id": "string",
  "Name": "string",
  "Email": "user@example.com",
  "IsClusterManagementAllowed": true
}

```

---

## IdentityProviderMembers

<a id="schemaidentityprovidermembers"></a>
<a id="schema_IdentityProviderMembers"></a>
<a id="tocSidentityprovidermembers"></a>
<a id="tocsidentityprovidermembers"></a>

Class to hold members in a group.

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Users|[[IdentityProviderUser](#schemaidentityprovideruser)]|false|false|List of users.|
|Groups|[[IdentityProviderGroup](#schemaidentityprovidergroup)]|false|false|List of groups.|
|SkipToken|string|false|true|Skip token for paging.|

```json
{
  "Users": [
    {
      "Id": "string",
      "GivenName": "string",
      "Surname": "string",
      "Name": "string",
      "Email": "user@example.com"
    }
  ],
  "Groups": [
    {
      "Id": "string",
      "Name": "string",
      "Email": "user@example.com",
      "IsClusterManagementAllowed": true
    }
  ],
  "SkipToken": "string"
}

```

---

