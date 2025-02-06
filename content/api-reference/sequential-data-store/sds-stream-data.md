---
uid: sds-stream-data

---

# Stream Data
The API in this section interacts with data from the specified streams.

## `Get First Value`

<a id="opIdStreamData_Get First Value"></a>

Returns the first value in the stream. If no values exist in the stream, null is returned.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/First
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Returns a serialized event|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

---

## `Get Last Value`

<a id="opIdStreamData_Get Last Value"></a>

Returns the last value in the stream. If no values exist in the stream, null is returned.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Last
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Returns a serialized event|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

---

## `List Values`

<a id="opIdStreamData_List Values"></a>

Returns a collection of stored values at indexes based on request parameters.
  
SDS supports four ways of specifying which stored events to return:
- [Find Distinct Value](xref:SdsDataQueryMethods#find-distinct-value): Returns a stored event based on the specified index and searchMode. 
    
    **Parameters**: Accepts ``index`` and ``searchMode``.
- [Filtered](xref:SdsDataQueryMethods#filtered): Returns a collection of stored values as determined by a filter.The filter limits results by applying an expression against event fields. 
    
    **Parameters**: Accepts a ``filter`` expression. 
- [Range](xref:SdsDataQueryMethods#range): Returns a collection of stored values as determined by a ``startIndex`` and ``count``. 
    Additional optional parameters specify the direction of the range, how to handle events near or at the start index, whether to skip a certain number of events at the start of the range, and how to filter the data.
    
    **Parameters**: Accepts ``startIndex`` and ``count``.
- [Window](xref:SdsDataQueryMethods#window): Returns a collection of stored events based on the specified ``startIndex`` and ``endIndex``. 
    
    **Parameters**: Accepts ``startIndex`` and ``endIndex``. This request has an optional continuation token for large collections of events.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data
?filter={filter}&startIndex={startIndex}&endIndex={endIndex}&count={count}&index={index}&searchMode={searchMode}&skip={skip}&reversed={reversed}&boundaryType={boundaryType}&startBoundaryType={startBoundaryType}&endBoundaryType={endBoundaryType}&continuationToken={continuationToken}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/>
`[optional] string filter`
<br/>Filter expression.<br/><br/>`[optional] string startIndex`
<br/>Index identifying the beginning of the series of events to return.<br/><br/>`[optional] string endIndex`
<br/>Index identifying the end of the series of events to return.<br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of objects to retrieve. If unspecified, a default value of 100 is used.<br/><br/>`[optional] string index`
<br/>The index.<br/><br/>`[optional] integer searchMode`
<br/>The `SdsSearchMode`, type of search: Exact (the default), ExactOrNext, Next, ExactOrPrevious, or Previous.<br/><br/>`[optional] integer skip`
<br/>Parameter representing the zero-based offset of the first object to retrieve.  If unspecified, a default value of 0 is used.<br/><br/>`[optional] boolean reversed`
<br/>Specification of the direction of the request. By default, range requests move forward from startIndex, collecting events after startIndex from the stream. A reversed request will collect events before startIndex from the stream.<br/><br/>`[optional] integer boundaryType`
<br/>SdsBoundaryType specifying the handling of events at or near the start and end indexes.<br/><br/>`[optional] integer startBoundaryType`
<br/>SdsBoundaryType specifying the first value in the result in relation to the start index. If startBoundaryType is specified, endBoundaryType must be specified.<br/><br/>`[optional] integer endBoundaryType`
<br/>SdsBoundaryType specifies the last value in the result in relation to the end index. If startBoundaryType is specified, endBoundaryType must be specified.<br/><br/>`[optional] string continuationToken`
<br/>Token used to retrieve the next page of data. If count is specified, a continuationToken must also be specified.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Returns a serialized collection of events|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

<h4>Example response body</h4>

> 200 Response

```json
[
  {
    "Time": "2017-11-23T14:00:00Z",
    "Measurement": 20
  },
  {
    "Time": "2017-11-23T15:00:00Z",
    "Measurement": 30
  },
  {
    "Time": "2017-11-23T16:00:00Z",
    "Measurement": 40
  }
]
```

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

## `Insert Values`

<a id="opIdStreamData_Insert Values"></a>

Inserts data into the specified stream. Returns an error if data is already present at the index of any event.

**Notes**: This request will return an error if an event already exists for any index in the request.
If any individual index encounters a problem, the entire operation is rolled back and no insertions are made.
The streamId and index that caused the issue are included in the error response.  

<h3>Request</h3>

```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|Specified values were successfully added|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|409|[ErrorResponseBody](#schemaerrorresponsebody)|Conflict|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

---

## `Update Values`

<a id="opIdStreamData_Update Values"></a>

Writes one or more events to or over existing events the specified stream. 

**Notes**: This request performs an insert or a replace depending on whether an event already exists at the event indexes.
If any item fails to write, the entire operation is rolled back and no events are written to the stream.
The index that caused the issue is included in the error response.

<h3>Request</h3>

```text 
PUT /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data
?allowCreate={allowCreate}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/>
`[optional] boolean allowCreate`
<br/>If false, writes one or more events over existing events in the specified stream.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|Specified values were successfully updated|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

---

## `Patch Values`

<a id="opIdStreamData_Patch Values"></a>

Modifies the specified stream event(s). 
Patching affects only the data item parameters that are included in the call.

**Notes**: Patching is used to patch the events of the selected fields for one or more events in the stream.
Only the fields indicated in ``selectExpression`` are modified.
The events to be modified are indicated by the index value of each entry in the collection. 
If there is a problem patching any individual event, the entire operation is rolled back and the error will indicate the ``streamId`` and ``index`` of the problem.

<h3>Request</h3>

```text 
PATCH /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data
?selectExpression={selectExpression}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/>
`[optional] string selectExpression`
<br/>Comma separated list of strings that indicates the event fields that will be changed in stream events.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|Specified values were successfully corrected|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

---

## `Remove Values`

<a id="opIdStreamData_Remove Values"></a>

There are two options for specifying which events to remove from a stream: index collection and windows

[Index Collection](xref:SdsDataQueryMethods#index-collection): Removes the event at each index from the specified stream. 
Different overloads are available to make it easier to indicate the index where you want to remove a data event. 
One or more indexes can be specified in the request.

[Window](xref:SdsDataQueryMethods#window): Removes events at and between the start index and end index.
A window can be specified with a start index and end index.

**Notes**: If any individual event fails to be removed, the entire operation is rolled back and no events are removed.
The ``streamId`` and ``index`` that caused the issue are included in the error response.
If you attempt to remove events at indexes that have no events, an error is returned.
If this occurs, use the [Window](xref:SdsDataQueryMethods#window) request format to remove any events from a specified window of indexes, which will not return an error if no data is found.

<h3>Request</h3>

```text 
DELETE /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data
?index={index}&startIndex={startIndex}&endIndex={endIndex}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/>
`[optional] string index`
<br/>One or more indexes of events to remove.<br/><br/>`[optional] string startIndex`
<br/>Index identifying the beginning of the window.<br/><br/>`[optional] string endIndex`
<br/>Index identifying the end of the window.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|Specified values were successfully deleted|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

---

## `List Interpolated Values`

<a id="opIdStreamData_List Interpolated Values"></a>

Returns a collection of values based on request parameters.
The stream's read characteristics determine how events are calculated for indexes at which no stored event exists.
Interpolation is not supported for streams with compound indexes.

SDS supports two ways of specifying which stored events to return: index collection and interval.

[Index collection](xref:SdsDataQueryMethods#index-collection): Returns events at the specified indexes.
If no stored event exists at a specified index, the stream's read characteristics determine how the returned event is calculated.

**Parameters**: Accepts ``index``.

[Interval](xref:SdsDataQueryMethods#interval): Returns events at evenly spaced intervals based on the specified ``startIndex``, ``endIndex``, and ``count``.
If no stored event exists at an index interval, the stream's read characteristics determine how the returned event is calculated.

**Parameters**: Accepts ``startIndex``, ``endIndex`` and ``count``.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Interpolated
?index={index}&startIndex={startIndex}&endIndex={endIndex}&count={count}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/>
`[optional] string index`
<br/>One or more indexes.<br/><br/>`[optional] string startIndex`
<br/>Index identifying the beginning of the series of events to return.<br/><br/>`[optional] string endIndex`
<br/>Index identifying the end of the series of events to return.<br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of objects to retrieve. If unspecified, a default value of 100 is used.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Returns a serialized collection of events. Depending on the specified indexes and read characteristics of the stream, it is possible to have less events returned than specified indexes. An empty collection can also be returned.|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

---

## `List Summaries`

<a id="opIdStreamData_List Summaries"></a>

Returns summary intervals between a specified start and end index. Index types that cannot be interpolated do not support summary requests. Strings are an example of indexes that cannot be interpolated. Summaries are not supported for streams with compound indexes. Interpolating between two indexes that consist of multiple properties is not defined and results in non-determinant behavior.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Summaries
?startIndex={startIndex}&endIndex={endIndex}&count={count}&filter={filter}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/>
`[optional] string startIndex`
<br/>Index identifying the beginning of the series of events to return.<br/><br/>`[optional] string endIndex`
<br/>Index identifying the end of the series of events to return.<br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of objects to retrieve. If unspecified, a default value of 100 is used.<br/><br/>`[optional] string filter`
<br/>Filter expression.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Returns a serialized collection of SdsIntervals. Each SdsInterval has a start, end, and collection of summary values.|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

---

## `List Sampled Values`

<a id="opIdStreamData_List Sampled Values"></a>

Returns representative data sampled by intervals between a specified start and end index. Sampling is driven by a specified property or properties of the stream's Sds Type. Property types that cannot be interpolated do not support sampling requests. Strings are an example of a property that cannot be interpolated.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Sampled
?startIndex={startIndex}&endIndex={endIndex}&intervals={intervals}&sampleBy={sampleBy}&boundaryType={boundaryType}&startBoundaryType={startBoundaryType}&endBoundaryType={endBoundaryType}&filter={filter}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/>
`[optional] string startIndex`
<br/>Index identifying the beginning of the series of events to return.<br/><br/>`[optional] string endIndex`
<br/>Index identifying the end of the series of events to return.<br/><br/>`[optional] integer intervals`
<br/>The number of intervals requested.<br/><br/>`[optional] string sampleBy`
<br/>Property or properties to use when sampling.<br/><br/>`[optional] integer boundaryType`
<br/>SdsBoundaryType specifying the handling of events at or near the start and end indexes.<br/><br/>`[optional] integer startBoundaryType`
<br/>SdsBoundaryType specifying the first value in the result in relation to the start index. If startBoundaryType is specified, endBoundaryType must be specified.<br/><br/>`[optional] integer endBoundaryType`
<br/>SdsBoundaryType specifies the last value in the result in relation to the end index. If startBoundaryType is specified, endBoundaryType must be specified.<br/><br/>`[optional] string filter`
<br/>Filter expression.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Returns a serialized collection of events|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

---
## Definitions

### ErrorResponseBody

<a id="schemaerrorresponsebody"></a>
<a id="schema_ErrorResponseBody"></a>
<a id="tocSerrorresponsebody"></a>
<a id="tocserrorresponsebody"></a>

The error response contains standard details on the cause and resolution of the error.

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

### SdsSearchMode

<a id="schemasdssearchmode"></a>
<a id="schema_SdsSearchMode"></a>
<a id="tocSsdssearchmode"></a>
<a id="tocssdssearchmode"></a>

The SdsSearchMode defines search behavior when seeking a stored event near a specified index.

<h4>Enumerated Values</h4>

|Property|Value|Description|
|---|---|---|
|Exact|0|If a stored event exists at the specified index, that event is returned. Otherwise no event is returned.|
|ExactOrNext|1|If a stored event exists at the specified index, that event is returned. Otherwise the next event in the stream is returned.|
|Next|2|Returns the stored event after the specified index.|
|ExactOrPrevious|3|If a stored event exists at the specified index, that event is returned. Otherwise the previous event in the stream is returned.|
|Previous|4|Returns the stored event before the specified index.|

---

### SdsBoundaryType

<a id="schemasdsboundarytype"></a>
<a id="schema_SdsBoundaryType"></a>
<a id="tocSsdsboundarytype"></a>
<a id="tocssdsboundarytype"></a>

The SdsBoundaryType defines how data on the boundary of queries is handled: around the start index for range value queries, and around the start and end index for window values.

<h4>Enumerated Values</h4>

|Property|Value|Description|
|---|---|---|
|Exact|0|Results include the event at the specified index boundary if a stored event exists at that index.|
|Inside|1|Results include only events within the index boundaries.|
|Outside|2|Results include up to one event that falls immediately outside of the specified index boundary.|
|ExactOrCalculated|3|Results include the event at the specified index boundary. If no stored event exists at that index, one is calculated based on the index type and interpolation and extrapolation settings.|

---

