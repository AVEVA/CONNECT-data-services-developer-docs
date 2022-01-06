---
uid: tenant-features

---

# Features
APIs for managing the feature states of a Tenant.

## `List All`

<a id="opIdTenantFeatureState_List All"></a>

Returns all `FeatureState`s for the specified `Tenant`.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Features
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[FeatureState](#schemafeaturestate)[]|An array of all `Feature`s for the tenant with identifier `tenantId`.|
|400|None|Missing or invalid inputs.|
|403|None|Forbidden.|

<h4>Example response body</h4>

> 200 Response ([FeatureState](#schemafeaturestate)[])

```json
[
  {
    "Feature": {
      "Id": "string",
      "Name": "string",
      "Description": "string",
      "DefaultState": 0
    },
    "CurrentState": 0
  }
]
```

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `Get`

<a id="opIdTenantFeatureState_Get"></a>

Returns a `FeatureState` with the specified identifier from a `Tenant`.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Features/{id}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string id`
<br/>Feature state identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[FeatureState](#schemafeaturestate)|The state of the `Feature` for the tenant with identifier `tenantId`.|
|400|None|Missing or invalid inputs.|
|403|None|Forbidden.|

<h4>Example response body</h4>

> 200 Response ([FeatureState](#schemafeaturestate))

```json
{
  "Feature": {
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "DefaultState": 0
  },
  "CurrentState": 0
}
```

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---
## Definitions

### FeatureState

<a id="schemafeaturestate"></a>
<a id="schema_FeatureState"></a>
<a id="tocSfeaturestate"></a>
<a id="tocsfeaturestate"></a>

Representation of a server-side database interpretation of a feature state.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Feature|[Feature](#schemafeature)|false|true|The feature to which the feature state corresponds.|
|CurrentState|int32|false|false|Current state of the feature.|

```json
{
  "Feature": {
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "DefaultState": 0
  },
  "CurrentState": 0
}

```

---

### Feature

<a id="schemafeature"></a>
<a id="schema_Feature"></a>
<a id="tocSfeature"></a>
<a id="tocsfeature"></a>

Representation of a server-side database interpretation of a feature.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Identifier of this feature.|
|Name|string|false|true|Name of the feature.|
|Description|string|false|true|Description of the feature.|
|DefaultState|int32|false|false|Default state of the feature.|

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "DefaultState": 0
}

```

---

