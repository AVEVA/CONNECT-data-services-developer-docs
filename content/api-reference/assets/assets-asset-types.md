---
uid: assets-asset-types

---

# Asset Types

## `Get Asset Types`

<a id="opIdAssetTypes_Get Asset Types"></a>

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/AssetTypes
?skip={skip}&count={count}&query={query}
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>
`[optional] integer skip`
<br/><br/>`[optional] integer count`
<br/><br/>`[optional] string query`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---

## `Create Asset Types2`

<a id="opIdAssetTypes_Create Asset Types2"></a>

### Request
```text 
POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/AssetTypes
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
  "TypeReferences": [
    {
      "StreamReferenceId": "Reference1",
      "StreamReferenceName": "ReferenceName",
      "TypeId": "PI-Float32"
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
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/AssetTypes/{assetTypeId}
```

#### Parameters

`string assetTypeId`
<br/><br/>`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|None|

---

## `Create Asset Type (Asset Types path)`

<a id="opIdAssetTypes_Create Asset Type (Asset Types path)"></a>

### Request
```text 
POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/AssetTypes/{assetTypeId}
```

#### Parameters

`string assetTypeId`
<br/><br/>`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Request Body

<br/>

```json
{
  "Id": "string",
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
  "TypeReferences": [
    {
      "StreamReferenceId": "Reference1",
      "StreamReferenceName": "ReferenceName",
      "TypeId": "PI-Float32"
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

## `Create Or Update Asset Type (Asset Types path)`

<a id="opIdAssetTypes_Create Or Update Asset Type (Asset Types path)"></a>

### Request
```text 
PUT /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/AssetTypes/{assetTypeId}
```

#### Parameters

`string assetTypeId`
<br/><br/>`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Request Body

<br/>

```json
{
  "Id": "string",
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
  "TypeReferences": [
    {
      "StreamReferenceId": "Reference1",
      "StreamReferenceName": "ReferenceName",
      "TypeId": "PI-Float32"
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

Deletes asset type with a specified identifier.

### Request
```text 
DELETE /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/AssetTypes/{assetTypeId}
?deleteAssets={deleteAssets}
```

#### Parameters

`string assetTypeId`
<br/>Asset type identifier<br/><br/>`string tenantId`
<br/>Tenant identifier<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier<br/><br/><br/>
`[optional] boolean deleteAssets`
<br/>Call should also delete all assets of this asset type. Default is false.<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|204|None|Asset type with specified identifier has been deleted.|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See response body for additional details.|
|401|[ErrorTemplate](#schemaerrortemplate)|Unauthorized<br/>|
|404|[ErrorTemplate](#schemaerrortemplate)|Not Found|
|409|[ErrorTemplate](#schemaerrortemplate)|Conflict. See response body for additional details.|

#### Example response body
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

## `Get Asset Type Acl`

<a id="opIdAssetTypes_Get Asset Type Acl"></a>

Returns access control of the specified asset type.

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/AssetTypes/{assetTypeId}/AccessControl
```

#### Parameters

`string assetTypeId`
<br/>Asset type identifier<br/><br/>`string tenantId`
<br/>Tenant identifier<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier<br/><br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[AccessControlList](#schemaaccesscontrollist)|Access control of the asset with the specified identifier.|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See response body for additional details.|
|401|[ErrorTemplate](#schemaerrortemplate)|Unauthorized|
|404|[ErrorTemplate](#schemaerrortemplate)|Not found|

#### Example response body
> 200 Response

```json
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

## `Update Asset Type Access Control`

<a id="opIdAssetTypes_Update Asset Type Access Control"></a>

Updates access control of the specified asset type.

### Request
```text 
PUT /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/AssetTypes/{assetTypeId}/AccessControl
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier<br/><br/><br/>`string assetTypeId`
<br/>Asset type identifier<br/><br/>

### Request Body

<br/>

```json
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

### Response

|Status Code|Body Type|Description|
|---|---|---|
|204|None|Access control of the asset type with the specified identifier.|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See response body for additional details.|
|401|[ErrorTemplate](#schemaerrortemplate)|Unauthorized|
|404|[ErrorTemplate](#schemaerrortemplate)|Not found|

#### Example response body
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

## `List Asset Type Access Rights`

<a id="opIdAssetTypes_List Asset Type Access Rights"></a>

Returns access rights of specified asset type.

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/AssetTypes/{assetTypeId}/AccessRights
```

#### Parameters

`string assetTypeId`
<br/>Asset type identifier<br/><br/>`string tenantId`
<br/>Tenant identifier<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier<br/><br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Access rights of the asset type with the specified identifier.|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See response body for additional details.|
|401|[ErrorTemplate](#schemaerrortemplate)|Unauthorized|
|404|[ErrorTemplate](#schemaerrortemplate)|Not found|

#### Example response body
> 200 Response

```json
[
  "Read",
  "Write",
  "Delete",
  "ManageAccessControl"
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

## `Get Asset Type Owner`

<a id="opIdAssetTypes_Get Asset Type Owner"></a>

Returns owner of specified asset type.

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/AssetTypes/{assetTypeId}/Owner
```

#### Parameters

`string assetTypeId`
<br/>Asset type identifier<br/><br/>`string tenantId`
<br/>Tenant identifier<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier<br/><br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[Trustee](#schematrustee)|Owner of asset type with the specified identifier.|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See response body for additional details.|
|401|[ErrorTemplate](#schemaerrortemplate)|Unauthorized|
|404|[ErrorTemplate](#schemaerrortemplate)|Not found|

#### Example response body
> 200 Response

```json
{
  "Type": 1,
  "TenantId": "55555555-5555-5555-5555-555555555555",
  "ObjectId": "44444444-4444-4444-4444-444444444444"
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

## `Update Asset Type Owner`

<a id="opIdAssetTypes_Update Asset Type Owner"></a>

Updates owner of specified asset type.

### Request
```text 
PUT /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/AssetTypes/{assetTypeId}/Owner
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier<br/><br/><br/>`string assetTypeId`
<br/>Asset type identifier<br/><br/>

### Request Body

<br/>

```json
{
  "Type": 1,
  "TenantId": "55555555-5555-5555-5555-555555555555",
  "ObjectId": "44444444-4444-4444-4444-444444444444"
}
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|204|None|No content if success.|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See response body for additional details.|
|401|[ErrorTemplate](#schemaerrortemplate)|Unauthorized|
|404|[ErrorTemplate](#schemaerrortemplate)|Not found|

#### Example response body
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

## `List Asset Types2`

<a id="opIdAssetTypes_List Asset Types2"></a>

Returns an array of asset types in a given namespace and the total number of asset types returned, specified as Total-Count in the HTTP response header.

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/AssetTypes2
?skip={skip}&count={count}&query={query}
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier<br/><br/><br/>
`[optional] integer skip`
<br/>Parameter representing the zero-based offset of the first object to retrieve.  If unspecified, a default value of 0 is used.<br/><br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of objects to retrieve. If unspecified, a default value of 100 is used.<br/><br/><br/>`[optional] string query`
<br/>Query identifier<br/><br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[DeprecatedAssetType](#schemadeprecatedassettype)[]|List of assets in the given namespace|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See the response body for additional details.|

#### Response Headers

|Status|Header|Type|Description|
|---|---|---|---|
|200|Total-Count|integer|Total number of asset types in the namespace.|

#### Example response body
> 200 Response

```json
[
  {
    "Id": "HeaterType",
    "Name": "HeaterType",
    "Description": "This is an Asset Type which represents heater asset."
  },
  {
    "Id": "PressureType",
    "Name": "PressureType",
    "Description": "This is an Asset Type which represents pressure asset."
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

## `Create Asset Types`

<a id="opIdAssetTypes_Create Asset Types"></a>

Create or update an asset type with a specified identifier.

### Request
```text 
POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/AssetTypes2
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier<br/><br/><br/>

### Request Body

<br/>

```json
{
  "Id": "SampleAssetType",
  "Description": "This is a sample asset type.",
  "Metadata": [
    {
      "Id": "fbd82b97-d29e-4022-968e-f8492cf86644",
      "Name": "ModelNumber",
      "Description": "This is a static attribute on the asset which represents the model number.",
      "SdsTypeCode": "Double",
      "Value": 0.01
    }
  ],
  "TypeReferences": [
    {
      "StreamReferenceId": "f1bf9da2-3858-4bcd-bf93-e7c26ab0d28e",
      "StreamReferenceName": "ReferenceName",
      "TypeId": "PI-Float32"
    }
  ]
}
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[AssetType](#schemaassettype)|The asset with the specified identifier.|
|201|[AssetType](#schemaassettype)|The asset with the specified identifier.|
|302|None|Asset type already exists.|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See response body for additional details.|
|409|[ErrorTemplate](#schemaerrortemplate)|Conflict. See response body for additional details.|

#### Response Headers

|Status|Header|Type|Description|
|---|---|---|---|
|200|Etag|integer|Version|
|201|Etag|integer|Version|

#### Example response body
> 200 Response

```json
{
  "Id": "SampleAssetType",
  "Description": "This is a sample asset type.",
  "Metadata": [
    {
      "Id": "fbd82b97-d29e-4022-968e-f8492cf86644",
      "Name": "ModelNumber",
      "Description": "This is a static attribute on the asset which represents the model number.",
      "SdsTypeCode": "Double",
      "Value": 0.01
    }
  ],
  "TypeReferences": [
    {
      "StreamReferenceId": "f1bf9da2-3858-4bcd-bf93-e7c26ab0d28e",
      "StreamReferenceName": "ReferenceName",
      "TypeId": "PI-Float32"
    }
  ]
}
```

> 201 Response

```json
{
  "Id": "SampleAssetType",
  "Description": "This is a sample asset type.",
  "Metadata": [
    {
      "Id": "fbd82b97-d29e-4022-968e-f8492cf86644",
      "Name": "ModelNumber",
      "Description": "This is a static attribute on the asset which represents the model number.",
      "SdsTypeCode": "Double",
      "Value": 0.01
    }
  ],
  "TypeReferences": [
    {
      "StreamReferenceId": "f1bf9da2-3858-4bcd-bf93-e7c26ab0d28e",
      "StreamReferenceName": "ReferenceName",
      "TypeId": "PI-Float32"
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

## `List Asset Type2`

<a id="opIdAssetTypes_List Asset Type2"></a>

Returns an array of asset types in a given namespace and the total number of asset types returned, specified as Total-Count in the HTTP response header.

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/AssetTypes2/{assetTypeId}
```

#### Parameters

`string assetTypeId`
<br/><br/>`string tenantId`
<br/>Tenant identifier<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier<br/><br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[DeprecatedAssetType](#schemadeprecatedassettype)[]|List of assets in the given namespace.|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See the response body for additional details.|
|404|[ErrorTemplate](#schemaerrortemplate)|Not found|

#### Response Headers

|Status|Header|Type|Description|
|---|---|---|---|
|200|Etag|integer|Version|

#### Example response body
> 200 Response

```json
{
  "Id": "HeaterType",
  "Name": "HeaterType",
  "Description": "This is an Asset Type which represents heater asset."
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

## `Create Asset Type (Asset Types2 path)`

<a id="opIdAssetTypes_Create Asset Type (Asset Types2 path)"></a>

Creates or updates an asset type with a specified identifier.

### Request
```text 
POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/AssetTypes2/{assetTypeId}
```

#### Parameters

`string assetTypeId`
<br/>Asset type identifier<br/><br/>`string tenantId`
<br/>Tenant identifier<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier<br/><br/><br/>

### Request Body

<br/>

```json
{
  "Id": "SampleAssetType",
  "Description": "This is a sample asset type.",
  "Metadata": [
    {
      "Id": "fbd82b97-d29e-4022-968e-f8492cf86644",
      "Name": "ModelNumber",
      "Description": "This is a static attribute on the asset which represents the model number.",
      "SdsTypeCode": "Double",
      "Value": 0.01
    }
  ],
  "TypeReferences": [
    {
      "StreamReferenceId": "f1bf9da2-3858-4bcd-bf93-e7c26ab0d28e",
      "StreamReferenceName": "ReferenceName",
      "TypeId": "PI-Float32"
    }
  ]
}
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[AssetType](#schemaassettype)|The asset with the specified identifier.|
|201|[AssetType](#schemaassettype)|The asset with the specified identifier.|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See response body for additional details.|
|409|[ErrorTemplate](#schemaerrortemplate)|Conflict. See response body for additional details.|
|412|[ErrorTemplate](#schemaerrortemplate)|Pre-Condition Failed. See response body for additional details.|

#### Response Headers

|Status|Header|Type|Description|
|---|---|---|---|
|200|Etag|integer|Version|
|201|Etag|integer|Version|

#### Example response body
> 200 Response

```json
{
  "Id": "SampleAssetType",
  "Description": "This is a sample asset type.",
  "Metadata": [
    {
      "Id": "fbd82b97-d29e-4022-968e-f8492cf86644",
      "Name": "ModelNumber",
      "Description": "This is a static attribute on the asset which represents the model number.",
      "SdsTypeCode": "Double",
      "Value": 0.01
    }
  ],
  "TypeReferences": [
    {
      "StreamReferenceId": "f1bf9da2-3858-4bcd-bf93-e7c26ab0d28e",
      "StreamReferenceName": "ReferenceName",
      "TypeId": "PI-Float32"
    }
  ]
}
```

> 201 Response

```json
{
  "Id": "SampleAssetType",
  "Description": "This is a sample asset type.",
  "Metadata": [
    {
      "Id": "fbd82b97-d29e-4022-968e-f8492cf86644",
      "Name": "ModelNumber",
      "Description": "This is a static attribute on the asset which represents the model number.",
      "SdsTypeCode": "Double",
      "Value": 0.01
    }
  ],
  "TypeReferences": [
    {
      "StreamReferenceId": "f1bf9da2-3858-4bcd-bf93-e7c26ab0d28e",
      "StreamReferenceName": "ReferenceName",
      "TypeId": "PI-Float32"
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

## `Create Or Update Asset Type (Asset Types2 path)`

<a id="opIdAssetTypes_Create Or Update Asset Type (Asset Types2 path)"></a>

Creates or updates an asset type with a specified identifier.

### Request
```text 
PUT /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/AssetTypes2/{assetTypeId}
```

#### Parameters

`string assetTypeId`
<br/>Asset type identifier<br/><br/>`string tenantId`
<br/>Tenant identifier<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier<br/><br/><br/>

### Request Body

<br/>

```json
{
  "Id": "TracerAssetType",
  "Name": "TracerAssetType",
  "Description": "This is an asset type which represents a tracer unit.",
  "Metadata": [
    {
      "Id": "ModelNumber",
      "Name": "ModelNumber",
      "SdsTypeCode": "Double"
    }
  ]
}
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[AssetType](#schemaassettype)|Asset type with specified identifier|
|201|[AssetType](#schemaassettype)|Asset type with specified identifier|
|400|[ErrorTemplate](#schemaerrortemplate)|The request is not valid. See the response body for additional details.|
|409|[ErrorTemplate](#schemaerrortemplate)|Conflict|
|412|[ErrorTemplate](#schemaerrortemplate)|Pre-Condition Failed|
|500|None|Internal Service Error, please try again later.|
|503|None|Service Unavailable, please try again later.|

#### Response Headers

|Status|Header|Type|Description|
|---|---|---|---|
|200|Etag|integer|Version|
|201|Etag|integer|Version|

#### Example response body
> 200 Response

```json
{
  "Id": "SampleAssetType",
  "Description": "This is a sample asset type.",
  "Metadata": [
    {
      "Id": "fbd82b97-d29e-4022-968e-f8492cf86644",
      "Name": "ModelNumber",
      "Description": "This is a static attribute on the asset which represents the model number.",
      "SdsTypeCode": "Double",
      "Value": 0.01
    }
  ],
  "TypeReferences": [
    {
      "StreamReferenceId": "f1bf9da2-3858-4bcd-bf93-e7c26ab0d28e",
      "StreamReferenceName": "ReferenceName",
      "TypeId": "PI-Float32"
    }
  ]
}
```

> 201 Response

```json
{
  "Id": "SampleAssetType",
  "Description": "This is a sample asset type.",
  "Metadata": [
    {
      "Id": "fbd82b97-d29e-4022-968e-f8492cf86644",
      "Name": "ModelNumber",
      "Description": "This is a static attribute on the asset which represents the model number.",
      "SdsTypeCode": "Double",
      "Value": 0.01
    }
  ],
  "TypeReferences": [
    {
      "StreamReferenceId": "f1bf9da2-3858-4bcd-bf93-e7c26ab0d28e",
      "StreamReferenceName": "ReferenceName",
      "TypeId": "PI-Float32"
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

## `Create Asset Types4`

<a id="opIdAssetTypes_Create Asset Types4"></a>

### Request
```text 
POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Bulk/AssetTypes
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
    "TypeReferences": [
      {
        "StreamReferenceId": "Reference1",
        "StreamReferenceName": "ReferenceName",
        "TypeId": "PI-Float32"
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

## `Create Asset Types3`

<a id="opIdAssetTypes_Create Asset Types3"></a>

Bulk creates asset types. Creates multiple asset types in a single call.

### Request
```text 
POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Bulk/AssetTypes2
```

#### Parameters

`string tenantId`
<br/>Tenant identifier<br/><br/><br/>`string namespaceId`
<br/>Namespace identifier<br/><br/><br/>

### Request Body

List of asset types you want to create.<br/>

```json
[
  {
    "Id": "FirstAssetTypeToCreate",
    "Name": "FirstAssetTypeToCreate",
    "Description": "This is the first Asset type to create in this bulk call."
  },
  {
    "Id": "SecondAssetTypeToCreate",
    "Name": "SecondAssetTypeToCreate",
    "Description": "This is the second Asset type to create in this bulk call.",
    "Metadata": [
      {
        "Id": "FirstMetdataOfTheSecondAssetType",
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
|200|[AssetType](#schemaassettype)[]|Asset types that were created.|
|207|[MultiStatusResultOfAssetTypeAndChildErrorTemplate](#schemamultistatusresultofassettypeandchilderrortemplate)|Asset types that were created.|
|400|[ErrorTemplate](#schemaerrortemplate)|Request is not valid. See response body for additional details.|

#### Example response body
> 200 Response

```json
[
  {
    "Id": "HeaterAssetType",
    "Name": "HeaterAssetType",
    "Description": "This is an asset type which represents heaters",
    "Metadata": [
      {
        "Id": "ModelNumber",
        "Name": "ModelNumber",
        "Description": "This is attribute with double value representing the model number.",
        "SdsTypeCode": "Double"
      }
    ]
  },
  {
    "Id": "TracerAssetType",
    "Name": "TracerAssetType",
    "Description": "This is an asset type which represents a tracer unit.",
    "Metadata": [
      {
        "Id": "ModelNumber",
        "Name": "ModelNumber",
        "SdsTypeCode": "Double"
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
      "Id": "SampleAssetType",
      "Description": "This is a sample asset type.",
      "Metadata": [
        {
          "Id": "fbd82b97-d29e-4022-968e-f8492cf86644",
          "Name": "ModelNumber",
          "Description": "This is a static attribute on the asset which represents the model number.",
          "SdsTypeCode": "Double",
          "Value": 0.01
        }
      ],
      "TypeReferences": [
        {
          "StreamReferenceId": "f1bf9da2-3858-4bcd-bf93-e7c26ab0d28e",
          "StreamReferenceName": "ReferenceName",
          "TypeId": "PI-Float32"
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
## Definitions

### DeprecatedAssetType

<a id="schemadeprecatedassettype"></a>
<a id="schema_DeprecatedAssetType"></a>
<a id="tocSdeprecatedassettype"></a>
<a id="tocsdeprecatedassettype"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|None|
|Name|string|false|true|None|
|Description|string|false|true|None|
|Metadata|[[MetadataItem](#schemametadataitem)]|false|true|[An asset or asset type metadata is static information associated with a given asset. A given metadata contains a list of individual metadata values. There is no limit on the number of metadata values defined by an asset. An asset or asset type metadata does not stand alone. It must be specified within an asset or asset type object and, therefore, there are no direct API routes to asset or asset type metadata.]|
|TypeReferences|[[TypeReference](#schematypereference)]|false|true|[An asset type type reference represents dynamic stream data associated with an asset. The references must either be an SDS stream or an SDS stream view. Asset-centric data routes provide direct access to dynamic data for a given asset. There are no limitations on the number of references an asset may contain. However, an asset cannot contain multiple references to the same SDS stream. An asset reference does not stand alone. It must be specified within an asset object and, therefore, asset references do not have direct API routes.]|
|Status|[StatusMapping](#schemastatusmapping)|false|true|None|

```json
{
  "Id": "string",
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
  "TypeReferences": [
    {
      "StreamReferenceId": "Reference1",
      "StreamReferenceName": "ReferenceName",
      "TypeId": "PI-Float32"
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

### TypeReference

<a id="schematypereference"></a>
<a id="schema_TypeReference"></a>
<a id="tocStypereference"></a>
<a id="tocstypereference"></a>

An asset type type reference represents dynamic stream data associated with an asset. The references must either be an SDS stream or an SDS stream view. Asset-centric data routes provide direct access to dynamic data for a given asset. There are no limitations on the number of references an asset may contain. However, an asset cannot contain multiple references to the same SDS stream. An asset reference does not stand alone. It must be specified within an asset object and, therefore, asset references do not have direct API routes.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|StreamReferenceId|string|false|true|The Id for this type reference. If an asset is derived from this asset type, this Id must be referenced in the asset reference type object. This Id must be unique within the asset type.|
|StreamReferenceName|string|false|true|The user friendly name for this type reference.|
|Description|string|false|true|Description text|
|TypeId|string|true|false|This string must be an SDS Type Id.|

```json
{
  "StreamReferenceId": "Reference1",
  "StreamReferenceName": "ReferenceName",
  "TypeId": "PI-Float32"
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
|Status|[StatusEnum](#schemastatusenum)|true|false|Pre-defined asset status values.|
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

### AssetType

<a id="schemaassettype"></a>
<a id="schema_AssetType"></a>
<a id="tocSassettype"></a>
<a id="tocsassettype"></a>

An asset type can be used to create multiple similar assets.A change to the asset type is reflected in all assets that are derived from the asset type.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Asset type id|
|Name|string|false|true|Asset type name|
|Description|string|false|true|Asset type description|
|Metadata|[[MetadataItem](#schemametadataitem)]|false|true|Asset type metadata|
|TypeReferences|[[TypeReference](#schematypereference)]|false|true|Asset type description|
|Status|[StatusConfiguration](#schemastatusconfiguration)|false|true|Asset type status. If an asset of an this asset type, asset type statuses will take precendence over asset status.|

```json
{
  "Id": "SampleAssetType",
  "Description": "This is a sample asset type.",
  "Metadata": [
    {
      "Id": "fbd82b97-d29e-4022-968e-f8492cf86644",
      "Name": "ModelNumber",
      "Description": "This is a static attribute on the asset which represents the model number.",
      "SdsTypeCode": "Double",
      "Value": 0.01
    }
  ],
  "TypeReferences": [
    {
      "StreamReferenceId": "f1bf9da2-3858-4bcd-bf93-e7c26ab0d28e",
      "StreamReferenceName": "ReferenceName",
      "TypeId": "PI-Float32"
    }
  ]
}

```

---

### StatusConfiguration

<a id="schemastatusconfiguration"></a>
<a id="schema_StatusConfiguration"></a>
<a id="tocSstatusconfiguration"></a>
<a id="tocsstatusconfiguration"></a>

Status is a property of an asset or asset type that defines the simple status of an asset or asset type. There is one status property for each asset or asset type. If an asset references an existing asset type and the asset type has a corresponding type reference, then the status mapping on the asset is ignored.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|DefinitionType|[StatusDefinitionType](#schemastatusdefinitiontype)|false|false|Status definition type. At this moment, only "StreamPropertyMapping" is supported.|
|Definition|any|false|true|Status definition|

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

### MultiStatusResultOfAssetTypeAndChildErrorTemplate

<a id="schemamultistatusresultofassettypeandchilderrortemplate"></a>
<a id="schema_MultiStatusResultOfAssetTypeAndChildErrorTemplate"></a>
<a id="tocSmultistatusresultofassettypeandchilderrortemplate"></a>
<a id="tocsmultistatusresultofassettypeandchilderrortemplate"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Reason|string|false|true|None|
|Error|string|false|true|None|
|OperationId|string|false|true|None|
|Data|[[AssetType](#schemaassettype)]|false|true|[An asset type can be used to create multiple similar assets.A change to the asset type is reflected in all assets that are derived from the asset type.]|
|ChildErrors|[[ChildErrorTemplate](#schemachilderrortemplate)]|false|true|None|

```json
{
  "Reason": "string",
  "Error": "string",
  "OperationId": "string",
  "Data": [
    {
      "Id": "SampleAssetType",
      "Description": "This is a sample asset type.",
      "Metadata": [
        {
          "Id": "fbd82b97-d29e-4022-968e-f8492cf86644",
          "Name": "ModelNumber",
          "Description": "This is a static attribute on the asset which represents the model number.",
          "SdsTypeCode": "Double",
          "Value": 0.01
        }
      ],
      "TypeReferences": [
        {
          "StreamReferenceId": "f1bf9da2-3858-4bcd-bf93-e7c26ab0d28e",
          "StreamReferenceName": "ReferenceName",
          "TypeId": "PI-Float32"
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

