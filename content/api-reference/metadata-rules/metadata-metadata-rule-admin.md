---
uid: metadata-metadata-rule-admin

---

# Metadata Rule Admin

## `Get Statistics`

<a id="opIdMetadataRuleAdmin_Get Statistics"></a>

Gets the `StoreStatistics` on the `IRuleStore`.

### Request
```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/admin/metadatarules/statistics
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[StoreStatistics](#schemastorestatistics)|The `IRuleStore` `StoreStatistics`.|
|403|[ResponseBody](#schemaresponsebody)|Forbidden.|
|500|[ResponseBody](#schemaresponsebody)|Internal server error.|

#### Example response body
> 200 Response

```json
{
  "RuleCount": 0
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

### StoreStatistics

<a id="schemastorestatistics"></a>
<a id="schema_StoreStatistics"></a>
<a id="tocSstorestatistics"></a>
<a id="tocsstorestatistics"></a>

Statistics on the rule store from /admin/metadatarules/statistics.

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|RuleCount|int32|false|false|The total number of rules.|

```json
{
  "RuleCount": 0
}

```

---

### ResponseBody

<a id="schemaresponsebody"></a>
<a id="schema_ResponseBody"></a>
<a id="tocSresponsebody"></a>
<a id="tocsresponsebody"></a>

#### Properties

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

