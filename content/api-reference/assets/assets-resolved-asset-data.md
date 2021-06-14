---
uid: assets-resolved-asset-data

---

# Resolved Asset Data

## `Get Window Data`

<a id="opIdResolvedAssetData_Get Window Data"></a>

### Request
```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/assets/{assetId}/Data
?startIndex={startIndex}&endIndex={endIndex}&stream={stream}
```

#### Parameters

`string assetId`
<br/><br/>`string startIndex`
<br/><br/>`string endIndex`
<br/><br/>`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>
`[optional] array stream`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---

## `Get Interpolated Data`

<a id="opIdResolvedAssetData_Get Interpolated Data"></a>

### Request
```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/assets/{assetId}/Data/Interpolated
?startIndex={startIndex}&endIndex={endIndex}&count={count}&stream={stream}
```

#### Parameters

`string assetId`
<br/><br/>`string startIndex`
<br/><br/>`string endIndex`
<br/><br/>`integer count`
<br/><br/>`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>
`[optional] array stream`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---

## `Get Last Data`

<a id="opIdResolvedAssetData_Get Last Data"></a>

### Request
```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/assets/{assetId}/Data/Last
?stream={stream}
```

#### Parameters

`string assetId`
<br/><br/>`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>
`[optional] array stream`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---

## `Get Sampled Data`

<a id="opIdResolvedAssetData_Get Sampled Data"></a>

### Request
```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/assets/{assetId}/Data/Sampled
?startIndex={startIndex}&endIndex={endIndex}&intervals={intervals}&stream={stream}
```

#### Parameters

`string assetId`
<br/><br/>`string startIndex`
<br/><br/>`string endIndex`
<br/><br/>`integer intervals`
<br/><br/>`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>
`[optional] array stream`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---

## `Get Summary Data`

<a id="opIdResolvedAssetData_Get Summary Data"></a>

### Request
```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/assets/{assetId}/Data/Summaries
?startIndex={startIndex}&endIndex={endIndex}&stream={stream}&count={count}
```

#### Parameters

`string assetId`
<br/><br/>`string startIndex`
<br/><br/>`string endIndex`
<br/><br/>`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>
`[optional] array stream`
<br/><br/>`[optional] integer count`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

