---
uid: virtual-table-sharing-sharing

---

# Sharing
The Sharing Asp.net Core controller.

## `List virtual table shares`

<a id="opIdSharing_List virtual table shares"></a>

Returns the List of virtual table shares.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantid}/namespaces/{namespaceid}/shares
?query={query}&orderBy={orderBy}&skip={skip}&count={count}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant Id<br/><br/>`string namespaceId`
<br/>Namespace Id<br/><br/>`string query`
<br/>query<br/><br/>`string orderBy`
<br/>orderBy<br/><br/>
`[optional] integer skip`
<br/>skip<br/><br/>`[optional] integer count`
<br/>count<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[ShareView](#schemashareview)|list of shares|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|Not Found.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

<h4>Example response body</h4>

> 200 Response ([ShareView](#schemashareview))

```json
{
  "id": "string",
  "name": "string",
  "type": "string",
  "virtualTables": [
    {
      "VirtualTableId": "string",
      "VirtualTableName": "string",
      "Status": "string"
    }
  ],
  "externalConfig": {
    "globalMetastoreId": "string",
    "clientId": "string",
    "clientSecret": "string",
    "snowflakeId": "string"
  }
}
```

---

## `Create virtual table share`

<a id="opIdSharing_Create virtual table share"></a>

Created the Virtual Table Share.

<h3>Request</h3>

```text 
POST /api/v1/tenants/{tenantid}/namespaces/{namespaceid}/shares
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant Id<br/><br/>`string namespaceId`
<br/>Namespace Id<br/><br/>

<h4>Request Body</h4>

Virtual table share details<br/>

```json
{
  "id": "string",
  "name": "string",
  "type": "string",
  "virtualTables": [
    {
      "id": "string"
    }
  ],
  "externalConfig": {
    "globalMetastoreId": "string",
    "clientId": "string",
    "clientSecret": "string",
    "snowflakeId": "string"
  },
  "SerializedSecurable": "string",
  "CreatedBy": "string",
  "CreatedOn": "2019-08-24T14:15:22Z"
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|201|[ShareView](#schemashareview)|None|
|400|[ErrorResponse](#schemaerrorresponse)|None|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

<h4>Example response body</h4>

> 201 Response ([ShareView](#schemashareview))

```json
{
  "id": "string",
  "name": "string",
  "type": "string",
  "virtualTables": [
    {
      "VirtualTableId": "string",
      "VirtualTableName": "string",
      "Status": "string"
    }
  ],
  "externalConfig": {
    "globalMetastoreId": "string",
    "clientId": "string",
    "clientSecret": "string",
    "snowflakeId": "string"
  }
}
```

---

## `Get virtual table share`

<a id="opIdSharing_Get virtual table share"></a>

Returns the Virtual Table Share.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantid}/namespaces/{namespaceid}/shares/{id}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant Id<br/><br/>`string namespaceId`
<br/>Namespace Id<br/><br/>`string id`
<br/>Virtual table share Id<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[ShareView](#schemashareview)|Successfully returns the virtual table share.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

<h4>Example response body</h4>

> 200 Response ([ShareView](#schemashareview))

```json
{
  "id": "string",
  "name": "string",
  "type": "string",
  "virtualTables": [
    {
      "VirtualTableId": "string",
      "VirtualTableName": "string",
      "Status": "string"
    }
  ],
  "externalConfig": {
    "globalMetastoreId": "string",
    "clientId": "string",
    "clientSecret": "string",
    "snowflakeId": "string"
  }
}
```

---

## `Update virtual table share`

<a id="opIdSharing_Update virtual table share"></a>

Updated the Virtual Table Share.

<h3>Request</h3>

```text 
PUT /api/v1/tenants/{tenantid}/namespaces/{namespaceid}/shares/{id}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant Id<br/><br/>`string namespaceId`
<br/>Namespace Id<br/><br/>`string id`
<br/>Virtual table share Id<br/><br/>

<h4>Request Body</h4>

Virtual table share details<br/>

```json
{
  "id": "string",
  "name": "string",
  "type": "string",
  "virtualTables": [
    {
      "id": "string"
    }
  ],
  "externalConfig": {
    "globalMetastoreId": "string",
    "clientId": "string",
    "clientSecret": "string",
    "snowflakeId": "string"
  },
  "SerializedSecurable": "string",
  "CreatedBy": "string",
  "CreatedOn": "2019-08-24T14:15:22Z"
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[ShareView](#schemashareview)|Successfully updated the Virtual Table Share.|
|400|[ErrorResponse](#schemaerrorresponse)|None|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

<h4>Example response body</h4>

> 200 Response ([ShareView](#schemashareview))

```json
{
  "id": "string",
  "name": "string",
  "type": "string",
  "virtualTables": [
    {
      "VirtualTableId": "string",
      "VirtualTableName": "string",
      "Status": "string"
    }
  ],
  "externalConfig": {
    "globalMetastoreId": "string",
    "clientId": "string",
    "clientSecret": "string",
    "snowflakeId": "string"
  }
}
```

---

## `Delete virtual table share`

<a id="opIdSharing_Delete virtual table share"></a>

Deleted the Virtual Table Share.

<h3>Request</h3>

```text 
DELETE /api/v1/tenants/{tenantid}/namespaces/{namespaceid}/shares/{id}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant Id<br/><br/>`string namespaceId`
<br/>Namespace Id<br/><br/>`string id`
<br/>Virtual table share Id<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|Successfully deleted the Virtual Table Share.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|404|[ErrorResponse](#schemaerrorresponse)|Not Found.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

---
## Definitions

### ShareView

<a id="schemashareview"></a>
<a id="schema_ShareView"></a>
<a id="tocSshareview"></a>
<a id="tocsshareview"></a>

Share view list

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|id|string|false|true|Share Id|
|name|string|false|true|Share name|
|type|string|false|true|Share Type|
|virtualTables|[[ShareVirtualTableView](#schemasharevirtualtableview)]|false|true|List of virtual tables associated with the share.|
|externalConfig|[ShareExternalConfig](#schemashareexternalconfig)|false|false|External configuration details for the share.|

```json
{
  "id": "string",
  "name": "string",
  "type": "string",
  "virtualTables": [
    {
      "VirtualTableId": "string",
      "VirtualTableName": "string",
      "Status": "string"
    }
  ],
  "externalConfig": {
    "globalMetastoreId": "string",
    "clientId": "string",
    "clientSecret": "string",
    "snowflakeId": "string"
  }
}

```

---

### ShareVirtualTableView

<a id="schemasharevirtualtableview"></a>
<a id="schema_ShareVirtualTableView"></a>
<a id="tocSsharevirtualtableview"></a>
<a id="tocssharevirtualtableview"></a>

Share virtual table view

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|VirtualTableId|string|false|false|Virtual Table Id|
|VirtualTableName|string|false|false|Virtual Table Name|
|Status|string|false|false|Materialization Status|

```json
{
  "VirtualTableId": "string",
  "VirtualTableName": "string",
  "Status": "string"
}

```

---

### ShareExternalConfig

<a id="schemashareexternalconfig"></a>
<a id="schema_ShareExternalConfig"></a>
<a id="tocSshareexternalconfig"></a>
<a id="tocsshareexternalconfig"></a>

Share External Config

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|globalMetastoreId|string|false|true|Global Metastore Id|
|clientId|string|false|true|Client Id|
|clientSecret|string|false|true|Client Secret|
|snowflakeId|string|false|true|Snowflake Id|

```json
{
  "globalMetastoreId": "string",
  "clientId": "string",
  "clientSecret": "string",
  "snowflakeId": "string"
}

```

---

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

### Share

<a id="schemashare"></a>
<a id="schema_Share"></a>
<a id="tocSshare"></a>
<a id="tocsshare"></a>

Share

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|id|string|false|true|Share Id|
|name|string|false|true|Share name|
|type|string|false|true|Share Type|
|virtualTables|[[ShareVirtualTableParam](#schemasharevirtualtableparam)]|false|true|List of virtual tables associated with the share.|
|externalConfig|[ShareExternalConfig](#schemashareexternalconfig)|false|false|External configuration details for the share.|
|SerializedSecurable|string|false|true|SerializedSecurable|
|CreatedBy|string|false|true|CreatedBy|
|CreatedOn|date-time|false|true|CreatedOn|

```json
{
  "id": "string",
  "name": "string",
  "type": "string",
  "virtualTables": [
    {
      "id": "string"
    }
  ],
  "externalConfig": {
    "globalMetastoreId": "string",
    "clientId": "string",
    "clientSecret": "string",
    "snowflakeId": "string"
  },
  "SerializedSecurable": "string",
  "CreatedBy": "string",
  "CreatedOn": "2019-08-24T14:15:22Z"
}

```

---

### ShareVirtualTableParam

<a id="schemasharevirtualtableparam"></a>
<a id="schema_ShareVirtualTableParam"></a>
<a id="tocSsharevirtualtableparam"></a>
<a id="tocssharevirtualtableparam"></a>

Share virtual table param

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|id|string|false|true|Virtual Table Id|

```json
{
  "id": "string"
}

```

---

