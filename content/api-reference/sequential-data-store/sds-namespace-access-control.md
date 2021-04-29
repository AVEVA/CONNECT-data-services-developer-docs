

# Namespace Access Control

## `Get Quantities Access Control List`

<a id="opIdNamespaceAccessControl_Get Quantities Access Control List"></a>

Gets the default ACL for the Quantities collection. An ETag header is returned, which can be used to prevent modification of the ACL, during a later call to modify the ACL, if the object has already been modified.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/AccessControl/Quantities
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[AccessControlList](#schemaaccesscontrollist)|Returns the default `AccessControlList` for Quantities|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|You are not authorized for this operation|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

#### Example response body
> 200 Response

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

## `Update Quantities Access Control List`

<a id="opIdNamespaceAccessControl_Update Quantities Access Control List"></a>

Updates the default ACL for the Quantities collection.

### Request
```text 
PUT /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/AccessControl/Quantities
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|204|None|No content|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|You are not authorized for this operation|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

#### Example response body
> 400 Response

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  }
}
```

---

## `Patch Quantities Access Control List`

<a id="opIdNamespaceAccessControl_Patch Quantities Access Control List"></a>

Updates the default ACL for the Quantities collection using an RFC 6902 compliant JSON Patch document. This allows the ACL to be modified without submitting the entire Access Control List.

### Request
```text 
PATCH /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/AccessControl/Quantities
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|204|None|No content|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|You are not authorized for this operation|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|412|[ErrorResponseBody](#schemaerrorresponsebody)|Precondition failed|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

#### Example response body
> 400 Response

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  }
}
```

---

## `Get Streams Access Control List`

<a id="opIdNamespaceAccessControl_Get Streams Access Control List"></a>

Gets the default ACL for the Streams collection. An ETag header is returned, which can be used to prevent modification of the ACL, during a later call to modify the ACL, if the object has already been modified.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/AccessControl/Streams
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[AccessControlList](#schemaaccesscontrollist)|Returns the default `AccessControlList` for Streams|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|You are not authorized for this operation|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

#### Example response body
> 200 Response

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

## `Update Streams Access Control List`

<a id="opIdNamespaceAccessControl_Update Streams Access Control List"></a>

Updates the default ACL for the Streams collection.

### Request
```text 
PUT /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/AccessControl/Streams
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|204|None|No content|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|You are not authorized for this operation|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

#### Example response body
> 400 Response

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  }
}
```

---

## `Patch Streams Access Control List`

<a id="opIdNamespaceAccessControl_Patch Streams Access Control List"></a>

Updates the default ACL for the Streams collection using an RFC 6902 compliant JSON Patch document. This allows the ACL to be modified without submitting the entire Access Control List.

### Request
```text 
PATCH /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/AccessControl/Streams
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|204|None|No content|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|You are not authorized for this operation|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|412|[ErrorResponseBody](#schemaerrorresponsebody)|Precondition failed|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

#### Example response body
> 400 Response

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  }
}
```

---

## `Get Stream Views Access Control List`

<a id="opIdNamespaceAccessControl_Get Stream Views Access Control List"></a>

Gets the default ACL for the Stream Views collection. An ETag header is returned, which can be used to prevent modification of the ACL, during a later call to modify the ACL, if the object has already been modified.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/AccessControl/StreamViews
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[AccessControlList](#schemaaccesscontrollist)|Returns the default `AccessControlList` for Stream Views|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|You are not authorized for this operation|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

#### Example response body
> 200 Response

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

## `Update Stream Views Access Control List`

<a id="opIdNamespaceAccessControl_Update Stream Views Access Control List"></a>

Updates the default ACL for the Stream Views collection.

### Request
```text 
PUT /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/AccessControl/StreamViews
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|204|None|No content|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|You are not authorized for this operation|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

#### Example response body
> 400 Response

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  }
}
```

---

## `Patch Stream Views Access Control List`

<a id="opIdNamespaceAccessControl_Patch Stream Views Access Control List"></a>

Updates the default ACL for the Stream Views collection using an RFC 6902 compliant JSON Patch document. This allows the ACL to be modified without submitting the entire Access Control List.

### Request
```text 
PATCH /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/AccessControl/StreamViews
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|204|None|No content|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|You are not authorized for this operation|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|412|[ErrorResponseBody](#schemaerrorresponsebody)|Precondition failed|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

#### Example response body
> 400 Response

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  }
}
```

---

## `Get Types Access Control List`

<a id="opIdNamespaceAccessControl_Get Types Access Control List"></a>

Gets the default ACL for the Types collection. An ETag header is returned, which can be used to prevent modification of the ACL, during a later call to modify the ACL, if the object has already been modified.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/AccessControl/Types
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[AccessControlList](#schemaaccesscontrollist)|Returns the default `AccessControlList` for Types|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|You are not authorized for this operation|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

#### Example response body
> 200 Response

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

## `Update Types Access Control List`

<a id="opIdNamespaceAccessControl_Update Types Access Control List"></a>

Updates the default ACL for the Types collection.

### Request
```text 
PUT /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/AccessControl/Types
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|204|None|No content|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|You are not authorized for this operation|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

#### Example response body
> 400 Response

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  }
}
```

---

## `Patch Types Access Control List`

<a id="opIdNamespaceAccessControl_Patch Types Access Control List"></a>

Updates the default ACL for the Types collection using an RFC 6902 compliant JSON Patch document. This allows the ACL to be modified without submitting the entire Access Control List.

### Request
```text 
PATCH /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/AccessControl/Types
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|204|None|No content|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|You are not authorized for this operation|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|412|[ErrorResponseBody](#schemaerrorresponsebody)|Precondition failed|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

#### Example response body
> 400 Response

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  }
}
```

---
## Definitions

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

### ErrorResponseBody

<a id="schemaerrorresponsebody"></a>
<a id="schema_ErrorResponseBody"></a>
<a id="tocSerrorresponsebody"></a>
<a id="tocserrorresponsebody"></a>

Contains the error message format that follows the OCS error standards

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|false|true|Operation unique identifier of action that caused the error|
|Error|string|false|true|Error description|
|Reason|string|false|true|Reason for the error|
|Resolution|string|false|true|Resolution to resolve the error|
|Parameters|object|false|true|IDs or values that are creating or are affected by the error|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  }
}

```

---

