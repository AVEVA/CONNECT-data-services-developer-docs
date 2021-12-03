---
uid: asset-asset-change-data

---

# Asset Change Data

## `Get Statistics For Rule`

<a id="opIdAssetChangeData_Get Statistics For Rule"></a>

Returns the `AssetRuleStatistics` for the ruleId.

<h3>Request</h3>

```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/admin/assetrules/changedata/rule/{ruleId}/statistics
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string ruleId`
<br/>Rule identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AssetRuleStatistics](#schemaassetrulestatistics)|The `AssetRuleStatistics` for the ruleId.|
|403|[ResponseBody](#schemaresponsebody)|Forbidden.|
|500|[ResponseBody](#schemaresponsebody)|Internal server error.|

<h4>Example response body</h4>

> 200 Response

```json
{
  "AssetsAffected": 0,
  "StreamsExecutedOn": 0
}
```

> 403 Response

```json
{
  "OperationId": "00000000-0000-0000-0000-000000000000",
  "Error": "Error message.",
  "Reason": "Reason that caused the error.",
  "Resolution": "Possible resolution for the error.",
  "Parameters": {
    "key1": "value1",
    "key2": "value2"
  }
}
```

> 500 Response

```json
{
  "OperationId": "00000000-0000-0000-0000-000000000000",
  "Error": "Error message.",
  "Reason": "Reason that caused the error.",
  "Resolution": "Possible resolution for the error.",
  "Parameters": {
    "key1": "value1",
    "key2": "value2"
  }
}
```

---

## `List Change Data For Rule`

<a id="opIdAssetChangeData_List Change Data For Rule"></a>

Returns the collection of `AssetChangeData` for the ruleId.

<h3>Request</h3>

```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/admin/assetrules/changedata/rule/{ruleId}
?Skip={Skip}&Count={Count}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string ruleId`
<br/>Rule identifier.<br/><br/>
`[optional] integer Skip`
<br/>An Int32 specifying the number of results to skip.
Defaults to 0.<br/><br/>`[optional] integer Count`
<br/>An Int32 specifying the number of results to return.
Defaults to 100.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AssetChangeData](#schemaassetchangedata)[]|The collection of `AssetChangeData` for the ruleId.|
|400|[ResponseBody](#schemaresponsebody)|Missing or invalid inputs.|
|403|[ResponseBody](#schemaresponsebody)|Forbidden.|
|500|[ResponseBody](#schemaresponsebody)|Internal server error.|

<h4>Example response body</h4>

> 200 Response

```json
[
  {
    "RuleId": "ruleId",
    "StreamId": "streamId",
    "GeneratedAsset": {
      "Id": "id",
      "AssetTypeId": "assetTypeId",
      "Name": "name",
      "Description": "description",
      "Metadata": [
        {
          "Id": "id",
          "Name": "name",
          "Description": "description",
          "SdsTypeCode": 18,
          "Value": "value",
          "Uom": "uom"
        }
      ],
      "StreamReferences": [
        {
          "Id": "id",
          "Name": "name",
          "Description": "description",
          "StreamId": "streamId"
        }
      ],
      "Status": {
        "Name": "name",
        "Description": "description",
        "StreamReferenceId": "streamReferenceId",
        "StreamPropertyId": "streamPropertyId",
        "ValueStatusMappings": [
          {
            "Value": "value",
            "Status": 1,
            "DisplayName": "displayName"
          }
        ]
      }
    }
  },
  {
    "RuleId": "ruleId",
    "StreamId": "streamId",
    "GeneratedAsset": {
      "Id": "id",
      "AssetTypeId": "assetTypeId",
      "Name": "name",
      "Description": "description",
      "Metadata": [
        {
          "Id": "id",
          "Name": "name",
          "Description": "description",
          "SdsTypeCode": 18,
          "Value": "value",
          "Uom": "uom"
        }
      ],
      "StreamReferences": [
        {
          "Id": "id",
          "Name": "name",
          "Description": "description",
          "StreamId": "streamId"
        }
      ],
      "Status": {
        "Name": "name",
        "Description": "description",
        "StreamReferenceId": "streamReferenceId",
        "StreamPropertyId": "streamPropertyId",
        "ValueStatusMappings": [
          {
            "Value": "value",
            "Status": 1,
            "DisplayName": "displayName"
          }
        ]
      }
    }
  }
]
```

> 400 Response

```json
{
  "OperationId": "00000000-0000-0000-0000-000000000000",
  "Error": "Error message.",
  "Reason": "Reason that caused the error.",
  "Resolution": "Possible resolution for the error.",
  "Parameters": {
    "key1": "value1",
    "key2": "value2"
  }
}
```

> 403 Response

```json
{
  "OperationId": "00000000-0000-0000-0000-000000000000",
  "Error": "Error message.",
  "Reason": "Reason that caused the error.",
  "Resolution": "Possible resolution for the error.",
  "Parameters": {
    "key1": "value1",
    "key2": "value2"
  }
}
```

> 500 Response

```json
{
  "OperationId": "00000000-0000-0000-0000-000000000000",
  "Error": "Error message.",
  "Reason": "Reason that caused the error.",
  "Resolution": "Possible resolution for the error.",
  "Parameters": {
    "key1": "value1",
    "key2": "value2"
  }
}
```

---

## `List Change Data For Asset`

<a id="opIdAssetChangeData_List Change Data For Asset"></a>

Returns the collection of `AssetChangeData` for the assetId.

<h3>Request</h3>

```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/admin/assetrules/changedata/asset/{assetId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string assetId`
<br/>Asset identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AssetChangeData](#schemaassetchangedata)[]|The collection of `AssetChangeData` for the assetId.|
|403|[ResponseBody](#schemaresponsebody)|Forbidden.|
|500|[ResponseBody](#schemaresponsebody)|Internal server error.|

<h4>Example response body</h4>

> 200 Response

```json
[
  {
    "RuleId": "ruleId",
    "StreamId": "streamId",
    "GeneratedAsset": {
      "Id": "id",
      "AssetTypeId": "assetTypeId",
      "Name": "name",
      "Description": "description",
      "Metadata": [
        {
          "Id": "id",
          "Name": "name",
          "Description": "description",
          "SdsTypeCode": 18,
          "Value": "value",
          "Uom": "uom"
        }
      ],
      "StreamReferences": [
        {
          "Id": "id",
          "Name": "name",
          "Description": "description",
          "StreamId": "streamId"
        }
      ],
      "Status": {
        "Name": "name",
        "Description": "description",
        "StreamReferenceId": "streamReferenceId",
        "StreamPropertyId": "streamPropertyId",
        "ValueStatusMappings": [
          {
            "Value": "value",
            "Status": 1,
            "DisplayName": "displayName"
          }
        ]
      }
    }
  },
  {
    "RuleId": "ruleId",
    "StreamId": "streamId",
    "GeneratedAsset": {
      "Id": "id",
      "AssetTypeId": "assetTypeId",
      "Name": "name",
      "Description": "description",
      "Metadata": [
        {
          "Id": "id",
          "Name": "name",
          "Description": "description",
          "SdsTypeCode": 18,
          "Value": "value",
          "Uom": "uom"
        }
      ],
      "StreamReferences": [
        {
          "Id": "id",
          "Name": "name",
          "Description": "description",
          "StreamId": "streamId"
        }
      ],
      "Status": {
        "Name": "name",
        "Description": "description",
        "StreamReferenceId": "streamReferenceId",
        "StreamPropertyId": "streamPropertyId",
        "ValueStatusMappings": [
          {
            "Value": "value",
            "Status": 1,
            "DisplayName": "displayName"
          }
        ]
      }
    }
  }
]
```

> 403 Response

```json
{
  "OperationId": "00000000-0000-0000-0000-000000000000",
  "Error": "Error message.",
  "Reason": "Reason that caused the error.",
  "Resolution": "Possible resolution for the error.",
  "Parameters": {
    "key1": "value1",
    "key2": "value2"
  }
}
```

> 500 Response

```json
{
  "OperationId": "00000000-0000-0000-0000-000000000000",
  "Error": "Error message.",
  "Reason": "Reason that caused the error.",
  "Resolution": "Possible resolution for the error.",
  "Parameters": {
    "key1": "value1",
    "key2": "value2"
  }
}
```

---

## `List Change Data For Stream`

<a id="opIdAssetChangeData_List Change Data For Stream"></a>

Returns the collection of `AssetChangeData` for the streamId.

<h3>Request</h3>

```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/admin/assetrules/changedata/stream/{streamId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string streamId`
<br/>Stream identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AssetChangeData](#schemaassetchangedata)[]|The collection of `AssetChangeData` for the streamId.|
|403|[ResponseBody](#schemaresponsebody)|Forbidden.|
|500|[ResponseBody](#schemaresponsebody)|Internal server error.|

<h4>Example response body</h4>

> 200 Response

```json
[
  {
    "RuleId": "ruleId",
    "StreamId": "streamId",
    "GeneratedAsset": {
      "Id": "id",
      "AssetTypeId": "assetTypeId",
      "Name": "name",
      "Description": "description",
      "Metadata": [
        {
          "Id": "id",
          "Name": "name",
          "Description": "description",
          "SdsTypeCode": 18,
          "Value": "value",
          "Uom": "uom"
        }
      ],
      "StreamReferences": [
        {
          "Id": "id",
          "Name": "name",
          "Description": "description",
          "StreamId": "streamId"
        }
      ],
      "Status": {
        "Name": "name",
        "Description": "description",
        "StreamReferenceId": "streamReferenceId",
        "StreamPropertyId": "streamPropertyId",
        "ValueStatusMappings": [
          {
            "Value": "value",
            "Status": 1,
            "DisplayName": "displayName"
          }
        ]
      }
    }
  },
  {
    "RuleId": "ruleId",
    "StreamId": "streamId",
    "GeneratedAsset": {
      "Id": "id",
      "AssetTypeId": "assetTypeId",
      "Name": "name",
      "Description": "description",
      "Metadata": [
        {
          "Id": "id",
          "Name": "name",
          "Description": "description",
          "SdsTypeCode": 18,
          "Value": "value",
          "Uom": "uom"
        }
      ],
      "StreamReferences": [
        {
          "Id": "id",
          "Name": "name",
          "Description": "description",
          "StreamId": "streamId"
        }
      ],
      "Status": {
        "Name": "name",
        "Description": "description",
        "StreamReferenceId": "streamReferenceId",
        "StreamPropertyId": "streamPropertyId",
        "ValueStatusMappings": [
          {
            "Value": "value",
            "Status": 1,
            "DisplayName": "displayName"
          }
        ]
      }
    }
  }
]
```

> 403 Response

```json
{
  "OperationId": "00000000-0000-0000-0000-000000000000",
  "Error": "Error message.",
  "Reason": "Reason that caused the error.",
  "Resolution": "Possible resolution for the error.",
  "Parameters": {
    "key1": "value1",
    "key2": "value2"
  }
}
```

> 500 Response

```json
{
  "OperationId": "00000000-0000-0000-0000-000000000000",
  "Error": "Error message.",
  "Reason": "Reason that caused the error.",
  "Resolution": "Possible resolution for the error.",
  "Parameters": {
    "key1": "value1",
    "key2": "value2"
  }
}
```

---
## Definitions

### AssetRuleStatistics

<a id="schemaassetrulestatistics"></a>
<a id="schema_AssetRuleStatistics"></a>
<a id="tocSassetrulestatistics"></a>
<a id="tocsassetrulestatistics"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|AssetsAffected|int32|false|false|None|
|StreamsExecutedOn|int32|false|false|None|

```json
{
  "AssetsAffected": 0,
  "StreamsExecutedOn": 0
}

```

---

### ResponseBody

<a id="schemaresponsebody"></a>
<a id="schema_ResponseBody"></a>
<a id="tocSresponsebody"></a>
<a id="tocsresponsebody"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|false|true|None|
|Error|string|false|true|None|
|Reason|string|false|true|None|
|Resolution|string|false|true|None|
|Parameters|object|false|true|None|

```json
{
  "OperationId": "00000000-0000-0000-0000-000000000000",
  "Error": "Error message.",
  "Reason": "Reason that caused the error.",
  "Resolution": "Possible resolution for the error.",
  "Parameters": {
    "key1": "value1",
    "key2": "value2"
  }
}

```

---

### AssetChangeData

<a id="schemaassetchangedata"></a>
<a id="schema_AssetChangeData"></a>
<a id="tocSassetchangedata"></a>
<a id="tocsassetchangedata"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|RuleId|string|false|true|None|
|StreamId|string|false|true|None|
|GeneratedAsset|[Asset](#schemaasset)|false|true|The asset which was generated by the RuleId and StreamId combination.|

```json
{
  "RuleId": "ruleId",
  "StreamId": "streamId",
  "GeneratedAsset": {
    "Id": "id",
    "AssetTypeId": "assetTypeId",
    "Name": "name",
    "Description": "description",
    "Metadata": [
      {
        "Id": "id",
        "Name": "name",
        "Description": "description",
        "SdsTypeCode": 18,
        "Value": "value",
        "Uom": "uom"
      }
    ],
    "StreamReferences": [
      {
        "Id": "id",
        "Name": "name",
        "Description": "description",
        "StreamId": "streamId"
      }
    ],
    "Status": {
      "Name": "name",
      "Description": "description",
      "StreamReferenceId": "streamReferenceId",
      "StreamPropertyId": "streamPropertyId",
      "ValueStatusMappings": [
        {
          "Value": "value",
          "Status": 1,
          "DisplayName": "displayName"
        }
      ]
    }
  }
}

```

---

### Asset

<a id="schemaasset"></a>
<a id="schema_Asset"></a>
<a id="tocSasset"></a>
<a id="tocsasset"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|None|
|AssetTypeId|string|false|true|None|
|Name|string|false|true|None|
|Description|string|false|true|None|
|Metadata|[[MetadataItem](#schemametadataitem)]|false|true|None|
|StreamReferences|[[StreamReference](#schemastreamreference)]|false|true|None|
|Status|[StatusConfiguration](#schemastatusconfiguration)|false|true|None|
|Tags|string[]|false|true|None|

```json
{
  "Id": "string",
  "AssetTypeId": "string",
  "Name": "string",
  "Description": "string",
  "Metadata": [
    {
      "Id": "string",
      "Name": "string",
      "Description": "string",
      "SdsTypeCode": 0,
      "Value": null,
      "Uom": "string"
    }
  ],
  "StreamReferences": [
    {
      "Id": "string",
      "Name": "string",
      "Description": "string",
      "StreamId": "string"
    }
  ],
  "Status": {
    "DefinitionType": 0,
    "Definition": null
  },
  "Tags": [
    "string"
  ]
}

```

---

### MetadataItem

<a id="schemametadataitem"></a>
<a id="schema_MetadataItem"></a>
<a id="tocSmetadataitem"></a>
<a id="tocsmetadataitem"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|None|
|Name|string|false|true|None|
|Description|string|false|true|None|
|SdsTypeCode|[SdsTypeCode](#schemasdstypecode)|false|false|None|
|Value|any|false|true|None|
|Uom|string|false|true|None|

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "SdsTypeCode": 0,
  "Value": null,
  "Uom": "string"
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

### StreamReference

<a id="schemastreamreference"></a>
<a id="schema_StreamReference"></a>
<a id="tocSstreamreference"></a>
<a id="tocsstreamreference"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|None|
|Name|string|false|true|None|
|Description|string|false|true|None|
|StreamId|string|false|true|None|

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "StreamId": "string"
}

```

---

### StatusConfiguration

<a id="schemastatusconfiguration"></a>
<a id="schema_StatusConfiguration"></a>
<a id="tocSstatusconfiguration"></a>
<a id="tocsstatusconfiguration"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|DefinitionType|[StatusDefinitionType](#schemastatusdefinitiontype)|false|false|None|
|Definition|any|false|true|None|

```json
{
  "DefinitionType": 0,
  "Definition": null
}

```

---

### StatusDefinitionType

<a id="schemastatusdefinitiontype"></a>
<a id="schema_StatusDefinitionType"></a>
<a id="tocSstatusdefinitiontype"></a>
<a id="tocsstatusdefinitiontype"></a>

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|Unspecified|0|
|StreamPropertyMapping|1|

---

