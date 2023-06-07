---
uid: event-type-store-enumeration-types

---

# Enumeration Types

## `List Enumerations`

<a id="opIdEnumerations_List Enumerations"></a>

Returns an array of Enumerations in a given namespace and the version ETag in the HTTP response header. The If-Match and If-None-Match headers are supported.

<h3>Request</h3>

```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations
?skip={skip}&count={count}&filter={filter}&includeDeleted={includeDeleted}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>
`[optional] integer skip`
<br/>Parameter representing the zero-based offset of the first object to retrieve.  If unspecified, a default value of 0 is used.<br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of objects to retrieve. If unspecified, a default value of 100 is used.<br/><br/>`[optional] string filter`
<br/><br/>`[optional] boolean includeDeleted`
<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[EventGraphEnumeration](#schemaeventgraphenumeration)[]|Success.|
|304|None|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/common.yaml#304|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|412|[ErrorResponse](#schemaerrorresponse)|Precondition failed.|

<h4>Example response body</h4>

> 200 Response ([EventGraphEnumeration](#schemaeventgraphenumeration)[])

```json
[
  {
    "Name": "string",
    "GraphQLName": "string",
    "Version": 0,
    "Id": "string",
    "State": 0,
    "CreatedDate": "2019-08-24T14:15:22Z",
    "ModifiedDate": "2019-08-24T14:15:22Z",
    "Description": "string",
    "Members": [
      {
        "Name": "string",
        "GraphQLName": "string",
        "Code": 0,
        "State": 0,
        "Description": "string"
      }
    ]
  }
]
```

---

## `Create Enumeration With Server Generated Id`

<a id="opIdEnumerations_Create Enumeration With Server Generated Id"></a>

Creates a new Enumeration. Response includes ETag header.

<h3>Request</h3>

```text 
POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

<h4>Request Body</h4>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/common.yaml#eventGraphEnumerationDto<br/>

```json
{
  "Id": "SimpleEnumeration",
  "Name": "SimpleEnumeration",
  "Members": [
    {
      "Name": "ACTIVE",
      "Code": 0
    },
    {
      "Name": "CLOSED",
      "Code": 1
    }
  ]
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|201|[EventGraphEnumeration](#schemaeventgraphenumeration)|Created.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|

<h4>Example response body</h4>

> 201 Response ([EventGraphEnumeration](#schemaeventgraphenumeration))

```json
{
  "Name": "string",
  "GraphQLName": "string",
  "Version": 0,
  "Id": "string",
  "State": 0,
  "CreatedDate": "2019-08-24T14:15:22Z",
  "ModifiedDate": "2019-08-24T14:15:22Z",
  "Description": "string",
  "Members": [
    {
      "Name": "string",
      "GraphQLName": "string",
      "Code": 0,
      "State": 0,
      "Description": "string"
    }
  ]
}
```

---

## `Get Enumeration By Id`

<a id="opIdEnumerations_Get Enumeration By Id"></a>

Returns the specified Enumeration and the version ETag in the HTTP response header. The If-Match and If-None-Match headers are supported.

<h3>Request</h3>

```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations/{id}
?includeDeleted={includeDeleted}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>Unordered list of identifiers for all clients to get. Empty or whitespace identifiers will be ignored.<br/><br/>
`[optional] boolean includeDeleted`
<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[EventGraphEnumeration](#schemaeventgraphenumeration)|Success.|
|304|None|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/common.yaml#304|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Client or tenant not found.|
|412|[ErrorResponse](#schemaerrorresponse)|Precondition failed.|

<h4>Example response body</h4>

> 200 Response ([EventGraphEnumeration](#schemaeventgraphenumeration))

```json
{
  "Name": "string",
  "GraphQLName": "string",
  "Version": 0,
  "Id": "string",
  "State": 0,
  "CreatedDate": "2019-08-24T14:15:22Z",
  "ModifiedDate": "2019-08-24T14:15:22Z",
  "Description": "string",
  "Members": [
    {
      "Name": "string",
      "GraphQLName": "string",
      "Code": 0,
      "State": 0,
      "Description": "string"
    }
  ]
}
```

---

## `Get Or Create Enumeration`

<a id="opIdEnumerations_Get Or Create Enumeration"></a>

Creates a new Enumeration or returns the current one if the body is equivalent to what is stored. Response includes ETag header.

<h3>Request</h3>

```text 
POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations/{id}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>Unordered list of identifiers for all clients to get. Empty or whitespace identifiers will be ignored.<br/><br/>

<h4>Request Body</h4>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/common.yaml#eventGraphEnumerationDto<br/>

```json
{
  "Id": "SimpleEnumeration",
  "Name": "SimpleEnumeration",
  "Members": [
    {
      "Name": "ACTIVE",
      "Code": 0
    },
    {
      "Name": "CLOSED",
      "Code": 1
    }
  ]
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[EventGraphEnumeration](#schemaeventgraphenumeration)|Success.|
|201|[EventGraphEnumeration](#schemaeventgraphenumeration)|Created.|
|302|None|Found.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|409|[ErrorResponse](#schemaerrorresponse)|Found.|

<h4>Example response body</h4>

> 200 Response ([EventGraphEnumeration](#schemaeventgraphenumeration))

```json
{
  "Name": "string",
  "GraphQLName": "string",
  "Version": 0,
  "Id": "string",
  "State": 0,
  "CreatedDate": "2019-08-24T14:15:22Z",
  "ModifiedDate": "2019-08-24T14:15:22Z",
  "Description": "string",
  "Members": [
    {
      "Name": "string",
      "GraphQLName": "string",
      "Code": 0,
      "State": 0,
      "Description": "string"
    }
  ]
}
```

---

## `Create Or Update Enumeration`

<a id="opIdEnumerations_Create Or Update Enumeration"></a>

Creates a new Enumeration or updates an existing and adds its Etag in the HTTP response header. The If-Match header is supported.

<h3>Request</h3>

```text 
PUT /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations/{id}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>Unordered list of identifiers for all clients to get. Empty or whitespace identifiers will be ignored.<br/><br/>

<h4>Request Body</h4>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/common.yaml#eventGraphEnumerationDto<br/>

```json
{
  "Id": "SimpleEnumeration",
  "Name": "SimpleEnumeration",
  "Members": [
    {
      "Name": "ACTIVE",
      "Code": 0
    },
    {
      "Name": "CLOSED",
      "Code": 1
    }
  ]
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[EventGraphEnumeration](#schemaeventgraphenumeration)|Success.|
|201|[EventGraphEnumeration](#schemaeventgraphenumeration)|Created.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|412|[ErrorResponse](#schemaerrorresponse)|Precondition failed.|

<h4>Example response body</h4>

> 200 Response ([EventGraphEnumeration](#schemaeventgraphenumeration))

```json
{
  "Name": "string",
  "GraphQLName": "string",
  "Version": 0,
  "Id": "string",
  "State": 0,
  "CreatedDate": "2019-08-24T14:15:22Z",
  "ModifiedDate": "2019-08-24T14:15:22Z",
  "Description": "string",
  "Members": [
    {
      "Name": "string",
      "GraphQLName": "string",
      "Code": 0,
      "State": 0,
      "Description": "string"
    }
  ]
}
```

---

## `Delete Enumeration By Id`

<a id="opIdEnumerations_Delete Enumeration By Id"></a>

Deletes the Enumeration.

<h3>Request</h3>

```text 
DELETE /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations/{id}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>Unordered list of identifiers for all clients to get. Empty or whitespace identifiers will be ignored.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|Deleted.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Client or tenant not found.|

---

## `Bulk Create Enumeration`

<a id="opIdEnumerations_Bulk Create Enumeration"></a>

Creates multiple new Enumeration and returns a list of any errors along with the created objects. Response includes ETag header.

<h3>Request</h3>

```text 
POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Bulk/Enumerations
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

<h4>Request Body</h4>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/common.yaml#eventGraphEnumerationDto<br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[EventGraphEnumeration](#schemaeventgraphenumeration)|Success.|
|207|[ErrorResponse](#schemaerrorresponse)|Partial.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|

<h4>Example response body</h4>

> 200 Response ([EventGraphEnumeration](#schemaeventgraphenumeration))

```json
{
  "Name": "string",
  "GraphQLName": "string",
  "Version": 0,
  "Id": "string",
  "State": 0,
  "CreatedDate": "2019-08-24T14:15:22Z",
  "ModifiedDate": "2019-08-24T14:15:22Z",
  "Description": "string",
  "Members": [
    {
      "Name": "string",
      "GraphQLName": "string",
      "Code": 0,
      "State": 0,
      "Description": "string"
    }
  ]
}
```

---

## `Get Enumeration Acl By Id`

<a id="opIdEnumerations_Get Enumeration Acl By Id"></a>

Returns the `AccessControlList` for the specified Enumeration.

<h3>Request</h3>

```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations/{id}/AccessControl
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>Unordered list of identifiers for all clients to get. Empty or whitespace identifiers will be ignored.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AccessControlList](#schemaaccesscontrollist)|Success.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Client or tenant not found.|

<h4>Example response body</h4>

> 200 Response ([AccessControlList](#schemaaccesscontrollist))

```json
{
  "RoleTrusteeAccessControlEntries": [
    {
      "Trustee": {
        "Type": 1,
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

## `Update Enumeration Acl By Id`

<a id="opIdEnumerations_Update Enumeration Acl By Id"></a>

Updates and returns the `AccessControlList` for the specified Enumeration.

<h3>Request</h3>

```text 
PUT /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations/{id}/AccessControl
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>Unordered list of identifiers for all clients to get. Empty or whitespace identifiers will be ignored.<br/><br/>

<h4>Request Body</h4>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/common.yaml#accessControlList<br/>

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
      },
      "AccessRights": 15
    }
  ]
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AccessControlList](#schemaaccesscontrollist)|Success.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Client or tenant not found.|

<h4>Example response body</h4>

> 200 Response ([AccessControlList](#schemaaccesscontrollist))

```json
{
  "RoleTrusteeAccessControlEntries": [
    {
      "Trustee": {
        "Type": 1,
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

## `Get Enumeration Owner By Id`

<a id="opIdEnumerations_Get Enumeration Owner By Id"></a>

Returns the `Trustee` for the specified Enumeration.

<h3>Request</h3>

```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations/{id}/Owner
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>Unordered list of identifiers for all clients to get. Empty or whitespace identifiers will be ignored.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Trustee](#schematrustee)|Success.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Client or tenant not found.|

<h4>Example response body</h4>

> 200 Response ([Trustee](#schematrustee))

```json
{
  "Type": 1,
  "ObjectId": "string",
  "TenantId": "string"
}
```

---

## `Update Enumeration Owner By Id`

<a id="opIdEnumerations_Update Enumeration Owner By Id"></a>

Updates and returns the `Trustee` for the specified Enumeration.

<h3>Request</h3>

```text 
PUT /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations/{id}/Owner
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>Unordered list of identifiers for all clients to get. Empty or whitespace identifiers will be ignored.<br/><br/>

<h4>Request Body</h4>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/common.yaml#owner<br/>

```json
{
  "Type": 1,
  "TenantId": "55555555-5555-5555-5555-555555555555",
  "ObjectId": "44444444-4444-4444-4444-444444444444"
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Trustee](#schematrustee)|Success.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Client or tenant not found.|

<h4>Example response body</h4>

> 200 Response ([Trustee](#schematrustee))

```json
{
  "Type": 1,
  "ObjectId": "string",
  "TenantId": "string"
}
```

---

## `List Enumeration Access Rights By Id`

<a id="opIdEnumerations_List Enumeration Access Rights By Id"></a>

Returns a list of `CommonAccessRights` for the specified Enumeration.

<h3>Request</h3>

```text 
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations/{id}/AccessRights
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>Unordered list of identifiers for all clients to get. Empty or whitespace identifiers will be ignored.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Success.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Client or tenant not found.|

---
## Definitions

### EventGraphEnumeration

<a id="schemaeventgraphenumeration"></a>
<a id="schema_EventGraphEnumeration"></a>
<a id="tocSeventgraphenumeration"></a>
<a id="tocseventgraphenumeration"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|None|
|GraphQLName|string|false|true|None|
|Version|int32|false|false|None|
|Id|string|false|true|None|
|State|[LifeCycleState](#schemalifecyclestate)|false|false|None|
|CreatedDate|date-time|false|true|None|
|ModifiedDate|date-time|false|true|None|
|Description|string|false|true|None|
|Members|[[EnumerationState](#schemaenumerationstate)]|false|true|None|

```json
{
  "Name": "string",
  "GraphQLName": "string",
  "Version": 0,
  "Id": "string",
  "State": 0,
  "CreatedDate": "2019-08-24T14:15:22Z",
  "ModifiedDate": "2019-08-24T14:15:22Z",
  "Description": "string",
  "Members": [
    {
      "Name": "string",
      "GraphQLName": "string",
      "Code": 0,
      "State": 0,
      "Description": "string"
    }
  ]
}

```

---

### LifeCycleState

<a id="schemalifecyclestate"></a>
<a id="schema_LifeCycleState"></a>
<a id="tocSlifecyclestate"></a>
<a id="tocslifecyclestate"></a>

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|Active|0|
|Deprecated|1|
|Deleted|2|

---

### EnumerationState

<a id="schemaenumerationstate"></a>
<a id="schema_EnumerationState"></a>
<a id="tocSenumerationstate"></a>
<a id="tocsenumerationstate"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|None|
|GraphQLName|string|false|true|None|
|Code|int32|false|false|None|
|State|[LifeCycleState](#schemalifecyclestate)|false|false|None|
|Description|string|false|true|None|

```json
{
  "Name": "string",
  "GraphQLName": "string",
  "Code": 0,
  "State": 0,
  "Description": "string"
}

```

---

### ErrorResponse

<a id="schemaerrorresponse"></a>
<a id="schema_ErrorResponse"></a>
<a id="tocSerrorresponse"></a>
<a id="tocserrorresponse"></a>

```json
{}

```

---

### AccessControlList

<a id="schemaaccesscontrollist"></a>
<a id="schema_AccessControlList"></a>
<a id="tocSaccesscontrollist"></a>
<a id="tocsaccesscontrollist"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|RoleTrusteeAccessControlEntries|[[AccessControlEntry](#schemaaccesscontrolentry)]|false|true|None|

```json
{
  "RoleTrusteeAccessControlEntries": [
    {
      "Trustee": {
        "Type": 1,
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

<h4>Properties</h4>

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

### Trustee

<a id="schematrustee"></a>
<a id="schema_Trustee"></a>
<a id="tocStrustee"></a>
<a id="tocstrustee"></a>

<h4>Properties</h4>

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

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|User|1|
|Client|2|
|Role|3|

---

### AccessType

<a id="schemaaccesstype"></a>
<a id="schema_AccessType"></a>
<a id="tocSaccesstype"></a>
<a id="tocsaccesstype"></a>

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|Allowed|0|
|Denied|1|

---
