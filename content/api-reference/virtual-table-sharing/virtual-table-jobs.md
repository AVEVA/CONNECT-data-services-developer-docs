---
uid: ""

---

# Virtual Table Jobs
Controller for job history.

## `Get Job History`

<a id="opIdVirtualTableJobs_Get Job History"></a>

Returns the job history.

<h3>Request</h3>

```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/virtualTableJobs
?startTime={startTime}&endTime={endTime}&virtualTableId={virtualTableId}&jobState={jobState}&skip={skip}&count={count}&activeDataGapsOnly={activeDataGapsOnly}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>
`[optional] string startTime`
<br/>If specified, jobs active or created after this time will be returned. Required if `endTime` is specified.<br/><br/>`[optional] string endTime`
<br/>If specified, jobs active or created before this time will be returned.<br/><br/>`[optional] string virtualTableId`
<br/>If specified, only jobs for this Virtual Table will be returned.<br/><br/>`[optional] string jobState`
<br/>If specified, only jobs matching this state will be returned. Allowed states: PENDING, RUNNING, COMPLETE, CANCELED, TIMEDOUT, FAILED.<br/><br/>`[optional] integer skip`
<br/>Number of entries to skip when paging. Default: 0.<br/><br/>`[optional] integer count`
<br/>Maximum number of entries to return. Default: 100. Maximum allowed: 1000.<br/><br/>`[optional] boolean activeDataGapsOnly`
<br/>If true, only jobs with active data gaps will be returned.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|string|Job history for all jobs matching filter conditions.|
|400|[ErrorResponse](#schemaerrorresponse)|Bad request.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

---

## `Refresh Data Gaps`

<a id="opIdVirtualTableJobs_Refresh Data Gaps"></a>

Refreshes all data gaps from a specified Job or Virtual Table.

<h3>Request</h3>

```text 
POST /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/virtualTableJobs
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>

<h4>Request Body</h4>

Data gap refresh DTO.<br/>

```json
{
  "jobId": 0,
  "virtualTableId": "string"
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|string|Empty response.|
|400|[ErrorResponse](#schemaerrorresponse)|Bad request.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

---

## `Get Job By Id`

<a id="opIdVirtualTableJobs_Get Job By Id"></a>

Gets a job by id.

<h3>Request</h3>

```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/virtualTableJobs/{jobId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`integer jobId`
<br/>ID of the job to retrieve.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|string|Job with specified ID.|
|400|[ErrorResponse](#schemaerrorresponse)|Bad request.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

---

## `Dismiss Data Gaps`

<a id="opIdVirtualTableJobs_Dismiss Data Gaps"></a>

Dismisses a data gap.

<h3>Request</h3>

```text 
POST /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/virtualTableJobs/{jobId}/dataGapDismissals
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`integer jobId`
<br/>ID of the job with gaps to dismiss.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|string|Empty response.|
|400|[ErrorResponse](#schemaerrorresponse)|Bad request.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

---
## Definitions

### ErrorResponse

<a id="schemaerrorresponse"></a>
<a id="schema_ErrorResponse"></a>
<a id="tocSerrorresponse"></a>
<a id="tocserrorresponse"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|false|true|None|
|Error|string|false|true|None|
|Reason|string|false|true|None|
|Resolution|string|false|true|None|
|Parameters|object|false|true|None|
|ChildErrors|object|false|true|None|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  },
  "ChildErrors": {
    "property1": null,
    "property2": null
  }
}

```

---

### DataGapRefreshDto

<a id="schemadatagaprefreshdto"></a>
<a id="schema_DataGapRefreshDto"></a>
<a id="tocSdatagaprefreshdto"></a>
<a id="tocsdatagaprefreshdto"></a>

DTO for refreshing all data gaps from a specified Job or Virtual Table.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|jobId|int64|false|true|JobId for a job with data gaps to be refreshed.|
|virtualTableId|string|false|true|VirtualTableId for a Virtual Table with data gaps to be refreshed.|

```json
{
  "jobId": 0,
  "virtualTableId": "string"
}

```

---

