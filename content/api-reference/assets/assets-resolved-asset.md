---
uid: assets-resolved-asset

---

# Resolved Asset
The resolved asset describes the consumption-oriented aspects of an OCS resource rather than describing how the resource is configured. The resolved asset corresponds to its metadata and referenced stream which define how the data is interpreted (that is, SdsTypeCode, InterpolationMode, and UOM).

## `Get Resolved Asset`

<a id="opIdResolvedAsset_Get Resolved Asset"></a>

Returns resolved view of specified asset.

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/Resolved
```

#### Parameters

`string assetId`
<br/>Asset identifier<br/><br/>`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[ResolvedAsset](#schemaresolvedasset)|Resolved asset with specified identifier|
|201|[Asset](#schemaasset)|Resolved asset with specified identifier|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See the response body for additional details.|
|403|None|Forbidden|
|404|[ErrorTemplate](#schemaerrortemplate)|Not found|

#### Example response body
> 200 Response

```json
{
  "Id": "Heater-8911ee90-467b-4a3f-bc7b-3b3512c23dfc",
  "Name": "Heater Asset",
  "Resolved": true,
  "Description": "Heater Asset on the first floor.",
  "AssetTypeId": "Heater_AssetType-6f53c911-f5de-4b7f-981f-d6f0ec139d9f",
  "AssetTypeName": "Heater_AssetType",
  "Metadata": [
    {
      "Id": "fbd82b97-d29e-4022-968e-f8492cf86644",
      "Name": "ModelNumber",
      "Description": "This is a static attribute on the asset which represents the model number.",
      "SdsTypeCode": "Double",
      "Value": 0.01
    }
  ],
  "Streams": [
    {
      "Name": "ResolvedReferenceName1",
      "Type": {
        "Id": "SdsType-ffdf2227-50e8-4196-b828-f1bd2b3689c8",
        "SdsTypeCode": "Object",
        "Properties": [
          {
            "Id": "Timestamp",
            "IsKey": true,
            "SdsType": {
              "Id": "0573b425-368a-369b-95d9-71c863df45a5",
              "SdsTypeCode": "DateTime"
            },
            "InterpolationMode": "Continuous"
          },
          {
            "Id": "Pressure",
            "SdsType": {
              "Id": "9144b7d6-3d5f-3b29-8131-ff0db551e17c",
              "SdsTypeCode": "Double"
            },
            "Uom": "bar",
            "InterpolationMode": "Continuous"
          }
        ]
      },
      "StreamReferenceName": "ResolvedReferenceName1",
      "StreamId": "Stream-b3c7a344-ce8a-4578-b4cd-1a6d78ca0610",
      "PropertyMaps": [
        {
          "Id": "Timestamp",
          "SourcePropertyId": "Timestamp"
        },
        {
          "Id": "Pressure",
          "SourcePropertyId": "Pressure"
        }
      ]
    }
  ],
  "UnresolvedStreams": [],
  "UnresolvedMetadata": [],
  "StatusDefinitionType": "StreamPropertyMapping",
  "Status": {
    "StreamId": "SdsStream_id_1",
    "SourcePropertyId": "Count"
  }
}
```

> 201 Response

```json
{
  "Id": "SampleAssetA",
  "Description": "This is a sample asset a.",
  "Metadata": [
    {
      "Id": "fbd82b97-d29e-4022-968e-f8492cf86644",
      "Name": "ModelNumber",
      "Description": "This is a static attribute on the asset which represents the model number.",
      "SdsTypeCode": "Double",
      "Value": 0.01
    }
  ],
  "StreamReferences": [
    {
      "Id": "f1bf9da2-3858-4bcd-bf93-e7c26ab0d28e",
      "Name": "Data",
      "Description": "This is reference to a stream. The stream id is PI_bifrostbigdaddy_1.",
      "StreamId": "PI_bifrostbigdaddy_1"
    }
  ]
}
```

> 400 Response ([ErrorTemplate](#schemaerrortemplate))

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
## Definitions

### ResolvedAsset

<a id="schemaresolvedasset"></a>
<a id="schema_ResolvedAsset"></a>
<a id="tocSresolvedasset"></a>
<a id="tocsresolvedasset"></a>

The resolved asset describes the consumption-oriented aspects of an OCS resource rather than describing how the resource is configured. The resolved asset corresponds to its metadata and referenced stream which define how the data is interpreted(that is, SdsTypeCode, InterpolationMode, and UOM).

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Asset identifier|
|Name|string|false|true|Asset name|
|Resolved|boolean|false|false|True if no shape is applied|
|Description|string|false|true|Asset description|
|AssetTypeId|string|false|true|Asset asset type id if applicable|
|AssetTypeName|string|false|true|Asset asset type name if applicable|
|ShapeId|string|false|true|Shape identifier for future enhancement|
|ShapeName|string|false|true|Shape name for future enhancement|
|Metadata|[[ResolvedMetadataItem](#schemaresolvedmetadataitem)]|false|true|Resolved asset metadata|
|Streams|[[ResolvedStream](#schemaresolvedstream)]|false|true|Resolved asset stream references|
|UnresolvedStreams|[[UnresolvedStream](#schemaunresolvedstream)]|false|true|Resolved asset unresolved streams|
|UnresolvedMetadata|[[UnresolvedMetadata](#schemaunresolvedmetadata)]|false|true|Resolved asset unresolved metadata|
|StatusDefinitionType|[StatusDefinitionType](#schemastatusdefinitiontype)|false|false|Resolved asset status definition|
|Status|any|false|true|Resolved asset status|
|UnresolvedStatus|[UnresolvedStatus](#schemaunresolvedstatus)|false|true|Resolved asset unresolved status|

```json
{
  "Id": "Heater-8911ee90-467b-4a3f-bc7b-3b3512c23dfc",
  "Name": "Heater Asset",
  "Resolved": true,
  "Description": "Heater Asset on the first floor.",
  "AssetTypeId": "Heater_AssetType-6f53c911-f5de-4b7f-981f-d6f0ec139d9f",
  "AssetTypeName": "Heater_AssetType",
  "Metadata": [
    {
      "Id": "fbd82b97-d29e-4022-968e-f8492cf86644",
      "Name": "ModelNumber",
      "Description": "This is a static attribute on the asset which represents the model number.",
      "SdsTypeCode": "Double",
      "Value": 0.01
    }
  ],
  "Streams": [
    {
      "Name": "ResolvedReferenceName1",
      "Type": {
        "Id": "SdsType-ffdf2227-50e8-4196-b828-f1bd2b3689c8",
        "SdsTypeCode": "Object",
        "Properties": [
          {
            "Id": "Timestamp",
            "IsKey": true,
            "SdsType": {
              "Id": "0573b425-368a-369b-95d9-71c863df45a5",
              "SdsTypeCode": "DateTime"
            },
            "InterpolationMode": "Continuous"
          },
          {
            "Id": "Pressure",
            "SdsType": {
              "Id": "9144b7d6-3d5f-3b29-8131-ff0db551e17c",
              "SdsTypeCode": "Double"
            },
            "Uom": "bar",
            "InterpolationMode": "Continuous"
          }
        ]
      },
      "StreamReferenceName": "ResolvedReferenceName1",
      "StreamId": "Stream-b3c7a344-ce8a-4578-b4cd-1a6d78ca0610",
      "PropertyMaps": [
        {
          "Id": "Timestamp",
          "SourcePropertyId": "Timestamp"
        },
        {
          "Id": "Pressure",
          "SourcePropertyId": "Pressure"
        }
      ]
    }
  ],
  "UnresolvedStreams": [],
  "UnresolvedMetadata": [],
  "StatusDefinitionType": "StreamPropertyMapping",
  "Status": {
    "StreamId": "SdsStream_id_1",
    "SourcePropertyId": "Count"
  }
}

```

---

### ResolvedMetadataItem

<a id="schemaresolvedmetadataitem"></a>
<a id="schema_ResolvedMetadataItem"></a>
<a id="tocSresolvedmetadataitem"></a>
<a id="tocsresolvedmetadataitem"></a>

Resolved metadata is a property of a resolved asset.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|Metadata name|
|SdsTypeCode|[SdsTypeCode](#schemasdstypecode)|false|false|Metadata data type represented as an SdsTypeCode|
|Value|any|false|true|Metadata static value|
|Uom|string|false|true|Metadata UOM|

```json
{
  "Name": "ModelNumber",
  "Description": "This is a static attribute on the asset which represents the model number.",
  "SdsTypeCode": "Double",
  "Value": 0.01
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

Resolved stream is a property of the resolved asset.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|Resolved stream name|
|Type|[SdsType](#schemasdstype)|false|true|SdsType of the referenced stream|
|StreamReferenceName|string|false|true|Stream reference name from the asset|
|StreamId|string|false|true|Sds stream id of the referenced stream|
|PropertyMaps|[[PropertyMap](#schemapropertymap)]|false|true|Sds stream property maps|

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

Property map

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Property map identifier|
|SourcePropertyId|string|false|true|Source identifier|

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

Unresolved stream is a property of the resolved asset. It represents streams which could not be resolved. Check reason as to why.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|Name of the stream reference that could not be resolved.|
|Reason|string|false|true|Reason why stream could not be resolved.|

```json
{
  "Name": "Name of stream which could not be resolved",
  "Reason": "Reason why stream could not be resolved."
}

```

---

### UnresolvedMetadata

<a id="schemaunresolvedmetadata"></a>
<a id="schema_UnresolvedMetadata"></a>
<a id="tocSunresolvedmetadata"></a>
<a id="tocsunresolvedmetadata"></a>

Unresolved metadata is a property of the resolved asset. It represents metadata which could not be resolved. Check reason as to why.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|Name of metadata item which could not be resolved.|
|Reason|string|false|true|Reason why metadata could not be resolved.|

```json
{
  "Name": "Name of metadata which could not be resolved",
  "Reason": "Reason why metadata could not be resolved."
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

Unresolved status is a property of the resolved asset. It represents statuses which could not be resolved. Check reason as to why.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Reason|string|false|true|Reason why the status could not be resolved.|

```json
{
  "Reason": "Reason why status could not be resolved."
}

```

---

### Asset

<a id="schemaasset"></a>
<a id="schema_Asset"></a>
<a id="tocSasset"></a>
<a id="tocsasset"></a>

Represents an asset object.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Asset identifier. If you do not provide an Id, OCS copies the name as the identifierId. If you do not provide a name, OCS assigns a random GUID for the Id.|
|AssetTypeId|string|false|true|Asset type identifier. Id for the asset type that this asset is derived from. To get the merged view of the asset, get the resolved asset through the /Assets/{assetId}/Resolved route.|
|Name|string|false|true|User-friendly asset name. Required if Id is not provided. If Name is used as the Id, it must be unique within a given namespace.|
|Description|string|false|true|Asset description|
|Metadata|[[MetadataItem](#schemametadataitem)]|false|true|Asset metadata|
|StreamReferences|[[StreamReference](#schemastreamreference)]|false|true|Asset stream reference|
|Status|[StatusConfiguration](#schemastatusconfiguration)|false|true|Asset status|

```json
{
  "Id": "SampleAssetA",
  "Description": "This is a sample asset a.",
  "Metadata": [
    {
      "Id": "fbd82b97-d29e-4022-968e-f8492cf86644",
      "Name": "ModelNumber",
      "Description": "This is a static attribute on the asset which represents the model number.",
      "SdsTypeCode": "Double",
      "Value": 0.01
    }
  ],
  "StreamReferences": [
    {
      "Id": "f1bf9da2-3858-4bcd-bf93-e7c26ab0d28e",
      "Name": "Data",
      "Description": "This is reference to a stream. The stream id is PI_bifrostbigdaddy_1.",
      "StreamId": "PI_bifrostbigdaddy_1"
    }
  ]
}

```

---

### MetadataItem

<a id="schemametadataitem"></a>
<a id="schema_MetadataItem"></a>
<a id="tocSmetadataitem"></a>
<a id="tocsmetadataitem"></a>

An asset or asset type metadata is static information associated with a given asset. A given metadata contains a list of individual metadata values. There is no limit on the number of metadata values defined by an asset. An asset or asset type metadata does not stand alone. It must be specified within an asset or asset type object and, therefore, there are no direct API routes to asset or asset type metadata.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Metadata identifier|
|Name|string|false|true|User-friendly name for the metadata value. If not null, must be unique within an asset or asset type.|
|Description|string|false|true|Metadata item description.|
|SdsTypeCode|[SdsTypeCode2](#schemasdstypecode2)|false|false|This integer corresponds to the SdsTypeCode. Asset metadata support the following integer or string values: 11 ("Int64"), 14 ("Double"), 16 ("DateTime"), and 18 ("String").|
|Value|any|false|true|String representation of the metadata value.|
|Uom|string|false|true|Asset metadata unit of measurement. Select from the list of supported Uom types.|

```json
{
  "Id": "Sample Metadata Id",
  "Name": "Asset Model number",
  "Description": "This metadata represents an model number attribute on the asset.",
  "SdsTypeCode": "Double",
  "Value": "RFA-123",
  "Uom": null
}

```

---

### SdsTypeCode2

<a id="schemasdstypecode2"></a>
<a id="schema_SdsTypeCode2"></a>
<a id="tocSsdstypecode2"></a>
<a id="tocssdstypecode2"></a>

#### Enumerated Values

|Property|Value|
|---|---|
|Empty|Empty|
|Object|Object|
|Boolean|Boolean|
|Char|Char|
|SByte|SByte|
|Byte|Byte|
|Int16|Int16|
|UInt16|UInt16|
|Int32|Int32|
|UInt32|UInt32|
|Int64|Int64|
|UInt64|UInt64|
|Single|Single|
|Double|Double|
|Decimal|Decimal|
|DateTime|DateTime|
|String|String|
|Guid|Guid|
|DateTimeOffset|DateTimeOffset|
|TimeSpan|TimeSpan|
|Version|Version|
|NullableBoolean|NullableBoolean|
|NullableChar|NullableChar|
|NullableSByte|NullableSByte|
|NullableByte|NullableByte|
|NullableInt16|NullableInt16|
|NullableUInt16|NullableUInt16|
|NullableInt32|NullableInt32|
|NullableUInt32|NullableUInt32|
|NullableInt64|NullableInt64|
|NullableUInt64|NullableUInt64|
|NullableSingle|NullableSingle|
|NullableDouble|NullableDouble|
|NullableDecimal|NullableDecimal|
|NullableDateTime|NullableDateTime|
|NullableGuid|NullableGuid|
|NullableDateTimeOffset|NullableDateTimeOffset|
|NullableTimeSpan|NullableTimeSpan|
|BooleanArray|BooleanArray|
|CharArray|CharArray|
|SByteArray|SByteArray|
|ByteArray|ByteArray|
|Int16Array|Int16Array|
|UInt16Array|UInt16Array|
|Int32Array|Int32Array|
|UInt32Array|UInt32Array|
|Int64Array|Int64Array|
|UInt64Array|UInt64Array|
|SingleArray|SingleArray|
|DoubleArray|DoubleArray|
|DecimalArray|DecimalArray|
|DateTimeArray|DateTimeArray|
|StringArray|StringArray|
|GuidArray|GuidArray|
|DateTimeOffsetArray|DateTimeOffsetArray|
|TimeSpanArray|TimeSpanArray|
|VersionArray|VersionArray|
|Array|Array|
|IList|IList|
|IDictionary|IDictionary|
|IEnumerable|IEnumerable|
|SdsType|SdsType|
|SdsTypeProperty|SdsTypeProperty|
|SdsStreamView|SdsStreamView|
|SdsStreamViewProperty|SdsStreamViewProperty|
|SdsStreamViewMap|SdsStreamViewMap|
|SdsStreamViewMapProperty|SdsStreamViewMapProperty|
|SdsStream|SdsStream|
|SdsStreamIndex|SdsStreamIndex|
|SdsTable|SdsTable|
|SdsColumn|SdsColumn|
|SdsValues|SdsValues|
|SdsObject|SdsObject|
|SByteEnum|SByteEnum|
|ByteEnum|ByteEnum|
|Int16Enum|Int16Enum|
|UInt16Enum|UInt16Enum|
|Int32Enum|Int32Enum|
|UInt32Enum|UInt32Enum|
|Int64Enum|Int64Enum|
|UInt64Enum|UInt64Enum|
|NullableSByteEnum|NullableSByteEnum|
|NullableByteEnum|NullableByteEnum|
|NullableInt16Enum|NullableInt16Enum|
|NullableUInt16Enum|NullableUInt16Enum|
|NullableInt32Enum|NullableInt32Enum|
|NullableUInt32Enum|NullableUInt32Enum|
|NullableInt64Enum|NullableInt64Enum|
|NullableUInt64Enum|NullableUInt64Enum|

---

### StreamReference

<a id="schemastreamreference"></a>
<a id="schema_StreamReference"></a>
<a id="tocSstreamreference"></a>
<a id="tocsstreamreference"></a>

An asset stream reference represents dynamic stream data associated with an asset. The references must either be an SDS stream or an SDS stream view. Asset-centric data routes provide direct access to dynamic data for a given asset. There are no limitations on the number of references an asset may contain. However, an asset cannot contain multiple references to the same SDS stream. An asset stream reference does not stand alone. It must be specified within an asset object and, therefore, asset references do not have direct API routes.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Stream Reference Id|
|Name|string|false|true|Stream Reference Name|
|Description|string|false|true|Description of this stream reference|
|StreamId|string|true|false|Sds stream id that's being referenced.|

```json
{
  "Id": "f1bf9da2-3858-4bcd-bf93-e7c26ab0d28e",
  "Name": "Data",
  "Description": "This is reference to a stream. The stream id is PI_bifrostbigdaddy_1.",
  "StreamId": "PI_bifrostbigdaddy_1"
}

```

---

### StatusConfiguration

<a id="schemastatusconfiguration"></a>
<a id="schema_StatusConfiguration"></a>
<a id="tocSstatusconfiguration"></a>
<a id="tocsstatusconfiguration"></a>

Status configuration is a property of an asset or asset type that defines the simple status of an asset or asset type.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|DefinitionType|[StatusDefinitionType](#schemastatusdefinitiontype)|false|false|Status definition type. At this moment, only "StreamPropertyMapping" is supported.|
|Definition|any|false|true|Status definition|

```json
{
  "DefinitionType": 0,
  "Definition": null
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

