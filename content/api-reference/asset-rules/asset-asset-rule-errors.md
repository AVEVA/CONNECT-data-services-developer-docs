---
uid: asset-asset-rule-errors

---

# Asset Rule Errors

## `List Rule Errors By Rule Id`

<a id="opIdRuleErrors_List Rule Errors By Rule Id"></a>

Gets the `RuleError` objects for the specified ruleId.

### Request
```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/assetrules/{ruleId}/errors
```

#### Parameters

`string ruleId`
<br/>The rule Id.<br/><br/>`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[RuleError](#schemaruleerror)[]|An `IEnumerable`1`|
|403|[ResponseBody](#schemaresponsebody)|Forbidden.|
|404|[ResponseBody](#schemaresponsebody)|The specified rule was not found.|
|500|[ResponseBody](#schemaresponsebody)|None|

#### Example response body
> 200 Response

```json
[
  {
    "Id": "00000000-0000-0000-0000-000000000000",
    "RuleId": "ruleId",
    "TimeGenerated": "0001-01-01T00:00:00",
    "ErrorDetails": "Error details.",
    "ErrorMessageType": 1
  },
  {
    "Id": "00000000-0000-0000-0000-000000000000",
    "RuleId": "ruleId",
    "TimeGenerated": "0001-01-01T00:00:00",
    "ErrorDetails": "Error details.",
    "ErrorMessageType": 1
  }
]
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

## `Delete Rule Errors By Rule Id`

<a id="opIdRuleErrors_Delete Rule Errors By Rule Id"></a>

Deletes the `!:RuleErrorDto` objects associated with the specified rule.

### Request
```text 
DELETE /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/assetrules/{ruleId}/errors
```

#### Parameters

`string ruleId`
<br/>The rule Id.<br/><br/>`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|204|None|No content.|
|403|[ResponseBody](#schemaresponsebody)|Forbidden.|
|404|[ResponseBody](#schemaresponsebody)|The specified rule was not found.|
|500|[ResponseBody](#schemaresponsebody)|None|

#### Example response body
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

### RuleError

<a id="schemaruleerror"></a>
<a id="schema_RuleError"></a>
<a id="tocSruleerror"></a>
<a id="tocsruleerror"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|guid|false|false|None|
|RuleId|string|false|true|None|
|TimeGenerated|date-time|false|false|None|
|ErrorDetails|string|false|true|None|
|ErrorMessageType|[ErrorMessageType](#schemaerrormessagetype)|false|false|None|

```json
{
  "Id": "00000000-0000-0000-0000-000000000000",
  "RuleId": "ruleId",
  "TimeGenerated": "0001-01-01T00:00:00",
  "ErrorDetails": "Error details.",
  "ErrorMessageType": 1
}

```

---

### ErrorMessageType

<a id="schemaerrormessagetype"></a>
<a id="schema_ErrorMessageType"></a>
<a id="tocSerrormessagetype"></a>
<a id="tocserrormessagetype"></a>

#### Enumerated Values

|Property|Value|
|---|---|
|ConflictBetweenRules|0|
|CreateOrUpdate|1|
|Generic|2|
|AutomationId|3|
|ConflictBetweenStreams|4|
|MissingMappings|5|
|ConflictBetweenRuleAndUser|6|

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

