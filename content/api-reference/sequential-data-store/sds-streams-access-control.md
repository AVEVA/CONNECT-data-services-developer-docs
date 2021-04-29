

# Stream Access Control
Controller for access control related methods hosted at Streams/{streamId}/

## `Get Stream Access Control List`

<a id="opIdStreamAccessControl_Get Stream Access Control List"></a>

Returns the ACL of the specified stream.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/AccessControl
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string streamId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[AccessControlList](#schemaaccesscontrollist)|Returns the `AccessControlList`|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
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

## `Update Stream Access Control List`

<a id="opIdStreamAccessControl_Update Stream Access Control List"></a>

Updates the ACL of the specified stream.

### Request
```text 
PUT /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/AccessControl
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string streamId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|204|None|`AccessControlList` was successfully updated|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|409|[ErrorResponseBody](#schemaerrorresponsebody)|Conflict|
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

## `Patch Stream Access Control List`

<a id="opIdStreamAccessControl_Patch Stream Access Control List"></a>

Updates the ACL of the specified stream using an RFC 6902 compliant JSON Patch document. This allows the ACL to be modified without submitting the entire Access Control List.

### Request
```text 
PATCH /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/AccessControl
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string streamId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|204|None|`AccessControlList` was successfully updated|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|409|[ErrorResponseBody](#schemaerrorresponsebody)|Conflict|
|412|[ErrorResponseBody](#schemaerrorresponsebody)|Precondition Failed|
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

## `List Stream Access Rights`

<a id="opIdStreamAccessControl_List Stream Access Rights"></a>

Returns the access rights associated with the specified stream for the requesting identity.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/AccessRights
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string streamId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Returns the `CommonAccessRights`|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
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

## `Get Stream Owner`

<a id="opIdStreamAccessControl_Get Stream Owner"></a>

Returns the Owner of the specified stream.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Owner
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string streamId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[Trustee](#schematrustee)|Returns the `Trustee`|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

#### Example response body
> 200 Response

```json
{
  "Type": 1,
  "ObjectId": "string",
  "TenantId": "string"
}
```

---

## `Update Stream Owner`

<a id="opIdStreamAccessControl_Update Stream Owner"></a>

Updates the Owner of the specified stream.

### Request
```text 
PUT /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Owner
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string streamId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|204|None|`Trustee` was successfully returned|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|409|[ErrorResponseBody](#schemaerrorresponsebody)|Conflict|
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

