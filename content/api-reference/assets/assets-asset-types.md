---
uid: assets-asset-types

---

# Asset Types

## `Get Asset Types`

<a id="opIdAssetTypes_Get Asset Types"></a>

### Request
```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/assetTypes
?skip={skip}&count={count}&query={query}
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>
`[optional] integer skip skip`
<br/><br/>`[optional] integer count count`
<br/><br/>`[optional] string query query`
<br/><br/>

#### Request Headers

|Header|Type|Required|Description|
|---|---|---|---|

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---

## `Create Asset Types`

<a id="opIdAssetTypes_Create Asset Types"></a>

### Request
```text 
POST /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/assetTypes
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

#### Request Headers

|Header|Type|Required|Description|
|---|---|---|---|

### Request Body

<br/>

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "Metadata": [
    {
      "Id": "string",
      "Name": "string",
      "Description": "string",
      "SdsTypeCode": "Empty",
      "Value": null,
      "Uom": "string"
    }
  ],
  "TypeReferences": [
    {
      "StreamReferenceId": "string",
      "StreamReferenceName": "string",
      "Description": "string",
      "TypeId": "string"
    }
  ],
  "Status": {
    "StreamReferenceId": "string",
    "StreamPropertyId": "string",
    "ValueStatusMappings": [
      {}
    ]
  }
}
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---

## `Get Asset Type`

<a id="opIdAssetTypes_Get Asset Type"></a>

### Request
```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/assetTypes/{assetTypeId}
```

#### Parameters

`string assetTypeId`
<br/><br/>`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

#### Request Headers

|Header|Type|Required|Description|
|---|---|---|---|

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---

## `Create Asset Type`

<a id="opIdAssetTypes_Create Asset Type"></a>

### Request
```text 
POST /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/assetTypes/{assetTypeId}
```

#### Parameters

`string assetTypeId`
<br/><br/>`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

#### Request Headers

|Header|Type|Required|Description|
|---|---|---|---|

### Request Body

<br/>

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "Metadata": [
    {
      "Id": "string",
      "Name": "string",
      "Description": "string",
      "SdsTypeCode": "Empty",
      "Value": null,
      "Uom": "string"
    }
  ],
  "TypeReferences": [
    {
      "StreamReferenceId": "string",
      "StreamReferenceName": "string",
      "Description": "string",
      "TypeId": "string"
    }
  ],
  "Status": {
    "StreamReferenceId": "string",
    "StreamPropertyId": "string",
    "ValueStatusMappings": [
      {}
    ]
  }
}
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---

## `Create Or Update Asset Type`

<a id="opIdAssetTypes_Create Or Update Asset Type"></a>

### Request
```text 
PUT /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/assetTypes/{assetTypeId}
```

#### Parameters

`string assetTypeId`
<br/><br/>`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

#### Request Headers

|Header|Type|Required|Description|
|---|---|---|---|

### Request Body

<br/>

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "Metadata": [
    {
      "Id": "string",
      "Name": "string",
      "Description": "string",
      "SdsTypeCode": "Empty",
      "Value": null,
      "Uom": "string"
    }
  ],
  "TypeReferences": [
    {
      "StreamReferenceId": "string",
      "StreamReferenceName": "string",
      "Description": "string",
      "TypeId": "string"
    }
  ],
  "Status": {
    "StreamReferenceId": "string",
    "StreamPropertyId": "string",
    "ValueStatusMappings": [
      {}
    ]
  }
}
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---

## `Delete Asset Type`

<a id="opIdAssetTypes_Delete Asset Type"></a>

### Request
```text 
DELETE /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/assetTypes/{assetTypeId}
?deleteAssets={deleteAssets}
```

#### Parameters

`string assetTypeId`
<br/><br/>`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>
`[optional] boolean deleteAssets deleteAssets`
<br/><br/>

#### Request Headers

|Header|Type|Required|Description|
|---|---|---|---|

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---

## `Get Asset Type Acl`

<a id="opIdAssetTypes_Get Asset Type Acl"></a>

### Request
```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/AssetTypes/{assetTypeId}/accesscontrol
```

#### Parameters

`string assetTypeId`
<br/><br/>`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

#### Request Headers

|Header|Type|Required|Description|
|---|---|---|---|

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---

## `Update Asset Type Access Control`

<a id="opIdAssetTypes_Update Asset Type Access Control"></a>

### Request
```text 
PUT /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/AssetTypes/{assetTypeId}/accesscontrol
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string assetTypeId`
<br/><br/>

#### Request Headers

|Header|Type|Required|Description|
|---|---|---|---|

### Request Body

<br/>

```json
{
  "RoleTrusteeAccessControlEntries": [
    {
      "Trustee": {},
      "AccessType": 0,
      "AccessRights": 0
    }
  ]
}
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---

## `Get Asset Type Access Rights`

<a id="opIdAssetTypes_Get Asset Type Access Rights"></a>

### Request
```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/AssetTypes/{assetTypeId}/accessrights
```

#### Parameters

`string assetTypeId`
<br/><br/>`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

#### Request Headers

|Header|Type|Required|Description|
|---|---|---|---|

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---

## `Get Asset Type Owner`

<a id="opIdAssetTypes_Get Asset Type Owner"></a>

### Request
```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/AssetTypes/{assetTypeId}/owner
```

#### Parameters

`string assetTypeId`
<br/><br/>`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

#### Request Headers

|Header|Type|Required|Description|
|---|---|---|---|

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---

## `Update Asset Type Owner`

<a id="opIdAssetTypes_Update Asset Type Owner"></a>

### Request
```text 
PUT /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/AssetTypes/{assetTypeId}/owner
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string assetTypeId`
<br/><br/>

#### Request Headers

|Header|Type|Required|Description|
|---|---|---|---|

### Request Body

<br/>

```json
{
  "Type": 1,
  "ObjectId": "string",
  "TenantId": "string"
}
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---

## `Create Asset Types (`bulk` path)`

<a id="opIdAssetTypes_Create Asset Types (`bulk` path)"></a>

### Request
```text 
POST /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/bulk/assetTypes
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

#### Request Headers

|Header|Type|Required|Description|
|---|---|---|---|

### Request Body

<br/>

```json
[
  {
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "Metadata": [
      {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "SdsTypeCode": "Empty",
        "Value": null,
        "Uom": "string"
      }
    ],
    "TypeReferences": [
      {
        "StreamReferenceId": "string",
        "StreamReferenceName": "string",
        "Description": "string",
        "TypeId": "string"
      }
    ],
    "Status": {
      "StreamReferenceId": "string",
      "StreamPropertyId": "string",
      "ValueStatusMappings": [
        {
          "Value": null,
          "Status": null,
          "DisplayName": null
        }
      ]
    }
  }
]
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---
## Definitions

### AssetType

<a id="schemaassettype"></a>
<a id="schema_AssetType"></a>
<a id="tocSassettype"></a>
<a id="tocsassettype"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|None|
|Name|string|false|true|None|
|Description|string|false|true|None|
|Metadata|[[MetadataItem](#schemametadataitem)]|false|true|None|
|TypeReferences|[[TypeReference](#schematypereference)]|false|true|None|
|Status|[StatusMapping](#schemastatusmapping)|false|true|None|

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "Metadata": [
    {
      "Id": "string",
      "Name": "string",
      "Description": "string",
      "SdsTypeCode": "Empty",
      "Value": null,
      "Uom": "string"
    }
  ],
  "TypeReferences": [
    {
      "StreamReferenceId": "string",
      "StreamReferenceName": "string",
      "Description": "string",
      "TypeId": "string"
    }
  ],
  "Status": {
    "StreamReferenceId": "string",
    "StreamPropertyId": "string",
    "ValueStatusMappings": [
      {
        "Value": null,
        "Status": "[",
        "DisplayName": "string"
      }
    ]
  }
}

```

---

### MetadataItem

<a id="schemametadataitem"></a>
<a id="schema_MetadataItem"></a>
<a id="tocSmetadataitem"></a>
<a id="tocsmetadataitem"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|None|
|Name|string|false|true|None|
|Description|string|false|true|None|
|SdsTypeCode|[SdsTypeCode2](#schemasdstypecode2)|false|false|None|
|Value|any|false|true|None|
|Uom|string|false|true|None|

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "SdsTypeCode": "Empty",
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

### TypeReference

<a id="schematypereference"></a>
<a id="schema_TypeReference"></a>
<a id="tocStypereference"></a>
<a id="tocstypereference"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|StreamReferenceId|string|false|true|None|
|StreamReferenceName|string|false|true|None|
|Description|string|false|true|None|
|TypeId|string|true|false|None|

```json
{
  "StreamReferenceId": "string",
  "StreamReferenceName": "string",
  "Description": "string",
  "TypeId": "string"
}

```

---

### StatusMapping

<a id="schemastatusmapping"></a>
<a id="schema_StatusMapping"></a>
<a id="tocSstatusmapping"></a>
<a id="tocsstatusmapping"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|StreamReferenceId|string|true|false|None|
|StreamPropertyId|string|true|false|None|
|ValueStatusMappings|[[ValueStatusMapping](#schemavaluestatusmapping)]|false|true|None|

```json
{
  "StreamReferenceId": "string",
  "StreamPropertyId": "string",
  "ValueStatusMappings": [
    {
      "Value": null,
      "Status": 0,
      "DisplayName": "string"
    }
  ]
}

```

---

### ValueStatusMapping

<a id="schemavaluestatusmapping"></a>
<a id="schema_ValueStatusMapping"></a>
<a id="tocSvaluestatusmapping"></a>
<a id="tocsvaluestatusmapping"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Value|any|false|true|None|
|Status|[StatusEnum](#schemastatusenum)|true|false|None|
|DisplayName|string|false|true|None|

```json
{
  "Value": null,
  "Status": 0,
  "DisplayName": "string"
}

```

---

### StatusEnum

<a id="schemastatusenum"></a>
<a id="schema_StatusEnum"></a>
<a id="tocSstatusenum"></a>
<a id="tocsstatusenum"></a>

#### Enumerated Values

|Property|Value|
|---|---|
|Unknown|0|
|Good|1|
|Warning|2|
|Bad|3|

---

### Trustee

<a id="schematrustee"></a>
<a id="schema_Trustee"></a>
<a id="tocStrustee"></a>
<a id="tocstrustee"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Type|[TrusteeType](#schematrusteetype)|false|false|None|
|ObjectId|string|false|true|None|
|TenantId|string|false|true|None|

```json
{
  "Type": 1,
  "ObjectId": "string",
  "TenantId": "string"
}

```

---

### TrusteeType

<a id="schematrusteetype"></a>
<a id="schema_TrusteeType"></a>
<a id="tocStrusteetype"></a>
<a id="tocstrusteetype"></a>

#### Enumerated Values

|Property|Value|
|---|---|
|User|1|
|Client|2|
|Role|3|

---

### AccessControlList

<a id="schemaaccesscontrollist"></a>
<a id="schema_AccessControlList"></a>
<a id="tocSaccesscontrollist"></a>
<a id="tocsaccesscontrollist"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|RoleTrusteeAccessControlEntries|[[AccessControlEntry](#schemaaccesscontrolentry)]|false|true|None|

```json
{
  "RoleTrusteeAccessControlEntries": [
    {
      "Trustee": {
        "Type": "[",
        "ObjectId": "string",
        "TenantId": "string"
      },
      "AccessType": 0,
      "AccessRights": 0
    }
  ]
}

```

---

### AccessControlEntry

<a id="schemaaccesscontrolentry"></a>
<a id="schema_AccessControlEntry"></a>
<a id="tocSaccesscontrolentry"></a>
<a id="tocsaccesscontrolentry"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Trustee|[Trustee](#schematrustee)|false|true|None|
|AccessType|[AccessType](#schemaaccesstype)|false|false|None|
|AccessRights|int64|false|false|None|

```json
{
  "Trustee": {
    "Type": 1,
    "ObjectId": "string",
    "TenantId": "string"
  },
  "AccessType": 0,
  "AccessRights": 0
}

```

---

### AccessType

<a id="schemaaccesstype"></a>
<a id="schema_AccessType"></a>
<a id="tocSaccesstype"></a>
<a id="tocsaccesstype"></a>

#### Enumerated Values

|Property|Value|
|---|---|
|Allowed|0|
|Denied|1|

---

