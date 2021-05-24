---
uid: operations-health

---

# Health
APIs related to querying OCS Service health states.

## `Get Tenant Health`

<a id="opIdQuery_Get Tenant Health"></a>

Gets **Tenant** health data containing an aggregated health state and a list of services related to the tenant.

### Request
```text 
GET /api/v1/tenants/{tenantId}/health
```

#### Parameters

`string tenantId`
<br/>Id of the Tenant<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[TenantViewModel](#schematenantviewmodel)|Health data for the requested **Tenant**|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs|
|401|None|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

#### Example response body
> 200 Response

```json
{
  "HealthState": 0,
  "Namespaces": [
    {
      "NamespaceId": "string",
      "Region": "string",
      "HealthState": 0,
      "Services": [
        {
          "Name": "string",
          "HealthState": null
        }
      ]
    }
  ]
}
```

---
## Definitions

### TenantViewModel

<a id="schematenantviewmodel"></a>
<a id="schema_TenantViewModel"></a>
<a id="tocStenantviewmodel"></a>
<a id="tocstenantviewmodel"></a>

This represents a view model of a TenantDbo

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|HealthState|[State](#schemastate)|false|false|Health state of the tenant|
|Namespaces|[[NamespaceViewModel](#schemanamespaceviewmodel)]|false|true|Namespaces scoped to this tenant|

```json
{
  "HealthState": 0,
  "Namespaces": [
    {
      "NamespaceId": "string",
      "Region": "string",
      "HealthState": 0,
      "Services": [
        {
          "Name": "string",
          "HealthState": null
        }
      ]
    }
  ]
}

```

---

### State

<a id="schemastate"></a>
<a id="schema_State"></a>
<a id="tocSstate"></a>
<a id="tocsstate"></a>

Represents the various health states a HealthEventViewModel can represent.

#### Enumerated Values

|Property|Value|
|---|---|
|Invalid|0|
|Ok|1|
|Warning|2|
|Error|3|
|Unknown|65535|

---

### NamespaceViewModel

<a id="schemanamespaceviewmodel"></a>
<a id="schema_NamespaceViewModel"></a>
<a id="tocSnamespaceviewmodel"></a>
<a id="tocsnamespaceviewmodel"></a>

This represents a view model of a TenantDbo namespace and its underlying services.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|NamespaceId|string|false|true|Id of the Namespace|
|Region|string|false|true|Region of the Namespace|
|HealthState|[State](#schemastate)|false|false|Health state of the Namespace|
|Services|[[ServiceForTenantViewModel](#schemaservicefortenantviewmodel)]|false|true|Services scoped to this Namespace|

```json
{
  "NamespaceId": "string",
  "Region": "string",
  "HealthState": 0,
  "Services": [
    {
      "Name": "string",
      "HealthState": 0
    }
  ]
}

```

---

### ServiceForTenantViewModel

<a id="schemaservicefortenantviewmodel"></a>
<a id="schema_ServiceForTenantViewModel"></a>
<a id="tocSservicefortenantviewmodel"></a>
<a id="tocsservicefortenantviewmodel"></a>

This represents a view model of a ServiceForTenantDbo

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|Name of the Service|
|HealthState|[State](#schemastate)|false|false|Health state of the service|

```json
{
  "Name": "string",
  "HealthState": 0
}

```

---

### ErrorResponse

<a id="schemaerrorresponse"></a>
<a id="schema_ErrorResponse"></a>
<a id="tocSerrorresponse"></a>
<a id="tocserrorresponse"></a>

Object used to represent error information.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|false|true|Gets or sets Operation Id of action that caused the Error.|
|Error|string|false|true|Gets or sets the Error description.|
|Reason|string|false|true|Gets or sets the Reason for the Error.|
|Resolution|string|false|true|Gets or set the Resolution for the Error.|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string"
}

```

---

