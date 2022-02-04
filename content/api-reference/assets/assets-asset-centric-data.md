---
uid: assets-asset-centric-data

---

# Asset Centric Data
The asset centric data API provides a quick way to retrieve data stored in an asset's referenced streams.

## `Get Last Data`

<a id="opIdResolvedAssetData_Get Last Data"></a>

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/Data/Last
?stream={stream}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string assetId`
<br/><br/>
`[optional] array stream`
<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[DataResults](#schemadataresults)|None|
|400|[ErrorTemplate](#schemaerrortemplate)|None|
|404|[ErrorTemplate](#schemaerrortemplate)|None|

<h4>Example response body</h4>

> 200 Response ([DataResults](#schemadataresults))

```json
{
  "Results": {
    "property1": [
      null
    ],
    "property2": [
      null
    ]
  },
  "Errors": {
    "OperationId": "string",
    "Error": "string",
    "Reason": "string",
    "ChildErrors": {
      "property1": null,
      "property2": null
    }
  }
}
```

---

## `Get Sampled Data`

<a id="opIdResolvedAssetData_Get Sampled Data"></a>

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/Data/Sampled
?startIndex={startIndex}&endIndex={endIndex}&intervals={intervals}&stream={stream}&boundaryType={boundaryType}&startBoundaryType={startBoundaryType}&endBoundaryType={endBoundaryType}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string assetId`
<br/><br/>`string startIndex`
<br/><br/>`string endIndex`
<br/><br/>`integer intervals`
<br/><br/>
`[optional] array stream`
<br/><br/>`[optional] any boundaryType`
<br/><br/>`[optional] any startBoundaryType`
<br/><br/>`[optional] any endBoundaryType`
<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[DataResults](#schemadataresults)|None|
|400|[ErrorTemplate](#schemaerrortemplate)|None|
|404|[ErrorTemplate](#schemaerrortemplate)|None|

<h4>Example response body</h4>

> 200 Response ([DataResults](#schemadataresults))

```json
{
  "Results": {
    "property1": [
      null
    ],
    "property2": [
      null
    ]
  },
  "Errors": {
    "OperationId": "string",
    "Error": "string",
    "Reason": "string",
    "ChildErrors": {
      "property1": null,
      "property2": null
    }
  }
}
```

---

## `Get Summary Data`

<a id="opIdResolvedAssetData_Get Summary Data"></a>

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/Data/Summaries
?startIndex={startIndex}&endIndex={endIndex}&stream={stream}&count={count}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string assetId`
<br/><br/>`string startIndex`
<br/><br/>`string endIndex`
<br/><br/>
`[optional] array stream`
<br/><br/>`[optional] integer count`
<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[DataResults](#schemadataresults)|None|
|400|[ErrorTemplate](#schemaerrortemplate)|None|
|404|[ErrorTemplate](#schemaerrortemplate)|None|

<h4>Example response body</h4>

> 200 Response ([DataResults](#schemadataresults))

```json
{
  "Results": {
    "property1": [
      null
    ],
    "property2": [
      null
    ]
  },
  "Errors": {
    "OperationId": "string",
    "Error": "string",
    "Reason": "string",
    "ChildErrors": {
      "property1": null,
      "property2": null
    }
  }
}
```

---

## `Get Interpolated Data`

<a id="opIdResolvedAssetData_Get Interpolated Data"></a>

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/Data/Interpolated
?startIndex={startIndex}&endIndex={endIndex}&count={count}&stream={stream}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string assetId`
<br/><br/>`string startIndex`
<br/><br/>`string endIndex`
<br/><br/>`integer count`
<br/><br/>
`[optional] array stream`
<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[DataResults](#schemadataresults)|None|
|400|[ErrorTemplate](#schemaerrortemplate)|None|
|404|[ErrorTemplate](#schemaerrortemplate)|None|

<h4>Example response body</h4>

> 200 Response ([DataResults](#schemadataresults))

```json
{
  "Results": {
    "property1": [
      null
    ],
    "property2": [
      null
    ]
  },
  "Errors": {
    "OperationId": "string",
    "Error": "string",
    "Reason": "string",
    "ChildErrors": {
      "property1": null,
      "property2": null
    }
  }
}
```

---

## `Get Window Data`

<a id="opIdResolvedAssetData_Get Window Data"></a>

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/Data
?startIndex={startIndex}&endIndex={endIndex}&stream={stream}&boundaryType={boundaryType}&startBoundaryType={startBoundaryType}&endBoundaryType={endBoundaryType}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string assetId`
<br/><br/>`string startIndex`
<br/><br/>`string endIndex`
<br/><br/>
`[optional] array stream`
<br/><br/>`[optional] any boundaryType`
<br/><br/>`[optional] any startBoundaryType`
<br/><br/>`[optional] any endBoundaryType`
<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[DataResults](#schemadataresults)|None|
|400|[ErrorTemplate](#schemaerrortemplate)|None|
|404|[ErrorTemplate](#schemaerrortemplate)|None|

<h4>Example response body</h4>

> 200 Response ([DataResults](#schemadataresults))

```json
{
  "Results": {
    "property1": [
      null
    ],
    "property2": [
      null
    ]
  },
  "Errors": {
    "OperationId": "string",
    "Error": "string",
    "Reason": "string",
    "ChildErrors": {
      "property1": null,
      "property2": null
    }
  }
}
```

---
## Definitions

### DataResults

<a id="schemadataresults"></a>
<a id="schema_DataResults"></a>
<a id="tocSdataresults"></a>
<a id="tocsdataresults"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Results|object|false|true|None|
|Errors|[DataErrors](#schemadataerrors)|false|true|None|

```json
{
  "Results": {
    "property1": [
      null
    ],
    "property2": [
      null
    ]
  },
  "Errors": {
    "OperationId": "string",
    "Error": "string",
    "Reason": "string",
    "ChildErrors": {
      "property1": null,
      "property2": null
    }
  }
}

```

---

### DataErrors

<a id="schemadataerrors"></a>
<a id="schema_DataErrors"></a>
<a id="tocSdataerrors"></a>
<a id="tocsdataerrors"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|false|true|None|
|Error|string|false|true|None|
|Reason|string|false|true|None|
|ChildErrors|object|false|true|None|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "ChildErrors": {
    "property1": null,
    "property2": null
  }
}

```

---

### ErrorTemplate

<a id="schemaerrortemplate"></a>
<a id="schema_ErrorTemplate"></a>
<a id="tocSerrortemplate"></a>
<a id="tocserrortemplate"></a>

<h4>Properties</h4>

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

### SdsBoundaryType

<a id="schemasdsboundarytype"></a>
<a id="schema_SdsBoundaryType"></a>
<a id="tocSsdsboundarytype"></a>
<a id="tocssdsboundarytype"></a>

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|Exact|0|
|Inside|1|
|Outside|2|
|ExactOrCalculated|3|

---

