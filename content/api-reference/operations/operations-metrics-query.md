

# Metrics Query
APIs related to querying tenant metrics.

## `List Namespace Metrics`

<a id="opIdQuery_List Namespace Metrics"></a>

Gets a namespace scoped metric.

### Request
```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/metrics/{collection}/{metricId}
?start={start}&end={end}
```

#### Parameters

`string tenantId`
<br/>Id of the tenant for this metric.<br/><br/>`string namespaceId`
<br/>Id of the namespace for this metric.<br/><br/>`string collection`
<br/>Collection name of this metric.<br/><br/>`string metricId`
<br/>Id of this metric under the supplied collection.<br/><br/>`string start`
<br/>Start date of the metric results to return.<br/><br/>`string end`
<br/>End date of the metric results to return.<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[AiMetricSample](#schemaaimetricsample)[]|Time series values for this queried metric.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs|
|401|None|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|404|None|Metric Not Found|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

#### Example response body
> 200 Response

```json
[
  {
    "Timestamp": "2019-08-24T14:15:22Z",
    "Value": 0
  }
]
```

---
## Definitions

### AiMetricSample

<a id="schemaaimetricsample"></a>
<a id="schema_AiMetricSample"></a>
<a id="tocSaimetricsample"></a>
<a id="tocsaimetricsample"></a>

Represents a sample from a range of requested metrics. Mainly used in testing and documentation.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Timestamp|date-time|false|false|The timestamp of when the value was sampled|
|Value|double|false|false|The value of the metric at the given timestamp|

```json
{
  "Timestamp": "2019-08-24T14:15:22Z",
  "Value": 0
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

