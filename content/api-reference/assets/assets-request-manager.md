---
uid: assets-request-manager

---

# Request Manager
The asset API allows you to programmatically model your on-premises assets in OSIsoft Cloud Services (OCS). A single stream with its metadata can be used to model very simple assets. However, in most instances, an asset relates to dynamic data from several streams and to static information that describe the asset. This is better structured as an asset instead of any single stream. The assets feature is well suited to model these aspects of an asset. It allows users to create an asset, add static metadata, and reference streams in a standard, structured way. The asset API includes search capabilities and features to directly retrieve the values of dynamic data associated with a given asset. It also provides methods to configure determining the asset status and to configure different user views of an asset.

## `List Assets`

<a id="opIdRequestManager_List Assets"></a>

Returns an array of assets in a given namespace and the total number of assets returned, specified as Total-Count in the HTTP response header.

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets
?skip={skip}&count={count}&orderBy={orderBy}&query={query}&pageSize={pageSize}&maxPages={maxPages}&continuationToken={continuationToken}&Comparer={Comparer}&Count={Count}&Keys={Keys}&System.Collections.Generic.IDictionary<TKey,TValue>.Keys={System.Collections.Generic.IDictionary<TKey,TValue>.Keys}&System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Keys={System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Keys}&Values={Values}&System.Collections.Generic.IDictionary<TKey,TValue>.Values={System.Collections.Generic.IDictionary<TKey,TValue>.Values}&System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Values={System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Values}&Item={Item}&System.Collections.Generic.ICollection<System.Collections.Generic.KeyValuePair<TKey,TValue>>.IsReadOnly={System.Collections.Generic.ICollection<System.Collections.Generic.KeyValuePair<TKey,TValue>>.IsReadOnly}&System.Collections.ICollection.IsSynchronized={System.Collections.ICollection.IsSynchronized}&System.Collections.ICollection.SyncRoot={System.Collections.ICollection.SyncRoot}&System.Collections.IDictionary.IsFixedSize={System.Collections.IDictionary.IsFixedSize}&System.Collections.IDictionary.IsReadOnly={System.Collections.IDictionary.IsReadOnly}&System.Collections.IDictionary.Keys={System.Collections.IDictionary.Keys}&System.Collections.IDictionary.Values={System.Collections.IDictionary.Values}&System.Collections.IDictionary.Item={System.Collections.IDictionary.Item}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>
`[optional] integer skip`
<br/>Parameter representing the zero-based offset of the first object to retrieve.  If unspecified, a default value of 0 is used.<br/><br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of objects to retrieve. If unspecified, a default value of 100 is used.<br/><br/><br/>`[optional] string orderBy`
<br/>Optional parameter which returns assets ordered either by the asset `Id` or the asset `Name`. Specify `asc` or `desc` to return the results in ascending or descending order. If not specified, the default is ascending order.<br/><br/>`[optional] string query`
<br/>Query identifier.<br/><br/><br/>`[optional] integer pageSize`
<br/>Page size, internal use only<br/><br/>`[optional] integer maxPages`
<br/>Max pages, internal use only<br/><br/>`[optional] string continuationToken`
<br/>Internal use only<br/><br/>`[optional] object Comparer`
<br/><br/>`[optional] integer Count`
<br/><br/>`[optional] array Keys`
<br/><br/>`[optional] array System.Collections.Generic.IDictionary<TKey,TValue>.Keys`
<br/><br/>`[optional] array System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Keys`
<br/><br/>`[optional] array Values`
<br/><br/>`[optional] array System.Collections.Generic.IDictionary<TKey,TValue>.Values`
<br/><br/>`[optional] array System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Values`
<br/><br/>`[optional] array Item`
<br/><br/>`[optional] boolean System.Collections.Generic.ICollection<System.Collections.Generic.KeyValuePair<TKey,TValue>>.IsReadOnly`
<br/><br/>`[optional] boolean System.Collections.ICollection.IsSynchronized`
<br/><br/>`[optional] any System.Collections.ICollection.SyncRoot`
<br/><br/>`[optional] boolean System.Collections.IDictionary.IsFixedSize`
<br/><br/>`[optional] boolean System.Collections.IDictionary.IsReadOnly`
<br/><br/>`[optional] array System.Collections.IDictionary.Keys`
<br/><br/>`[optional] array System.Collections.IDictionary.Values`
<br/><br/>`[optional] any System.Collections.IDictionary.Item`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[Asset](#schemaasset)[]|List of assets in the system.|
|400|[ErrorTemplate](#schemaerrortemplate)|The request is not valid. See the response body for additional details.|

#### Response Headers

|Status|Header|Type|Description|
|---|---|---|---|
|200|Total-Count|integer|Total number of assets in the namespace.|

#### Example response body
> 200 Response

```json
[
  {
    "Id": "SampleAsset",
    "Description": "This is a sample asset.",
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
        "Description": "This is reference to a stream. The stream Id is PI_bifrostbigdaddy_1.",
        "StreamId": "PI_bifrostbigdaddy_1"
      }
    ]
  },
  {
    "Id": "SecondSampleAsset",
    "Description": "This is a scond sample asset.",
    "Metadata": [
      {
        "Id": "90ef6205-152b-40ed-8ffa-bac3feff6fa2",
        "Name": "ModelNumber",
        "Description": "This is a static attribute on the asset which represents the model number.",
        "SdsTypeCode": "Double",
        "Value": 900
      }
    ],
    "StreamReferences": [
      {
        "Id": "fdda0985-7dba-48aa-95fc-55620a9b59ad",
        "Name": "Data",
        "Description": "This is reference to a stream. The stream Id is PI_bifrostbigdaddy_2.",
        "StreamId": "PI_bifrostbigdaddy_2"
      }
    ]
  }
]
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

## `Create Asset`

<a id="opIdRequestManager_Create Asset"></a>

Creates a new asset. If the asset you are trying to create references an asset type (through the AssetTypeId property) and if the corresponding asset type has a metadata value with the same Id, then the name and SDS type code of the metadata value on the asset must be null. If the asset type does not have metadata value with a corresponding Id, the name and SDS type code on the asset cannot be null. To support flexibility on creation and update, the following rules and behaviors are executed for metadata and stream references on a given asset when that asset is created from an asset type.

### Request
```text 
POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>

### Request Body

Asset you want to create<br/>

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
      "Description": "This is reference to a stream. The stream Id is PI_bifrostbigdaddy_1.",
      "StreamId": "PI_bifrostbigdaddy_1"
    }
  ]
}
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[Asset](#schemaasset)|OK|
|201|[Asset](#schemaasset)|Asset created|
|302|None|Asset you attempted to create is identical to one that already exists.|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See response body for additional details.|
|403|[ErrorTemplate](#schemaerrortemplate)|You are not authorized to create assets.|
|409|[ErrorTemplate](#schemaerrortemplate)|Conflict. See the response body for additional details.|

#### Response Headers

|Status|Header|Type|Description|
|---|---|---|---|
|200|Etag|integer|Version|
|201|Etag|integer|Version|
|302|Location|string|Location to get the identical resource.|

#### Example response body
> 200 Response

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
      "Description": "This is reference to a stream. The stream Id is PI_bifrostbigdaddy_1.",
      "StreamId": "PI_bifrostbigdaddy_1"
    }
  ]
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
      "Description": "This is reference to a stream. The stream Id is PI_bifrostbigdaddy_1.",
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

## `Bulk Create Assets`

<a id="opIdRequestManager_Bulk Create Assets"></a>

Creates assets in bulk. Creates multiple assets in a single call.

### Request
```text 
POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Bulk/Assets
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>

### Request Body

List of assets you want to create.<br/>

```json
[
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
        "Description": "This is reference to a stream. The stream Id is PI_bifrostbigdaddy_1.",
        "StreamId": "PI_bifrostbigdaddy_1"
      }
    ]
  }
]
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[Asset](#schemaasset)[]|Assets as persisted, including values for optional parameters that were omitted in the request.|
|207|[MultiStatusResultOfAssetAndChildErrorTemplate](#schemamultistatusresultofassetandchilderrortemplate)|Partial success. Some assets were created. See response body for additional details.|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See response body for additional details.|

#### Example response body
> 200 Response

```json
[
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
        "Description": "This is reference to a stream. The stream Id is PI_bifrostbigdaddy_1.",
        "StreamId": "PI_bifrostbigdaddy_1"
      }
    ]
  },
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
        "Description": "This is reference to a stream. The stream Id is PI_bifrostbigdaddy_1.",
        "StreamId": "PI_bifrostbigdaddy_1"
      }
    ]
  }
]
```

> 207 Response ([MultiStatusResultOfAssetAndChildErrorTemplate](#schemamultistatusresultofassetandchilderrortemplate))

```json
{
  "Reason": "string",
  "Error": "string",
  "OperationId": "string",
  "Data": [
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
          "Description": "This is reference to a stream. The stream Id is PI_bifrostbigdaddy_1.",
          "StreamId": "PI_bifrostbigdaddy_1"
        }
      ]
    }
  ],
  "ChildErrors": [
    {
      "OperationId": "string",
      "Error": "string",
      "Resolution": "string",
      "Reason": "string",
      "StatusCode": 0,
      "property1": null,
      "property2": null
    }
  ]
}
```

---

## `Bulk Delete Assets`

<a id="opIdRequestManager_Bulk Delete Assets"></a>

Deletes all assets with the specified identifiers. This API can delete up to a maximum of 1000 assets in one API call.

### Request
```text 
DELETE /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Bulk/Assets
?id={id}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>
`[optional] array id`
<br/>Comma separated asset identifiers in the form of id={assetId_1},id={assetId_2}<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|204|None|Assets with the specified ids has been deleted.|
|207|[MultiStatusResultOfStringAndChildErrorTemplate](#schemamultistatusresultofstringandchilderrortemplate)|Partial success. Not all assets were deleted. See response body for additional details.|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See the response body for additional details.|

#### Example response body
> 207 Response ([MultiStatusResultOfStringAndChildErrorTemplate](#schemamultistatusresultofstringandchilderrortemplate))

```json
{
  "Reason": "string",
  "Error": "string",
  "OperationId": "string",
  "Data": [
    "string"
  ],
  "ChildErrors": [
    {
      "OperationId": "string",
      "Error": "string",
      "Resolution": "string",
      "Reason": "string",
      "StatusCode": 0,
      "property1": null,
      "property2": null
    }
  ]
}
```

---

## `Get Assets In Search Result Format`

<a id="opIdRequestManager_Get Assets In Search Result Format"></a>

Searches all assets and returns a list of asset Ids and their matched fields. Use this API to identify the fields in the asset that match your query string.

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Search/Assets
?skip={skip}&count={count}&orderBy={orderBy}&query={query}&pageSize={pageSize}&maxPages={maxPages}&continuationToken={continuationToken}&Comparer={Comparer}&Count={Count}&Keys={Keys}&System.Collections.Generic.IDictionary<TKey,TValue>.Keys={System.Collections.Generic.IDictionary<TKey,TValue>.Keys}&System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Keys={System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Keys}&Values={Values}&System.Collections.Generic.IDictionary<TKey,TValue>.Values={System.Collections.Generic.IDictionary<TKey,TValue>.Values}&System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Values={System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Values}&Item={Item}&System.Collections.Generic.ICollection<System.Collections.Generic.KeyValuePair<TKey,TValue>>.IsReadOnly={System.Collections.Generic.ICollection<System.Collections.Generic.KeyValuePair<TKey,TValue>>.IsReadOnly}&System.Collections.ICollection.IsSynchronized={System.Collections.ICollection.IsSynchronized}&System.Collections.ICollection.SyncRoot={System.Collections.ICollection.SyncRoot}&System.Collections.IDictionary.IsFixedSize={System.Collections.IDictionary.IsFixedSize}&System.Collections.IDictionary.IsReadOnly={System.Collections.IDictionary.IsReadOnly}&System.Collections.IDictionary.Keys={System.Collections.IDictionary.Keys}&System.Collections.IDictionary.Values={System.Collections.IDictionary.Values}&System.Collections.IDictionary.Item={System.Collections.IDictionary.Item}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>
`[optional] integer skip`
<br/>Parameter representing the zero-based offset of the first object to retrieve.  If unspecified, a default value of 0 is used.<br/><br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of objects to retrieve. If unspecified, a default value of 100 is used.<br/><br/><br/>`[optional] string orderBy`
<br/>Optional parameter which returns assets ordered either by the asset `Id` or the asset `Name`. Specify `asc` or `desc` to return the results in ascending or descending order. If not specified, the default is ascending order.<br/><br/>`[optional] string query`
<br/>Query identifier.<br/><br/><br/>`[optional] integer pageSize`
<br/>Page size, internal use only<br/><br/>`[optional] integer maxPages`
<br/>Max pages, internal use only<br/><br/>`[optional] string continuationToken`
<br/>Internal use only<br/><br/>`[optional] object Comparer`
<br/><br/>`[optional] integer Count`
<br/><br/>`[optional] array Keys`
<br/><br/>`[optional] array System.Collections.Generic.IDictionary<TKey,TValue>.Keys`
<br/><br/>`[optional] array System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Keys`
<br/><br/>`[optional] array Values`
<br/><br/>`[optional] array System.Collections.Generic.IDictionary<TKey,TValue>.Values`
<br/><br/>`[optional] array System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Values`
<br/><br/>`[optional] array Item`
<br/><br/>`[optional] boolean System.Collections.Generic.ICollection<System.Collections.Generic.KeyValuePair<TKey,TValue>>.IsReadOnly`
<br/><br/>`[optional] boolean System.Collections.ICollection.IsSynchronized`
<br/><br/>`[optional] any System.Collections.ICollection.SyncRoot`
<br/><br/>`[optional] boolean System.Collections.IDictionary.IsFixedSize`
<br/><br/>`[optional] boolean System.Collections.IDictionary.IsReadOnly`
<br/><br/>`[optional] array System.Collections.IDictionary.Keys`
<br/><br/>`[optional] array System.Collections.IDictionary.Values`
<br/><br/>`[optional] any System.Collections.IDictionary.Item`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[SearchResultsOfSearchResult](#schemasearchresultsofsearchresult)|OK|
|204|None|No assets match your query.|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See the response body for additional details.|

#### Example response body
> 200 Response

```json
{
  "Count": 1,
  "Results": [
    {
      "MatchedProperties": [
        {
          "Field": "Name",
          "Value": "Asset Mine Truck 353e3cfe-f20b-4bef-b9c4-f75fbbdc0818"
        }
      ],
      "Id": "AssetId2b5f41ae-0929-4977-bfbd-1e046d8a66f4",
      "TypeId": "AssetMineTruckType",
      "Name": "Asset Mine Truck 353e3cfe-f20b-4bef-b9c4-f75fbbdc0818",
      "Description": "First mine truck used the mine diamon hands",
      "ETag": "1",
      "CreatedDate": "2021-05-26T19:05:33.8979442Z",
      "LastModifiedDate": "2021-05-26T19:05:33.8979442Z"
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

## `List Faceted List Results`

<a id="opIdRequestManager_List Faceted List Results"></a>

Searches for assets using facets. Asset facets are not case-sensitive. Only asset metadata can be used in faceted searches.

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Search/Assets/Facets
?count={count}&name={name}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>
`[optional] integer count`
<br/>Parameter representing the maximum number of objects to retrieve. If unspecified, a default value of 100 is used.<br/><br/><br/>`[optional] string name`
<br/>Name of the asset metadata for which you want to retrieve the facet values.<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[FacetResult](#schemafacetresult)[]|OK|
|204|None|No assets match your query.|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See response body for additional details.|

#### Example response body
> 200 Response

```json
[
  {
    "Name": "Location",
    "FacetValues": [
      {
        "Value": "California",
        "DocumentCount": 2
      },
      {
        "Value": "Philly",
        "DocumentCount": 1
      }
    ]
  }
]
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

## `Get Bulk Last Status Data For Assets`

<a id="opIdRequestManager_Get Bulk Last Status Data For Assets"></a>

Returns status of multiple assets.

### Request
```text 
POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Bulk/Assets/Status/Last
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>

### Request Body

Asset identifiers<br/>

```json
[
  "AssetId-1",
  "AssetId-2",
  "AssetId-3"
]
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[LastStatusData](#schemalaststatusdata)[]|Last status of assets in the body.|
|207|[MultiStatusResultOfLastStatusDataAndChildErrorTemplate](#schemamultistatusresultoflaststatusdataandchilderrortemplate)|Partial success. Some assets encountered errors. See response body for additional details.|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See response body for additional details.|

#### Example response body
> 200 Response

```json
[
  {
    "AssetId": "AssetId-1",
    "Status": 1,
    "Value": "85",
    "DisplayName": "TemperatureSensorBuild1InF",
    "DataRetrievalTime": "2020-05-04T16:55:26.3732693Z"
  },
  {
    "AssetId": "AssetId-2",
    "Status": 2,
    "Value": "185",
    "DisplayName": "DeviceMeasurement",
    "DataRetrievalTime": "2020-05-04T16:55:26.3732693Z"
  }
]
```

> 207 Response ([MultiStatusResultOfLastStatusDataAndChildErrorTemplate](#schemamultistatusresultoflaststatusdataandchilderrortemplate))

```json
{
  "Reason": "string",
  "Error": "string",
  "OperationId": "string",
  "Data": [
    {
      "AssetId": "AssetId-1",
      "Status": "Good",
      "Value": "85",
      "DisplayName": "AssetId-1Good",
      "DataRetrievalTime": "2020-05-04T16:55:26.3732693Z"
    }
  ],
  "ChildErrors": [
    {
      "OperationId": "string",
      "Error": "string",
      "Resolution": "string",
      "Reason": "string",
      "StatusCode": 0,
      "property1": null,
      "property2": null
    }
  ]
}
```

---

## `Bulk Get Resolved Assets`

<a id="opIdRequestManager_Bulk Get Resolved Assets"></a>

Returns multiple resolved assets.

### Request
```text 
POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Bulk/Assets/Resolved
```

#### Parameters

`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>

### Request Body

Asset identifiers<br/>

```json
[
  "AssetId-1",
  "AssetId-2"
]
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[ResolvedAsset](#schemaresolvedasset)[]|Returns the resolved view of multiple assets.|
|207|[MultiStatusResultOfStringAndChildErrorTemplate](#schemamultistatusresultofstringandchilderrortemplate)|Partial success. Not all assets were able to be resolved. See response body for additional details.|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See the response body for additional details.|

#### Example response body
> 200 Response

```json
[
  {
    "Id": "AssetId-1",
    "Name": "Asset1",
    "Description": "An example asset.",
    "AssetTypeId": "Asset1Type",
    "AssetTypeName": "NameOfAsset1Type",
    "Metadata": [
      {
        "Id": "Metadata1",
        "Name": "Metadata1",
        "Description": "Description of Metadata1",
        "SdsTypeCode": "String",
        "Value": "This is an example metadata for example asset",
        "Uom": null
      }
    ],
    "Streams": [
      {
        "Name": "StreamReference1",
        "Properties": [
          {
            "Id": "pi_bifrostincinerate1",
            "IsKey": true,
            "Uom": null,
            "Order": 0,
            "InterpolationMode": "Default",
            "ExtrapolationMode": "All",
            "SdsType": "SimpleSdsType",
            "Source": null
          }
        ]
      }
    ],
    "UnresolvedStreams": [
      {}
    ],
    "Status": {}
  },
  {
    "Id": "AssetId-2",
    "Name": "Asset2",
    "Description": "A second example asset.",
    "AssetTypeId": null,
    "AssetTypeName": null,
    "Metadata": [
      {
        "Id": "Metadata2",
        "Name": "Metadata2",
        "Description": "Description of Metadata2",
        "SdsTypeCode": "String",
        "Value": "This is an example metadata for example asset 2",
        "Uom": null
      }
    ],
    "Streams": [
      {}
    ],
    "UnresolvedStreams": [
      {}
    ],
    "Status": {}
  }
]
```

> 207 Response ([MultiStatusResultOfStringAndChildErrorTemplate](#schemamultistatusresultofstringandchilderrortemplate))

```json
{
  "Reason": "string",
  "Error": "string",
  "OperationId": "string",
  "Data": [
    "string"
  ],
  "ChildErrors": [
    {
      "OperationId": "string",
      "Error": "string",
      "Resolution": "string",
      "Reason": "string",
      "StatusCode": 0,
      "property1": null,
      "property2": null
    }
  ]
}
```

---

## `Get Autocomplete Results`

<a id="opIdRequestManager_Get Autocomplete Results"></a>

Returns a list of suggested assets based on your search criteria. The autocomplete feature can be used with the following asset properties: Name, Description, AssetTypeName, and Metadata.

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Search/Assets/Autocomplete
?term={term}&termCount={termCount}&facetCount={facetCount}
```

#### Parameters

`string term`
<br/>Search term that you want to search for<br/><br/>`integer termCount`
<br/>Maximum number of facet autocompleted items to return. Default is 0.<br/><br/>`integer facetCount`
<br/>Maximum number of token autocompleted items to return. Default is 0.<br/><br/>`string tenantId`
<br/>Tenant identifier.<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[SuggestionResults](#schemasuggestionresults)|Returns the suggestions|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See response body for additional details.|

#### Example response body
> 200 Response

```json
{
  "Facets": [
    {
      "Value": "trackUnit1",
      "FacetCategories": [
        {
          "Name": "track",
          "DocumentCount": 1
        }
      ]
    },
    {
      "Value": "t1000",
      "FacetCategories": [
        {
          "Name": "tractorNumber",
          "DocumentCount": 1
        }
      ]
    }
  ],
  "Tokens": [
    {
      "Value": "tracerround",
      "DocumentCount": 2
    },
    {
      "Value": "t1000",
      "DocumentCount": 1
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

### Asset

<a id="schemaasset"></a>
<a id="schema_Asset"></a>
<a id="tocSasset"></a>
<a id="tocsasset"></a>

Represents an asset object.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Asset identifier. If you do not provide an Id, OCS copies the name as the identifier. If you do not provide a name, OCS assigns a random GUID for the Id.|
|AssetTypeId|string|false|true|Asset type identifier. Id for the asset type that this asset is derived from. To get the merged view of the asset, get the resolved asset through the /Assets/{assetId}/Resolved route.|
|Name|string|false|true|User-friendly name for asset. Required if identifier is not provided. If name is used as the identifier, it must be unique within a given namespace.|
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
      "Description": "This is reference to a stream. The stream Id is PI_bifrostbigdaddy_1.",
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

### StreamReference

<a id="schemastreamreference"></a>
<a id="schema_StreamReference"></a>
<a id="tocSstreamreference"></a>
<a id="tocsstreamreference"></a>

An asset stream reference represents dynamic stream data associated with an asset. The references must either be an SDS stream or an SDS stream view. Asset-centric data routes provide direct access to dynamic data for a given asset. There are no limitations on the number of references an asset may contain. However, an asset cannot contain multiple references to the same SDS stream. An asset stream reference does not stand alone. It must be specified within an asset object and, therefore, asset references do not have direct API routes.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Stream Reference identifier|
|Name|string|false|true|User-friendly name for stream reference|
|Description|string|false|true|Description of the stream reference|
|StreamId|string|true|false|SDS stream Id that is being referenced.|

```json
{
  "Id": "f1bf9da2-3858-4bcd-bf93-e7c26ab0d28e",
  "Name": "Data",
  "Description": "This is reference to a stream. The stream Id is PI_bifrostbigdaddy_1.",
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
|DefinitionType|[StatusDefinitionType](#schemastatusdefinitiontype)|false|false|Status definition type. Only "StreamPropertyMapping" is supported.|
|Definition|any|false|true|Status definition|

```json
{
  "DefinitionType": "StreamPropertyMapping",
  "Definition": {
    "StreamReferenceId": "StatusMappingOnAssetTypeCrudFunctionalTest_streamRef",
    "StreamPropertyId": "Value",
    "ValueStatusMappings": [
      {
        "Value": 3,
        "Status": "Bad",
        "DisplayName": "Bad"
      },
      {
        "Value": 1,
        "Status": "Good",
        "DisplayName": "Good"
      }
    ]
  }
}

```

---

### StatusDefinitionType

<a id="schemastatusdefinitiontype"></a>
<a id="schema_StatusDefinitionType"></a>
<a id="tocSstatusdefinitiontype"></a>
<a id="tocsstatusdefinitiontype"></a>

Status definition type. Currently, only StreamPropertyMapping is supported.

#### Enumerated Values

|Property|Value|
|---|---|
|Unspecified|0|
|StreamPropertyMapping|1|

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

### MultiStatusResultOfAssetAndChildErrorTemplate

<a id="schemamultistatusresultofassetandchilderrortemplate"></a>
<a id="schema_MultiStatusResultOfAssetAndChildErrorTemplate"></a>
<a id="tocSmultistatusresultofassetandchilderrortemplate"></a>
<a id="tocsmultistatusresultofassetandchilderrortemplate"></a>

A multi status result is returned to indicate a partial success.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Reason|string|false|true|None|
|Error|string|false|true|None|
|OperationId|string|false|true|None|
|Data|[[Asset](#schemaasset)]|false|true|[Represents an asset object.]|
|ChildErrors|[[ChildErrorTemplate](#schemachilderrortemplate)]|false|true|None|

```json
{
  "Reason": "string",
  "Error": "string",
  "OperationId": "string",
  "Data": [
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
          "Description": "This is reference to a stream. The stream Id is PI_bifrostbigdaddy_1.",
          "StreamId": "PI_bifrostbigdaddy_1"
        }
      ]
    }
  ],
  "ChildErrors": [
    {
      "OperationId": "string",
      "Error": "string",
      "Resolution": "string",
      "Reason": "string",
      "StatusCode": 0,
      "property1": null,
      "property2": null
    }
  ]
}

```

---

### ChildErrorTemplate

<a id="schemachilderrortemplate"></a>
<a id="schema_ChildErrorTemplate"></a>
<a id="tocSchilderrortemplate"></a>
<a id="tocschilderrortemplate"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|false|true|Operation identifier|
|Error|string|false|true|Error string|
|Resolution|string|false|true|Resolution string|
|Reason|string|false|true|Error reason string|
|StatusCode|int32|false|false|None|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Resolution": "string",
  "Reason": "string",
  "StatusCode": 0,
  "property1": null,
  "property2": null
}

```

---

### IEqualityComparerOfString

<a id="schemaiequalitycomparerofstring"></a>
<a id="schema_IEqualityComparerOfString"></a>
<a id="tocSiequalitycomparerofstring"></a>
<a id="tocsiequalitycomparerofstring"></a>

```json
{}

```

---

### SearchResultsOfSearchResult

<a id="schemasearchresultsofsearchresult"></a>
<a id="schema_SearchResultsOfSearchResult"></a>
<a id="tocSsearchresultsofsearchresult"></a>
<a id="tocssearchresultsofsearchresult"></a>

The set of search results matching search query.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|TotalCount|int32|false|false|Total number of items matching search that is returned.|
|Results|[[SearchResult](#schemasearchresult)]|false|true|The search results.|
|ContinuationTokens|string[]|false|true|List of continuation tokens for navigation.|

```json
{
  "Count": 1,
  "Results": [
    {
      "MatchedProperties": [
        {
          "Field": "Name",
          "Value": "Asset Mine Truck 353e3cfe-f20b-4bef-b9c4-f75fbbdc0818"
        }
      ],
      "Id": "AssetId2b5f41ae-0929-4977-bfbd-1e046d8a66f4",
      "TypeId": "AssetMineTruckType",
      "Name": "Asset Mine Truck 353e3cfe-f20b-4bef-b9c4-f75fbbdc0818",
      "Description": "First mine truck used the mine diamon hands",
      "ETag": "1",
      "CreatedDate": "2021-05-26T19:05:33.8979442Z",
      "LastModifiedDate": "2021-05-26T19:05:33.8979442Z"
    }
  ]
}

```

---

### SearchResult

<a id="schemasearchresult"></a>
<a id="schema_SearchResult"></a>
<a id="tocSsearchresult"></a>
<a id="tocssearchresult"></a>

Search results

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|MatchedFields|[[MatchedField](#schemamatchedfield)]|false|true|A list of matched property objects. Each MatchProperties object contains the matched fields and their values.|
|Score|double|false|false|Calculated score of the match. For internal use.|
|Id|string|false|true|Identifier of the matched asset.|
|TypeId|string|false|true|Asset type identifier of the matched asset.|
|Name|string|false|true|Name of the matched asset.|
|Description|string|false|true|Description of the matched asset.|
|LastStatus|[StatusData](#schemastatusdata)|false|true|Last status of the matched asset.|
|ETag|string|false|true|Etag of the matched asset.|
|CreatedDate|date-time|false|false|Created date of the matched asset.|
|LastModifiedDate|date-time|false|false|Modified date of the matched asset.|

```json
{
  "TotalCount": 2,
  "Results": [
    {
      "MatchedFields": [
        {
          "Field": "Description",
          "Terms": [
            "searchedDescription"
          ]
        },
        {
          "Field": "Name",
          "Terms": [
            "searchedName"
          ]
        }
      ],
      "Score": 0.07410964510231982,
      "Id": "AssetsSearchDemo1",
      "Name": "SearchedName 1",
      "Description": "SearchedDescription 1",
      "ETag": "1",
      "CreatedDate": "2021-06-28T05:57:13.4249707Z",
      "LastModifiedDate": "2021-06-28T05:57:13.4249707Z"
    },
    {
      "MatchedFields": [
        {
          "Field": "Description",
          "Terms": [
            "searchedDescription"
          ]
        },
        {
          "Field": "Name",
          "Terms": [
            "searchedName"
          ]
        }
      ],
      "Score": 0.062210717451675585,
      "Id": "AssetsSearchDemo2",
      "Name": "SearchResultName 2",
      "Description": "SearchResultDescription 2",
      "ETag": "6",
      "CreatedDate": "2021-06-28T05:57:13.5965826Z",
      "LastModifiedDate": "2021-06-28T05:57:13.5965826Z"
    }
  ]
}

```

---

### MatchedField

<a id="schemamatchedfield"></a>
<a id="schema_MatchedField"></a>
<a id="tocSmatchedfield"></a>
<a id="tocsmatchedfield"></a>

Matched fields. Includes the matched property and matched terms.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Field|string|false|true|Matching property|
|Terms|string[]|false|true|Matching terms|

```json
"\"MatchedFields\": [\n{\n    \"Field\": \"Description\",\n    \"Terms\": [\n        \"searchedDescription\"\n    ]\n    },{\n    \"Field\": \"Name\",\n    \"Terms\": [\n        \"searchedName\"\n    ]\n}]"

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

### FacetResult

<a id="schemafacetresult"></a>
<a id="schema_FacetResult"></a>
<a id="tocSfacetresult"></a>
<a id="tocsfacetresult"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|None|
|FacetValues|[[FacetValue](#schemafacetvalue)]|false|true|None|

```json
{
  "Name": "string",
  "FacetValues": [
    {
      "Value": "string",
      "DocumentCount": 0
    }
  ]
}

```

---

### FacetValue

<a id="schemafacetvalue"></a>
<a id="schema_FacetValue"></a>
<a id="tocSfacetvalue"></a>
<a id="tocsfacetvalue"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Value|string|false|true|None|
|DocumentCount|int32|false|false|None|

```json
{
  "Value": "string",
  "DocumentCount": 0
}

```

---

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

### MultiStatusResultOfLastStatusDataAndChildErrorTemplate

<a id="schemamultistatusresultoflaststatusdataandchilderrortemplate"></a>
<a id="schema_MultiStatusResultOfLastStatusDataAndChildErrorTemplate"></a>
<a id="tocSmultistatusresultoflaststatusdataandchilderrortemplate"></a>
<a id="tocsmultistatusresultoflaststatusdataandchilderrortemplate"></a>

A multi status result is returned to indicate a partial success.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Reason|string|false|true|None|
|Error|string|false|true|None|
|OperationId|string|false|true|None|
|Data|[[LastStatusData](#schemalaststatusdata)]|false|true|[Asset's last status]|
|ChildErrors|[[ChildErrorTemplate](#schemachilderrortemplate)]|false|true|None|

```json
{
  "Reason": "string",
  "Error": "string",
  "OperationId": "string",
  "Data": [
    {
      "AssetId": "AssetId-1",
      "Status": "Good",
      "Value": "85",
      "DisplayName": "AssetId-1Good",
      "DataRetrievalTime": "2020-05-04T16:55:26.3732693Z"
    }
  ],
  "ChildErrors": [
    {
      "OperationId": "string",
      "Error": "string",
      "Resolution": "string",
      "Reason": "string",
      "StatusCode": 0,
      "property1": null,
      "property2": null
    }
  ]
}

```

---

### MultiStatusResultOfStringAndChildErrorTemplate

<a id="schemamultistatusresultofstringandchilderrortemplate"></a>
<a id="schema_MultiStatusResultOfStringAndChildErrorTemplate"></a>
<a id="tocSmultistatusresultofstringandchilderrortemplate"></a>
<a id="tocsmultistatusresultofstringandchilderrortemplate"></a>

A multi status result is returned to indicate a partial success.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Reason|string|false|true|None|
|Error|string|false|true|None|
|OperationId|string|false|true|None|
|Data|string[]|false|true|None|
|ChildErrors|[[ChildErrorTemplate](#schemachilderrortemplate)]|false|true|None|

```json
{
  "Reason": "string",
  "Error": "string",
  "OperationId": "string",
  "Data": [
    "string"
  ],
  "ChildErrors": [
    {
      "OperationId": "string",
      "Error": "string",
      "Resolution": "string",
      "Reason": "string",
      "StatusCode": 0,
      "property1": null,
      "property2": null
    }
  ]
}

```

---

### ResolvedAsset

<a id="schemaresolvedasset"></a>
<a id="schema_ResolvedAsset"></a>
<a id="tocSresolvedasset"></a>
<a id="tocsresolvedasset"></a>

The resolved asset describes the consumption-oriented aspects of an OCS resource rather than describing how the resource is configured. The resolved asset corresponds to its metadata and referenced stream which define how the data is interpreted (that is, SdsTypeCode, InterpolationMode, and UOM).

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Asset identifier|
|Name|string|false|true|Asset name|
|Resolved|boolean|false|false|True if no shape is applied|
|Description|string|false|true|Asset description|
|AssetTypeId|string|false|true|Asset type Id of asset, if applicable|
|AssetTypeName|string|false|true|Asset type name of asset's asset type, if applicable|
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
|StreamReferenceName|string|false|true|Stream reference name used in the asset|
|StreamId|string|false|true|SDS stream Id of the referenced stream|
|PropertyMaps|[[PropertyMap](#schemapropertymap)]|false|true|SDS stream property maps|

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
    "GenericArguments": "[<SdsType>]",
    "Properties": [
      {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "Order": 0,
        "IsKey": true,
        "FixedSize": 0,
        "SdsType": "<SdsType>",
        "Value": null,
        "Uom": "string",
        "InterpolationMode": 0
      }
    ],
    "BaseType": "<SdsType>",
    "DerivedTypes": "[<SdsType>]",
    "InterpolationMode": 0,
    "ExtrapolationMode": 0
  },
  "StreamReferenceName": "string",
  "StreamId": "string",
  "PropertyMaps": [
    {
      "Id": "Timestamp",
      "SourcePropertyId": "Timestamp"
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
  "GenericArguments": "[<SdsType>]",
  "Properties": [
    {
      "Id": "string",
      "Name": "string",
      "Description": "string",
      "Order": 0,
      "IsKey": true,
      "FixedSize": 0,
      "SdsType": "<SdsType>",
      "Value": null,
      "Uom": "string",
      "InterpolationMode": 0
    }
  ],
  "BaseType": "<SdsType>",
  "DerivedTypes": "[<SdsType>]",
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
    "GenericArguments": "[<SdsType>]",
    "Properties": "[<SdsTypeProperty>]",
    "BaseType": "<SdsType>",
    "DerivedTypes": "[<SdsType>]",
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
|SourcePropertyId|string|false|true|Source property identifier|

```json
{
  "Id": "Timestamp",
  "SourcePropertyId": "Timestamp"
}

```

---

### UnresolvedStream

<a id="schemaunresolvedstream"></a>
<a id="schema_UnresolvedStream"></a>
<a id="tocSunresolvedstream"></a>
<a id="tocsunresolvedstream"></a>

Unresolved stream, a property of the resolved asset, is a stream that could not be resolved.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|Name of the stream reference that could not be resolved.|
|Reason|string|false|true|Reason why the stream could not be resolved.|

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

Currently not used. Unresolved metadata, a property of the resolved asset, is metadata that could not be resolved.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|Name of the metadata which could not be resolved.|
|Reason|string|false|true|Reason why the metadata could not be resolved.|

```json
{
  "Name": "Name of metadata which could not be resolved",
  "Reason": "Reason why metadata could not be resolved."
}

```

---

### UnresolvedStatus

<a id="schemaunresolvedstatus"></a>
<a id="schema_UnresolvedStatus"></a>
<a id="tocSunresolvedstatus"></a>
<a id="tocsunresolvedstatus"></a>

Unresolved status, a property of the resolved asset, means asset status could not be resolved.

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

### SuggestionResults

<a id="schemasuggestionresults"></a>
<a id="schema_SuggestionResults"></a>
<a id="tocSsuggestionresults"></a>
<a id="tocssuggestionresults"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Facets|[[FacetSuggestion](#schemafacetsuggestion)]|false|true|None|
|Tokens|[[TokenSuggestion](#schematokensuggestion)]|false|true|None|

```json
{
  "Facets": [
    {
      "Value": "string",
      "FacetCategories": [
        {
          "Name": "string",
          "DocumentCount": 0
        }
      ]
    }
  ],
  "Tokens": [
    {
      "Value": "string",
      "DocumentCount": 0
    }
  ]
}

```

---

### FacetSuggestion

<a id="schemafacetsuggestion"></a>
<a id="schema_FacetSuggestion"></a>
<a id="tocSfacetsuggestion"></a>
<a id="tocsfacetsuggestion"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Value|string|false|true|None|
|FacetCategories|[[FacetCategory](#schemafacetcategory)]|false|true|None|

```json
{
  "Value": "string",
  "FacetCategories": [
    {
      "Name": "string",
      "DocumentCount": 0
    }
  ]
}

```

---

### FacetCategory

<a id="schemafacetcategory"></a>
<a id="schema_FacetCategory"></a>
<a id="tocSfacetcategory"></a>
<a id="tocsfacetcategory"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|None|
|DocumentCount|int32|false|false|None|

```json
{
  "Name": "string",
  "DocumentCount": 0
}

```

---

### TokenSuggestion

<a id="schematokensuggestion"></a>
<a id="schema_TokenSuggestion"></a>
<a id="tocStokensuggestion"></a>
<a id="tocstokensuggestion"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Value|string|false|true|None|
|DocumentCount|int32|false|false|None|

```json
{
  "Value": "string",
  "DocumentCount": 0
}

```

---

