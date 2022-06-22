---
uid: asset-sds-read-only-replica-admin

---

# Sds Read Only Replica Admin

## `Refresh Stream`

<a id="opIdAssetRuleAdminSdsCache_Refresh Stream"></a>

Refreshes a stream by requesting the most up-to-date information from SDS

<h3>Request</h3>

```text 
POST /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/admin/assetrules/replica/sds/refresh/{streamId}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string streamId`
<br/>The stream to be refreshed.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Ok if the stream was refreshed.|
|400|[ResponseBody](#schemaresponsebody)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/common.yaml#400|
|403|[ResponseBody](#schemaresponsebody)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/common.yaml#403|
|500|[ResponseBody](#schemaresponsebody)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/common.yaml#500|

---

## `Get Stream From Cache`

<a id="opIdAssetRuleAdminSdsCache_Get Stream From Cache"></a>

Returns the `CompleteSdsInfoEntry` for the stream.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/admin/assetrules/replica/sds/{streamId}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string streamId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/common.yaml#streamId<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[CompleteSdsInfoEntry](#schemacompletesdsinfoentry)|The `CompleteSdsInfoEntry` for the stream.|
|403|[ResponseBody](#schemaresponsebody)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/common.yaml#403|
|404|[ResponseBody](#schemaresponsebody)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/common.yaml#404|
|500|[ResponseBody](#schemaresponsebody)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/common.yaml#500|

<h4>Example response body</h4>

> 200 Response

```json
{
  "Stream": {
    "Id": "SimpleStream",
    "Name": "SimpleStream",
    "TypeId": "SimpleType"
  },
  "Type": {
    "Id": "SimpleType",
    "Name": "Simple Type",
    "Description": "",
    "Properties": [
      {
        "Id": "Timestamp",
        "Name": "Time",
        "Order": 0,
        "IsKey": true,
        "FixedSize": 0,
        "SdsType": {
          "Id": "datestrType",
          "Name": "datestrType",
          "SdsTypeCode": "DateTime",
          "IsGenericType": false,
          "IsReferenceType": false,
          "InterpolationMode": "Continuous",
          "ExtrapolationMode": "All"
        },
        "IsQuality": false
      },
      {
        "Id": "Value",
        "Name": "Value",
        "Order": 0,
        "IsKey": false,
        "FixedSize": 0,
        "SdsType": {
          "Id": "doubleType",
          "Name": "doubleType",
          "SdsTypeCode": "Double",
          "IsGenericType": false,
          "IsReferenceType": false,
          "InterpolationMode": "Continuous",
          "ExtrapolationMode": "All"
        },
        "IsQuality": false
      }
    ]
  },
  "Metadata": {
    "name": {
      "Value": "",
      "ChangeData": {
        "Timestamp": "2021-12-10T17:07:20.8674253Z",
        "CreatorId": "",
        "CreatorType": "User"
      }
    }
  },
  "Acl": {
    "RoleTrusteeAccessControlEntries": [
      {
        "Trustee": {
          "Type": "Role",
          "ObjectId": "00000000-0000-0000-0000-000000000000"
        },
        "AccessType": "Allowed",
        "AccessRights": 3
      },
      {
        "Trustee": {
          "Type": "Role",
          "ObjectId": "00000000-0000-0000-0000-000000000000"
        },
        "AccessType": "Allowed",
        "AccessRights": 15
      },
      {
        "Trustee": {
          "Type": "Role",
          "ObjectId": "00000000-0000-0000-0000-000000000000"
        },
        "AccessType": "Allowed",
        "AccessRights": 1
      }
    ]
  },
  "Owner": {
    "Type": "Client",
    "ObjectId": "00000000-0000-0000-0000-000000000000",
    "TenantId": "00000000-0000-0000-0000-000000000000"
  },
  "StreamLastUpdated": "2021-12-10T17:07:20.8674253Z",
  "MetadataLastUpdated": "2021-12-10T17:07:20.8674253Z"
}
```

> 403 Response

```json
{
  "OperationId": "00000000-0000-0000-0000-000000000000",
  "Error": "Error message.",
  "Reason": "Reason that caused the error.",
  "Resolution": "Possible resolution for the error.",
  "Parameters": {
    "key1": "value1",
    "key2": "value2"
  }
}
```

> 404 Response

```json
{
  "OperationId": "00000000-0000-0000-0000-000000000000",
  "Error": "Error message.",
  "Reason": "Reason that caused the error.",
  "Resolution": "Possible resolution for the error.",
  "Parameters": {
    "key1": "value1",
    "key2": "value2"
  }
}
```

> 500 Response

```json
{
  "OperationId": "00000000-0000-0000-0000-000000000000",
  "Error": "Error message.",
  "Reason": "Reason that caused the error.",
  "Resolution": "Possible resolution for the error.",
  "Parameters": {
    "key1": "value1",
    "key2": "value2"
  }
}
```

---
## Definitions

### ResponseBody

<a id="schemaresponsebody"></a>
<a id="schema_ResponseBody"></a>
<a id="tocSresponsebody"></a>
<a id="tocsresponsebody"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|false|true|None|
|Error|string|false|true|None|
|Reason|string|false|true|None|
|Resolution|string|false|true|None|
|Parameters|object|false|true|None|

```json
{
  "OperationId": "00000000-0000-0000-0000-000000000000",
  "Error": "Error message.",
  "Reason": "Reason that caused the error.",
  "Resolution": "Possible resolution for the error.",
  "Parameters": {
    "key1": "value1",
    "key2": "value2"
  }
}

```

---

### CompleteSdsInfoEntry

<a id="schemacompletesdsinfoentry"></a>
<a id="schema_CompleteSdsInfoEntry"></a>
<a id="tocScompletesdsinfoentry"></a>
<a id="tocscompletesdsinfoentry"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Stream|[SdsStreamModel](#schemasdsstreammodel)|false|true|None|
|Metadata|object|false|true|None|
|Acl|[AccessControlList](#schemaaccesscontrollist)|false|true|None|
|Owner|[Trustee](#schematrustee)|false|true|None|
|StreamTimestamp|date-time|false|false|None|
|MetadataTimestamp|date-time|false|false|None|

```json
{
  "Stream": {
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "TypeId": "string"
  },
  "Metadata": {
    "property1": "string",
    "property2": "string"
  },
  "Acl": {
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
  },
  "Owner": {
    "Type": 1,
    "ObjectId": "string",
    "TenantId": "string"
  },
  "StreamTimestamp": "2019-08-24T14:15:22Z",
  "MetadataTimestamp": "2019-08-24T14:15:22Z"
}

```

---

### SdsStreamModel

<a id="schemasdsstreammodel"></a>
<a id="schema_SdsStreamModel"></a>
<a id="tocSsdsstreammodel"></a>
<a id="tocssdsstreammodel"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|None|
|Name|string|false|true|None|
|Description|string|false|true|None|
|TypeId|string|false|true|None|

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "TypeId": "string"
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

