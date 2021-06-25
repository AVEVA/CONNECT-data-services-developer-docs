---
uid: assets-resolved-asset

---

# Resolved Asset

## `Get Resolved Asset`

<a id="opIdResolvedAsset_Get Resolved Asset"></a>

Returns the specified asset and the version Etag in the HTTP response header.

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/Resolved
```

#### Parameters

`string assetId`
<br/>Asset identifier<br/><br/>`string tenantId`
<br/>Tenant identifier<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier<br/><br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[ResolvedAsset](#schemaresolvedasset)|The resolved asset with the specified asset identifier.|
|400|[ErrorTemplate](#schemaerrortemplate)|The request is not valid. See the response body for additional details.|
|401|[ErrorTemplate](#schemaerrortemplate)|Unauthorized|
|404|[ErrorTemplate](#schemaerrortemplate)|Asset with specified identifier not found.|
|500|None|Internal Service Error, please try again later.|
|503|None|Service Unavailable, please try again later.|

#### Example response body
> 200 Response

```json
{
  "Id": "string",
  "Name": "string",
  "Resolved": true,
  "Description": "string",
  "AssetTypeId": "string",
  "AssetTypeName": "string",
  "ShapeId": "string",
  "ShapeName": "string",
  "Metadata": [
    {
      "Name": "string",
      "SdsTypeCode": 0,
      "Value": null,
      "Uom": "string"
    }
  ],
  "Streams": [
    {
      "Name": "string",
      "Type": {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "SdsTypeCode": "[",
        "IsGenericType": true,
        "IsReferenceType": true,
        "GenericArguments": [
          null
        ],
        "Properties": [
          null
        ],
        "BaseType": null,
        "DerivedTypes": [
          null
        ],
        "InterpolationMode": "[",
        "ExtrapolationMode": "["
      },
      "StreamReferenceName": "string",
      "StreamId": "string",
      "PropertyMaps": [
        {
          "Id": "string",
          "SourcePropertyId": "string"
        }
      ]
    }
  ],
  "UnresolvedStreams": [
    {
      "Name": "string",
      "Reason": "string"
    }
  ],
  "UnresolvedMetadata": [
    {
      "Name": "string",
      "Reason": "string"
    }
  ],
  "StatusDefinitionType": 0,
  "Status": null,
  "UnresolvedStatus": {
    "Reason": "string"
  }
}
```

---
## Definitions

### ResolvedAsset

<a id="schemaresolvedasset"></a>
<a id="schema_ResolvedAsset"></a>
<a id="tocSresolvedasset"></a>
<a id="tocsresolvedasset"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|None|
|Name|string|false|true|None|
|Resolved|boolean|false|false|None|
|Description|string|false|true|None|
|AssetTypeId|string|false|true|None|
|AssetTypeName|string|false|true|None|
|ShapeId|string|false|true|None|
|ShapeName|string|false|true|None|
|Metadata|[[ResolvedMetadataItem](#schemaresolvedmetadataitem)]|false|true|None|
|Streams|[[ResolvedStream](#schemaresolvedstream)]|false|true|None|
|UnresolvedStreams|[[UnresolvedStream](#schemaunresolvedstream)]|false|true|None|
|UnresolvedMetadata|[[UnresolvedMetadata](#schemaunresolvedmetadata)]|false|true|None|
|StatusDefinitionType|[StatusDefinitionType](#schemastatusdefinitiontype)|false|false|None|
|Status|any|false|true|None|
|UnresolvedStatus|[UnresolvedStatus](#schemaunresolvedstatus)|false|true|None|

```json
{
  "Id": "string",
  "Name": "string",
  "Resolved": true,
  "Description": "string",
  "AssetTypeId": "string",
  "AssetTypeName": "string",
  "ShapeId": "string",
  "ShapeName": "string",
  "Metadata": [
    {
      "Name": "string",
      "SdsTypeCode": 0,
      "Value": null,
      "Uom": "string"
    }
  ],
  "Streams": [
    {
      "Name": "string",
      "Type": {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "SdsTypeCode": "[",
        "IsGenericType": true,
        "IsReferenceType": true,
        "GenericArguments": [
          null
        ],
        "Properties": [
          null
        ],
        "BaseType": null,
        "DerivedTypes": [
          null
        ],
        "InterpolationMode": "[",
        "ExtrapolationMode": "["
      },
      "StreamReferenceName": "string",
      "StreamId": "string",
      "PropertyMaps": [
        {
          "Id": "string",
          "SourcePropertyId": "string"
        }
      ]
    }
  ],
  "UnresolvedStreams": [
    {
      "Name": "string",
      "Reason": "string"
    }
  ],
  "UnresolvedMetadata": [
    {
      "Name": "string",
      "Reason": "string"
    }
  ],
  "StatusDefinitionType": 0,
  "Status": null,
  "UnresolvedStatus": {
    "Reason": "string"
  }
}

```

---

### ResolvedMetadataItem

<a id="schemaresolvedmetadataitem"></a>
<a id="schema_ResolvedMetadataItem"></a>
<a id="tocSresolvedmetadataitem"></a>
<a id="tocsresolvedmetadataitem"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|None|
|SdsTypeCode|[SdsTypeCode](#schemasdstypecode)|false|false|None|
|Value|any|false|true|None|
|Uom|string|false|true|None|

```json
{
  "Name": "string",
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

#### Enumerated Values

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

### ResolvedStream

<a id="schemaresolvedstream"></a>
<a id="schema_ResolvedStream"></a>
<a id="tocSresolvedstream"></a>
<a id="tocsresolvedstream"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|None|
|Type|[SdsType](#schemasdstype)|false|true|None|
|StreamReferenceName|string|false|true|None|
|StreamId|string|false|true|None|
|PropertyMaps|[[PropertyMap](#schemapropertymap)]|false|true|None|

```json
{
  "Name": "string",
  "Type": {
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "SdsTypeCode": 0,
    "IsGenericType": true,
    "IsReferenceType": true,
    "GenericArguments": [
      {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "SdsTypeCode": "[",
        "IsGenericType": true,
        "IsReferenceType": true,
        "GenericArguments": [
          null
        ],
        "Properties": [
          null
        ],
        "BaseType": null,
        "DerivedTypes": [
          null
        ],
        "InterpolationMode": "[",
        "ExtrapolationMode": "["
      }
    ],
    "Properties": [
      {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "Order": 0,
        "IsKey": true,
        "FixedSize": 0,
        "SdsType": null,
        "Value": null,
        "Uom": "string",
        "InterpolationMode": null
      }
    ],
    "BaseType": {
      "Id": null,
      "Name": null,
      "Description": null,
      "SdsTypeCode": null,
      "IsGenericType": null,
      "IsReferenceType": null,
      "GenericArguments": null,
      "Properties": null,
      "BaseType": null,
      "DerivedTypes": null,
      "InterpolationMode": null,
      "ExtrapolationMode": null
    },
    "DerivedTypes": [
      {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "SdsTypeCode": "[",
        "IsGenericType": true,
        "IsReferenceType": true,
        "GenericArguments": [
          null
        ],
        "Properties": [
          null
        ],
        "BaseType": null,
        "DerivedTypes": [
          null
        ],
        "InterpolationMode": "[",
        "ExtrapolationMode": "["
      }
    ],
    "InterpolationMode": 0,
    "ExtrapolationMode": 0
  },
  "StreamReferenceName": "string",
  "StreamId": "string",
  "PropertyMaps": [
    {
      "Id": "string",
      "SourcePropertyId": "string"
    }
  ]
}

```

---

### SdsType

<a id="schemasdstype"></a>
<a id="schema_SdsType"></a>
<a id="tocSsdstype"></a>
<a id="tocssdstype"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|None|
|Name|string|false|true|None|
|Description|string|false|true|None|
|SdsTypeCode|[SdsTypeCode](#schemasdstypecode)|false|false|None|
|IsGenericType|boolean|false|false|None|
|IsReferenceType|boolean|false|false|None|
|GenericArguments|[[SdsType](#schemasdstype)]|false|true|None|
|Properties|[[SdsTypeProperty](#schemasdstypeproperty)]|false|true|None|
|BaseType|[SdsType](#schemasdstype)|false|true|None|
|DerivedTypes|[[SdsType](#schemasdstype)]|false|true|None|
|InterpolationMode|[SdsInterpolationMode](#schemasdsinterpolationmode)|false|false|None|
|ExtrapolationMode|[SdsExtrapolationMode](#schemasdsextrapolationmode)|false|false|None|

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "SdsTypeCode": 0,
  "IsGenericType": true,
  "IsReferenceType": true,
  "GenericArguments": [
    {
      "Id": "string",
      "Name": "string",
      "Description": "string",
      "SdsTypeCode": 0,
      "IsGenericType": true,
      "IsReferenceType": true,
      "GenericArguments": [
        {
          "Id": "string",
          "Name": "string",
          "Description": "string",
          "SdsTypeCode": 0,
          "IsGenericType": true,
          "IsReferenceType": true,
          "GenericArguments": [
            {}
          ],
          "Properties": [
            {}
          ],
          "BaseType": null,
          "DerivedTypes": [
            {}
          ],
          "InterpolationMode": 0,
          "ExtrapolationMode": 0
        }
      ],
      "Properties": [
        {
          "Id": "string",
          "Name": "string",
          "Description": "string",
          "Order": 0,
          "IsKey": true,
          "FixedSize": 0,
          "SdsType": null,
          "Value": null,
          "Uom": "string",
          "InterpolationMode": null
        }
      ],
      "BaseType": {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "SdsTypeCode": "[",
        "IsGenericType": true,
        "IsReferenceType": true,
        "GenericArguments": [
          null
        ],
        "Properties": [
          null
        ],
        "BaseType": null,
        "DerivedTypes": [
          null
        ],
        "InterpolationMode": "[",
        "ExtrapolationMode": "["
      },
      "DerivedTypes": [
        {
          "Id": "string",
          "Name": "string",
          "Description": "string",
          "SdsTypeCode": 0,
          "IsGenericType": true,
          "IsReferenceType": true,
          "GenericArguments": [
            {}
          ],
          "Properties": [
            {}
          ],
          "BaseType": null,
          "DerivedTypes": [
            {}
          ],
          "InterpolationMode": 0,
          "ExtrapolationMode": 0
        }
      ],
      "InterpolationMode": 0,
      "ExtrapolationMode": 0
    }
  ],
  "Properties": [
    {
      "Id": "string",
      "Name": "string",
      "Description": "string",
      "Order": 0,
      "IsKey": true,
      "FixedSize": 0,
      "SdsType": {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "SdsTypeCode": "[",
        "IsGenericType": true,
        "IsReferenceType": true,
        "GenericArguments": [
          null
        ],
        "Properties": [
          null
        ],
        "BaseType": null,
        "DerivedTypes": [
          null
        ],
        "InterpolationMode": "[",
        "ExtrapolationMode": "["
      },
      "Value": null,
      "Uom": "string",
      "InterpolationMode": 0
    }
  ],
  "BaseType": {
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "SdsTypeCode": 0,
    "IsGenericType": true,
    "IsReferenceType": true,
    "GenericArguments": [
      {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "SdsTypeCode": "[",
        "IsGenericType": true,
        "IsReferenceType": true,
        "GenericArguments": [
          null
        ],
        "Properties": [
          null
        ],
        "BaseType": null,
        "DerivedTypes": [
          null
        ],
        "InterpolationMode": "[",
        "ExtrapolationMode": "["
      }
    ],
    "Properties": [
      {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "Order": 0,
        "IsKey": true,
        "FixedSize": 0,
        "SdsType": null,
        "Value": null,
        "Uom": "string",
        "InterpolationMode": null
      }
    ],
    "BaseType": {
      "Id": null,
      "Name": null,
      "Description": null,
      "SdsTypeCode": null,
      "IsGenericType": null,
      "IsReferenceType": null,
      "GenericArguments": null,
      "Properties": null,
      "BaseType": null,
      "DerivedTypes": null,
      "InterpolationMode": null,
      "ExtrapolationMode": null
    },
    "DerivedTypes": [
      {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "SdsTypeCode": "[",
        "IsGenericType": true,
        "IsReferenceType": true,
        "GenericArguments": [
          null
        ],
        "Properties": [
          null
        ],
        "BaseType": null,
        "DerivedTypes": [
          null
        ],
        "InterpolationMode": "[",
        "ExtrapolationMode": "["
      }
    ],
    "InterpolationMode": 0,
    "ExtrapolationMode": 0
  },
  "DerivedTypes": [
    {
      "Id": "string",
      "Name": "string",
      "Description": "string",
      "SdsTypeCode": 0,
      "IsGenericType": true,
      "IsReferenceType": true,
      "GenericArguments": [
        {
          "Id": "string",
          "Name": "string",
          "Description": "string",
          "SdsTypeCode": 0,
          "IsGenericType": true,
          "IsReferenceType": true,
          "GenericArguments": [
            {}
          ],
          "Properties": [
            {}
          ],
          "BaseType": null,
          "DerivedTypes": [
            {}
          ],
          "InterpolationMode": 0,
          "ExtrapolationMode": 0
        }
      ],
      "Properties": [
        {
          "Id": "string",
          "Name": "string",
          "Description": "string",
          "Order": 0,
          "IsKey": true,
          "FixedSize": 0,
          "SdsType": null,
          "Value": null,
          "Uom": "string",
          "InterpolationMode": null
        }
      ],
      "BaseType": {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "SdsTypeCode": "[",
        "IsGenericType": true,
        "IsReferenceType": true,
        "GenericArguments": [
          null
        ],
        "Properties": [
          null
        ],
        "BaseType": null,
        "DerivedTypes": [
          null
        ],
        "InterpolationMode": "[",
        "ExtrapolationMode": "["
      },
      "DerivedTypes": [
        {
          "Id": "string",
          "Name": "string",
          "Description": "string",
          "SdsTypeCode": 0,
          "IsGenericType": true,
          "IsReferenceType": true,
          "GenericArguments": [
            {}
          ],
          "Properties": [
            {}
          ],
          "BaseType": null,
          "DerivedTypes": [
            {}
          ],
          "InterpolationMode": 0,
          "ExtrapolationMode": 0
        }
      ],
      "InterpolationMode": 0,
      "ExtrapolationMode": 0
    }
  ],
  "InterpolationMode": 0,
  "ExtrapolationMode": 0
}

```

---

### SdsTypeProperty

<a id="schemasdstypeproperty"></a>
<a id="schema_SdsTypeProperty"></a>
<a id="tocSsdstypeproperty"></a>
<a id="tocssdstypeproperty"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|None|
|Name|string|false|true|None|
|Description|string|false|true|None|
|Order|int32|false|false|None|
|IsKey|boolean|false|false|None|
|FixedSize|int32|false|false|None|
|SdsType|[SdsType](#schemasdstype)|false|true|None|
|Value|any|false|true|None|
|Uom|string|false|true|None|
|InterpolationMode|[SdsInterpolationMode](#schemasdsinterpolationmode)|false|true|None|

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "Order": 0,
  "IsKey": true,
  "FixedSize": 0,
  "SdsType": {
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "SdsTypeCode": 0,
    "IsGenericType": true,
    "IsReferenceType": true,
    "GenericArguments": [
      {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "SdsTypeCode": "[",
        "IsGenericType": true,
        "IsReferenceType": true,
        "GenericArguments": [
          null
        ],
        "Properties": [
          null
        ],
        "BaseType": null,
        "DerivedTypes": [
          null
        ],
        "InterpolationMode": "[",
        "ExtrapolationMode": "["
      }
    ],
    "Properties": [
      {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "Order": 0,
        "IsKey": true,
        "FixedSize": 0,
        "SdsType": null,
        "Value": null,
        "Uom": "string",
        "InterpolationMode": null
      }
    ],
    "BaseType": {
      "Id": null,
      "Name": null,
      "Description": null,
      "SdsTypeCode": null,
      "IsGenericType": null,
      "IsReferenceType": null,
      "GenericArguments": null,
      "Properties": null,
      "BaseType": null,
      "DerivedTypes": null,
      "InterpolationMode": null,
      "ExtrapolationMode": null
    },
    "DerivedTypes": [
      {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "SdsTypeCode": "[",
        "IsGenericType": true,
        "IsReferenceType": true,
        "GenericArguments": [
          null
        ],
        "Properties": [
          null
        ],
        "BaseType": null,
        "DerivedTypes": [
          null
        ],
        "InterpolationMode": "[",
        "ExtrapolationMode": "["
      }
    ],
    "InterpolationMode": 0,
    "ExtrapolationMode": 0
  },
  "Value": null,
  "Uom": "string",
  "InterpolationMode": 0
}

```

---

### SdsInterpolationMode

<a id="schemasdsinterpolationmode"></a>
<a id="schema_SdsInterpolationMode"></a>
<a id="tocSsdsinterpolationmode"></a>
<a id="tocssdsinterpolationmode"></a>

#### Enumerated Values

|Property|Value|
|---|---|
|Default|0|
|Continuous|0|
|StepwiseContinuousLeading|1|
|StepwiseContinuousTrailing|2|
|Discrete|3|
|ContinuousNullableLeading|4|
|ContinuousNullableTrailing|5|

---

### SdsExtrapolationMode

<a id="schemasdsextrapolationmode"></a>
<a id="schema_SdsExtrapolationMode"></a>
<a id="tocSsdsextrapolationmode"></a>
<a id="tocssdsextrapolationmode"></a>

#### Enumerated Values

|Property|Value|
|---|---|
|All|0|
|None|1|
|Forward|2|
|Backward|3|

---

### PropertyMap

<a id="schemapropertymap"></a>
<a id="schema_PropertyMap"></a>
<a id="tocSpropertymap"></a>
<a id="tocspropertymap"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|None|
|SourcePropertyId|string|false|true|None|

```json
{
  "Id": "string",
  "SourcePropertyId": "string"
}

```

---

### UnresolvedStream

<a id="schemaunresolvedstream"></a>
<a id="schema_UnresolvedStream"></a>
<a id="tocSunresolvedstream"></a>
<a id="tocsunresolvedstream"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|None|
|Reason|string|false|true|None|

```json
{
  "Name": "string",
  "Reason": "string"
}

```

---

### UnresolvedMetadata

<a id="schemaunresolvedmetadata"></a>
<a id="schema_UnresolvedMetadata"></a>
<a id="tocSunresolvedmetadata"></a>
<a id="tocsunresolvedmetadata"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|None|
|Reason|string|false|true|None|

```json
{
  "Name": "string",
  "Reason": "string"
}

```

---

### StatusDefinitionType

<a id="schemastatusdefinitiontype"></a>
<a id="schema_StatusDefinitionType"></a>
<a id="tocSstatusdefinitiontype"></a>
<a id="tocsstatusdefinitiontype"></a>

#### Enumerated Values

|Property|Value|
|---|---|
|Unspecified|0|
|StreamPropertyMapping|1|

---

### UnresolvedStatus

<a id="schemaunresolvedstatus"></a>
<a id="schema_UnresolvedStatus"></a>
<a id="tocSunresolvedstatus"></a>
<a id="tocsunresolvedstatus"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Reason|string|false|true|None|

```json
{
  "Reason": "string"
}

```

---

### ErrorTemplate

<a id="schemaerrortemplate"></a>
<a id="schema_ErrorTemplate"></a>
<a id="tocSerrortemplate"></a>
<a id="tocserrortemplate"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|false|true|Operation identifier|
|Error|string|false|true|Error string|
|Resolution|string|false|true|Resolution string|
|Reason|string|false|true|Error reason string|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Resolution": "string",
  "Reason": "string",
  "property1": null,
  "property2": null
}

```

---

