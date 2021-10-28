---
uid: data-views-data-views-data

---

# Data Views Data
#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-summaries.yaml#class-dataviewsdatacontroller

## `Get Data View Interpolated Data`

<a id="opIdDataViewsData_Get Data View Interpolated Data"></a>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-summaries.yaml#data-interpolated-get

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/data/interpolated
?startIndex={startIndex}&endIndex={endIndex}&interval={interval}&form={form}&continuationToken={continuationToken}&count={count}&cache={cache}
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#tenantId<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#namespaceId<br/><br/>`string id`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#dataViewId<br/><br/>`string startIndex`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-parameters.yaml#start-index<br/><br/>`string endIndex`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-parameters.yaml#end-index<br/><br/>`string interval`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-parameters.yaml#interval<br/><br/>`string form`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-parameters.yaml#form<br/><br/>`string continuationToken`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-parameters.yaml#continuation-token<br/><br/>`integer count`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-parameters.yaml#count-data<br/><br/>
`[optional] string cache`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-parameters.yaml#cache-data<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|string|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#200-data-get|
|400|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#400-data-get|
|403|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#403-standard-message|
|404|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#404-dataviewid-standard-message|
|500|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#500-standard-message|

<h4>Response Headers</h4>

|Status|Header|Type|Description|
|---|---|---|---|
|200|Link|string|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-headers.yaml#link-data-get|
|200|Next-Page|string|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-headers.yaml#next-page-standard-message|
|200|First-Page|string|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-headers.yaml#first-page-standard-message|

<h4>Example response body</h4>

> 200 Response

```json
null
```

> 400 Response ([ErrorResponse](#schemaerrorresponse))

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

## `Get Data View Stored Data`

<a id="opIdDataViewsData_Get Data View Stored Data"></a>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-summaries.yaml#data-stored-get

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/data/stored
?startIndex={startIndex}&endIndex={endIndex}&form={form}&continuationToken={continuationToken}&count={count}&cache={cache}
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#tenantId<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#namespaceId<br/><br/>`string id`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#dataViewId<br/><br/>`string startIndex`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-parameters.yaml#start-index<br/><br/>`string endIndex`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-parameters.yaml#end-index<br/><br/>`string form`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-parameters.yaml#form<br/><br/>`string continuationToken`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-parameters.yaml#continuation-token<br/><br/>`integer count`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-parameters.yaml#count-data<br/><br/>
`[optional] string cache`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-parameters.yaml#cache-data<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|string|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#200-data-get|
|400|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#400-data-get|
|403|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#403-standard-message|
|404|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#404-dataviewid-standard-message|
|409|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#409-data-get|
|500|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#500-standard-message|

<h4>Response Headers</h4>

|Status|Header|Type|Description|
|---|---|---|---|
|200|Link|string|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-headers.yaml#link-data-get|
|200|Next-Page|string|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-headers.yaml#next-page-standard-message|
|200|First-Page|string|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-headers.yaml#first-page-standard-message|

<h4>Example response body</h4>

> 200 Response

```json
null
```

> 400 Response ([ErrorResponse](#schemaerrorresponse))

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

