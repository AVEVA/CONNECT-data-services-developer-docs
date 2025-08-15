---
uid: virtual-table-sharing-materialization

---

# Materialization
The Materialization Asp.net Core controller.

## `Get All Tables`

<a id="opIdMaterialization_Get All Tables"></a>

Returns a list of Virtual Tables.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/virtualTables
?query={query}&orderBy={orderBy}&skip={skip}&count={count}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string query`
<br/>Optional query string for filtering results.<br/><br/>`string orderBy`
<br/>Optional parameter to specify sorting order.<br/><br/>
`[optional] integer skip`
<br/>The number of records to skip.<br/><br/>`[optional] integer count`
<br/>The maximum number of records to return.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|string|The virtual tables list was successfully retrieved.|
|400|[ErrorResponse](#schemaerrorresponse)|Bad request.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

---

## `Create Virtual Table`

<a id="opIdMaterialization_Create Virtual Table"></a>

Creates a new Virtual Table.

<h3>Request</h3>

```text 
POST /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/virtualTables
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>

<h4>Request Body</h4>

Virtual Table.<br/>

```json
{
  "CreatedOn": "2019-08-24T14:15:22Z",
  "LastRefreshed": "2019-08-24T14:15:22Z",
  "id": "string",
  "name": "string",
  "MaterializationStart": "2019-08-24T14:15:22Z",
  "MaterializationEnd": "2019-08-24T14:15:22Z",
  "TenantId": "string",
  "NamespaceId": "string",
  "dataViewId": "string",
  "DataviewName": "string",
  "retrievalMode": "string",
  "interval": "string",
  "MaterializationRunID": "string",
  "Status": "string",
  "TableFormat": "string",
  "CreatedBy": "string",
  "roleids": [
    "string"
  ],
  "SerializedSecurable": "string",
  "ClientId": "string",
  "SecretId": 0,
  "RefreshInterval": "string",
  "Shares": [
    {
      "ShareId": "string",
      "ShareName": "string",
      "ShareType": "string",
      "VirtualTables": [
        {
          "VirtualTableId": "string",
          "VirtualTableName": "string",
          "Status": "string"
        }
      ],
      "ExternalConfig": {
        "globalMetastoreId": "string",
        "clientId": "string",
        "clientSecret": "string",
        "snowflakeId": "string"
      }
    }
  ],
  "SecretExpirationTime": "2019-08-24T14:15:22Z"
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|string|Successfully created the virtual table.|
|400|[ErrorResponse](#schemaerrorresponse)|Bad request.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

---

## `Refresh Virtual Table (Refresh path)`

<a id="opIdMaterialization_Refresh Virtual Table (Refresh path)"></a>

Refreshes the Virtual Table.

<h3>Request</h3>

```text 
POST /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/virtualTables/{virtualTableId}/Refresh
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string virtualtableId`
<br/>Virtual Table identifier.<br/><br/>

<h4>Request Body</h4>

Virtual Table.<br/>

```json
{
  "MaterializationStart": "2019-08-24T14:15:22Z",
  "MaterializationEnd": "2019-08-24T14:15:22Z",
  "VirtualTableId": "string",
  "TenantId": "string",
  "IsUpdateProcess": true,
  "IsManualRefresh": true,
  "MessageId": "string"
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|string|Successfully refreshed the virtual table.|
|400|[ErrorResponse](#schemaerrorresponse)|Bad request.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

---

## `Refresh Virtual Table 1`

<a id="opIdMaterialization_Refresh Virtual Table 1"></a>

Refreshes the Virtual Table.

<h3>Request</h3>

```text 
POST /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/virtualTables/{virtualTableId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string virtualtableId`
<br/>Virtual Table identifier.<br/><br/>

<h4>Request Body</h4>

Virtual Table.<br/>

```json
{
  "MaterializationStart": "2019-08-24T14:15:22Z",
  "MaterializationEnd": "2019-08-24T14:15:22Z",
  "VirtualTableId": "string",
  "TenantId": "string",
  "IsUpdateProcess": true,
  "IsManualRefresh": true,
  "MessageId": "string"
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|string|Successfully refreshed the virtual table.|
|400|[ErrorResponse](#schemaerrorresponse)|Bad request.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

---

## `Update Virtual Table`

<a id="opIdMaterialization_Update Virtual Table"></a>

Updates the Virtual Table.

<h3>Request</h3>

```text 
PUT /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/virtualTables/{virtualTableId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string virtualtableId`
<br/>Virtual Table identifier.<br/><br/>

<h4>Request Body</h4>

Virtual Table.<br/>

```json
{
  "CreatedOn": "2019-08-24T14:15:22Z",
  "LastRefreshed": "2019-08-24T14:15:22Z",
  "id": "string",
  "name": "string",
  "MaterializationStart": "2019-08-24T14:15:22Z",
  "MaterializationEnd": "2019-08-24T14:15:22Z",
  "TenantId": "string",
  "NamespaceId": "string",
  "dataViewId": "string",
  "DataviewName": "string",
  "retrievalMode": "string",
  "interval": "string",
  "MaterializationRunID": "string",
  "Status": "string",
  "TableFormat": "string",
  "CreatedBy": "string",
  "roleids": [
    "string"
  ],
  "SerializedSecurable": "string",
  "ClientId": "string",
  "SecretId": 0,
  "RefreshInterval": "string",
  "Shares": [
    {
      "ShareId": "string",
      "ShareName": "string",
      "ShareType": "string",
      "VirtualTables": [
        {
          "VirtualTableId": "string",
          "VirtualTableName": "string",
          "Status": "string"
        }
      ],
      "ExternalConfig": {
        "globalMetastoreId": "string",
        "clientId": "string",
        "clientSecret": "string",
        "snowflakeId": "string"
      }
    }
  ],
  "SecretExpirationTime": "2019-08-24T14:15:22Z"
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|string|Successfully updated the properties of the virtual table.|
|400|[ErrorResponse](#schemaerrorresponse)|Bad request.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

---

## `Get Table`

<a id="opIdMaterialization_Get Table"></a>

Returns the specified Virtual Table.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/virtualTables/{virtualtableId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string virtualtableId`
<br/>Virtual Table identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|string|Successfully returns the properties of the virtual table.|
|400|[ErrorResponse](#schemaerrorresponse)|Bad request.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

---

## `Delete Virtual Table`

<a id="opIdMaterialization_Delete Virtual Table"></a>

Deletes the Virtual Table.

<h3>Request</h3>

```text 
DELETE /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/virtualTables/{virtualtableid}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string virtualtableId`
<br/>Virtual Table identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|string|Successfully deleted the virtual table.|
|400|[ErrorResponse](#schemaerrorresponse)|Bad request.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

---

## `Get Materialized Virtual Table`

<a id="opIdMaterialization_Get Materialized Virtual Table"></a>

Returns the Materialized Virtual table.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/virtualTables/{virtualTableId}/data/{format}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string virtualtableid`
<br/>Virtual Table identifier.<br/><br/>`string format`
<br/>Format<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|string|Successfully retrieved materialized virtual table.|
|400|[ErrorResponse](#schemaerrorresponse)|Bad request.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
|500|[ErrorResponse](#schemaerrorresponse)|An error occurred while processing the request.|

---

## `Get Materialized Virtual Table Status`

<a id="opIdMaterialization_Get Materialized Virtual Table Status"></a>

Returns the Materialized Virtual Table Status.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/virtualTables/{virtualTableId}/status
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string virtualtableid`
<br/>Virtual Table identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|string|Successfully retrieved the status of the virtual table materialization.|
|400|[ErrorResponse](#schemaerrorresponse)|Bad request.|
|403|[ErrorResponse](#schemaerrorresponse)|You are not authorized for this operation.|
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

### VirtualTable

<a id="schemavirtualtable"></a>
<a id="schema_VirtualTable"></a>
<a id="tocSvirtualtable"></a>
<a id="tocsvirtualtable"></a>

Virtual Table

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|CreatedOn|date-time|false|false|Creation Date of Virtual table|
|LastRefreshed|date-time|false|true|Date Virtual table was last refreshed on.|
|id|string|false|true|Virtual Table Id|
|name|string|false|true|Virtual Table Name|
|MaterializationStart|date-time|false|true|Materialization start|
|MaterializationEnd|date-time|false|true|Materialization end|
|TenantId|guid|false|false|Tenant Id|
|NamespaceId|string|false|true|Namespace Id|
|dataViewId|string|false|true|Dataview Id|
|DataviewName|string|false|true|Dataview Name|
|retrievalMode|string|false|false|Retreival Mode|
|interval|string|false|true|Interpolation Interval|
|MaterializationRunID|string|false|true|Materialization RunID|
|Status|string|false|false|Status|
|TableFormat|string|false|false|Table Format|
|CreatedBy|string|false|true|Created By|
|roleids|string[]|false|true|Role Ids|
|SerializedSecurable|string|false|true|Serialized Securable|
|ClientId|string|false|true|Client Id|
|SecretId|int32|false|false|Secret Id|
|RefreshInterval|string|false|true|Refresh Interval|
|Shares|[[ShareView](#schemashareview)]|false|true|Shares associated with VirtualTable|
|SecretExpirationTime|date-time|false|true|Secret Expiration Time|

```json
{
  "CreatedOn": "2019-08-24T14:15:22Z",
  "LastRefreshed": "2019-08-24T14:15:22Z",
  "id": "string",
  "name": "string",
  "MaterializationStart": "2019-08-24T14:15:22Z",
  "MaterializationEnd": "2019-08-24T14:15:22Z",
  "TenantId": "string",
  "NamespaceId": "string",
  "dataViewId": "string",
  "DataviewName": "string",
  "retrievalMode": "string",
  "interval": "string",
  "MaterializationRunID": "string",
  "Status": "string",
  "TableFormat": "string",
  "CreatedBy": "string",
  "roleids": [
    "string"
  ],
  "SerializedSecurable": "string",
  "ClientId": "string",
  "SecretId": 0,
  "RefreshInterval": "string",
  "Shares": [
    {
      "ShareId": "string",
      "ShareName": "string",
      "ShareType": "string",
      "VirtualTables": [
        {
          "VirtualTableId": "string",
          "VirtualTableName": "string",
          "Status": "string"
        }
      ],
      "ExternalConfig": {
        "globalMetastoreId": "string",
        "clientId": "string",
        "clientSecret": "string",
        "snowflakeId": "string"
      }
    }
  ],
  "SecretExpirationTime": "2019-08-24T14:15:22Z"
}

```

---

### ShareView

<a id="schemashareview"></a>
<a id="schema_ShareView"></a>
<a id="tocSshareview"></a>
<a id="tocsshareview"></a>

Share view list

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|ShareId|string|false|true|Share Id|
|ShareName|string|false|true|Share name|
|ShareType|string|false|true|Share Type|
|VirtualTables|[[ShareVirtualTableView](#schemasharevirtualtableview)]|false|true|List of virtual tables associated with the share.|
|ExternalConfig|[ShareExternalConfig](#schemashareexternalconfig)|false|false|External configuration details for the share.|

```json
{
  "ShareId": "string",
  "ShareName": "string",
  "ShareType": "string",
  "VirtualTables": [
    {
      "VirtualTableId": "string",
      "VirtualTableName": "string",
      "Status": "string"
    }
  ],
  "ExternalConfig": {
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

### VirtualTableRefresh

<a id="schemavirtualtablerefresh"></a>
<a id="schema_VirtualTableRefresh"></a>
<a id="tocSvirtualtablerefresh"></a>
<a id="tocsvirtualtablerefresh"></a>

Represents the refresh details for a virtual table.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|MaterializationStart|date-time|true|false|Materialization start|
|MaterializationEnd|date-time|true|false|Materialization end|
|VirtualTableId|string|false|true|Virtual Table id|
|TenantId|string|false|true|Virtual Table TenantId|
|IsUpdateProcess|boolean|false|false|Boolean value indicating whether the process is an update.|
|IsManualRefresh|boolean|false|false|Boolean value indicating whether the refresh is manual.|
|MessageId|string|false|true|Message Id|

```json
{
  "MaterializationStart": "2019-08-24T14:15:22Z",
  "MaterializationEnd": "2019-08-24T14:15:22Z",
  "VirtualTableId": "string",
  "TenantId": "string",
  "IsUpdateProcess": true,
  "IsManualRefresh": true,
  "MessageId": "string"
}

```

---

