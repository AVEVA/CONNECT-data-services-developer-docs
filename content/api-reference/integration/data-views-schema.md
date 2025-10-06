---
uid: ""

---

# Data Views Schema
This portion of the overall [data views API](xref:DataViewsAPIOverview) provides mechanisms to create, read, and delete data view schemas.

## `Get Data View Schemas`

<a id="opIdDataViewsSchema_Get Data View Schemas"></a>

Returns a list of data view schemas for the specified data view.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/schemas
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string id`
<br/>Data view identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|string|A list of data view schemas for the specified data view.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|The specified data view identifier is not found.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request. See the response body for details.|

<h4>Response Headers</h4>

|Status|Header|Type|Description|
|---|---|---|---|
|200|Total-Count|integer|The total count of data view schemas for the specified data view.|

<h4>Example response body</h4>

> 200 Response

```json
HTTP 200 OK
Content-Type: application/json
[
  {
    "Id": "00000000-0000-0000-0000-000000000000",
    "DataViewId": "demo view 1",
    "CreatedDate": "2019-12-13T01:23:45Z",
    "Fields": [
      ...
    ]
  },
  {
    "Id": "11111111-1111-1111-1111-111111111111",
    "DataViewId": "demo view 1",
    "CreatedDate": "2020-01-06T06:23:15Z",
    "Fields": [
      ...
    ]
  },
  {
    "Id": "22222222-2222-2222-2222-222222222222",
    "DataViewId": "demo view 1",
    "CreatedDate": "2020-02-15T01:31:13Z",
    "Fields": [
      ...
    ]
  }
]
```
> 403 Response ([ErrorResponse](#schemaerrorresponse))

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

## `Create Data View Schema`

<a id="opIdDataViewsSchema_Create Data View Schema"></a>

Creates a new data view schema and returns the schema as generated in the response.

<h3>Request</h3>

```text 
POST /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/schemas
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string id`
<br/>Data view identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|201|string|None|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|The specified data view identifier is not found.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request. See the response body for details.|

---

## `Get Data View Schema`

<a id="opIdDataViewsSchema_Get Data View Schema"></a>

Returns the specified data view schema.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/schemas/{schemaId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string id`
<br/>Data view identifier.<br/><br/>`string schemaId`
<br/>Data view schema identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|string|The requested data view schema.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|The specified data view identifier is not found.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request. See the response body for details.|

<h4>Example response body</h4>

> 200 Response

```json
HTTP 200 OK
Content-Type: application/json
{
  "Id": "00000000-0000-0000-0000-000000000000",
  "DataViewId": "demo view 1",
  "CreatedDate": "2019-12-13T01:23:45Z",
  "Fields": [
    {
      "Id": "Timestamp",
      "Label": "Timestamp",
      "TypeCode": "DateTime"
    },
    {
      "Id": "Site",
      "Label": "Site",
      "TypeCode": "String",
      "FieldIndex": 0
    },
    {
      "Id": "Power In Value",
      "Label": "Power In Value",
      "TypeCode": "Double",
      "FieldSetIndex": 0,
      "FieldIndex": 0,
      "IdentifyingValue": "Power In"
    },
    {
      "Id": "Power Out Value",
      "Label": "Power Out Value",
      "TypeCode": "Double",
      "FieldSetIndex": 0,
      "FieldIndex": 0,
      "IdentifyingValue": "Power Out"
    }
  ]
}
```
> 403 Response ([ErrorResponse](#schemaerrorresponse))

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

## `Delete Data View Schema`

<a id="opIdDataViewsSchema_Delete Data View Schema"></a>

Deletes the data view schema with the specified id.

<h3>Request</h3>

```text 
DELETE /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/schemas/{schemaId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string id`
<br/>Data view identifier.<br/><br/>`string schemaId`
<br/>Data view schema identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|string|Successfully deleted the data view schema.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|The specified data view identifier is not found.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request. See the response body for details.|

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

