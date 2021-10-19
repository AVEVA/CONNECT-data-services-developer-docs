---
uid: AssetsAPI
---

# Assets API

The Assets API allows you to create, read, update, and delete assets. 

***

## `Get Asset by Id` 
Returns the specified asset and the version Etag in the HTTP response header.

### Request 
``` 
GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}  
```

### Parameters  
`string tenantId`  
Tenant identifier

`string namespaceId`  
Namespace identifier

`string assetId`  
Asset identifier

### Response 

The response includes a status code and a response body. 

| Status Code | Body Type | Description |
|--|--|--|
| 200 OK | `Asset` | The requested asset. |
| 400 Bad Request | error | The request is not valid. See the response body for additional details. |
| 403 Forbidden | error | You are not authorized to view the requested asset. |
| 404 Not Found | error | The asset with the specified identifier is not found. |

#### Example response body
```json 
HTTP 200 OK 
Content-Type: application/json
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
***

## `Get Assets` 
Returns an array of assets and the total number of assets returned, specified as `Total-Count` in the HTTP response header. 

### Request 
```
GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets?skip={skip}&count={count} 
```

### Parameters  
`string tenantId`   
Tenant identifier

`string namespaceId`   
Namespace identifier

[optional] `int skip`   
Optional parameter representing the zero-based offset of the first asset to retrieve. If not specified, a default value of 0 is used.

[optional] `int count`   
Optional parameter, between 1 and 1000 (inclusive), that represents the maximum number of retrieved assets. If not specified, the default is 100.

### Response 
The response includes a status code and a body. 

| Status Code | Body Type | Description |
|--|--|--|
| 200 OK | `Asset[]` | A page of assets. A response header, `Total-Count`, indicates the total size of the collection. |
| 204 No Content | none | No assets were found or you do not have permission to view assets. |
| 400 Bad Request | error | The request is not valid. See the response body for additional details. |
| 503 Service Unavailable | error | An error occurred while processing the request. See the response body for additional details. |

***

## `Create Asset` 
Creates a new asset with a specified `Id`. 

### Request 
```text 
POST api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId} 
```

### Parameters  
`string tenantId`   
Tenant identifier

`string namespaceId`   
Namespace identifier

`string assetId`  
Asset identifier


#### Request body 
An `asset` object

#### Example request body 
**NOTE:** To create an asset with a specific `Id`, use the API route with `Id`. If this is used, you must specify a matching `Id` field for the asset object in the JSON object below.

```json 
{
    "Name": "HeaterOnFirstFloor",
    "Description": "This is Asset which represents a heater on the first floor.",
    "Metadata": [
        {
            "Id": "c0e29698-d157-4288-9dea-db290de1fb35",
            "Name": "ModelNumber",
            "Description": "This is attribute with double value representing the model number.",
            "SdsTypeCode": "Double",
            "Value": 1.3
        }
    ],
    "StreamReferences": [
        {
            "Id": "a1b1c2cc-0a1d-4d89-b53e-e7db746bb4d2",
            "Name": "Data",
            "Description": "This is reference to a stream. The stream has data coming from a heater.",
            "StreamId": "heaterData_1"
        }
    ]
}
```
### Response 

The response includes a status code, a body, and the Etag version in the HTTP response header.

| Status Code               | Body Type | Description                                     |
| ------------------------- | --------- | ----------------------------------------------- |
| 200 OK                    | `Asset`  | The asset as persisted, including values for optional parameters that were omitted in the request.                           |
| 302 Found | Redirect | The asset you attempted to create is identical to one that already exists |
| 400 Bad Request           | error     | The request is not valid. See the response body for additional details.      |
| 403 Forbidden            | error     | You are not authorized to create assets.           |
| 409 Conflict | error     | The asset you attempted to create has a conflict. See the response body for additional details. |

***

## `Create Assets (Bulk create)` 

Creates multiple assets in a single call.

### Request 

```text 
POST api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/bulk/Assets 
```

### Parameters  

`string tenantId`   
Tenant identifier

`string namespaceId`   
Namespace identifier

#### Request body 

An array of `asset` objects

### Response 

The response includes a status code and a body. 

| Status Code               | Body Type | Description                                     |
| ------------------------- | --------- | ----------------------------------------------- |
| 200 OK                    | `Asset[]`  | An array of assets as persisted, including values for optional parameters that were omitted in the request.                               |
| 207 Multi-Status          | partial success | Array of errors. Assets that did not encounter errors are created. |
| 400 Bad Request           | error     | The request is not valid. The response includes which asset failed validation checks. See the response body for additional details.     |
| 403 Forbidden             | error     | You are not authorized to create assets.           |
| 409 Conflict              | error      | The asset create has a conflict. See the response body for additional details.  |

***

## `Create or Update Asset` 

Creates or updates an asset with a specified `Id`. If the asset already exists, you can specify an `If-Match` property in the HTTP request header to ensure that the asset is modified only if its version matches.

### Request 

```text 
PUT api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId} 
```

### Parameters  

`string tenantId`   
Tenant identifier

`string namespaceId`   
Namespace identifier

`string assetId`  
Asset identifier

#### Request body 

The newly created or updated `asset` object.

### Response 

The response includes a status code, body, and Etag version in the HTTP response header. 

| Status Code              | Body Type | Description                                     |
| -------------------------| --------- | ----------------------------------------------- |
| 200 OK                   | `Asset`  | The newly created or updated asset as persisted, including values for optional parameters that were omitted in the request.                               |
| 400 Bad Request          | error     | The request is not valid. The response includes which asset failed validation checks. See the response body for additional details.    |
| 403 Forbidden            | error     | You are not authorized to update assets. |
| 404 Not Found            | error     | The asset, with the specified identifier, was not found.            |
| 409 Conflict             | error     | The asset update or create has a conflict. See the response body for additional details. |
| 412 Pre-Condition Failed | error     | The asset failed to update because the If-Match condition failed.  |

***

## `Delete Asset` 

Deletes an asset with a specified `Id`. You can include an `If-Match` property in the HTTP request header to specify the asset version. The asset is deleted only if the version matches.

### Request 

```text 
DELETE api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}   
```

### Parameters  

`string tenantId`   
Tenant identifier

`string namespaceId`   
Namespace identifier

`string assetId`  
Asset identifier

#### Request body 

None

### Response 

The response includes a status code and a body.

| Status Code               | Body Type | Description                                     |
| ------------------------- | --------- | ----------------------------------------------- |
| 204 No Content            | none  | The asset with the specified `Id` is deleted.                              |
| 400 Bad Request           | error     | The request is not valid. The response includes which asset failed validation checks. See the response body for additional details.      |
| 403 Forbidden             | error     | You are not authorized to delete this asset.       |
| 404 Not Found             | error     | The asset with the specified `Id` could not be found.  |
| 412 Pre-Condition Failed  | error     | The asset failed to update because the `If-Match` condition failed. |

## `Delete Asset (bulk)`

Deletes all assets with the specified Ids. Use this API to delete up to a maximum of 1000 assets in one API call.

### Request 

```text 
DELETE api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/bulk/Assets?id={assetId_1}[&id={assetId_n}]
```

### Parameters  

`string tenantId`   
Tenant identifier

`string namespaceId`   
Namespace identifier

`string[] id`  
Parameter consisting of the asset Ids that you want to delete.

### Response 

The response includes a status code and a body.

| Status Code               | Body Type | Description                                     |
| ------------------------- | --------- | ----------------------------------------------- |
| 204 No Content            | none  | The assets with the specified `Id`s are deleted.                              |
| 207 Multi-Status | partial success | Array of errors. Assets that did not encounter errors are deleted. |
| 400 Bad Request | error | The request is not valid. See the response body for additional details. |
