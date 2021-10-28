---
uid: identity-claim-type-names

---

# Claim Type Names
An identity provider claim type name is the attribute needed when creating an identity provider claim.

## `List All Identity Provider Claim Type Names`

<a id="opIdClaimTypeNames_List All Identity Provider Claim Type Names"></a>

Returns all identity provider claim type names for an identity provider on a tenant.

<h3>Request</h3>

```text 
GET /api/v1/IdentityProviders/{identityProviderId}/ClaimTypeNames
?query={query}&skip={skip}&count={count}
```

<h4>Parameters</h4>

`string identityProviderId`
<br/>##identityProviderId<br/><br/>
`[optional] string query`
<br/>##query-searchstring<br/><br/>`[optional] integer skip`
<br/>##skip<br/><br/>`[optional] integer count`
<br/>##count<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[IdentityProviderClaimTypeName](#schemaidentityproviderclaimtypename)[]|List of identity provider type names found|
|401|[ErrorResponse](#schemaerrorresponse)|##401|
|403|[ErrorResponse](#schemaerrorresponse)|##403|
|404|[ErrorResponse](#schemaerrorresponse)|Identity provider not found|
|500|[ErrorResponse](#schemaerrorresponse)|##500|

<h4>Example response body</h4>

> 200 Response ([IdentityProviderClaimTypeName](#schemaidentityproviderclaimtypename)[])

```json
[
  {
    "Id": "string",
    "TypeName": "string",
    "IdentityProviderId": "string"
  }
]
```

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Administrator</li>
</ul>

---

## `Get All Identity Provider Claim Type Names Header`

<a id="opIdClaimTypeNames_Get All Identity Provider Claim Type Names Header"></a>

Returns a header for all identity provider claim type names for an identity provider on a tenant.

<h3>Request</h3>

```text 
HEAD /api/v1/IdentityProviders/{identityProviderId}/ClaimTypeNames
```

<h4>Parameters</h4>

`string identityProviderId`
<br/>##identityProviderId<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Header for identity provider claim type names|
|401|None|##401|
|403|None|##403|
|404|None|Identity provider not found|
|500|None|##500|

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Administrator</li>
</ul>

---

## `Get Identity Provider Claim Type Name`

<a id="opIdClaimTypeNames_Get Identity Provider Claim Type Name"></a>

Returns an identity provider claim type name from an identity provider.

<h3>Request</h3>

```text 
GET /api/v1/IdentityProviders/{identityProviderId}/ClaimTypeNames/{identityProviderClaimTypeNameId}
```

<h4>Parameters</h4>

`string identityProviderId`
<br/>##identityProviderId<br/><br/>`string identityProviderClaimTypeNameId`
<br/>##identityProviderTypeNameClaimId<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[IdentityProviderClaim](#schemaidentityproviderclaim)|Identity provider claim type name specified|
|401|[ErrorResponse](#schemaerrorresponse)|##401|
|403|[ErrorResponse](#schemaerrorresponse)|##403|
|404|[ErrorResponse](#schemaerrorresponse)|Identity provider or identity provider claim type name not found|
|500|[ErrorResponse](#schemaerrorresponse)|##500|

<h4>Example response body</h4>

> 200 Response ([IdentityProviderClaim](#schemaidentityproviderclaim))

```json
{
  "Id": "string",
  "TypeName": "string",
  "Value": "string",
  "RoleIds": [
    "string"
  ],
  "IsBuiltIn": true
}
```

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Administrator</li>
</ul>

---

## `Get Identity Provider Claim Type Name Header`

<a id="opIdClaimTypeNames_Get Identity Provider Claim Type Name Header"></a>

Returns an identity provider claim type name header from an identity provider.

<h3>Request</h3>

```text 
HEAD /api/v1/IdentityProviders/{identityProviderId}/ClaimTypeNames/{identityProviderClaimTypeNameId}
```

<h4>Parameters</h4>

`string identityProviderId`
<br/>##identityProviderId<br/><br/>`string identityProviderClaimTypeNameId`
<br/>##identityProviderTypeNameClaimId<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Header for identity provider claim type name specified|
|401|None|##401|
|403|None|##403|
|404|None|Identity provider or identity provider claim type name not found|
|500|None|##500|

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Administrator</li>
</ul>

---
## Definitions

### IdentityProviderClaimTypeName

<a id="schemaidentityproviderclaimtypename"></a>
<a id="schema_IdentityProviderClaimTypeName"></a>
<a id="tocSidentityproviderclaimtypename"></a>
<a id="tocsidentityproviderclaimtypename"></a>

Claim type name associated with an identity provider

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|guid|false|false|Claim type name identifier|
|TypeName|string|false|true|Claim type name|
|IdentityProviderId|guid|false|false|Identifier of identity provider associated with this claim type name|

```json
{
  "Id": "string",
  "TypeName": "string",
  "IdentityProviderId": "string"
}

```

---

### ErrorResponse

<a id="schemaerrorresponse"></a>
<a id="schema_ErrorResponse"></a>
<a id="tocSerrorresponse"></a>
<a id="tocserrorresponse"></a>

Object returned whenever there is an error

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|true|false|Operation identifier of action that caused the error|
|Error|string|true|false|Error description|
|Reason|string|true|false|Reason for the error|
|Resolution|string|true|false|Resolution to resolve the error|
|DynamicProperties|object|false|true|Additional properties|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "DynamicProperties": {
    "property1": null,
    "property2": null
  },
  "property1": null,
  "property2": null
}

```

---

### IdentityProviderClaim

<a id="schemaidentityproviderclaim"></a>
<a id="schema_IdentityProviderClaim"></a>
<a id="tocSidentityproviderclaim"></a>
<a id="tocsidentityproviderclaim"></a>

Object representing a claim from an identity provider to map to a role

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|guid|false|false|Identity provider claim identifier|
|TypeName|string|false|true|Type name for this identity provider claim|
|Value|string|false|true|Value for this identity provider claim|
|RoleIds|string[]|false|true|List of role identifiers that this claim on this identity provider will map|
|IsBuiltIn|boolean|false|false|Indicates if this claim entry is built-in. When this value is true, callers cannot modify or delete the claim.|

```json
{
  "Id": "string",
  "TypeName": "string",
  "Value": "string",
  "RoleIds": [
    "string"
  ],
  "IsBuiltIn": true
}

```

---

