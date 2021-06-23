---
uid: assets-request-manager

---

# Request Manager
The asset type API provides methods to create, read, update, and delete asset types.An asset type can be used to build many similar assets.Some of the key benefits of using an asset type as the base model for assets are: - Multiple similar assets can be created more quickly and with less effort. - Maintaining assets is simplified...

## `Get Assets`

<a id="opIdRequestManager_Get Assets"></a>

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets
?skip={skip}&count={count}&orderBy={orderBy}&query={query}&pageSize={pageSize}&maxPages={maxPages}&continuationToken={continuationToken}&Comparer={Comparer}&Count={Count}&Keys={Keys}&System.Collections.Generic.IDictionary<TKey,TValue>.Keys={System.Collections.Generic.IDictionary<TKey,TValue>.Keys}&System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Keys={System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Keys}&Values={Values}&System.Collections.Generic.IDictionary<TKey,TValue>.Values={System.Collections.Generic.IDictionary<TKey,TValue>.Values}&System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Values={System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Values}&Item={Item}&System.Collections.Generic.ICollection<System.Collections.Generic.KeyValuePair<TKey,TValue>>.IsReadOnly={System.Collections.Generic.ICollection<System.Collections.Generic.KeyValuePair<TKey,TValue>>.IsReadOnly}&System.Collections.ICollection.IsSynchronized={System.Collections.ICollection.IsSynchronized}&System.Collections.ICollection.SyncRoot={System.Collections.ICollection.SyncRoot}&System.Collections.IDictionary.IsFixedSize={System.Collections.IDictionary.IsFixedSize}&System.Collections.IDictionary.IsReadOnly={System.Collections.IDictionary.IsReadOnly}&System.Collections.IDictionary.Keys={System.Collections.IDictionary.Keys}&System.Collections.IDictionary.Values={System.Collections.IDictionary.Values}&System.Collections.IDictionary.Item={System.Collections.IDictionary.Item}
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>
`[optional] integer skip`
<br/><br/>`[optional] integer count`
<br/><br/>`[optional] string orderBy`
<br/><br/>`[optional] string query`
<br/><br/>`[optional] integer pageSize`
<br/><br/>`[optional] integer maxPages`
<br/><br/>`[optional] string continuationToken`
<br/><br/>`[optional] object Comparer`
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
|200|string|None|

---

## `Create Asset`

<a id="opIdRequestManager_Create Asset"></a>

### Request
```text 
POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Request Body

<br/>

```json
{
  "Id": "string",
  "AssetTypeId": "string",
  "Name": "string",
  "Description": "string",
  "Metadata": [
    {
      "Id": "Sample Metadata Id",
      "Name": "Asset Model number",
      "Description": "This metadata represents an model number attribute on the asset.",
      "SdsTypeCode": "Double",
      "Value": "RFA-123",
      "Uom": null
    }
  ],
  "StreamReferences": [
    {
      "Id": "f1bf9da2-3858-4bcd-bf93-e7c26ab0d28e",
      "Name": "Data",
      "Description": "This is reference to a stream. The stream id is PI_bifrostbigdaddy_1.",
      "StreamId": "PI_bifrostbigdaddy_1"
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

## `List Assets Async2`

<a id="opIdRequestManager_List Assets Async2"></a>

Returns an array of assets in a given namespace and the total number of assets returned, specified as Total-Count in the HTTP response header.

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets2
?skip={skip}&count={count}&orderBy={orderBy}&query={query}&pageSize={pageSize}&maxPages={maxPages}&continuationToken={continuationToken}&Comparer={Comparer}&Count={Count}&Keys={Keys}&System.Collections.Generic.IDictionary<TKey,TValue>.Keys={System.Collections.Generic.IDictionary<TKey,TValue>.Keys}&System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Keys={System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Keys}&Values={Values}&System.Collections.Generic.IDictionary<TKey,TValue>.Values={System.Collections.Generic.IDictionary<TKey,TValue>.Values}&System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Values={System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Values}&Item={Item}&System.Collections.Generic.ICollection<System.Collections.Generic.KeyValuePair<TKey,TValue>>.IsReadOnly={System.Collections.Generic.ICollection<System.Collections.Generic.KeyValuePair<TKey,TValue>>.IsReadOnly}&System.Collections.ICollection.IsSynchronized={System.Collections.ICollection.IsSynchronized}&System.Collections.ICollection.SyncRoot={System.Collections.ICollection.SyncRoot}&System.Collections.IDictionary.IsFixedSize={System.Collections.IDictionary.IsFixedSize}&System.Collections.IDictionary.IsReadOnly={System.Collections.IDictionary.IsReadOnly}&System.Collections.IDictionary.Keys={System.Collections.IDictionary.Keys}&System.Collections.IDictionary.Values={System.Collections.IDictionary.Values}&System.Collections.IDictionary.Item={System.Collections.IDictionary.Item}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/>`string namespaceId`
<br/>Namespace identifier<br/><br/>
`[optional] integer skip`
<br/>An optional parameter representing the zero-based offset of the first asset to retrieve. If not specified, a default value of 0 is used.<br/><br/>`[optional] integer count`
<br/>An optional parameter, between 1 and 1000 (inclusive), that represents the maximum number of retrieved assets. If not specified, the default is 100.<br/><br/>`[optional] string orderBy`
<br/>An optional parameter which returns assets ordered either by the asset Id or the asset name. Specify asc or desc to return the results in ascending or descending order. If not specified, the default is ascending order.<br/><br/>`[optional] string query`
<br/>Query parameter<br/><br/>`[optional] integer pageSize`
<br/><br/>`[optional] integer maxPages`
<br/><br/>`[optional] string continuationToken`
<br/><br/>`[optional] object Comparer`
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
|200|[Asset](#schemaasset)[]|List of assets in the given namespace.|
|400|[ErrorTemplate](#schemaerrortemplate)|The request is not valid. See the response body for additional details.|
|500|None|Internal Service Error, please try again later.|
|503|None|Service Unavaiable, please try again later.|

#### Response Headers

|Status|Header|Type|Description|
|---|---|---|---|
|200|Total-Count|integer|Total number of assets in the namespace.|

#### Example response body
> 200 Response

```json
[
  {
    "Id": "Heater_HIJK",
    "Name": "HeaterOnFirstFloor",
    "Description": "This is Asset which represents a heater on the first floor."
  },
  {
    "Id": "Heater_ABCDEF",
    "Name": "HeaterOnFirstFloor",
    "Description": "This is Asset which represents a heater on the first floor."
  }
]
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

## `Create Asset Async2`

<a id="opIdRequestManager_Create Asset Async2"></a>

Creates a new asset. If the asset you are trying to create references an asset type (through the AssetTypeId property) and if the corresponding asset type has a metadata value with the same Id, then the name and SDS type code of the metadata value on the asset must be null. If the asset type does not have metadata value with a corresponding Id, the name and SDS type code on the asset cannot be null. To support flexibility on creation and update, the following rules and behaviors are executed for metadata and stream references on a given asset when that asset is created from an asset type.

### Request
```text 
POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets2
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/>`string namespaceId`
<br/>Namespace identifier<br/><br/>

### Request Body

The asset you want to create.<br/>

```json
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
      "Description": "This is reference to a stream. The stream id is PI_bifrostbigdaddy_1.",
      "StreamId": "PI_bifrostbigdaddy_1"
    }
  ]
}
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[Asset](#schemaasset)|The asset that was created.|
|302|None|The asset you attempted to create is identical to one that already exists.|
|400|[ErrorTemplate](#schemaerrortemplate)|The request is not valid. See the response body for additional details.|
|403|[ErrorTemplate](#schemaerrortemplate)|You are not authorized to create assets.|
|409|[ErrorTemplate](#schemaerrortemplate)|The asset you attempted to create has a conflict. See the response body for additional details.|
|500|None|Internal Service Error, please try again later.|
|503|None|Service Unavaiable, please try again later.|

#### Response Headers

|Status|Header|Type|Description|
|---|---|---|---|
|302|Location|string|Location to get the identical resource.|

#### Example response body
> 200 Response

```json
{
  "Id": "Heater_01_01_02",
  "Name": "HeaterOnFirstFloor",
  "Description": "This is Asset which represents a heater on the first floor.",
  "Metadata": [
    {
      "Id": "17020d80-1dc8-4690-932f-3421c9cff0d1",
      "Name": "ModelNumber",
      "Description": "This is attribute with double value representing the model number.",
      "SdsTypeCode": "Double",
      "Value": 1.3
    }
  ],
  "StreamReferences": [
    {
      "Id": "63c0ba1d-f2db-4b28-b650-7e45afca9ab4",
      "Name": "Data",
      "Description": "This is reference to a stream. The stream has data coming from a heater.",
      "StreamId": "PI_bifrostbigdaddy_1"
    }
  ]
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

## `Bulk Create Assets`

<a id="opIdRequestManager_Bulk Create Assets"></a>

### Request
```text 
POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Bulk/Assets
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Request Body

<br/>

```json
[
  {
    "Id": "string",
    "AssetTypeId": "string",
    "Name": "string",
    "Description": "string",
    "Metadata": [
      {
        "Id": "Sample Metadata Id",
        "Name": "Asset Model number",
        "Description": "This metadata represents an model number attribute on the asset.",
        "SdsTypeCode": "Double",
        "Value": "RFA-123",
        "Uom": null
      }
    ],
    "StreamReferences": [
      {
        "Id": "f1bf9da2-3858-4bcd-bf93-e7c26ab0d28e",
        "Name": "Data",
        "Description": "This is reference to a stream. The stream id is PI_bifrostbigdaddy_1.",
        "StreamId": "PI_bifrostbigdaddy_1"
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

## `Bulk Delete Assets`

<a id="opIdRequestManager_Bulk Delete Assets"></a>

Delete all assets with the specified Ids.Use this API to delete up to a maximum of 1000 assets in one API call.

### Request
```text 
DELETE /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Bulk/Assets
?id={id}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/>`string namespaceId`
<br/>Namespace identifier<br/><br/>
`[optional] array id`
<br/>Asset identifiers<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|204|None|The assets with the specified ids has been deleted.|
|207|[MultiStatusResultOfStringAndChildErrorTemplate](#schemamultistatusresultofstringandchilderrortemplate)|Array of errors. Assets that did not encounter errors are deleted.|
|400|[ErrorTemplate](#schemaerrortemplate)|The request is not valid. See the response body for additional details.|
|500|None|Internal Service Error, please try again later.|
|503|None|Service Unavaiable, please try again later.|

#### Example response body
> 207 Response

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

## `Bulk Deprecated Get Resolved Assets`

<a id="opIdRequestManager_Bulk Deprecated Get Resolved Assets"></a>

View multiple resolved assets.

### Request
```text 
POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Bulk/Assets/Resolved
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/>`string namespaceId`
<br/>Namespace identifier<br/><br/>

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
|200|[DeprecatedResolvedAsset](#schemadeprecatedresolvedasset)[]|Returns the resolved view of multiple assets.|
|207|[MultiStatusResultOfStringAndChildErrorTemplate](#schemamultistatusresultofstringandchilderrortemplate)|On POST, returns the resolved view of multiple assets. For error responses, check the multi-status response for the error and cause.|
|400|[ErrorTemplate](#schemaerrortemplate)|The request is not valid. See the response body for additional details.|
|500|None|Internal Service Error, please try again later.|
|503|None|Service Unavaiable, please try again later.|

#### Example response body
> 200 Response

```json
[
  {
    "Id": "Asset1",
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
  }
]
```

> 207 Response

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

## `Bulk Get Resolved Assets`

<a id="opIdRequestManager_Bulk Get Resolved Assets"></a>

### Request
```text 
POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Bulk/Assets/Resolved2
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Request Body

<br/>

```json
[
  "string"
]
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---

## `Get Bulk Last Status Data For Assets`

<a id="opIdRequestManager_Get Bulk Last Status Data For Assets"></a>

View the status of multiple assets.

### Request
```text 
POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Bulk/Assets/Status/Last
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/>`string namespaceId`
<br/>Namespace identifier<br/><br/>

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
|200|[LastStatusData](#schemalaststatusdata)[]|The last status of assets in the POST body.|
|207|[MultiStatusResultOfLastStatusDataAndChildErrorTemplate](#schemamultistatusresultoflaststatusdataandchilderrortemplate)|On POST, returns the status of multiple assets. Errors are returned for assets which status couldn't resolve.|
|400|[ErrorTemplate](#schemaerrortemplate)|The request is not valid. See the response body for additional details.|
|500|None|Internal Service Error, please try again later.|
|503|None|Service Unavaiable, please try again later.|

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

> 207 Response

```json
{
  "Reason": "string",
  "Error": "string",
  "OperationId": "string",
  "Data": [
    {
      "Index": null,
      "Status": 0,
      "Value": null,
      "DisplayName": "string",
      "AssetId": "string",
      "DataRetrievalTime": "2019-08-24T14:15:22Z"
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

## `Bulk Create Assets Async2`

<a id="opIdRequestManager_Bulk Create Assets Async2"></a>

Bulk create assets. Creates multiple assets in a single call.

### Request
```text 
POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Bulk/Assets2
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/>`string namespaceId`
<br/>Namespace identifier<br/><br/>

### Request Body

The list of assets you want to create.<br/>

```json
[
  {
    "Id": "FirstAssetToCreate",
    "Name": "FirstAssetToCreate",
    "Description": "This is the first Asset to create in this bulk call."
  },
  {
    "Id": "SecondAssetToCreate",
    "Name": "SecondAssetToCreate",
    "Description": "This is the second Asset to create in this bulk call.",
    "Metadata": [
      {
        "Id": "FirstMetdataOfTheSecondAsset",
        "Name": "ModelNumber",
        "SdsTypeCode": "Double",
        "Value": 1234
      }
    ]
  }
]
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[Asset](#schemaasset)[]|The asset that was created.|
|207|[MultiStatusResultOfAssetAndChildErrorTemplate](#schemamultistatusresultofassetandchilderrortemplate)|The asset that was created.|
|400|[ErrorTemplate](#schemaerrortemplate)|The request is not valid. See the response body for additional details.|
|500|None|Internal Service Error, please try again later.|
|503|None|Service Unavaiable, please try again later.|

#### Example response body
> 200 Response

```json
[
  {
    "Id": "Heater_01_01_02",
    "Name": "HeaterOnFirstFloor",
    "Description": "This is Asset which represents a heater on the first floor.",
    "Metadata": [
      {
        "Id": "17020d80-1dc8-4690-932f-3421c9cff0d1",
        "Name": "ModelNumber",
        "Description": "This is attribute with double value representing the model number.",
        "SdsTypeCode": "Double",
        "Value": 1.3
      }
    ]
  },
  {
    "Id": "TracerUnit_101",
    "Name": "TracerOnRoof",
    "Description": "This is Asset which represents a tracer.",
    "Metadata": [
      {
        "Id": "Tracer_1234",
        "Name": "ModelNumber",
        "SdsTypeCode": "Double",
        "Value": 1234
      }
    ]
  }
]
```

> 207 Response

```json
{
  "Reason": "string",
  "Error": "string",
  "OperationId": "string",
  "Data": [
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
          "Description": "This is reference to a stream. The stream id is PI_bifrostbigdaddy_1.",
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

## `Get Assets In Search Result Format`

<a id="opIdRequestManager_Get Assets In Search Result Format"></a>

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Search/Assets
?skip={skip}&count={count}&orderBy={orderBy}&query={query}&pageSize={pageSize}&maxPages={maxPages}&continuationToken={continuationToken}&Comparer={Comparer}&Count={Count}&Keys={Keys}&System.Collections.Generic.IDictionary<TKey,TValue>.Keys={System.Collections.Generic.IDictionary<TKey,TValue>.Keys}&System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Keys={System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Keys}&Values={Values}&System.Collections.Generic.IDictionary<TKey,TValue>.Values={System.Collections.Generic.IDictionary<TKey,TValue>.Values}&System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Values={System.Collections.Generic.IReadOnlyDictionary<TKey,TValue>.Values}&Item={Item}&System.Collections.Generic.ICollection<System.Collections.Generic.KeyValuePair<TKey,TValue>>.IsReadOnly={System.Collections.Generic.ICollection<System.Collections.Generic.KeyValuePair<TKey,TValue>>.IsReadOnly}&System.Collections.ICollection.IsSynchronized={System.Collections.ICollection.IsSynchronized}&System.Collections.ICollection.SyncRoot={System.Collections.ICollection.SyncRoot}&System.Collections.IDictionary.IsFixedSize={System.Collections.IDictionary.IsFixedSize}&System.Collections.IDictionary.IsReadOnly={System.Collections.IDictionary.IsReadOnly}&System.Collections.IDictionary.Keys={System.Collections.IDictionary.Keys}&System.Collections.IDictionary.Values={System.Collections.IDictionary.Values}&System.Collections.IDictionary.Item={System.Collections.IDictionary.Item}
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>
`[optional] integer skip`
<br/><br/>`[optional] integer count`
<br/><br/>`[optional] string orderBy`
<br/><br/>`[optional] string query`
<br/><br/>`[optional] integer pageSize`
<br/><br/>`[optional] integer maxPages`
<br/><br/>`[optional] string continuationToken`
<br/><br/>`[optional] object Comparer`
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
|200|string|None|

---

## `Get Autocomplete Results`

<a id="opIdRequestManager_Get Autocomplete Results"></a>

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Search/Assets/Autocomplete
?term={term}&termCount={termCount}&facetCount={facetCount}
```

#### Parameters

`string term`
<br/><br/>`integer termCount`
<br/><br/>`integer facetCount`
<br/><br/>`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---

## `Get Faceted Search Results`

<a id="opIdRequestManager_Get Faceted Search Results"></a>

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Search/Assets/Facets
?count={count}&name={name}
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>
`[optional] integer count`
<br/><br/>`[optional] string name`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---
## Definitions

### Asset

<a id="schemaasset"></a>
<a id="schema_Asset"></a>
<a id="tocSasset"></a>
<a id="tocsasset"></a>

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

#### Properties

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
|OperationId|string|false|true|None|
|Error|string|false|true|None|
|Resolution|string|false|true|None|
|Reason|string|false|true|None|

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

### DeprecatedAsset

<a id="schemadeprecatedasset"></a>
<a id="schema_DeprecatedAsset"></a>
<a id="tocSdeprecatedasset"></a>
<a id="tocsdeprecatedasset"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Asset Id|
|AssetTypeId|string|false|true|Asset Type Id|
|Name|string|false|true|Asset Name|
|Description|string|false|true|None|
|Metadata|[[MetadataItem](#schemametadataitem)]|false|true|None|
|StreamReferences|[[StreamReference](#schemastreamreference)]|false|true|None|
|Status|[StatusMapping](#schemastatusmapping)|false|true|None|

```json
{
  "Id": "string",
  "AssetTypeId": "string",
  "Name": "string",
  "Description": "string",
  "Metadata": [
    {
      "Id": "Sample Metadata Id",
      "Name": "Asset Model number",
      "Description": "This metadata represents an model number attribute on the asset.",
      "SdsTypeCode": "Double",
      "Value": "RFA-123",
      "Uom": null
    }
  ],
  "StreamReferences": [
    {
      "Id": "f1bf9da2-3858-4bcd-bf93-e7c26ab0d28e",
      "Name": "Data",
      "Description": "This is reference to a stream. The stream id is PI_bifrostbigdaddy_1.",
      "StreamId": "PI_bifrostbigdaddy_1"
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

### MultiStatusResultOfAssetAndChildErrorTemplate

<a id="schemamultistatusresultofassetandchilderrortemplate"></a>
<a id="schema_MultiStatusResultOfAssetAndChildErrorTemplate"></a>
<a id="tocSmultistatusresultofassetandchilderrortemplate"></a>
<a id="tocsmultistatusresultofassetandchilderrortemplate"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Reason|string|false|true|None|
|Error|string|false|true|None|
|OperationId|string|false|true|None|
|Data|[[Asset](#schemaasset)]|false|true|None|
|ChildErrors|[[ChildErrorTemplate](#schemachilderrortemplate)]|false|true|None|

```json
{
  "Reason": "string",
  "Error": "string",
  "OperationId": "string",
  "Data": [
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
          "Description": "This is reference to a stream. The stream id is PI_bifrostbigdaddy_1.",
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
|OperationId|string|false|true|None|
|Error|string|false|true|None|
|Resolution|string|false|true|None|
|Reason|string|false|true|None|
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

### MultiStatusResultOfLastStatusDataAndChildErrorTemplate

<a id="schemamultistatusresultoflaststatusdataandchilderrortemplate"></a>
<a id="schema_MultiStatusResultOfLastStatusDataAndChildErrorTemplate"></a>
<a id="tocSmultistatusresultoflaststatusdataandchilderrortemplate"></a>
<a id="tocsmultistatusresultoflaststatusdataandchilderrortemplate"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Reason|string|false|true|None|
|Error|string|false|true|None|
|OperationId|string|false|true|None|
|Data|[[LastStatusData](#schemalaststatusdata)]|false|true|None|
|ChildErrors|[[ChildErrorTemplate](#schemachilderrortemplate)]|false|true|None|

```json
{
  "Reason": "string",
  "Error": "string",
  "OperationId": "string",
  "Data": [
    {
      "Index": null,
      "Status": 0,
      "Value": null,
      "DisplayName": "string",
      "AssetId": "string",
      "DataRetrievalTime": "2019-08-24T14:15:22Z"
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

### DeprecatedResolvedAsset

<a id="schemadeprecatedresolvedasset"></a>
<a id="schema_DeprecatedResolvedAsset"></a>
<a id="tocSdeprecatedresolvedasset"></a>
<a id="tocsdeprecatedresolvedasset"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|None|
|Name|string|false|true|None|
|Description|string|false|true|None|
|AssetTypeId|string|false|true|None|
|AssetTypeName|string|false|true|None|
|Metadata|[[MetadataItem2](#schemametadataitem2)]|false|true|None|
|Streams|[[DeprecatedResolvedStream](#schemadeprecatedresolvedstream)]|false|true|None|
|UnresolvedStreams|[[UnresolvedStream](#schemaunresolvedstream)]|false|true|None|
|Status|[ResolvedStatus](#schemaresolvedstatus)|false|true|None|

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "AssetTypeId": "string",
  "AssetTypeName": "string",
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
  "Streams": [
    {
      "Name": "string",
      "Properties": [
        {
          "Id": "string",
          "IsKey": true,
          "Uom": "string",
          "Order": 0,
          "InterpolationMode": 0,
          "ExtrapolationMode": 0,
          "SdsType": null,
          "Source": null
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
  "Status": {
    "Name": "string",
    "StreamName": "string",
    "StreamPropertyId": "string"
  }
}

```

---

### MetadataItem2

<a id="schemametadataitem2"></a>
<a id="schema_MetadataItem2"></a>
<a id="tocSmetadataitem2"></a>
<a id="tocsmetadataitem2"></a>

#### Properties

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

### DeprecatedResolvedStream

<a id="schemadeprecatedresolvedstream"></a>
<a id="schema_DeprecatedResolvedStream"></a>
<a id="tocSdeprecatedresolvedstream"></a>
<a id="tocsdeprecatedresolvedstream"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|None|
|Properties|[[ResolvedProperty](#schemaresolvedproperty)]|false|true|None|

```json
{
  "Name": "string",
  "Properties": [
    {
      "Id": "string",
      "IsKey": true,
      "Uom": "string",
      "Order": 0,
      "InterpolationMode": 0,
      "ExtrapolationMode": 0,
      "SdsType": {
        "SdsTypeCode": "[",
        "Properties": [
          null
        ]
      },
      "Source": {
        "StreamId": "string",
        "PropertyId": "string"
      }
    }
  ]
}

```

---

### ResolvedProperty

<a id="schemaresolvedproperty"></a>
<a id="schema_ResolvedProperty"></a>
<a id="tocSresolvedproperty"></a>
<a id="tocsresolvedproperty"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|None|
|IsKey|boolean|false|false|None|
|Uom|string|false|true|None|
|Order|int32|false|false|None|
|InterpolationMode|[SdsInterpolationMode](#schemasdsinterpolationmode)|false|false|None|
|ExtrapolationMode|[SdsExtrapolationMode](#schemasdsextrapolationmode)|false|false|None|
|SdsType|[ResolvedSdsType](#schemaresolvedsdstype)|false|true|None|
|Source|[ResolvedSource](#schemaresolvedsource)|false|true|None|

```json
{
  "Id": "string",
  "IsKey": true,
  "Uom": "string",
  "Order": 0,
  "InterpolationMode": 0,
  "ExtrapolationMode": 0,
  "SdsType": {
    "SdsTypeCode": 0,
    "Properties": [
      {
        "Id": "string",
        "Value": null
      }
    ]
  },
  "Source": {
    "StreamId": "string",
    "PropertyId": "string"
  }
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

### ResolvedSdsType

<a id="schemaresolvedsdstype"></a>
<a id="schema_ResolvedSdsType"></a>
<a id="tocSresolvedsdstype"></a>
<a id="tocsresolvedsdstype"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|SdsTypeCode|[SdsTypeCode](#schemasdstypecode)|false|false|None|
|Properties|[[ResolvedEnum](#schemaresolvedenum)]|false|true|None|

```json
{
  "SdsTypeCode": 0,
  "Properties": [
    {
      "Id": "string",
      "Value": null
    }
  ]
}

```

---

### ResolvedEnum

<a id="schemaresolvedenum"></a>
<a id="schema_ResolvedEnum"></a>
<a id="tocSresolvedenum"></a>
<a id="tocsresolvedenum"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|None|
|Value|any|false|true|None|

```json
{
  "Id": "string",
  "Value": null
}

```

---

### ResolvedSource

<a id="schemaresolvedsource"></a>
<a id="schema_ResolvedSource"></a>
<a id="tocSresolvedsource"></a>
<a id="tocsresolvedsource"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|StreamId|string|false|true|None|
|PropertyId|string|false|true|None|

```json
{
  "StreamId": "string",
  "PropertyId": "string"
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

### ResolvedStatus

<a id="schemaresolvedstatus"></a>
<a id="schema_ResolvedStatus"></a>
<a id="tocSresolvedstatus"></a>
<a id="tocsresolvedstatus"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|None|
|StreamName|string|false|true|None|
|StreamPropertyId|string|false|true|None|

```json
{
  "Name": "string",
  "StreamName": "string",
  "StreamPropertyId": "string"
}

```

---

