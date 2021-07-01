---
uid: sds-stream-data-transform

---

# Stream Data Transform
ERROR: The URL https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/datacalls.yaml#stream-data-transform is invalid and/or its contents could not be read.

## `List Data`

<a id="opIdStreamDataTransform_List Data"></a>

ERROR: The URL https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/datacalls.yaml#list-values is invalid and/or its contents could not be read.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>

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
> 400 Response

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

## `Get Data2`

<a id="opIdStreamDataTransform_Get Data2"></a>

ERROR: The URL https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/datacalls.yaml#list-values is invalid and/or its contents could not be read.

### Request
```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>

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
> 400 Response

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

## `Get First`

<a id="opIdStreamDataTransform_Get First"></a>

Returns the first value in the stream. If no values exist in the stream, null is returned.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/First
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>

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
> 400 Response

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

## `Get First2`

<a id="opIdStreamDataTransform_Get First2"></a>

Returns the first value in the stream. If no values exist in the stream, null is returned.

### Request
```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/First
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>

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
> 400 Response

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

## `List Data Interpolated`

<a id="opIdStreamDataTransform_List Data Interpolated"></a>

ERROR: The URL https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/datacalls.yaml#interpolated-values is invalid and/or its contents could not be read.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Interpolated
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>

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
> 400 Response

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

## `Get Data Interpolated2`

<a id="opIdStreamDataTransform_Get Data Interpolated2"></a>

ERROR: The URL https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/datacalls.yaml#interpolated-values is invalid and/or its contents could not be read.

### Request
```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Interpolated
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>

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
> 400 Response

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

## `Get Last`

<a id="opIdStreamDataTransform_Get Last"></a>

Returns the last value in the stream. If no values exist in the stream, null is returned.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Last
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>

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
> 400 Response

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

## `Get Last2`

<a id="opIdStreamDataTransform_Get Last2"></a>

Returns the last value in the stream. If no values exist in the stream, null is returned.

### Request
```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Last
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>

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
> 400 Response

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

## `List Data Samples`

<a id="opIdStreamDataTransform_List Data Samples"></a>

Returns representative data sampled by intervals between a specified start and end index. Sampling is driven by a specified property or properties of the stream's Sds Type. Property types that cannot be interpolated do not support sampling requests. Strings are an example of a property that cannot be interpolated.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Sampled
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>

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
> 400 Response

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

## `Get Data Samples2`

<a id="opIdStreamDataTransform_Get Data Samples2"></a>

Returns representative data sampled by intervals between a specified start and end index. Sampling is driven by a specified property or properties of the stream's Sds Type. Property types that cannot be interpolated do not support sampling requests. Strings are an example of a property that cannot be interpolated.

### Request
```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Sampled
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>

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
> 400 Response

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

## `List Data Summaries`

<a id="opIdStreamDataTransform_List Data Summaries"></a>

Returns summary intervals between a specified start and end index. Index types that cannot be interpolated do not support summary requests. Strings are an example of indexes that cannot be interpolated. Summaries are not supported for streams with compound indexes. Interpolating between two indexes that consist of multiple properties is not defined and results in non-determinant behavior.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Summaries
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>

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
> 400 Response

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

## `Get Data Summaries2`

<a id="opIdStreamDataTransform_Get Data Summaries2"></a>

Returns summary intervals between a specified start and end index. Index types that cannot be interpolated do not support summary requests. Strings are an example of indexes that cannot be interpolated. Summaries are not supported for streams with compound indexes. Interpolating between two indexes that consist of multiple properties is not defined and results in non-determinant behavior.

### Request
```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Transform/Summaries
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/><br/>

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
> 400 Response

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

