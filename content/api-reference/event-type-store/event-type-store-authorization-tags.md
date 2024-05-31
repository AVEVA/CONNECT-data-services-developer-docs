---
uid: event-type-store-authorization-tags

---

# Authorization Tags

## `List Authorization Tags`

<a id="opIdAuthorizationTags_List Authorization Tags"></a>

Returns an array of Authorization Tags in a given namespace and the version ETag in the HTTP response header. The If-Match and If-None-Match headers are supported.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/AuthorizationTags
?skip={skip}&count={count}&includeDeleted={includeDeleted}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>
`[optional] integer skip`
<br/>Parameter representing the zero-based offset of the first object to retrieve.  If unspecified, a default value of 0 is used.<br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of objects to retrieve. If unspecified, a default value of 100 is used.<br/><br/>`[optional] boolean includeDeleted`
<br/>Parameter indicating whether to include soft-deleted Authorization Tags. If unspecified, a default value of false is used.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AuthorizationTag](#schemaauthorizationtag)[]|Success.|
|400|[AdhErrorResponse](#schemaadherrorresponse)|Missing or invalid inputs.|
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|

<h4>Example response body</h4>

> 200 Response

```json
[
  {
    "Id": "SimpleAuthorizationTag",
    "State": "Active",
    "CreatedDate": "0001-01-01T00:00:00Z",
    "ModifiedDate": "0001-01-01T00:00:00Z",
    "Description": "This is a simple authorization tag"
  },
  {
    "Id": "SimpleAuthorizationTag",
    "State": "Active",
    "CreatedDate": "0001-01-01T00:00:00Z",
    "ModifiedDate": "0001-01-01T00:00:00Z",
    "Description": "This is a simple authorization tag"
  }
]
```

> 400 Response ([AdhErrorResponse](#schemaadherrorresponse))

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "property1": null,
  "property2": null
}
```

---

## `Get Authorization Tag By Id`

<a id="opIdAuthorizationTags_Get Authorization Tag By Id"></a>

Returns the specified Authorization Tag.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/AuthorizationTags/{id}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>The id of the Authorization Tag.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AuthorizationTag](#schemaauthorizationtag)|Success.|
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|
|404|[AdhErrorResponse](#schemaadherrorresponse)|Authorization Tag not found.|

<h4>Example response body</h4>

> 200 Response

```json
{
  "Id": "SimpleAuthorizationTag",
  "State": "Active",
  "CreatedDate": "0001-01-01T00:00:00Z",
  "ModifiedDate": "0001-01-01T00:00:00Z",
  "Description": "This is a simple authorization tag"
}
```

> 403 Response ([AdhErrorResponse](#schemaadherrorresponse))

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "property1": null,
  "property2": null
}
```

---

## `Get Or Create Authorization Tag`

<a id="opIdAuthorizationTags_Get Or Create Authorization Tag"></a>

Creates a new Authorization Tag or returns the current one if the body is equivalent to what is stored.

<h3>Request</h3>

```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/AuthorizationTags/{id}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>The id of the Authorization Tag.<br/><br/>

<h4>Request Body</h4>

An AuthorizationTag.<br/>

```json
{
  "Id": "SimpleAuthorizationTag",
  "State": "Active",
  "CreatedDate": "0001-01-01T00:00:00Z",
  "ModifiedDate": "0001-01-01T00:00:00Z"
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AuthorizationTag](#schemaauthorizationtag)|Success.|
|201|[AuthorizationTag](#schemaauthorizationtag)|Created.|
|302|None|Found.|
|400|[AdhErrorResponse](#schemaadherrorresponse)|Missing or invalid inputs.|
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|
|409|[AdhErrorResponse](#schemaadherrorresponse)|Conflict.|

<h4>Example response body</h4>

> 200 Response

```json
{
  "Id": "SimpleAuthorizationTag",
  "State": "Active",
  "CreatedDate": "0001-01-01T00:00:00Z",
  "ModifiedDate": "0001-01-01T00:00:00Z",
  "Description": "This is a simple authorization tag"
}
```

> 201 Response

```json
{
  "Id": "SimpleAuthorizationTag",
  "State": "Active",
  "CreatedDate": "0001-01-01T00:00:00Z",
  "ModifiedDate": "0001-01-01T00:00:00Z",
  "Description": "This is a simple authorization tag"
}
```

> 400 Response ([AdhErrorResponse](#schemaadherrorresponse))

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "property1": null,
  "property2": null
}
```

---

## `Create Or Update Authorization Tag`

<a id="opIdAuthorizationTags_Create Or Update Authorization Tag"></a>

Creates a new Authorization Tag or updates an existing Authorization Tag.

<h3>Request</h3>

```text 
PUT /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/AuthorizationTags/{id}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>The id of the Authorization Tag.<br/><br/>

<h4>Request Body</h4>

An AuthorizationTag.<br/>

```json
{
  "Id": "SimpleAuthorizationTag",
  "State": "Active",
  "CreatedDate": "0001-01-01T00:00:00Z",
  "ModifiedDate": "0001-01-01T00:00:00Z"
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AuthorizationTag](#schemaauthorizationtag)|Success.|
|201|[AuthorizationTag](#schemaauthorizationtag)|Created.|
|400|[AdhErrorResponse](#schemaadherrorresponse)|Missing or invalid inputs.|
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|

<h4>Example response body</h4>

> 200 Response

```json
{
  "Id": "SimpleAuthorizationTag",
  "State": "Active",
  "CreatedDate": "0001-01-01T00:00:00Z",
  "ModifiedDate": "0001-01-01T00:00:00Z",
  "Description": "This is a simple authorization tag"
}
```

> 201 Response

```json
{
  "Id": "SimpleAuthorizationTag",
  "State": "Active",
  "CreatedDate": "0001-01-01T00:00:00Z",
  "ModifiedDate": "0001-01-01T00:00:00Z",
  "Description": "This is a simple authorization tag"
}
```

> 400 Response ([AdhErrorResponse](#schemaadherrorresponse))

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "property1": null,
  "property2": null
}
```

---

## `Delete Authorization Tag`

<a id="opIdAuthorizationTags_Delete Authorization Tag"></a>

Deletes the Authorization Tag.

<h3>Request</h3>

```text 
DELETE /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/AuthorizationTags/{id}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>The id of the Authorization Tag.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|Deleted.|
|304|None|Not modified.|
|400|[AdhErrorResponse](#schemaadherrorresponse)|Missing or invalid inputs.|
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|
|404|[AdhErrorResponse](#schemaadherrorresponse)|Authorization Tag not found.|

---

## `Get Authorization Tag Acl By Id`

<a id="opIdAuthorizationTags_Get Authorization Tag Acl By Id"></a>

Returns the `AccessControlList` for the specified Authorization Tag.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/AuthorizationTags/{id}/AccessControl
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>The id of the Authorization Tag.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AccessControlList](#schemaaccesscontrollist)|Success.|
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|
|404|[AdhErrorResponse](#schemaadherrorresponse)|Authorization Tag not found.|

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

## `Update Authorization Tag Acl By Id`

<a id="opIdAuthorizationTags_Update Authorization Tag Acl By Id"></a>

Updates and returns the `AccessControlList` for the specified Authorization Tag.

<h3>Request</h3>

```text 
PUT /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/AuthorizationTags/{id}/AccessControl
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>The id of the Authorization Tag.<br/><br/>

<h4>Request Body</h4>

An AccessControlList.<br/>

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
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|
|404|[AdhErrorResponse](#schemaadherrorresponse)|Authorization Tag not found.|

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

## `Get Authorization Tag Owner By Id`

<a id="opIdAuthorizationTags_Get Authorization Tag Owner By Id"></a>

Returns the `Trustee` for the specified AuthorizationTag.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/AuthorizationTags/{id}/Owner
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>The id of the Authorization Tag.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Trustee](#schematrustee)|Success.|
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|
|404|[AdhErrorResponse](#schemaadherrorresponse)|Authorization Tag not found.|

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

## `Update Event Type Owner By Id`

<a id="opIdAuthorizationTags_Update Event Type Owner By Id"></a>

Updates and returns the `Trustee` for the specified AuthorizationTag.

<h3>Request</h3>

```text 
PUT /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/AuthorizationTags/{id}/Owner
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>The id of the Authorization Tag.<br/><br/>

<h4>Request Body</h4>

A Trustee.<br/>

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
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|
|404|[AdhErrorResponse](#schemaadherrorresponse)|Authorization Tag not found.|

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
## Definitions

### AuthorizationTag

<a id="schemaauthorizationtag"></a>
<a id="schema_AuthorizationTag"></a>
<a id="tocSauthorizationtag"></a>
<a id="tocsauthorizationtag"></a>

Represents an AuthorizationTag object.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|The id which is used in lookup|
|State|[LifeCycleState](#schemalifecyclestate)|false|false|The lifecycle state of this object|
|CreatedDate|date-time|false|true|Date this object was created|
|ModifiedDate|date-time|false|true|The last time this object was modified|
|Description|string|false|true|Description of what this object is|

```json
{
  "Id": "SimpleAuthorizationTag",
  "State": "Active",
  "CreatedDate": "0001-01-01T00:00:00Z",
  "ModifiedDate": "0001-01-01T00:00:00Z",
  "Description": "This is a simple authorization tag"
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

### AdhErrorResponse

<a id="schemaadherrorresponse"></a>
<a id="schema_AdhErrorResponse"></a>
<a id="tocSadherrorresponse"></a>
<a id="tocsadherrorresponse"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|false|true|An optional unique string used to identify an operation|
|Error|string|false|true|Description of the error|
|Reason|string|false|true|Short blurb on why the error occured|
|Resolution|string|false|true|Short blurb on how to fix the error|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "property1": null,
  "property2": null
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

