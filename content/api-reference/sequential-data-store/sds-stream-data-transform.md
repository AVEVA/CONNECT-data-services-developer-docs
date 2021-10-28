---
uid: sds-stream-data-transform

---

# Stream Data Transform
#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/datacalls.yaml#stream-data-transform

## `Get First (GET Method)`

<a id="opIdStreamDataTransform_Get First (GET Method)"></a>

Returns the first value in the stream. If no values exist in the stream, null is returned.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/First
?streamViewId={streamViewId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#tenant<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#namespace<br/><br/>`string streamId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#stream<br/><br/>
`[optional] string streamViewId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#view<br/><br/>

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

## `Get First (POST Method)`

<a id="opIdStreamDataTransform_Get First (POST Method)"></a>

Returns the first value in the stream. If no values exist in the stream, null is returned.

<h3>Request</h3>

```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/First
?streamViewId={streamViewId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#tenant<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#namespace<br/><br/>`string streamId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#stream<br/><br/>
`[optional] string streamViewId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#view<br/><br/>

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

## `Get Last (GET Method)`

<a id="opIdStreamDataTransform_Get Last (GET Method)"></a>

Returns the last value in the stream. If no values exist in the stream, null is returned.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Last
?streamViewId={streamViewId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#tenant<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#namespace<br/><br/>`string streamId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#stream<br/><br/>
`[optional] string streamViewId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#view<br/><br/>

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

## `Get Last (POST Method)`

<a id="opIdStreamDataTransform_Get Last (POST Method)"></a>

Returns the last value in the stream. If no values exist in the stream, null is returned.

<h3>Request</h3>

```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Last
?streamViewId={streamViewId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#tenant<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#namespace<br/><br/>`string streamId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#stream<br/><br/>
`[optional] string streamViewId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#view<br/><br/>

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

## `List Data (GET Method)`

<a id="opIdStreamDataTransform_List Data (GET Method)"></a>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/datacalls.yaml#list-values

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform
?streamViewId={streamViewId}&filter={filter}&startIndex={startIndex}&endIndex={endIndex}&count={count}&index={index}&searchMode={searchMode}&skip={skip}&reversed={reversed}&boundaryType={boundaryType}&startBoundaryType={startBoundaryType}&endBoundaryType={endBoundaryType}&continuationToken={continuationToken}
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#tenant<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#namespace<br/><br/>`string streamId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#stream<br/><br/>
`[optional] string streamViewId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#view<br/><br/>`[optional] string filter`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#filter<br/><br/>`[optional] string startIndex`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#startindex<br/><br/>`[optional] string endIndex`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#endindex<br/><br/>`[optional] integer count`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#count<br/><br/>`[optional] string index`
<br/>The index.<br/><br/>`[optional] integer searchMode`
<br/>The `SdsSearchMode`, type of search: Exact (the default), ExactOrNext, Next, ExactOrPrevious, or Previous.<br/><br/>`[optional] integer skip`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#skip<br/><br/>`[optional] boolean reversed`
<br/>Specification of the direction of the request. By default, range requests move forward from startIndex, collecting events after startIndex from the stream. A reversed request will collect events before startIndex from the stream.<br/><br/>`[optional] integer boundaryType`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#boundaryType<br/><br/>`[optional] integer startBoundaryType`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#startBoundaryType<br/><br/>`[optional] integer endBoundaryType`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#endBoundaryType<br/><br/>`[optional] string continuationToken`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#continuationToken<br/><br/>

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

## `Get Data (POST Method)`

<a id="opIdStreamDataTransform_Get Data (POST Method)"></a>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/datacalls.yaml#list-values

<h3>Request</h3>

```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform
?streamViewId={streamViewId}&filter={filter}&startIndex={startIndex}&endIndex={endIndex}&count={count}&index={index}&searchMode={searchMode}&skip={skip}&reversed={reversed}&boundaryType={boundaryType}&startBoundaryType={startBoundaryType}&endBoundaryType={endBoundaryType}&continuationToken={continuationToken}
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#tenant<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#namespace<br/><br/>`string streamId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#stream<br/><br/>
`[optional] string streamViewId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#view<br/><br/>`[optional] string filter`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#filter<br/><br/>`[optional] string startIndex`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#startindex<br/><br/>`[optional] string endIndex`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#endindex<br/><br/>`[optional] integer count`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#count<br/><br/>`[optional] string index`
<br/>The index.<br/><br/>`[optional] integer searchMode`
<br/>The `SdsSearchMode`, type of search: Exact (the default), ExactOrNext, Next, ExactOrPrevious, or Previous.<br/><br/>`[optional] integer skip`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#skip<br/><br/>`[optional] boolean reversed`
<br/>Specification of the direction of the request. By default, range requests move forward from startIndex, collecting events after startIndex from the stream. A reversed request will collect events before startIndex from the stream.<br/><br/>`[optional] integer boundaryType`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#boundaryType<br/><br/>`[optional] integer startBoundaryType`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#startBoundaryType<br/><br/>`[optional] integer endBoundaryType`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#endBoundaryType<br/><br/>`[optional] string continuationToken`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#continuationToken<br/><br/>

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

## `List Data Interpolated (GET Method)`

<a id="opIdStreamDataTransform_List Data Interpolated (GET Method)"></a>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/datacalls.yaml#interpolated-values

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Interpolated
?streamViewId={streamViewId}&index={index}&startIndex={startIndex}&endIndex={endIndex}&count={count}
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#tenant<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#namespace<br/><br/>`string streamId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#stream<br/><br/>
`[optional] string streamViewId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#view<br/><br/>`[optional] string index`
<br/>One or more indexes.<br/><br/>`[optional] string startIndex`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#startindex<br/><br/>`[optional] string endIndex`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#endindex<br/><br/>`[optional] integer count`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#count<br/><br/>

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

## `Get Data Interpolated (POST Method)`

<a id="opIdStreamDataTransform_Get Data Interpolated (POST Method)"></a>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/datacalls.yaml#interpolated-values

<h3>Request</h3>

```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Interpolated
?streamViewId={streamViewId}&index={index}&startIndex={startIndex}&endIndex={endIndex}&count={count}
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#tenant<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#namespace<br/><br/>`string streamId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#stream<br/><br/>
`[optional] string streamViewId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#view<br/><br/>`[optional] string index`
<br/>One or more indexes.<br/><br/>`[optional] string startIndex`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#startindex<br/><br/>`[optional] string endIndex`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#endindex<br/><br/>`[optional] integer count`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#count<br/><br/>

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

## `List Data Summaries (GET Method)`

<a id="opIdStreamDataTransform_List Data Summaries (GET Method)"></a>

Returns summary intervals between a specified start and end index. Index types that cannot be interpolated do not support summary requests. Strings are an example of indexes that cannot be interpolated. Summaries are not supported for streams with compound indexes. Interpolating between two indexes that consist of multiple properties is not defined and results in non-determinant behavior.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Summaries
?streamViewId={streamViewId}&startIndex={startIndex}&endIndex={endIndex}&count={count}&filter={filter}
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#tenant<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#namespace<br/><br/>`string streamId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#stream<br/><br/>
`[optional] string streamViewId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#view<br/><br/>`[optional] string startIndex`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#startindex<br/><br/>`[optional] string endIndex`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#endindex<br/><br/>`[optional] integer count`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#count<br/><br/>`[optional] string filter`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#filter<br/><br/>

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

## `Get Data Summaries (POST Method)`

<a id="opIdStreamDataTransform_Get Data Summaries (POST Method)"></a>

Returns summary intervals between a specified start and end index. Index types that cannot be interpolated do not support summary requests. Strings are an example of indexes that cannot be interpolated. Summaries are not supported for streams with compound indexes. Interpolating between two indexes that consist of multiple properties is not defined and results in non-determinant behavior.

<h3>Request</h3>

```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Summaries
?streamViewId={streamViewId}&startIndex={startIndex}&endIndex={endIndex}&count={count}&filter={filter}
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#tenant<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#namespace<br/><br/>`string streamId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#stream<br/><br/>
`[optional] string streamViewId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#view<br/><br/>`[optional] string startIndex`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#startindex<br/><br/>`[optional] string endIndex`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#endindex<br/><br/>`[optional] integer count`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#count<br/><br/>`[optional] string filter`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#filter<br/><br/>

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

## `List Data Samples (GET Method)`

<a id="opIdStreamDataTransform_List Data Samples (GET Method)"></a>

Returns representative data sampled by intervals between a specified start and end index. Sampling is driven by a specified property or properties of the stream's Sds Type. Property types that cannot be interpolated do not support sampling requests. Strings are an example of a property that cannot be interpolated.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Sampled
?streamViewId={streamViewId}&startIndex={startIndex}&endIndex={endIndex}&intervals={intervals}&sampleBy={sampleBy}&boundaryType={boundaryType}&startBoundaryType={startBoundaryType}&endBoundaryType={endBoundaryType}&filter={filter}
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#tenant<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#namespace<br/><br/>`string streamId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#stream<br/><br/>
`[optional] string streamViewId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#view<br/><br/>`[optional] string startIndex`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#startindex<br/><br/>`[optional] string endIndex`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#endindex<br/><br/>`[optional] integer intervals`
<br/>The number of intervals requested.<br/><br/>`[optional] string sampleBy`
<br/>Property or properties to use when sampling.<br/><br/>`[optional] integer boundaryType`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#boundaryType<br/><br/>`[optional] integer startBoundaryType`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#startBoundaryType<br/><br/>`[optional] integer endBoundaryType`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#endBoundaryType<br/><br/>`[optional] string filter`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#filter<br/><br/>

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

## `Get Data Samples (POST Method)`

<a id="opIdStreamDataTransform_Get Data Samples (POST Method)"></a>

Returns representative data sampled by intervals between a specified start and end index. Sampling is driven by a specified property or properties of the stream's Sds Type. Property types that cannot be interpolated do not support sampling requests. Strings are an example of a property that cannot be interpolated.

<h3>Request</h3>

```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Sampled
?streamViewId={streamViewId}&startIndex={startIndex}&endIndex={endIndex}&intervals={intervals}&sampleBy={sampleBy}&boundaryType={boundaryType}&startBoundaryType={startBoundaryType}&endBoundaryType={endBoundaryType}&filter={filter}
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#tenant<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#namespace<br/><br/>`string streamId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#stream<br/><br/>
`[optional] string streamViewId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#view<br/><br/>`[optional] string startIndex`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#startindex<br/><br/>`[optional] string endIndex`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#endindex<br/><br/>`[optional] integer intervals`
<br/>The number of intervals requested.<br/><br/>`[optional] string sampleBy`
<br/>Property or properties to use when sampling.<br/><br/>`[optional] integer boundaryType`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#boundaryType<br/><br/>`[optional] integer startBoundaryType`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#startBoundaryType<br/><br/>`[optional] integer endBoundaryType`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#endBoundaryType<br/><br/>`[optional] string filter`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/sds.yaml#filter<br/><br/>

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

