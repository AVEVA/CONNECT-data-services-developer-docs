---
uid: sds-stream-data-transform

---

# Stream Data Transform
The API in this section transforms data from the specified stream.
- [Reading with SdsStreamViews](https://ocs-docs.osisoft.com/Content_Portal/Documentation/SequentialDataStore/Reading_Data.html#reading-with-sdsstreamviews):Changing the shape of the returned data.
When transforming data with an SdsStreamView, the data read is converted to the target type specified in the SdsStreamView. 
All stream view transformations are HTTP GET requests. 
Specify the stream view ID `(streamViewId={streamViewId})` at the end of the transformation endpoint.
When data is requested with an SdsStreamView, the read characteristics defined by the target type of the SdsStreamView determine what is returned. 
- [Unit of measure conversions](xref:sdsReadingData#unit-conversion-of-data): Converting the unit of measure of the data. 
SDS supports assigning Units of Measure (UOM) to stream data.
If stream data has UOM information associated, SDS supports reading data with unit conversions applied.
On each read data request, unit conversions are specified by a user defined collection of SdsStreamPropertyOverride objects in read requests. 
All unit conversions of data are HTTP POST requests with a request body containing a collection of SdsStreamPropertyOverride objects. 

## `Get First (GET Method)`

<a id="opIdStreamDataTransform_Get First (GET Method)"></a>

Returns the first value in the stream. If no values exist in the stream, null is returned.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/First
?streamViewId={streamViewId}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>
`[optional] string streamViewId`
<br/>Stream view identifier.<br/><br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Returns a serialized event|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
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

## `Get First (POST Method)`

<a id="opIdStreamDataTransform_Get First (POST Method)"></a>

Returns the first value in the stream. If no values exist in the stream, null is returned.

### Request
```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/First
?streamViewId={streamViewId}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>
`[optional] string streamViewId`
<br/>Stream view identifier.<br/><br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Returns a serialized event|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
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

## `Get Last (GET Method)`

<a id="opIdStreamDataTransform_Get Last (GET Method)"></a>

Returns the last value in the stream. If no values exist in the stream, null is returned.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Last
?streamViewId={streamViewId}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>
`[optional] string streamViewId`
<br/>Stream view identifier.<br/><br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Returns a serialized event|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
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

## `Get Last (POST Method)`

<a id="opIdStreamDataTransform_Get Last (POST Method)"></a>

Returns the last value in the stream. If no values exist in the stream, null is returned.

### Request
```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Last
?streamViewId={streamViewId}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>
`[optional] string streamViewId`
<br/>Stream view identifier.<br/><br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Returns a serialized event|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
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

## `List Data (GET Method)`

<a id="opIdStreamDataTransform_List Data (GET Method)"></a>

Returns a collection of stored values at indexes based on request parameters.
  
SDS supports four ways of specifying which stored events to return:
- [Find Distinct Value](xref:sdsReadingDataApi#find-distinct-value): Returns a stored event based on the specified index and searchMode. 
    
    **Parameters**: Accepts ``index`` and ``searchMode``.
- [Filtered](xref:sdsReadingDataApi#getvaluesfiltered): Returns a collection of stored values as determined by a filter.The filter limits results by applying an expression against event fields. 
    
    **Parameters**: Accepts a ``filter`` expression. 
- [Range](xref:sdsReadingDataApi#getvaluesrange): Returns a collection of stored values as determined by a ``startIndex`` and ``count``. 
    Additional optional parameters specify the direction of the range, how to handle events near or at the start index, whether to skip a certain number of events at the start of the range, and how to filter the data.
    
    **Parameters**: Accepts ``startIndex`` and ``count``.
- [Window](xref:sdsReadingDataApi#getvalueswindow): Returns a collection of stored events based on the specified ``startIndex`` and ``endIndex``. 
    
    **Parameters**: Accepts ``startIndex`` and ``endIndex``. This request has an optional continuation token for large collections of events.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform
?streamViewId={streamViewId}&filter={filter}&startIndex={startIndex}&endIndex={endIndex}&count={count}&index={index}&searchMode={searchMode}&skip={skip}&reversed={reversed}&boundaryType={boundaryType}&startBoundaryType={startBoundaryType}&endBoundaryType={endBoundaryType}&continuationToken={continuationToken}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>
`[optional] string streamViewId`
<br/>Stream view identifier.<br/><br/><br/>`[optional] string filter`
<br/>Filter expression.<br/><br/><br/>`[optional] string startIndex`
<br/>Index identifying the beginning of the series of events to return.<br/><br/><br/>`[optional] string endIndex`
<br/>Index identifying the end of the series of events to return.<br/><br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of objects to retrieve. If unspecified, a default value of 100 is used.<br/><br/><br/>`[optional] string index`
<br/>The index.<br/><br/>`[optional] integer searchMode`
<br/>The , the default is exact<br/><br/>`[optional] integer skip`
<br/>Parameter representing the zero-based offset of the first object to retrieve.  If unspecified, a default value of 0 is used.<br/><br/><br/>`[optional] boolean reversed`
<br/>Specification of the direction of the request. By default, range requests move forward from startIndex, collecting events after startIndex 
            from the stream. A reversed request will collect events before startIndex from the stream.<br/><br/>`[optional] integer boundaryType`
<br/>SdsBoundaryType specifying the handling of events at or near the start and end indexes.<br/><br/><br/>`[optional] integer startBoundaryType`
<br/>SdsBoundaryType specifying the first value in the result in relation to the start index. If startBoundaryType is specified, endBoundaryType must be specified.<br/><br/><br/>`[optional] integer endBoundaryType`
<br/>SdsBoundaryType specifies the last value in the result in relation to the end index. If startBoundaryType is specified, endBoundaryType must be specified.<br/><br/><br/>`[optional] string continuationToken`
<br/>Token used to retrieve the next page of data. If count is specified, a continuationToken must also be specified.<br/><br/><br/>

#### Enumerated Values

|Parameter|Value|
|---|---|
|searchMode|0|
|searchMode|1|
|searchMode|2|
|searchMode|3|
|searchMode|4|
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

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Returns a serialized collection of events|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
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

## `Get Data (POST Method)`

<a id="opIdStreamDataTransform_Get Data (POST Method)"></a>

Returns a collection of stored values at indexes based on request parameters.
  
SDS supports four ways of specifying which stored events to return:
- [Find Distinct Value](xref:sdsReadingDataApi#find-distinct-value): Returns a stored event based on the specified index and searchMode. 
    
    **Parameters**: Accepts ``index`` and ``searchMode``.
- [Filtered](xref:sdsReadingDataApi#getvaluesfiltered): Returns a collection of stored values as determined by a filter.The filter limits results by applying an expression against event fields. 
    
    **Parameters**: Accepts a ``filter`` expression. 
- [Range](xref:sdsReadingDataApi#getvaluesrange): Returns a collection of stored values as determined by a ``startIndex`` and ``count``. 
    Additional optional parameters specify the direction of the range, how to handle events near or at the start index, whether to skip a certain number of events at the start of the range, and how to filter the data.
    
    **Parameters**: Accepts ``startIndex`` and ``count``.
- [Window](xref:sdsReadingDataApi#getvalueswindow): Returns a collection of stored events based on the specified ``startIndex`` and ``endIndex``. 
    
    **Parameters**: Accepts ``startIndex`` and ``endIndex``. This request has an optional continuation token for large collections of events.

### Request
```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform
?streamViewId={streamViewId}&filter={filter}&startIndex={startIndex}&endIndex={endIndex}&count={count}&index={index}&searchMode={searchMode}&skip={skip}&reversed={reversed}&boundaryType={boundaryType}&startBoundaryType={startBoundaryType}&endBoundaryType={endBoundaryType}&continuationToken={continuationToken}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>
`[optional] string streamViewId`
<br/>Stream view identifier.<br/><br/><br/>`[optional] string filter`
<br/>Filter expression.<br/><br/><br/>`[optional] string startIndex`
<br/>Index identifying the beginning of the series of events to return.<br/><br/><br/>`[optional] string endIndex`
<br/>Index identifying the end of the series of events to return.<br/><br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of objects to retrieve. If unspecified, a default value of 100 is used.<br/><br/><br/>`[optional] string index`
<br/>The index.<br/><br/>`[optional] integer searchMode`
<br/>The , the default is exact<br/><br/>`[optional] integer skip`
<br/>Parameter representing the zero-based offset of the first object to retrieve.  If unspecified, a default value of 0 is used.<br/><br/><br/>`[optional] boolean reversed`
<br/>Specification of the direction of the request. By default, range requests move forward from startIndex, collecting events after startIndex 
            from the stream. A reversed request will collect events before startIndex from the stream.<br/><br/>`[optional] integer boundaryType`
<br/>SdsBoundaryType specifying the handling of events at or near the start and end indexes.<br/><br/><br/>`[optional] integer startBoundaryType`
<br/>SdsBoundaryType specifying the first value in the result in relation to the start index. If startBoundaryType is specified, endBoundaryType must be specified.<br/><br/><br/>`[optional] integer endBoundaryType`
<br/>SdsBoundaryType specifies the last value in the result in relation to the end index. If startBoundaryType is specified, endBoundaryType must be specified.<br/><br/><br/>`[optional] string continuationToken`
<br/>Token used to retrieve the next page of data. If count is specified, a continuationToken must also be specified.<br/><br/><br/>

#### Enumerated Values

|Parameter|Value|
|---|---|
|searchMode|0|
|searchMode|1|
|searchMode|2|
|searchMode|3|
|searchMode|4|
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

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Returns a serialized collection of events|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
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

## `List Data Interpolated (GET Method)`

<a id="opIdStreamDataTransform_List Data Interpolated (GET Method)"></a>

Returns a collection of values based on request parameters.
The stream's read characteristics determine how events are calculated for indexes at which no stored event exists.
Interpolation is not supported for streams with compound indexes.

SDS supports two ways of specifying which stored events to return: index collection and interval.

[Index collection](xref:sdsReadingDataApi#index-collection): Returns events at the specified indexes.
If no stored event exists at a specified index, the stream's read characteristics determine how the returned event is calculated.

**Parameters**: Accepts ``index``.

[Interval](xref:sdsReadingDataApi#interval): Returns events at evenly spaced intervals based on the specified ``startIndex``, ``endIndex``, and ``count``. 
If no stored event exists at an index interval, the stream's read characteristics determine how the returned event is calculated. 

**Parameters**: Accepts ``startIndex``, ``endIndex`` and ``count``.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Interpolated
?streamViewId={streamViewId}&index={index}&startIndex={startIndex}&endIndex={endIndex}&count={count}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>
`[optional] string streamViewId`
<br/>Stream view identifier.<br/><br/><br/>`[optional] string index`
<br/>One or more indexes.<br/><br/>`[optional] string startIndex`
<br/>Index identifying the beginning of the series of events to return.<br/><br/><br/>`[optional] string endIndex`
<br/>Index identifying the end of the series of events to return.<br/><br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of objects to retrieve. If unspecified, a default value of 100 is used.<br/><br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Returns a serialized collection of events. Depending on the specified indexes and read characteristics of the stream, it is possible to have less events returned than specified indexes. An empty collection can also be returned.|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
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

## `Get Data Interpolated (POST Method)`

<a id="opIdStreamDataTransform_Get Data Interpolated (POST Method)"></a>

Returns a collection of values based on request parameters.
The stream's read characteristics determine how events are calculated for indexes at which no stored event exists.
Interpolation is not supported for streams with compound indexes.

SDS supports two ways of specifying which stored events to return: index collection and interval.

[Index collection](xref:sdsReadingDataApi#index-collection): Returns events at the specified indexes.
If no stored event exists at a specified index, the stream's read characteristics determine how the returned event is calculated.

**Parameters**: Accepts ``index``.

[Interval](xref:sdsReadingDataApi#interval): Returns events at evenly spaced intervals based on the specified ``startIndex``, ``endIndex``, and ``count``. 
If no stored event exists at an index interval, the stream's read characteristics determine how the returned event is calculated. 

**Parameters**: Accepts ``startIndex``, ``endIndex`` and ``count``.

### Request
```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Interpolated
?streamViewId={streamViewId}&index={index}&startIndex={startIndex}&endIndex={endIndex}&count={count}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>
`[optional] string streamViewId`
<br/>Stream view identifier.<br/><br/><br/>`[optional] string index`
<br/>One or more indexes.<br/><br/>`[optional] string startIndex`
<br/>Index identifying the beginning of the series of events to return.<br/><br/><br/>`[optional] string endIndex`
<br/>Index identifying the end of the series of events to return.<br/><br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of objects to retrieve. If unspecified, a default value of 100 is used.<br/><br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Returns a serialized collection of events. Depending on the specified indexes and read characteristics of the stream, it is possible to have less events returned than specified indexes. An empty collection can also be returned.|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
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

## `List Data Summaries (GET Method)`

<a id="opIdStreamDataTransform_List Data Summaries (GET Method)"></a>

Returns summary intervals between a specified start and end index. Index types that cannot be interpolated do not support summary requests. Strings are an example of indexes that cannot be interpolated. Summaries are not supported for streams with compound indexes. Interpolating between two indexes that consist of multiple properties is not defined and results in non-determinant behavior.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Summaries
?streamViewId={streamViewId}&startIndex={startIndex}&endIndex={endIndex}&count={count}&filter={filter}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>
`[optional] string streamViewId`
<br/>Stream view identifier.<br/><br/><br/>`[optional] string startIndex`
<br/>Index identifying the beginning of the series of events to return.<br/><br/><br/>`[optional] string endIndex`
<br/>Index identifying the end of the series of events to return.<br/><br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of objects to retrieve. If unspecified, a default value of 100 is used.<br/><br/><br/>`[optional] string filter`
<br/>Filter expression.<br/><br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Returns a serialized collection of SdsIntervals. Each SdsInterval has a start, end, and collection of summary values.|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
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

## `Get Data Summaries (POST Method)`

<a id="opIdStreamDataTransform_Get Data Summaries (POST Method)"></a>

Returns summary intervals between a specified start and end index. Index types that cannot be interpolated do not support summary requests. Strings are an example of indexes that cannot be interpolated. Summaries are not supported for streams with compound indexes. Interpolating between two indexes that consist of multiple properties is not defined and results in non-determinant behavior.

### Request
```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Summaries
?streamViewId={streamViewId}&startIndex={startIndex}&endIndex={endIndex}&count={count}&filter={filter}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>
`[optional] string streamViewId`
<br/>Stream view identifier.<br/><br/><br/>`[optional] string startIndex`
<br/>Index identifying the beginning of the series of events to return.<br/><br/><br/>`[optional] string endIndex`
<br/>Index identifying the end of the series of events to return.<br/><br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of objects to retrieve. If unspecified, a default value of 100 is used.<br/><br/><br/>`[optional] string filter`
<br/>Filter expression.<br/><br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Returns a serialized collection of SdsIntervals. Each SdsInterval has a start, end, and collection of summary values.|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
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

## `List Data Samples (GET Method)`

<a id="opIdStreamDataTransform_List Data Samples (GET Method)"></a>

Returns representative data sampled by intervals between a specified start and end index. Sampling is driven by a specified property or properties of the stream's Sds Type. Property types that cannot be interpolated do not support sampling requests. Strings are an example of a property that cannot be interpolated.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Sampled
?streamViewId={streamViewId}&startIndex={startIndex}&endIndex={endIndex}&intervals={intervals}&sampleBy={sampleBy}&boundaryType={boundaryType}&startBoundaryType={startBoundaryType}&endBoundaryType={endBoundaryType}&filter={filter}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>
`[optional] string streamViewId`
<br/>Stream view identifier.<br/><br/><br/>`[optional] string startIndex`
<br/>Index identifying the beginning of the series of events to return.<br/><br/><br/>`[optional] string endIndex`
<br/>Index identifying the end of the series of events to return.<br/><br/><br/>`[optional] integer intervals`
<br/>The number of intervals requested.<br/><br/>`[optional] string sampleBy`
<br/>Property or properties to use when sampling.<br/><br/>`[optional] integer boundaryType`
<br/>SdsBoundaryType specifying the handling of events at or near the start and end indexes.<br/><br/><br/>`[optional] integer startBoundaryType`
<br/>SdsBoundaryType specifying the first value in the result in relation to the start index. If startBoundaryType is specified, endBoundaryType must be specified.<br/><br/><br/>`[optional] integer endBoundaryType`
<br/>SdsBoundaryType specifies the last value in the result in relation to the end index. If startBoundaryType is specified, endBoundaryType must be specified.<br/><br/><br/>`[optional] string filter`
<br/>Filter expression.<br/><br/><br/>

#### Enumerated Values

|Parameter|Value|
|---|---|
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

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Returns a serialized collection of events|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
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

## `Get Data Samples (POST Method)`

<a id="opIdStreamDataTransform_Get Data Samples (POST Method)"></a>

Returns representative data sampled by intervals between a specified start and end index. Sampling is driven by a specified property or properties of the stream's Sds Type. Property types that cannot be interpolated do not support sampling requests. Strings are an example of a property that cannot be interpolated.

### Request
```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Sampled
?streamViewId={streamViewId}&startIndex={startIndex}&endIndex={endIndex}&intervals={intervals}&sampleBy={sampleBy}&boundaryType={boundaryType}&startBoundaryType={startBoundaryType}&endBoundaryType={endBoundaryType}&filter={filter}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>
`[optional] string streamViewId`
<br/>Stream view identifier.<br/><br/><br/>`[optional] string startIndex`
<br/>Index identifying the beginning of the series of events to return.<br/><br/><br/>`[optional] string endIndex`
<br/>Index identifying the end of the series of events to return.<br/><br/><br/>`[optional] integer intervals`
<br/>The number of intervals requested.<br/><br/>`[optional] string sampleBy`
<br/>Property or properties to use when sampling.<br/><br/>`[optional] integer boundaryType`
<br/>SdsBoundaryType specifying the handling of events at or near the start and end indexes.<br/><br/><br/>`[optional] integer startBoundaryType`
<br/>SdsBoundaryType specifying the first value in the result in relation to the start index. If startBoundaryType is specified, endBoundaryType must be specified.<br/><br/><br/>`[optional] integer endBoundaryType`
<br/>SdsBoundaryType specifies the last value in the result in relation to the end index. If startBoundaryType is specified, endBoundaryType must be specified.<br/><br/><br/>`[optional] string filter`
<br/>Filter expression.<br/><br/><br/>

#### Enumerated Values

|Parameter|Value|
|---|---|
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

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Returns a serialized collection of events|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
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

### SdsSearchMode

<a id="schemasdssearchmode"></a>
<a id="schema_SdsSearchMode"></a>
<a id="tocSsdssearchmode"></a>
<a id="tocssdssearchmode"></a>

#### Enumerated Values

|Property|Value|
|---|---|
|Exact|0|
|ExactOrNext|1|
|Next|2|
|ExactOrPrevious|3|
|Previous|4|

---

### SdsBoundaryType

<a id="schemasdsboundarytype"></a>
<a id="schema_SdsBoundaryType"></a>
<a id="tocSsdsboundarytype"></a>
<a id="tocssdsboundarytype"></a>

#### Enumerated Values

|Property|Value|
|---|---|
|Exact|0|
|Inside|1|
|Outside|2|
|ExactOrCalculated|3|

---

