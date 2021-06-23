---
uid: assets-asset-status-data

---

# Asset Status Data

## `Get Last Asset Status Data`

<a id="opIdAssetStatusData_Get Last Asset Status Data"></a>

View the status of an asset.

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/Status/Last
```

#### Parameters

`string assetId`
<br/>Asset identifier<br/><br/>`string tenantId`
<br/>Tenant identifier<br/><br/>`string namespaceId`
<br/>Namespace identifier<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[LastStatusData](#schemalaststatusdata)|The last status of the specified asset.|
|400|[ErrorTemplate](#schemaerrortemplate)|The request is not valid. See the response body for additional details.|
|422|None|The request is not valid. See the response body for additional details.|
|500|None|Internal Service Error, please try again later.|
|503|None|Service Unavaiable, please try again later.|

#### Example response body
> 200 Response

```json
{
  "AssetId": "AssetId-1",
  "Status": 1,
  "Value": "85",
  "DisplayName": "TemperatureSensorBuild1InF",
  "DataRetrievalTime": "2020-05-04T16:55:26.3732693Z"
}
```

> 400 Response

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

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/Status/Summary
?startIndex={startIndex}&endIndex={endIndex}&intervals={intervals}
```

#### Parameters

`string assetId`
<br/><br/>`string startIndex`
<br/><br/>`string endIndex`
<br/><br/>`integer intervals`
<br/><br/>`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---
## Definitions

### LastStatusData

<a id="schemalaststatusdata"></a>
<a id="schema_LastStatusData"></a>
<a id="tocSlaststatusdata"></a>
<a id="tocslaststatusdata"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Index|any|false|true|None|
|Status|[StatusEnum](#schemastatusenum)|false|false|None|
|Value|any|false|true|None|
|DisplayName|string|false|true|None|
|AssetId|string|false|true|None|
|DataRetrievalTime|date-time|false|false|None|

```json
{
  "Index": null,
  "Status": 0,
  "Value": null,
  "DisplayName": "string",
  "AssetId": "string",
  "DataRetrievalTime": "2019-08-24T14:15:22Z"
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

