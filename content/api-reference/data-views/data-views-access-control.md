---
uid: data-views-access-control

---

# Access Control
#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-summaries.yaml#class-dataviewspermissionscontroller

## `List Data Views Access Rights`

<a id="opIdCollectionAccessRights_List Data Views Access Rights"></a>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-summaries.yaml#dataviews-accessrights-get

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/accessrights/dataviews
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#tenantId<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#namespaceId<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#200-dataviews-accessrights-get|
|403|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#403-dataviews-accessrights-get|
|500|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#500-standard-message|

<h4>Example response body</h4>

> 200 Response

```json
null
```

> 403 Response ([ErrorResponse](#schemaerrorresponse))

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

# Access Control
#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-summaries.yaml#class-dataviewspermissionscontroller

## `Get Data Views Access Control List`

<a id="opIdCollectionAcl_Get Data Views Access Control List"></a>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-summaries.yaml#dataviews-acl-get

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/accesscontrol/dataviews
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#tenantId<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#namespaceId<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AccessControlList](#schemaaccesscontrollist)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#200-dataviews-acl-get|
|403|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#403-dataviews-acl-get|
|500|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#500-standard-message|

<h4>Example response body</h4>

> 200 Response

```json
null
```

> 403 Response ([ErrorResponse](#schemaerrorresponse))

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

## `Update Data Views Access Control List`

<a id="opIdCollectionAcl_Update Data Views Access Control List"></a>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-summaries.yaml#dataviews-acl-update.

<h3>Request</h3>

```text 
PUT /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/accesscontrol/dataviews
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#tenantId<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#namespaceId<br/><br/>

<h4>Request Body</h4>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-parameters.yaml#acl<br/>

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
|204|None|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#204-dataviews-acl-update|
|400|string|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#400-standard-message|
|403|string|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#403-dataviews-acl-update|
|500|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#500-standard-message|

# Access Control
#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-summaries.yaml#class-dataviewspermissionscontroller

## `Get Data View Access Control List`

<a id="opIdDataViewsPermissions_Get Data View Access Control List"></a>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-summaries.yaml#dataviews-acl-get

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/accesscontrol
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#tenantId<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#namespaceId<br/><br/>`string id`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#dataViewId<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AccessControlList](#schemaaccesscontrollist)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#200-dataview-acl-get|
|403|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#403-dataview-acl-get|
|404|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#404-dataview-standard-message|
|500|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#500-standard-message|

<h4>Example response body</h4>

> 200 Response

```json
null
```

> 403 Response ([ErrorResponse](#schemaerrorresponse))

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

## `Update Data View Access Control List`

<a id="opIdDataViewsPermissions_Update Data View Access Control List"></a>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-summaries.yaml#dataviews-acl-update

<h3>Request</h3>

```text 
PUT /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/accesscontrol
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#tenantId<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#namespaceId<br/><br/>`string id`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#dataViewId<br/><br/>

<h4>Request Body</h4>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-parameters.yaml#acl<br/>

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
|204|None|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#204-dataview-acl-update|
|400|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#400-standard-message|
|403|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#403-dataview-acl-update|
|404|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#404-dataview-standard-message|
|500|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#500-standard-message|

---

## `Get Data View Owner`

<a id="opIdDataViewsPermissions_Get Data View Owner"></a>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-summaries.yaml#dataview-owner-get

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/owner
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#tenantId<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#namespaceId<br/><br/>`string id`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#dataViewId<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Trustee](#schematrustee)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#200-dataview-owner-get|
|403|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#403-dataview-owner-get|
|404|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#404-dataview-standard-message|
|500|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#500-standard-message|

<h4>Example response body</h4>

> 200 Response

```json
null
```

> 403 Response ([ErrorResponse](#schemaerrorresponse))

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

## `Update Data View Owner`

<a id="opIdDataViewsPermissions_Update Data View Owner"></a>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-summaries.yaml#dataview-owner-update

<h3>Request</h3>

```text 
PUT /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/owner
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#tenantId<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#namespaceId<br/><br/>`string id`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#dataViewId<br/><br/>

<h4>Request Body</h4>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-parameters.yaml#owner<br/>

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
|204|None|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#204-dataviews-owner-update|
|400|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#400-standard-message|
|403|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#403-dataview-owner-update|
|404|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#404-dataview-standard-message|
|500|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#500-standard-message|

---

## `List Data View Access Rights`

<a id="opIdDataViewsPermissions_List Data View Access Rights"></a>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-summaries.yaml#dataview-accessrights-get

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/accessrights
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#tenantId<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#namespaceId<br/><br/>`string id`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#dataViewId<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#200-dataview-accessrights-get|
|403|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#403-standard-message|
|404|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#404-dataview-standard-message|
|500|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#500-standard-message|

<h4>Example response body</h4>

> 200 Response

```json
null
```

> 403 Response ([ErrorResponse](#schemaerrorresponse))

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

