---
uid: assets-asset-status-data

---

# Asset Status Data

## `Get Last Asset Status Data`

<a id="opIdAssetStatusData_Get Last Asset Status Data"></a>

### Request
```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/assets/{assetId}/status/last
```

#### Parameters

`string assetId`
<br/><br/>`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---

## `Get Asset Status Range Summary Data`

<a id="opIdAssetStatusData_Get Asset Status Range Summary Data"></a>

### Request
```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/assets/{assetId}/status/summary
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

