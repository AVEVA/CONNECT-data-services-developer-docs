---
uid: sds-stream-bulk-data

---

# Stream Bulk Data
The API in this section interacts with data from multiple streams.

## `List Window Values (GET Method)`

<a id="opIdStreamsData_List Window Values (GET Method)"></a>

Returns data from multiple streams, joined based on the request specifications. Streams must be of the same type.
GET and POST join requests are supported.
        
[GET method](xref:sdsReadingDataApi#getjoin): ``stream``, ``joinMode``, ``startIndex``, and ``endIndex`` are specified in the request URI.

[POST method](xref:sdsReadingDataApi#post-request): only ``joinMode`` is specified in the URI. Streams and read specifications for each stream are specified in the request body.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Bulk/Streams/Data/Joins
?streams={streams}&joinMode={joinMode}&startIndex={startIndex}&endIndex={endIndex}&count={count}&boundaryType={boundaryType}&startBoundaryType={startBoundaryType}&endBoundaryType={endBoundaryType}&filter={filter}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>
`[optional] string streams`
<br/>Comma separated list of stream identifiers.<br/><br/>`[optional] integer joinMode`
<br/>The , type of join: Inner, Outer, Interpolated, MergeLeft, or MergeRight.<br/><br/>`[optional] string startIndex`
<br/>Index identifying the beginning of the series of events to return.<br/><br/>`[optional] string endIndex`
<br/>Index identifying the end of the series of events to return.<br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of objects to retrieve. If unspecified, a default value of 100 is used.<br/><br/>`[optional] integer boundaryType`
<br/>SdsBoundaryType specifying the handling of events at or near the start and end indexes.<br/><br/>`[optional] integer startBoundaryType`
<br/>SdsBoundaryType specifying the first value in the result in relation to the start index. If startBoundaryType is specified, endBoundaryType must be specified.<br/><br/>`[optional] integer endBoundaryType`
<br/>SdsBoundaryType specifies the last value in the result in relation to the end index. If startBoundaryType is specified, endBoundaryType must be specified.<br/><br/>`[optional] string filter`
<br/>Filter expression.<br/><br/>

<h4>Enumerated Values</h4>

|Parameter|Value|
|---|---|
|joinMode|0|
|joinMode|1|
|joinMode|2|
|joinMode|3|
|joinMode|4|
|boundaryType|0|
|boundaryType|1|
|boundaryType|2|
|boundaryType|3|
|startBoundaryType|0|
|startBoundaryType|1|
|startBoundaryType|2|
|startBoundaryType|3|
|endBoundaryType|0|
|endBoundaryType|1|
|endBoundaryType|2|
|endBoundaryType|3|

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Returns multiple serialized events|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|409|[ErrorResponseBody](#schemaerrorresponsebody)|Conflict|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

<h4>Example response body</h4>

> 400 Response ([ErrorResponseBody](#schemaerrorresponsebody))

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  }
}
```

---

## `Get Window Values (POST Method)`

<a id="opIdStreamsData_Get Window Values (POST Method)"></a>

Returns data from multiple streams, joined based on the request specifications. Streams must be of the same type.
GET and POST join requests are supported.
        
[GET method](xref:sdsReadingDataApi#getjoin): ``stream``, ``joinMode``, ``startIndex``, and ``endIndex`` are specified in the request URI.

[POST method](xref:sdsReadingDataApi#post-request): only ``joinMode`` is specified in the URI. Streams and read specifications for each stream are specified in the request body.

<h3>Request</h3>

```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Bulk/Streams/Data/Joins
?streams={streams}&joinMode={joinMode}&startIndex={startIndex}&endIndex={endIndex}&count={count}&boundaryType={boundaryType}&startBoundaryType={startBoundaryType}&endBoundaryType={endBoundaryType}&filter={filter}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>
`[optional] string streams`
<br/>Comma separated list of stream identifiers.<br/><br/>`[optional] integer joinMode`
<br/>The , type of join: Inner, Outer, Interpolated, MergeLeft, or MergeRight.<br/><br/>`[optional] string startIndex`
<br/>Index identifying the beginning of the series of events to return.<br/><br/>`[optional] string endIndex`
<br/>Index identifying the end of the series of events to return.<br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of objects to retrieve. If unspecified, a default value of 100 is used.<br/><br/>`[optional] integer boundaryType`
<br/>SdsBoundaryType specifying the handling of events at or near the start and end indexes.<br/><br/>`[optional] integer startBoundaryType`
<br/>SdsBoundaryType specifying the first value in the result in relation to the start index. If startBoundaryType is specified, endBoundaryType must be specified.<br/><br/>`[optional] integer endBoundaryType`
<br/>SdsBoundaryType specifies the last value in the result in relation to the end index. If startBoundaryType is specified, endBoundaryType must be specified.<br/><br/>`[optional] string filter`
<br/>Filter expression.<br/><br/>

<h4>Enumerated Values</h4>

|Parameter|Value|
|---|---|
|joinMode|0|
|joinMode|1|
|joinMode|2|
|joinMode|3|
|joinMode|4|
|boundaryType|0|
|boundaryType|1|
|boundaryType|2|
|boundaryType|3|
|startBoundaryType|0|
|startBoundaryType|1|
|startBoundaryType|2|
|startBoundaryType|3|
|endBoundaryType|0|
|endBoundaryType|1|
|endBoundaryType|2|
|endBoundaryType|3|

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Returns multiple serialized events|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|409|[ErrorResponseBody](#schemaerrorresponsebody)|Conflict|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

<h4>Example response body</h4>

> 400 Response ([ErrorResponseBody](#schemaerrorresponsebody))

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  }
}
```

---
## Definitions

### ErrorResponseBody

<a id="schemaerrorresponsebody"></a>
<a id="schema_ErrorResponseBody"></a>
<a id="tocSerrorresponsebody"></a>
<a id="tocserrorresponsebody"></a>

Contains the error message format that follows the OCS error standards

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|false|true|Operation unique identifier of action that caused the error|
|Error|string|false|true|Error description|
|Reason|string|false|true|Reason for the error|
|Resolution|string|false|true|Resolution to resolve the error|
|Parameters|object|false|true|IDs or values that are creating or are affected by the error|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  }
}

```

---

### SdsJoinMode

<a id="schemasdsjoinmode"></a>
<a id="schema_SdsJoinMode"></a>
<a id="tocSsdsjoinmode"></a>
<a id="tocssdsjoinmode"></a>

Join modes that specify how streams are joined

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|Inner|0|
|Outer|1|
|Interpolated|2|
|MergeLeft|3|
|MergeRight|4|

---

### SdsBoundaryType

<a id="schemasdsboundarytype"></a>
<a id="schema_SdsBoundaryType"></a>
<a id="tocSsdsboundarytype"></a>
<a id="tocssdsboundarytype"></a>

The SdsBoundaryType defines how data on the boundary of queries is handled: around the start index for range value queries, and around the start and end index for window values

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|Exact|0|
|Inside|1|
|Outside|2|
|ExactOrCalculated|3|

---

