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

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Bulk/Streams/Data/Joins
?streams={streams}&joinMode={joinMode}&startIndex={startIndex}&endIndex={endIndex}&count={count}&boundaryType={boundaryType}&startBoundaryType={startBoundaryType}&endBoundaryType={endBoundaryType}&filter={filter}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>
`[optional] string streams`
<br/>Comma separated list of stream identifiers.<br/><br/>`[optional] string joinMode`
<br/>The , type of join: inner, outer, interpolated, merge left, or merge right.<br/><br/>`[optional] string startIndex`
<br/>Index identifying the beginning of the series of events to return.<br/><br/><br/>`[optional] string endIndex`
<br/>Index identifying the end of the series of events to return.<br/><br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of objects to retrieve. If unspecified, a default value of 100 is used.<br/><br/><br/>`[optional] string boundaryType`
<br/>SdsBoundaryType specifying the handling of events at or near the start and end indexes.<br/><br/><br/>`[optional] string startBoundaryType`
<br/>SdsBoundaryType specifying the first value in the result in relation to the start index. If startBoundaryType is specified, endBoundaryType must be specified.<br/><br/><br/>`[optional] string endBoundaryType`
<br/>SdsBoundaryType specifies the last value in the result in relation to the end index. If startBoundaryType is specified, endBoundaryType must be specified.<br/><br/><br/>`[optional] string filter`
<br/>Filter expression.<br/><br/><br/>

### Response

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

#### Example response body
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

### Request
```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Bulk/Streams/Data/Joins
?streams={streams}&joinMode={joinMode}&startIndex={startIndex}&endIndex={endIndex}&count={count}&boundaryType={boundaryType}&startBoundaryType={startBoundaryType}&endBoundaryType={endBoundaryType}&filter={filter}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>
`[optional] string streams`
<br/>Comma separated list of stream identifiers.<br/><br/>`[optional] string joinMode`
<br/>The , type of join: inner, outer, interpolated, merge left, or merge right.<br/><br/>`[optional] string startIndex`
<br/>Index identifying the beginning of the series of events to return.<br/><br/><br/>`[optional] string endIndex`
<br/>Index identifying the end of the series of events to return.<br/><br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of objects to retrieve. If unspecified, a default value of 100 is used.<br/><br/><br/>`[optional] string boundaryType`
<br/>SdsBoundaryType specifying the handling of events at or near the start and end indexes.<br/><br/><br/>`[optional] string startBoundaryType`
<br/>SdsBoundaryType specifying the first value in the result in relation to the start index. If startBoundaryType is specified, endBoundaryType must be specified.<br/><br/><br/>`[optional] string endBoundaryType`
<br/>SdsBoundaryType specifies the last value in the result in relation to the end index. If startBoundaryType is specified, endBoundaryType must be specified.<br/><br/><br/>`[optional] string filter`
<br/>Filter expression.<br/><br/><br/>

### Response

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

#### Example response body
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

#### Properties

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

