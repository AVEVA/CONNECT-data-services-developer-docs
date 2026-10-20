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
|200|[PageOfDataViewSchema](#schemapageofdataviewschema)|A list of data view schemas for the specified data view.|
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
|201|[DataViewSchema](#schemadataviewschema)|None|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|The specified data view identifier is not found.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request. See the response body for details.|

<h4>Example response body</h4>

> 201 Response ([DataViewSchema](#schemadataviewschema))

```json
{
  "Id": "string",
  "DataViewId": "string",
  "CreatedDate": "2019-08-24T14:15:22Z",
  "Fields": [
    {
      "Id": "string",
      "Label": "string",
      "TypeCode": 0,
      "Uom": "string",
      "FieldSetIndex": 0,
      "FieldIndex": 0,
      "IdentifyingValue": "string"
    }
  ],
  "LastStatus": 0,
  "LastErrors": [
    {
      "Error": "string",
      "Reason": "string",
      "Resolution": "string"
    }
  ]
}
```

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
|200|[DataViewSchema](#schemadataviewschema)|The requested data view schema.|
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
|204|None|Successfully deleted the data view schema.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|The specified data view identifier is not found.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request. See the response body for details.|

---

## `Get Bulk Data View Schemas`

<a id="opIdDataViewsSchema_Get Bulk Data View Schemas"></a>

#https://raw.githubusercontent.com/aveva/CONNECT-data-services-developer-docs/main/content/external-references/dataviews-summaries.yaml#schemas-getbulk

<h3>Request</h3>

```text 
POST /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/bulk/schemas/read
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

<h4>Request Body</h4>

#https://raw.githubusercontent.com/aveva/CONNECT-data-services-developer-docs/main/content/external-references/dataviews-parameters.yaml#get-schemas-bulk-request<br/>

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
|207|[GetBulkSchemasResponse](#schemagetbulkschemasresponse)|#https://raw.githubusercontent.com/aveva/CONNECT-data-services-developer-docs/main/content/external-references/dataviews-response-codes.yaml#207-schemas-getbulk|
|400|[ErrorResponse](#schemaerrorresponse)|The request is not valid. See the response body for details.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request. See the response body for details.|

<h4>Example response body</h4>

> 207 Response ([GetBulkSchemasResponse](#schemagetbulkschemasresponse))

```json
{
  "Schemas": [
    {
      "Id": "string",
      "DataViewId": "string",
      "CreatedDate": "2019-08-24T14:15:22Z",
      "Fields": [
        {
          "Id": "string",
          "Label": "string",
          "TypeCode": 0,
          "Uom": "string",
          "FieldSetIndex": 0,
          "FieldIndex": 0,
          "IdentifyingValue": "string"
        }
      ],
      "LastStatus": 0,
      "LastErrors": [
        {
          "Error": "string",
          "Reason": "string",
          "Resolution": "string"
        }
      ]
    }
  ],
  "Errors": [
    {
      "OperationId": "string",
      "Error": "string",
      "Reason": "string",
      "Resolution": "string",
      "Kind": 0,
      "Parameters": {
        "property1": "string",
        "property2": "string"
      },
      "ChildErrors": "[<ResultError>]"
    }
  ]
}
```

---
## Definitions

### PageOfDataViewSchema

<a id="schemapageofdataviewschema"></a>
<a id="schema_PageOfDataViewSchema"></a>
<a id="tocSpageofdataviewschema"></a>
<a id="tocspageofdataviewschema"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Items|[[DataViewSchema](#schemadataviewschema)]|false|true|[An object describing the schema (column information) of a resolved data view]|
|TotalCount|int32|false|false|None|

```json
{
  "Items": [
    {
      "Id": "string",
      "DataViewId": "string",
      "CreatedDate": "2019-08-24T14:15:22Z",
      "Fields": [
        {
          "Id": "string",
          "Label": "string",
          "TypeCode": 0,
          "Uom": "string",
          "FieldSetIndex": 0,
          "FieldIndex": 0,
          "IdentifyingValue": "string"
        }
      ],
      "LastStatus": 0,
      "LastErrors": [
        {
          "Error": "string",
          "Reason": "string",
          "Resolution": "string"
        }
      ]
    }
  ],
  "TotalCount": 0
}

```

---

### DataViewSchema

<a id="schemadataviewschema"></a>
<a id="schema_DataViewSchema"></a>
<a id="tocSdataviewschema"></a>
<a id="tocsdataviewschema"></a>

An object describing the schema (column information) of a resolved data view

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|The Data View Schema's unique identifier|
|DataViewId|string|false|true|The Id of the Data View used to generate this schema.|
|CreatedDate|date-time|false|false|When the Data View Schema was generated.|
|Fields|[[FrozenField](#schemafrozenfield)]|false|true|A list of frozen fields that contain information needed to ensure the schema does not change once generated|
|LastStatus|[DataViewSchemaStatus](#schemadataviewschemastatus)|false|false|The status of the last time an instance was retrieved with this schema.|
|LastErrors|[[DataViewSchemaError](#schemadataviewschemaerror)]|false|true|Any errors from the last time an instance was retrieved with this schema.|

```json
{
  "Id": "string",
  "DataViewId": "string",
  "CreatedDate": "2019-08-24T14:15:22Z",
  "Fields": [
    {
      "Id": "string",
      "Label": "string",
      "TypeCode": 0,
      "Uom": "string",
      "FieldSetIndex": 0,
      "FieldIndex": 0,
      "IdentifyingValue": "string"
    }
  ],
  "LastStatus": 0,
  "LastErrors": [
    {
      "Error": "string",
      "Reason": "string",
      "Resolution": "string"
    }
  ]
}

```

---

### FrozenField

<a id="schemafrozenfield"></a>
<a id="schema_FrozenField"></a>
<a id="tocSfrozenfield"></a>
<a id="tocsfrozenfield"></a>

An object containing all potentially mutable information about a field upon resolution, allowing schema reconstruction

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|The id of the field at resolution time|
|Label|string|false|true|The label of the field at resolution time|
|TypeCode|[SdsTypeCode](#schemasdstypecode)|false|true|The type code (if any) of the field at resolution time|
|Uom|string|false|true|The Uom (if any) of the field at resolution time|
|FieldSetIndex|int32|false|true|The (zero-based) index of the field set that the field belonged to at resolution time|
|FieldIndex|int32|false|true|The (zero-based) index of the field within the field set it belonged to at resolution time|
|IdentifyingValue|string|false|true|The identifying value of the field at resolution time|

```json
{
  "Id": "string",
  "Label": "string",
  "TypeCode": 0,
  "Uom": "string",
  "FieldSetIndex": 0,
  "FieldIndex": 0,
  "IdentifyingValue": "string"
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

### DataViewSchemaStatus

<a id="schemadataviewschemastatus"></a>
<a id="schema_DataViewSchemaStatus"></a>
<a id="tocSdataviewschemastatus"></a>
<a id="tocsdataviewschemastatus"></a>

Represents the status of the last data view resolution using this schema. The status will indicate if the instance of the data view was compatible, incompatible (out of date or missing some fields), or in an error state.

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|Compatible|0|
|Incompatible|1|
|InFallback|2|
|FallbackFailed|3|

---

### DataViewSchemaError

<a id="schemadataviewschemaerror"></a>
<a id="schema_DataViewSchemaError"></a>
<a id="tocSdataviewschemaerror"></a>
<a id="tocsdataviewschemaerror"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Error|string|false|true|None|
|Reason|string|false|true|None|
|Resolution|string|false|true|None|

```json
{
  "Error": "string",
  "Reason": "string",
  "Resolution": "string"
}

```

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

<a id="schemagetbulkschemasresponse"></a>
<a id="schema_GetBulkSchemasResponse"></a>
<a id="tocSgetbulkschemasresponse"></a>
<a id="tocsgetbulkschemasresponse"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Schemas|[[DataViewSchema](#schemadataviewschema)]|false|true|[An object describing the schema (column information) of a resolved data view]|
|Errors|[[ResultError](#schemaresulterror)]|false|true|None|

```json
{
  "Schemas": [
    {
      "Id": "string",
      "DataViewId": "string",
      "CreatedDate": "2019-08-24T14:15:22Z",
      "Fields": [
        {
          "Id": "string",
          "Label": "string",
          "TypeCode": 0,
          "Uom": "string",
          "FieldSetIndex": 0,
          "FieldIndex": 0,
          "IdentifyingValue": "string"
        }
      ],
      "LastStatus": 0,
      "LastErrors": [
        {
          "Error": "string",
          "Reason": "string",
          "Resolution": "string"
        }
      ]
    }
  ],
  "Errors": [
    {
      "OperationId": "string",
      "Error": "string",
      "Reason": "string",
      "Resolution": "string",
      "Kind": 0,
      "Parameters": {
        "property1": "string",
        "property2": "string"
      },
      "ChildErrors": "[<ResultError>]"
    }
  ]
}

```

---

### ResultError

<a id="schemaresulterror"></a>
<a id="schema_ResultError"></a>
<a id="tocSresulterror"></a>
<a id="tocsresulterror"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|false|true|None|
|Error|string|false|true|None|
|Reason|string|false|true|None|
|Resolution|string|false|true|None|
|Kind|[ResultErrorKind](#schemaresulterrorkind)|false|false|None|
|Parameters|object|false|true|None|
|ChildErrors|[[ResultError](#schemaresulterror)]|false|true|None|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Kind": 0,
  "Parameters": {
    "property1": "string",
    "property2": "string"
  },
  "ChildErrors": "[<ResultError>]"
}

```

---

### ResultErrorKind

<a id="schemaresulterrorkind"></a>
<a id="schema_ResultErrorKind"></a>
<a id="tocSresulterrorkind"></a>
<a id="tocsresulterrorkind"></a>

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|UnspecifiedServerError|0|
|RequestInvalid|1|
|ResourceNotFound|2|
|OperationForbidden|3|
|OperationInvalid|4|
|OperationFailed|5|
|ResourceUnavailable|6|
|SchemaInvalid|7|

---

### GetBulkSchemasRequest

<a id="schemagetbulkschemasrequest"></a>
<a id="schema_GetBulkSchemasRequest"></a>
<a id="tocSgetbulkschemasrequest"></a>
<a id="tocsgetbulkschemasrequest"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Ids|string[]|false|true|None|

```json
{
  "Ids": [
    "string"
  ]
}

```

---

