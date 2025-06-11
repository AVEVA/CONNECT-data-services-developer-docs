---
uid: metadata-metadata-rule-expression-preview

---

# Metadata Rule Expression Preview

## `Get Expression Preview Results`

<a id="opIdMetadataRuleExpressionPreview_Get Expression Preview Results"></a>

Returns a `ExpressionPreviewResult`.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/preview/metadatarules/expressions
?token={token}&skip={skip}&count={count}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string token`
<br/>A `Guid` which corresponds to a preview that has been created using the `StartExpressionPreview` method.<br/><br/>
`[optional] integer skip`
<br/>An `Int32` to determine the number of preview results to skip.<br/><br/>`[optional] integer count`
<br/>An `Int32` to determine the number of preview results to return.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[ExpressionPreviewResult](#schemaexpressionpreviewresult)|A `ExpressionPreviewResult` object.|
|400|[ResponseBody](#schemaresponsebody)|Missing or invalid inputs.|
|403|[ResponseBody](#schemaresponsebody)|Forbidden.|
|404|[ResponseBody](#schemaresponsebody)|The specified preview was not found.|
|500|[ResponseBody](#schemaresponsebody)|Internal server error.|

<h4>Example response body</h4>

> 200 Response

```json
{
  "Streams": [
    {
      "Id": "streamId",
      "Name": "streamName",
      "TypeId": "streamTypeId"
    }
  ],
  "Status": "Complete",
  "Statistics": {
    "StreamsProcessed": 4,
    "MatchingStreams": 1
  }
}
```

> 400 Response

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

## `Start Expression Preview`

<a id="opIdMetadataRuleExpressionPreview_Start Expression Preview"></a>

Creates a `ExpressionPreviewResponse` of a `RuleExpression` object.

<h3>Request</h3>

```text 
POST /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/preview/metadatarules/expressions
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

<h4>Request Body</h4>

The RuleModel object to preview.<br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|202|[ExpressionPreviewResponse](#schemaexpressionpreviewresponse)|A `ExpressionPreviewResponse` object.|
|400|[ResponseBody](#schemaresponsebody)|Missing or invalid inputs.|
|403|[ResponseBody](#schemaresponsebody)|Forbidden.|
|500|[ResponseBody](#schemaresponsebody)|Internal server error.|

<h4>Example response body</h4>

> 202 Response

```json
{
  "PreviewLink": "/api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/preview/metadatarules/expressions?Token=00000000-0000-0000-0000-000000000000",
  "Expires": 7200
}
```

> 400 Response

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

## `Cancel Expression Preview`

<a id="opIdMetadataRuleExpressionPreview_Cancel Expression Preview"></a>

Cancels a running preview.

<h3>Request</h3>

```text 
DELETE /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/preview/metadatarules/expressions
?token={token}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string token`
<br/>A `Guid` which corresponds to a preview that has been created using the `StartExpressionPreview` method.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|No content.|
|400|[ResponseBody](#schemaresponsebody)|Missing or invalid inputs.|
|403|[ResponseBody](#schemaresponsebody)|Forbidden.|
|404|[ResponseBody](#schemaresponsebody)|The specified preview was not found.|
|500|[ResponseBody](#schemaresponsebody)|Internal server error.|

---
## Definitions

### ExpressionPreviewResponse

<a id="schemaexpressionpreviewresponse"></a>
<a id="schema_ExpressionPreviewResponse"></a>
<a id="tocSexpressionpreviewresponse"></a>
<a id="tocsexpressionpreviewresponse"></a>

Expression preview response

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|ExpressionPreviewLink|string|false|true|Preview link|
|Expires|int32|false|false|Preview expires in|

```json
{
  "ExpressionPreviewLink": "string",
  "Expires": 0
}

```

---

### ResponseBody

<a id="schemaresponsebody"></a>
<a id="schema_ResponseBody"></a>
<a id="tocSresponsebody"></a>
<a id="tocsresponsebody"></a>

Create instance of ResponseBody

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|false|true|Operation id|
|Error|string|false|true|Error|
|Reason|string|false|true|Reason|
|Resolution|string|false|true|Resolution|
|Parameters|object|false|true|Parameters|

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

### RuleExpression

<a id="schemaruleexpression"></a>
<a id="schema_RuleExpression"></a>
<a id="tocSruleexpression"></a>
<a id="tocsruleexpression"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Field|string|false|true|None|
|Specifications|[[Specification](#schemaspecification)]|false|true|[Specification]|

```json
{
  "Field": "string",
  "Specifications": [
    {
      "Type": 0,
      "Value": "string",
      "Name": "string",
      "CharacterType": 0,
      "CharacterLength": 0,
      "StrictValueMappings": true,
      "RequiredDelimiters": [
        "string"
      ],
      "ValueMappings": {
        "property1": "string",
        "property2": "string"
      }
    }
  ]
}

```

---

### Specification

<a id="schemaspecification"></a>
<a id="schema_Specification"></a>
<a id="tocSspecification"></a>
<a id="tocsspecification"></a>

Specification

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Type|[SpecificationType](#schemaspecificationtype)|false|false|Specification type|
|Value|string|false|true|Spec value|
|Name|string|false|true|Name|
|CharacterType|[CharacterType](#schemacharactertype)|false|false|Character type|
|CharacterLength|int32|false|true|Null represents the longest string length within the group.|
|StrictValueMappings|boolean|false|false|Strict value mappings|
|RequiredDelimiters|string[]|false|true|Required delimiters|
|ValueMappings|object|false|true|Value mappings|

```json
{
  "Type": 0,
  "Value": "string",
  "Name": "string",
  "CharacterType": 0,
  "CharacterLength": 0,
  "StrictValueMappings": true,
  "RequiredDelimiters": [
    "string"
  ],
  "ValueMappings": {
    "property1": "string",
    "property2": "string"
  }
}

```

---

### SpecificationType

<a id="schemaspecificationtype"></a>
<a id="schema_SpecificationType"></a>
<a id="tocSspecificationtype"></a>
<a id="tocsspecificationtype"></a>

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|Unspecified|0|
|Group|1|
|Wildcard|2|
|Literal|3|
|Delimiter|4|

---

### CharacterType

<a id="schemacharactertype"></a>
<a id="schema_CharacterType"></a>
<a id="tocScharactertype"></a>
<a id="tocscharactertype"></a>

Character type

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|Any|0|
|Letter|1|
|Digit|2|
|Alphanumeric|3|

---

### ExpressionPreviewResult

<a id="schemaexpressionpreviewresult"></a>
<a id="schema_ExpressionPreviewResult"></a>
<a id="tocSexpressionpreviewresult"></a>
<a id="tocsexpressionpreviewresult"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Status|string|false|true|None|
|Streams|[[SdsStream](#schemasdsstream)]|false|true|Stream list|
|Statistics|[ExpressionPreviewStatistics](#schemaexpressionpreviewstatistics)|false|true|Statistics for preview|

```json
{
  "Streams": [
    {
      "Id": "streamId",
      "Name": "streamName",
      "TypeId": "streamTypeId"
    }
  ],
  "Status": "Complete",
  "Statistics": {
    "StreamsProcessed": 4,
    "MatchingStreams": 1
  }
}

```

---

### SdsStream

<a id="schemasdsstream"></a>
<a id="schema_SdsStream"></a>
<a id="tocSsdsstream"></a>
<a id="tocssdsstream"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|None|
|Name|string|false|true|None|
|Description|string|false|true|None|
|TypeId|string|false|true|None|
|Indexes|[[SdsStreamIndex](#schemasdsstreamindex)]|false|true|None|
|InterpolationMode|[SdsInterpolationMode](#schemasdsinterpolationmode)|false|true|None|
|ExtrapolationMode|[SdsExtrapolationMode](#schemasdsextrapolationmode)|false|true|None|
|PropertyOverrides|[[SdsStreamPropertyOverride](#schemasdsstreampropertyoverride)]|false|true|None|
|CreatedDate|date-time|false|false|None|
|ModifiedDate|date-time|false|false|None|

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "TypeId": "string",
  "Indexes": [
    {
      "SdsTypePropertyId": "string"
    }
  ],
  "InterpolationMode": 0,
  "ExtrapolationMode": 0,
  "PropertyOverrides": [
    {
      "SdsTypePropertyId": "string",
      "Uom": "string",
      "InterpolationMode": 0
    }
  ],
  "CreatedDate": "2019-08-24T14:15:22Z",
  "ModifiedDate": "2019-08-24T14:15:22Z"
}

```

---

### SdsStreamIndex

<a id="schemasdsstreamindex"></a>
<a id="schema_SdsStreamIndex"></a>
<a id="tocSsdsstreamindex"></a>
<a id="tocssdsstreamindex"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|SdsTypePropertyId|string|false|true|None|

```json
{
  "SdsTypePropertyId": "string"
}

```

---

### SdsInterpolationMode

<a id="schemasdsinterpolationmode"></a>
<a id="schema_SdsInterpolationMode"></a>
<a id="tocSsdsinterpolationmode"></a>
<a id="tocssdsinterpolationmode"></a>

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|Continuous|0|
|Default|0|
|StepwiseContinuousLeading|1|
|StepwiseContinuousTrailing|2|
|Discrete|3|
|ContinuousNullableLeading|4|
|ContinuousNullableTrailing|5|

---

### SdsExtrapolationMode

<a id="schemasdsextrapolationmode"></a>
<a id="schema_SdsExtrapolationMode"></a>
<a id="tocSsdsextrapolationmode"></a>
<a id="tocssdsextrapolationmode"></a>

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|All|0|
|None|1|
|Forward|2|
|Backward|3|

---

### SdsStreamPropertyOverride

<a id="schemasdsstreampropertyoverride"></a>
<a id="schema_SdsStreamPropertyOverride"></a>
<a id="tocSsdsstreampropertyoverride"></a>
<a id="tocssdsstreampropertyoverride"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|SdsTypePropertyId|string|false|true|None|
|Uom|string|false|true|None|
|InterpolationMode|[SdsInterpolationMode](#schemasdsinterpolationmode)|false|true|None|

```json
{
  "SdsTypePropertyId": "string",
  "Uom": "string",
  "InterpolationMode": 0
}

```

---

### ExpressionPreviewStatistics

<a id="schemaexpressionpreviewstatistics"></a>
<a id="schema_ExpressionPreviewStatistics"></a>
<a id="tocSexpressionpreviewstatistics"></a>
<a id="tocsexpressionpreviewstatistics"></a>

Expression preview statistics

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|StreamsProcessed|int32|false|false|Number of streams procesed|
|MatchingStreams|int32|false|false|Number of matching streams|

```json
{
  "StreamsProcessed": 0,
  "MatchingStreams": 0
}

```

---

