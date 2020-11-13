---
uid: AssetOrAssetTypeAccessControlAPI
---

# Asset and AssetType Access Control API
The access control API is used to secure assets by setting their ownership and permissions. For more information about OCS access control, see [Role-based access control][xref:accessControl].

***
## `Get Asset or AssetType Access Control List ` 
Get the default `AccessControlList` for the assets collection and asset type collection.

### Request 

Assets collections

```text 
GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/AccessControl/Assets 

```

Asset types collections

```text 
GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/AccessControl/AssetTypes 

```

### Parameters  
`string tenantId` 

The tenant identifier 

`string namespaceId` 

The namespace identifier 

### Response

The response includes a status code and a body.

| Status Code | Body Type | Description |
|--|--|--|
| 200 OK | `AccessControlList` | The default access control list of the assets collection or asset type collection.
| 403 Forbidden | error | You are not authorized to view the requested asset or asset type collection's access control list. |

#### Example response body
```json 
HTTP 200 OK
{
    "RoleTrusteeAccessControlEntries": [
        {
            "Trustee": {
                "Type": 3,
                "ObjectId": "11111111-1111-1111-1111-111111111111"
            },
            "AccessRights": 3
        },
        {
            "Trustee": {
                "Type": 3,
                "ObjectId": "22222222-2222-2222-1111-111111111111"
            },
            "AccessRights": 1
        },
        {
            "Trustee": {
                "Type": 3,
                "ObjectId": "33333333-3333-3333-1111-111111111111"
            },
            "AccessRights": 15
        }
    ]
} 
```

***

## `Update Assets or AssetType Access Control List` 

Update the default `AccessControlList` for the assets or asset type collections 

### Request 

Assets collections

```text 
PUT api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/AccessControl/Assets  

```

Asset types collections
```text 
PUT api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/AccessControl/AssetTypes  

```

### Parameters  

`string tenantId` 

The tenant identifier 

`string namespaceId` 

The namespace identifier 


#### Request body 

An `AccessControlList`

### Response 

The response includes a status code and, in some instances, a body.

| Status Code               | Body Type | Description                                     |
| ------------------------- | --------- | ----------------------------------------------- |
| 204 No Content                    | (empty)  | Successfully updated the default access control list of the assets collection or asset type collection. |
| 400 Bad Request             | error     | The request is not valid. See the response body for details.       |
| 403 Forbidden             | error     | You are not authorized to update the asset or asset type collection's default access control list. |

***

## `Get Asset or AssetType Access Control List` 

Get the `AssetControlList` of the specified asset or asset type.

### Request 

Assets
```text 
GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/AccessControl 

```

Asset type

```text 
GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetTypeId}/AccessControl 

```


### Parameters  

`string tenantId` 

The tenant identifier 

`string namespaceId` 

The namespace identifier 

`string assetId`

The asset identifier

`string assetTypeId`

The asset type identifier

### Response 

The response includes a status code and a body.

| Status Code               | Body Type | Description                                     |
| ------------------------- | --------- | ----------------------------------------------- |
| 200 OK                    | `AccessControlList`  | The access control list of the requested asset or asset type.           |
| 403 Forbidden             | error     | You are not authorized to view the access control list of the requested asset or asset type. |
| 404 Not Found             | error     | The requested asset or asset type with the specified `Id` was not found. |
| 500 Internal Server Error             | error     | An error occurred while processing the request. See the response body for details.       |

#### Example request body 

```json 
HTTP 200 OK
{
    "RoleTrusteeAccessControlEntries": [
        {
            "Trustee": {
                "Type": 3,
                "ObjectId": "11111111-1111-1111-1111-111111111111"
            },
            "AccessRights": 3
        },
        {
            "Trustee": {
                "Type": 3,
                "ObjectId": "22222222-2222-2222-1111-111111111111"
            }
        }
    ]
}

```
***

## `Update Asset or AssetType Access Control List` 

Update the `AccessControlList` of the specified asset or asset type.

### Request 

Asset

```text 
PUT api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/AccessControl 

```


Asset type

```text 
PUT api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetTypeId}/AccessControl 

```
### Parameters  

`string tenantId` 

The tenant identifier 

`string namespaceId` 

The namespace identifier 

`string assetId`

The asset identifier

`string assetTypeId`

The asset type identifier

#### Request body 

An `AccessControlList`

### Response 

The response includes a status code and, in some instances, a body.

| Status Code               | Body Type | Description                                     |
| ------------------------- | --------- | ----------------------------------------------- |
| 204 No Content                    | (empty)  | Successfully updated the access control list of the specified asset or asset type.            |
| 400 Bad Request             | error     | The request is not valid. See the response body for details.       |
| 403 Forbidden             | error     | You are not authorized to update the access control list of the requested asset or asset type. |
| 404 Not Found             | error     | The requested asset or asset type with the specified `Id` was not found. |

***

## `Get Asset or AssetType Access Rights` 

Get the calling user or client's access rights to the requested asset or asset type.

### Request 

Asset

```text 
GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/AccessRights

```



Asset type

```text 
GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetTypeId}/AccessRights

```


### Parameters  

`string tenantId`  
The tenant identifier 

`string namespaceId`  
The namespace identifier 

`string assetId`  
The asset identifier

`string assetTypeId`  
The asset type identifier

### Response 

The response includes a status code and a body. 

| Status Code   | Body Type | Description                                                  |
| ------------- | --------- | ------------------------------------------------------------ |
| 200 OK        | string[]  | A list of access rights to the requested asset or asset type. |
| 403 Forbidden | error     | You are not authorized to make this request.                 |
| 404 Not Found | error     | The requested asset or asset type with the specified `Id` was not found. |


#### Example response body

```
HTTP 200 OK
[
    "Read",
    "Write",
    "Delete",
    "ManageAccessControl"
]

```
***

## `Get Asset or AssetType Owner` 

Get the owner `Trustee` of the specified asset or asset type.

### Request 

Asset
```text 
GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/owner

```

Asset type

```text 
GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetTypeId}/owner

```



### Parameters  

`string tenantId`  
The tenant identifier 

`string namespaceId`  
The namespace identifier 

`string assetTypeId`  
The asset type identifier

### Response 

The response includes a status code and a body.

| Status Code               | Body Type | Description                                     |
| ------------------------- | --------- | ----------------------------------------------- |
| 200 OK                    | `Trustee`  | The owner of the requested asset or asset type.             |
| 403 Forbidden             | error     | You are not authorized to view the owner of the requested asset or asset type. |
| 404 Not Found             | error     | The requested asset or asset type with the specified `Id` was not found. |

#### Example response body

```json 
HTTP 200 OK
Content-Type: application/json
{
    "Type": 1,
    "TenantId": "55555555-5555-5555-5555-555555555555",
    "ObjectId": "44444444-4444-4444-4444-444444444444"
}

```
***

## `Update Asset or AssetType Owner` 

Update the owner `Trustee` of the specified asset or asset type.

### Request 

Asset

```text 
PUT api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/owner

```



Asset type

```text 
PUT api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/AssetTypes/{assetTypeId}/owner

```

###  Parameters  

`string tenantId`  
The tenant identifier 

`string namespaceId`  
The namespace identifier 

`string assetId`  
The asset identifier

`string assetTypeId`  
The AssetType identifier

#### Request body 

A `Trustee`

#### Example request body 

```json 
{
    "Type": 2,
    "TenantId": "55555555-5555-5555-5555-555555555555",
    "ObjectId": "44444444-4444-4444-4444-444444444444"
}

```

### Response 

The response includes a status code and, in some instances, a body.

| Status Code               | Body Type | Description                                     |
| ------------------------- | --------- | ----------------------------------------------- |
| 204 No Content                    | (empty)  | Successfully updated the asset or asset type owner.            |
| 400 Bad Request            | error     | The request is not valid. See the response body for details.      |
| 403 Forbidden             | error     | You are not authorized to update the owner for the requested asset or asset type. |
| 404 Not Found | error     | The requested asset or asset type with the specified `Id` was not found. |
