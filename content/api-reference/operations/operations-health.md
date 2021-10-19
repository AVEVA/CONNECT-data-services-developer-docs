---
uid: operations-health

---

# Health
APIs related to querying OCS Service health states.

## `Get Tenant Health`

<a id="opIdQuery_Get Tenant Health"></a>

Get **Tenant** health data containing an aggregated health state and a list of services related to the tenant.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/health
```

<h4>Parameters</h4>

`string tenantId`
<br/>Id of the Tenant<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[TenantViewModel](#schematenantviewmodel)|Health data for the requested **Tenant**|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs|
|401|None|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

<h4>Example response body</h4>

> 200 Response ([TenantViewModel](#schematenantviewmodel))

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
          "HealthState": 0
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

<h4>Properties</h4>

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
          "HealthState": 0
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

<h4>Enumerated Values</h4>

|Property|Value|Description|
|---|---|---|
|Invalid|0|Not used, means the enumeration value is invalid.|
|Ok|1|Health event is in a good state.|
|Warning|2|Health event is in a warning state.|
|Error|3|Health event is in an error state.|
|Unknown|65535|Health event is in an unknown state indicating the service is starting up.|

---

### NamespaceViewModel

<a id="schemanamespaceviewmodel"></a>
<a id="schema_NamespaceViewModel"></a>
<a id="tocSnamespaceviewmodel"></a>
<a id="tocsnamespaceviewmodel"></a>

This represents a view model of a TenantDbo namespace and its underlying services.

<h4>Properties</h4>

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

<h4>Properties</h4>

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

<h4>Properties</h4>

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

