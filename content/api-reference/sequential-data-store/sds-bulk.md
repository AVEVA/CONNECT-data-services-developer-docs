---
uid: streams-bulk

---

# Bulk Streams
Defines the API endpoint for bulk stream data access.

## `Join Bulk Stream Values`

<a id="opIdStreamBulk_Join Bulk Stream Values"></a>

Returns all values between a given start and end date, joined according to a given join mode for all stream IDs in a comma-separated list. If no value exists for a stream at a timestamp that is required by the join mode, null is returned.

<h3>Request</h3>

```text
GET /api/v1/Tenants/{tenantId}/Namespaces{namespaceId}/Bulk/Streams/Data/Joins?streams={streamIds}&joinMode={joinMode}&startIndex={startIndex}&endIndex={endIndex}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>
`string namespaceId`
<br/>Namespace identifier.<br/><br/>
`string streamIds`
<br/>Stream IDs, comma seperated.<br/><br/>
`integer joinMode`
<br/>join mode for the query<br/>
|Join Mode|Join Type|Description|
|---|---|---|
|0|Inner|Returns one row for each unique timestamp that occurs in all streams in the data set|
|1|Outer|Returns one row for every unique timestamp in the data set, returns null when a stream does not have a value for the timestamp|
|2|Outer Interpolated|Returns one row for every unique timestamp in the data set, returns an interpolated value when a stream does not have a value for the timestamp|
|3|Outer Left|Returns one row for every unique timestamp in the data set with one column of values corresponding to the first non-null value starting from the left-most streamId|
|4|Outer Right|Returns one row for every unique timestamp in the data set with one column of values corresponding to the first non-null value starting from the right-most streamId|
<br/><br/>
`string startIndex`
<br/>Index identifying the beginning of the request window<br/><br/>
`string endIndex`
<br/>Index identifying the end of the request window<br/><br/>

<h3>Response</h3>
|Status Code|Body Type|Description|
|200|Inline|Returns a serialized collection of events in a format defined by the joinMode|
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

The error response contains details on the cause of the error.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Message|string|false|true|Error description|

```json
{
  "Message": "string"
}

```