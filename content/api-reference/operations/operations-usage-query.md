

# Usage Query
APIs related to querying Usage data.

## `List Namespace Usage`

<a id="opIdQuery_List Namespace Usage"></a>

Gets **Namespace** usage data calculated based on active / completed billing cycles, when the **start** and **end** parameters are omitted. When **start** is provided and **end** is omitted, a single day of usage data is returned. When both **start** and **end** are provided, daily usage data is returned from the provided range.

### Request
```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/usage
?start={start}&end={end}
```

#### Parameters

`string tenantId`
<br/>Id of the Tenant<br/><br/>`string namespaceId`
<br/>Id of the Namespace<br/><br/>
`[optional] string start`
<br/>Start date of the usage for daily usage data.<br/><br/>`[optional] string end`
<br/>End date of the daily usage data, if there is no end date only one summary is returned<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[UsageDataRecord](#schemausagedatarecord)[]|Usage data for the requested **Namespace**|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs|
|401|None|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

#### Example response body
> 200 Response

```json
[
  {
    "Date": "2019-08-24T14:15:22Z",
    "TenantId": "string",
    "NamespaceId": "string",
    "ClusterRegion": "string",
    "IngressEvents": 0,
    "IngressStreamsAccessed": 0,
    "EgressEvents": 0,
    "EgressStreamsAccessed": 0
  }
]
```

---

## `Get Tenant Resource Usage`

<a id="opIdQuery_Get Tenant Resource Usage"></a>

Gets the current resource usage vs the entitled resource usage.

### Request
```text 
GET /api/v1/tenants/{tenantId}/resources/usage
```

#### Parameters

`string tenantId`
<br/>Id of the Tenant<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[ResourceUsage](#schemaresourceusage)|Current resource usage vs entitled resource usage.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs|
|401|None|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

#### Example response body
> 200 Response

```json
{
  "StreamCount": 0,
  "EntitledStreamCount": 0,
  "NamespaceCount": 0,
  "EntitledNamespaceCount": 0,
  "EntitledStreamAccessCount": 0
}
```

---

## `List Tenant Billing Cycles`

<a id="opIdQuery_List Tenant Billing Cycles"></a>

Gets the billing cycles for an account inferred from the account's subscription.

### Request
```text 
GET /api/v1/tenants/{tenantId}/subscriptionterm/billingcycles
```

#### Parameters

`string tenantId`
<br/>Id of the Tenant<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[BillingCycle](#schemabillingcycle)[]|List of billing cycles for the account's subscription that have elapsed.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs|
|401|None|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

#### Example response body
> 200 Response

```json
[
  {
    "StartDate": "2019-08-24T14:15:22Z",
    "EndDate": "2019-08-24T14:15:22Z"
  }
]
```

---

## `List Tenant Usage`

<a id="opIdQuery_List Tenant Usage"></a>

Gets **Tenant** usage data calculated based on active / completed billing cycles, when the **start** and **end** parameters are omitted. When **start** is provided and **end** is omitted, a single day of usage data is returned. When both **start** and **end** are provided, daily usage data is returned from the provided range.

### Request
```text 
GET /api/v1/tenants/{tenantId}/usage
?start={start}&end={end}&groupByNamespace={groupByNamespace}
```

#### Parameters

`string tenantId`
<br/>Id of the Tenant<br/><br/>
`[optional] string start`
<br/>Start date of the usage for daily usage data.<br/><br/>`[optional] string end`
<br/>End date of the daily usage data, if there is no end date only one summary is returned<br/><br/>`[optional] boolean groupByNamespace`
<br/>When **true** the usage data is grouped by namespaces.<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[UsageDataRecord](#schemausagedatarecord)[]|Usage data for the requested **Tenant**|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs|
|401|None|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

#### Example response body
> 200 Response

```json
[
  {
    "Date": "2019-08-24T14:15:22Z",
    "TenantId": "string",
    "NamespaceId": "string",
    "ClusterRegion": "string",
    "IngressEvents": 0,
    "IngressStreamsAccessed": 0,
    "EgressEvents": 0,
    "EgressStreamsAccessed": 0
  }
]
```

---
## Definitions

### UsageDataRecord

<a id="schemausagedatarecord"></a>
<a id="schema_UsageDataRecord"></a>
<a id="tocSusagedatarecord"></a>
<a id="tocsusagedatarecord"></a>

Model representing Usage within OCS.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Date|date-time|true|false|Represents the date property of a usage record|
|TenantId|guid|true|false|Represents the tenant name of a usage record|
|NamespaceId|string|false|true|Represents the namespaceId of a usage record|
|ClusterRegion|string|false|true|Represents the cluster region the record belongs to|
|IngressEvents|int64|true|false|Represents the total amount of events ingressed of a usage record|
|IngressStreamsAccessed|int64|true|false|Represents the count of ingress streams accessed of a usage record|
|EgressEvents|int64|true|false|Represents the total amount of events egressed of a usage record|
|EgressStreamsAccessed|int64|true|false|Represents the count of egress streams accessed of a usage record|

```json
{
  "Date": "2019-08-24T14:15:22Z",
  "TenantId": "string",
  "NamespaceId": "string",
  "ClusterRegion": "string",
  "IngressEvents": 0,
  "IngressStreamsAccessed": 0,
  "EgressEvents": 0,
  "EgressStreamsAccessed": 0
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
|OperationId|string|false|true|Gets or sets operationId of action that caused the Error.|
|Error|string|false|true|Gets or sets error description.|
|Reason|string|false|true|Gets or sets reason for the Error.|
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

### ResourceUsage

<a id="schemaresourceusage"></a>
<a id="schema_ResourceUsage"></a>
<a id="tocSresourceusage"></a>
<a id="tocsresourceusage"></a>

Resources currently allocated by an account and their entitled amounts

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|StreamCount|int64|true|false|Streams allocated by the account across all namespaces.|
|EntitledStreamCount|int64|true|false|Entitled amount of streams that can be allocated.|
|NamespaceCount|int64|true|false|Number of namespaces allocated by the account.|
|EntitledNamespaceCount|int64|true|false|Entitled number of namespaces that can be allocated.|
|EntitledStreamAccessCount|int64|true|false|Entitled number of average streams that can be accessed per day.|

```json
{
  "StreamCount": 0,
  "EntitledStreamCount": 0,
  "NamespaceCount": 0,
  "EntitledNamespaceCount": 0,
  "EntitledStreamAccessCount": 0
}

```

---

### BillingCycle

<a id="schemabillingcycle"></a>
<a id="schema_BillingCycle"></a>
<a id="tocSbillingcycle"></a>
<a id="tocsbillingcycle"></a>

Represents a completed billing cycle for an account.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|StartDate|date-time|true|false|Start of the billing cycle.|
|EndDate|date-time|true|false|End of the billing cycle|

```json
{
  "StartDate": "2019-08-24T14:15:22Z",
  "EndDate": "2019-08-24T14:15:22Z"
}

```

---

