---
uid: virtual-table-sharing-access-control

---

# Access Control

## `List Virtual Table Access Rights`

<a id="opIdCollectionAccessRights_List Virtual Table Access Rights"></a>

Returns the Virtual Table Access Rights.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/accessrights/virtualTables
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Successfully returns the virtual table access rights.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

---

## `List Sharing Table Access Rights`

<a id="opIdCollectionAccessRights_List Sharing Table Access Rights"></a>

Returns the Sharing Table Access Rights.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/accessrights/shares
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Successfully returns the Sharing table access rights.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

# Access Control

## `Get virtualtable Access Control List`

<a id="opIdCollectionAcl_Get virtualtable Access Control List"></a>

Returns the Virtualtable Access Control List

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/accesscontrol/virtualTables
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AccessControlList](#schemaaccesscontrollist)|Successfully retrieved the Virtualtable Access Control List.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

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

## `Update virtualtable Access Control List`

<a id="opIdCollectionAcl_Update virtualtable Access Control List"></a>

Updates the Virtualtable Access Control List

<h3>Request</h3>

```text 
PUT /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/accesscontrol/virtualTables
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>

<h4>Request Body</h4>

Access Control List<br/>

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

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|Successfully updated the Virtualtable Access Control List.|
|400|[ErrorResponse](#schemaerrorresponse)|Bad request.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

---

## `Get Sharing Table Access Control List`

<a id="opIdCollectionAcl_Get Sharing Table Access Control List"></a>

Returns the Sharing Table Access Control List

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/accesscontrol/shares
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AccessControlList](#schemaaccesscontrollist)|Successfully retrieved the Sharing Table Access Control List.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

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

## `Update Sharing Access Control List`

<a id="opIdCollectionAcl_Update Sharing Access Control List"></a>

Updates the Sharing Table Access Control List

<h3>Request</h3>

```text 
PUT /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/accesscontrol/shares
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>

<h4>Request Body</h4>

Access Control List<br/>

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

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|Successfully updated the Sharing Table Access Control List.|
|400|[ErrorResponse](#schemaerrorresponse)|Bad request.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

# Access Control

## `Virtual Table Access Control List 1`

<a id="opIdVirtualTablePermissions_Virtual Table Access Control List 1"></a>

Returns the Virtual Table Access Control List.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/virtualTables/{id}/accesscontrol
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string id`
<br/>Virtual Table identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AccessControlList](#schemaaccesscontrollist)|Successfully retrieved the Virtual Table Access Control List.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|Not Found.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

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

## `Virtual Table Access Control List 2`

<a id="opIdVirtualTablePermissions_Virtual Table Access Control List 2"></a>

Updates the Virtual Table Access Control List.

<h3>Request</h3>

```text 
PUT /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/virtualTables/{id}/accesscontrol
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string id`
<br/>Virtual Table identifier.<br/><br/>

<h4>Request Body</h4>

Access Control List<br/>

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

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AccessControlList](#schemaaccesscontrollist)|Successfully updated the Virtual Table Access Control List.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|None|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

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

## `Get Virtual Table Owner`

<a id="opIdVirtualTablePermissions_Get Virtual Table Owner"></a>

Returns the Virtual Table Owner.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/virtualTables/{id}/owner
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string id`
<br/>Virtual Table identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Trustee](#schematrustee)|Successfully returns the Virtual Table Owner.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|None|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

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

## `Update Virtual Table Owner`

<a id="opIdVirtualTablePermissions_Update Virtual Table Owner"></a>

Updates the Virtual Table Owner.

<h3>Request</h3>

```text 
PUT /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/virtualTables/{id}/owner
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string id`
<br/>Virtual Table identifier.<br/><br/>

<h4>Request Body</h4>

Virtual Table Owner<br/>

```json
{
  "Type": 1,
  "ObjectId": "string",
  "TenantId": "string"
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Trustee](#schematrustee)|Successfully updates the Virtual Table Owner.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|Not Found.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

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

## `List Virtual Table Access Rights`

<a id="opIdVirtualTablePermissions_List Virtual Table Access Rights"></a>

Returns the Virtual Table Access Rights.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/virtualTables/{id}/accessrights
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string id`
<br/>Virtual Table identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Successfully returns the Virtual Table Access Rights.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|Not Found.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

# Access Control

## `Sharing Table Access Control List`

<a id="opIdSharingTablePermissions_Sharing Table Access Control List"></a>

Returns the Sharing Table Access Control List.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/shares/{id}/accesscontrol
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string id`
<br/>Virtual Table identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AccessControlList](#schemaaccesscontrollist)|Successfully retrieved the Sharing Table Access Control List.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|Not Found.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

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

## `Sharing Access Control List`

<a id="opIdSharingTablePermissions_Sharing Access Control List"></a>

Updates the Sharing Table Access Control List.

<h3>Request</h3>

```text 
PUT /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/shares/{id}/accesscontrol
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string id`
<br/>Virtual Table identifier.<br/><br/>

<h4>Request Body</h4>

Access Control List<br/>

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

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AccessControlList](#schemaaccesscontrollist)|Successfully updated the Sharing Table Access Control List.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|Not Found.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

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

## `Get Share Table Owner`

<a id="opIdSharingTablePermissions_Get Share Table Owner"></a>

Returns the Share Table Owner.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/shares/{id}/owner
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string id`
<br/>Virtual Table identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Trustee](#schematrustee)|Successfully returns the Share Table Owner.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|None|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

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

## `Update Share Table Owner`

<a id="opIdSharingTablePermissions_Update Share Table Owner"></a>

Updates the Share Table Owner.

<h3>Request</h3>

```text 
PUT /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/shares/{id}/owner
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string id`
<br/>Virtual Table identifier.<br/><br/>

<h4>Request Body</h4>

Virtual Table Owner<br/>

```json
{
  "Type": 1,
  "ObjectId": "string",
  "TenantId": "string"
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Trustee](#schematrustee)|Successfully updates the Share Table Owner.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|Not Found.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

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

## `List Virtual Table Access Rights`

<a id="opIdSharingTablePermissions_List Virtual Table Access Rights"></a>

Returns the Virtual Table Access Rights.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/shares/{id}/accessrights
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string id`
<br/>Virtual Table identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Successfully returns the Virtual Table Access Rights.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|Not Found.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

---
## Definitions

### ErrorResponse

<a id="schemaerrorresponse"></a>
<a id="schema_ErrorResponse"></a>
<a id="tocSerrorresponse"></a>
<a id="tocserrorresponse"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|false|true|None|
|Error|string|false|true|None|
|Reason|string|false|true|None|
|Resolution|string|false|true|None|
|Parameters|object|false|true|None|
|ChildErrors|object|false|true|None|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  },
  "ChildErrors": {
    "property1": null,
    "property2": null
  }
}

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

