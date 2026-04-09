---
uid: data-views-data-views-schemas

---

# Data View Schemas
The `DataViewSchema` API provides mechanisms to create, read, and delete data view schemas. This is one portion of the whole [data views API](xref:DataViewsAPIOverview).

## `List Data View Schemas`

<a id="opIdDataViews_List Data View Schemas"></a>

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
|200|[DataViewSchema](#schemadataviewschema)[]|A list of data view schemas for the specified data view. A response header, Total-Count, indicates the total size of the collection.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|The data view does not exist.|
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

---

## `Get Data View Schema`

<a id="opIdDataViews_Get Data View Schema"></a>

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
<br/>Schema identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[DataViewSchema](#schemadataviewschema)|The specified data view schema.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|The data view or data view schema does not exist.|
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

---

## `Create Data View Schema`

<a id="opIdDataViews_Create Data View Schema"></a>

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
|201|[DataViewSchema](#schemadataviewschema)|The created data view schema.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|The data view does not exist.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request. See the response body for details.|

<h4>Example response body</h4>

> 201 Response

```json
HTTP 201 Created
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

---

## `Delete Data View Schema`

<a id="opIdDataViews_Get Data View Schema"></a>

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
<br/>Schema identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|Successfully deleted the data view schema.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|The data view or data view schema does not exist.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request. See the response body for details.|

---

## `Get Data View Schemas in Bulk`

<a id="opIdDataViews_Get Data View Schemas in Bulk"></a>

Queries for and returns multiple data view schemas at once. The schemas requested may be associated one or more data views.

<h3>Request</h3>

```text 
POST /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/bulk/schemas/read
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string id`

<h4>Request Body</h4>

A `GetBulkSchemasRequest` object.<br/>

```json
{
  "Ids": [
    "string"
  ]
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|207|[GetBulkSchemasResponse](#schemabulkschemaresponse)[]|An object containing all requested schemas and any errors encountered during retrieval.|
|400|[ErrorResponse](#schemaerrorresponse)|The request is not valid. See the response body for details.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request. See the response body for details.|

<h4>Example response body</h4>

> 200 Response

```json
HTTP 207 Multistatus
Content-Type: application/json
{
  "Schemas": [
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
      "DataViewId": "demo view 2",
      "CreatedDate": "2020-02-15T01:31:13Z",
      "Fields": [
        ...
      ]
    },
  ],
  "Errors": [
    {
      "Error": "Error text",
      "Reason": "Reason text",
      "Resolution": "Resolution text"
      "Kind":  "ErrorKind",
      "Parameters": {
        "Schema Id": "33333333-3333-3333-3333-333333333333",
        ...
      },
      "ChildErrors": [
        ...
      ]
    },
    {
      "Error": "Error text",
      "Reason": "Reason text",
      "Resolution": "Resolution text"
      "Kind":  "ErrorKind",
      "Parameters": {
        "Schema Id": "44444444-4444-4444-4444-444444444444",
        ...
      },
      "ChildErrors": [
        ...
      ]
    }
  ]
}
```

---

## Definitions

### DataViewSchema

<a id="schemadataviewschema"></a>
<a id="schema_DataViewSchema"></a>
<a id="tocSdataviewschema"></a>
<a id="tocsdataviewschema"></a>

A fixed representation of the fields in a resolved data view as generated at a point in time.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|true|false|The data view schema's unique identifier|
|DataViewId|string|true|false|The unique identifier of the data view used to generate the schema|
|CreatedDate|date-time|true|false|The date and time when the schema was created|
|Fields|[Field](#schemafrozenfield)[]|true|false|The list of fields included in the schema|

```json
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

---

### Field

<a id="schemafrozenfield"></a>
<a id="schema_FrozenField"></a>
<a id="tocSfrozenfield"></a>
<a id="tocsfrozenfield"></a>

A fixed representation of a single field or column in a resolved data view as generated at a point in time.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|true|false|The unique identifer of the field at schema creation time|
|Label|string|true|false|The label of the field at schema creation time|
|TypeCode|[SdsTypeCode](#schemasdstypecode)|false|true|The SDS type of the field at schema creation time|
|Uom|string|false|true|The unit of measure of the field at schema creation time|
|FieldSetIndex|int|false|true|The field set index of the field at schema creation time|
|FieldIndex|int|false|true|The field index of the field at schema creation time|
|IdentifyingValue|string|false|true|The identifying value of the field at schema creation time|

```json
{
  "Id": "Power In Value",
  "Label": "Power In Value",
  "TypeCode": "Double",
  "Uom": "kW",
  "FieldSetIndex": 0,
  "FieldIndex": 0,
  "IdentifyingValue": "Power In"
}

```

---

### SdsTypeCode

<a id="schemasdstypecode"></a>
<a id="schema_SdsTypeCode"></a>
<a id="tocSsdstypecode"></a>
<a id="tocssdstypecode"></a>

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|Empty|0|
|Object|1|
|Boolean|3|
|Char|4|
|SByte|5|
|Byte|6|
|Int16|7|
|UInt16|8|
|Int32|9|
|UInt32|10|
|Int64|11|
|UInt64|12|
|Single|13|
|Double|14|
|Decimal|15|
|DateTime|16|
|String|18|
|Guid|19|
|DateTimeOffset|20|
|TimeSpan|21|
|Version|22|
|NullableBoolean|103|
|NullableChar|104|
|NullableSByte|105|
|NullableByte|106|
|NullableInt16|107|
|NullableUInt16|108|
|NullableInt32|109|
|NullableUInt32|110|
|NullableInt64|111|
|NullableUInt64|112|
|NullableSingle|113|
|NullableDouble|114|
|NullableDecimal|115|
|NullableDateTime|116|
|NullableGuid|119|
|NullableDateTimeOffset|120|
|NullableTimeSpan|121|
|BooleanArray|203|
|CharArray|204|
|SByteArray|205|
|ByteArray|206|
|Int16Array|207|
|UInt16Array|208|
|Int32Array|209|
|UInt32Array|210|
|Int64Array|211|
|UInt64Array|212|
|SingleArray|213|
|DoubleArray|214|
|DecimalArray|215|
|DateTimeArray|216|
|StringArray|218|
|GuidArray|219|
|DateTimeOffsetArray|220|
|TimeSpanArray|221|
|VersionArray|222|
|Array|400|
|IList|401|
|IDictionary|402|
|IEnumerable|403|
|SdsType|501|
|SdsTypeProperty|502|
|SdsStreamView|503|
|SdsStreamViewProperty|504|
|SdsStreamViewMap|505|
|SdsStreamViewMapProperty|506|
|SdsStream|507|
|SdsStreamIndex|508|
|SdsTable|509|
|SdsColumn|510|
|SdsValues|511|
|SdsObject|512|
|SByteEnum|605|
|ByteEnum|606|
|Int16Enum|607|
|UInt16Enum|608|
|Int32Enum|609|
|UInt32Enum|610|
|Int64Enum|611|
|UInt64Enum|612|
|NullableSByteEnum|705|
|NullableByteEnum|706|
|NullableInt16Enum|707|
|NullableUInt16Enum|708|
|NullableInt32Enum|709|
|NullableUInt32Enum|710|
|NullableInt64Enum|711|
|NullableUInt64Enum|712|

---

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

### GetBulkSchemasResponse

<a id="schemabulkschemaresponse"></a>
<a id="schema_GetBulkSchemasResponse"></a>
<a id="tocSbulkschemaresponse"></a>
<a id="tocsbulkschemaresponse"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Schemas|Array|true|false|Array containing successfully retrieved schemas.|
|Errors|Array|true|false|Array containing any errors in schema retrieval.|

```json
{
  "Schemas": [
    {
      "Id": "string",
      "DataViewId": "string",
      "CreatedDate": DateTime,
      "Fields": [
        ...
      ]
    }
  ],
  "Errors": [
    {
      "Error": "string",
      "Reason": "string",
      "Resolution": "string"
      "Kind":  "ErrorKind",
      "Parameters": {
        "Schema Id": "string",
        ...
      },
      "ChildErrors": [
        ...
      ]
    }
  ]
}

```

---