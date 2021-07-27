---
uid: assets-asset-status-data

---

# Asset Status Data
Status is a property of an asset or asset type that defines the simple status of an asset or asset type. There is one status property for each asset or asset type. If an asset references an existing asset type and the asset type has a corresponding type reference, then the status mapping on the asset is ignored. Create, read, update, and delete of an asset status mapping is done through the asset or asset type itself.

## `Get Last Asset Status Data`

<a id="opIdAssetStatusData_Get Last Asset Status Data"></a>

Returns status of an asset. Status of an asset is determined by an exact match of the Sds stream property value to the value of the ValueStatusMapping. If there are no exact matches, the status is a 0 (Unknown).

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/Status/Last
```

#### Parameters

`string assetId`
<br/>Asset identifier<br/><br/>`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[LastStatusData](#schemalaststatusdata)|Last status of the specified asset.|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See the response body for additional details.|
|404|[ErrorTemplate](#schemaerrortemplate)|Not found|
|422|[ErrorTemplate](#schemaerrortemplate)|Cannot be processed. See the response body for additional details.|

#### Example response body
> 200 Response

```json
{
  "AssetId": "AssetId-1",
  "Status": "Good",
  "Value": "85",
  "DisplayName": "AssetId-1Good",
  "DataRetrievalTime": "2020-05-04T16:55:26.3732693Z"
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

## `Get Asset Status Range Summary Data`

<a id="opIdAssetStatusData_Get Asset Status Range Summary Data"></a>

Returns status summary of an asset.

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/Status/Summary
?startIndex={startIndex}&endIndex={endIndex}&intervals={intervals}
```

#### Parameters

`string assetId`
<br/>Asset identifier<br/><br/>`string startIndex`
<br/>Start index<br/><br/>`string endIndex`
<br/>End index<br/><br/>`integer intervals`
<br/>Number of intervals<br/><br/>`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[StatusRangeSummary](#schemastatusrangesummary)|Last status of the specified asset.|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See the response body for additional details.|
|404|[ErrorTemplate](#schemaerrortemplate)|Not found|
|422|[ErrorTemplate](#schemaerrortemplate)|Cannot be processed. See the response body for additional details.|
|502|None|Bad gateway|

#### Example response body
> 200 Response

```json
{
  "RangeValues": [
    {
      "Index": "2019-01-02T00:00:00Z",
      "Status": "Warning",
      "Value": 2,
      "DisplayName": "AssetInWarning"
    },
    {
      "Index": "2019-01-02T00:30:00Z",
      "Status": "Bad",
      "Value": 4,
      "DisplayName": "AssetInBadState"
    }
  ],
  "Statistics": [
    {
      "Status": "Warning",
      "TotalInterval": "00:30:00",
      "Values": [
        {
          "Value": 2,
          "Interval": "00:30:00"
        }
      ]
    },
    {
      "Status": "Bad",
      "TotalInterval": "1246.06:30:00",
      "Values": [
        {
          "Value": 4,
          "Interval": "1246.06:30:00"
        }
      ]
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

### LastStatusData

<a id="schemalaststatusdata"></a>
<a id="schema_LastStatusData"></a>
<a id="tocSlaststatusdata"></a>
<a id="tocslaststatusdata"></a>

Asset's last status

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Index|any|false|true|Index which the status was last updated|
|Status|[StatusEnum](#schemastatusenum)|false|false|Status enumeration. Valid values are: Unknown, Good, Warning and Bad.|
|Value|any|false|true|Value of the last data retrieved|
|DisplayName|string|false|true|Status display name|
|AssetId|string|false|true|Asset identifier|
|DataRetrievalTime|date-time|false|false|Date and time when the status was last updated.|

```json
{
  "AssetId": "AssetId-1",
  "Status": "Good",
  "Value": "85",
  "DisplayName": "AssetId-1Good",
  "DataRetrievalTime": "2020-05-04T16:55:26.3732693Z"
}

```

---

### StatusEnum

<a id="schemastatusenum"></a>
<a id="schema_StatusEnum"></a>
<a id="tocSstatusenum"></a>
<a id="tocsstatusenum"></a>

Pre-defined asset status values.

#### Enumerated Values

|Property|Value|
|---|---|
|Unknown|0|
|Good|1|
|Warning|2|
|Bad|3|

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

### StatusRangeSummary

<a id="schemastatusrangesummary"></a>
<a id="schema_StatusRangeSummary"></a>
<a id="tocSstatusrangesummary"></a>
<a id="tocsstatusrangesummary"></a>

Returns the status summary of an asset.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|RangeValues|[[StatusData](#schemastatusdata)]|false|true|Status values|
|Statistics|[[StatusValueStatistics](#schemastatusvaluestatistics)]|false|true|Status data statistics|

```json
{
  "RangeValues": [
    {
      "Index": "2019-01-02T00:00:00Z",
      "Status": "Warning",
      "Value": 2,
      "DisplayName": "AssetInWarning"
    },
    {
      "Index": "2019-01-02T00:30:00Z",
      "Status": "Bad",
      "Value": 4,
      "DisplayName": "AssetInBadState"
    }
  ],
  "Statistics": [
    {
      "Status": "Warning",
      "TotalInterval": "00:30:00",
      "Values": [
        {
          "Value": 2,
          "Interval": "00:30:00"
        }
      ]
    },
    {
      "Status": "Bad",
      "TotalInterval": "1246.06:30:00",
      "Values": [
        {
          "Value": 4,
          "Interval": "1246.06:30:00"
        }
      ]
    }
  ]
}

```

---

### StatusData

<a id="schemastatusdata"></a>
<a id="schema_StatusData"></a>
<a id="tocSstatusdata"></a>
<a id="tocsstatusdata"></a>

Status data that is assocated with asset.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Index|any|false|true|Index which the status was last updated|
|Status|[StatusEnum](#schemastatusenum)|false|false|Status enumeration. Valid values are: Unknown, Good, Warning and Bad.|
|Value|any|false|true|Value of the last data retrieved|
|DisplayName|string|false|true|Status display name|

```json
{
  "Index": "2019-01-02T00:00:00Z",
  "Status": "Warning",
  "Value": 2,
  "DisplayName": "AssetInWarning"
}

```

---

### StatusValueStatistics

<a id="schemastatusvaluestatistics"></a>
<a id="schema_StatusValueStatistics"></a>
<a id="tocSstatusvaluestatistics"></a>
<a id="tocsstatusvaluestatistics"></a>

Status value statistics returns asset status statistics

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Status|[StatusEnum](#schemastatusenum)|false|false|Asset status|
|TotalInterval|any|false|true|Total interval|
|Values|[[UnderlyingValueStatistics](#schemaunderlyingvaluestatistics)]|false|true|Asset status statistics per interval|

```json
{
  "Status": 0,
  "TotalInterval": null,
  "Values": [
    {
      "Value": null,
      "Interval": null,
      "DisplayName": "string"
    }
  ]
}

```

---

### UnderlyingValueStatistics

<a id="schemaunderlyingvaluestatistics"></a>
<a id="schema_UnderlyingValueStatistics"></a>
<a id="tocSunderlyingvaluestatistics"></a>
<a id="tocsunderlyingvaluestatistics"></a>

Underlying value statistics represents statistics for a single interval

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Value|any|false|true|Value of the status mapping.|
|Interval|any|false|true|Summary interval|
|DisplayName|string|false|true|User-friendly display name for that status mapping|

```json
{
  "Value": null,
  "Interval": null,
  "DisplayName": "string"
}

```

---

