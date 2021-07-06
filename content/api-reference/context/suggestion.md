---
uid: ""

---

# Suggestion

## `Get Suggestion`

<a id="opIdSuggestion_Get Suggestion"></a>

Creates a `SuggestionResult` of a metadata `RuleModel` object.

### Request
```text 
POST /api/v1/tenants/{tenantid}/namespaces/{namespaceid}/suggestion/metadatarules
```

#### Parameters

`string tenantid`
<br/><br/>`string namespaceid`
<br/><br/>

### Request Body

The RuleModel object to create suggestions for.<br/>

```json
{
  "Id": "ruleId",
  "Name": "name",
  "Description": "description",
  "ExampleStreamId": "exampleId",
  "AutomationId": "00000000-0000-0000-0000-000000000000",
  "IsDraft": "false",
  "Expressions": [
    {
      "Field": "Id",
      "Specification": [
        {
          "Type": "Wildcard",
          "Name": "id"
        }
      ]
    }
  ],
  "Outputs": [
    {
      "Field": "Metadata",
      "Value": {
        "key": "{id}"
      }
    }
  ],
  "CreationTime": "0001-01-01T00:00:00",
  "ModifiedTime": "0001-01-01T00:00:00"
}
```

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[SuggestionResult](#schemasuggestionresult)|A `SuggestionResult` object.|
|400|[ResponseBody](#schemaresponsebody)|Invalid rule.|
|403|[ResponseBody](#schemaresponsebody)|Forbidden.|
|500|[ResponseBody](#schemaresponsebody)|Internal server error.|
|503|[ResponseBody](#schemaresponsebody)|Dependent service error.|

#### Example response body
> 200 Response

```json
{
  "Results": {
    "key1": [
      "value1",
      "value2"
    ],
    "key2": [
      "value1",
      "value2"
    ]
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

> 503 Response

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

### SuggestionResult

<a id="schemasuggestionresult"></a>
<a id="schema_SuggestionResult"></a>
<a id="tocSsuggestionresult"></a>
<a id="tocssuggestionresult"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Results|object|false|true|None|

```json
{
  "Results": {
    "key1": [
      "value1",
      "value2"
    ],
    "key2": [
      "value1",
      "value2"
    ]
  }
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

### RuleModel

<a id="schemarulemodel"></a>
<a id="schema_RuleModel"></a>
<a id="tocSrulemodel"></a>
<a id="tocsrulemodel"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|None|
|Name|string|false|true|None|
|Description|string|false|true|None|
|ExampleStreamId|string|false|true|None|
|AutomationId|string|false|true|None|
|IsDraft|boolean|false|false|None|
|Expressions|[[RuleExpression](#schemaruleexpression)]|false|true|None|
|Outputs|[[RuleOutput](#schemaruleoutput)]|false|true|None|
|CreationTime|date-time|false|false|None|
|ModifiedTime|date-time|false|false|None|

```json
{
  "Id": "ruleId",
  "Name": "name",
  "Description": "description",
  "ExampleStreamId": "exampleId",
  "AutomationId": "00000000-0000-0000-0000-000000000000",
  "IsDraft": "false",
  "Expressions": [
    {
      "Field": "Id",
      "Specification": [
        {
          "Type": "Wildcard",
          "Name": "id"
        }
      ]
    }
  ],
  "Outputs": [
    {
      "Field": "Metadata",
      "Value": {
        "key": "{id}"
      }
    }
  ],
  "CreationTime": "0001-01-01T00:00:00",
  "ModifiedTime": "0001-01-01T00:00:00"
}

```

---

### RuleExpression

<a id="schemaruleexpression"></a>
<a id="schema_RuleExpression"></a>
<a id="tocSruleexpression"></a>
<a id="tocsruleexpression"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Field|string|false|true|None|
|Specifications|[[Specification](#schemaspecification)]|false|true|None|

```json
{
  "Field": "string",
  "Specifications": [
    {
      "Type": "Unspecified",
      "Value": "string",
      "Name": "string",
      "CharacterType": "Any",
      "CharacterLength": 0,
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

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Type|[SpecificationType](#schemaspecificationtype)|false|false|None|
|Value|string|false|true|None|
|Name|string|false|true|None|
|CharacterType|[CharacterType](#schemacharactertype)|false|false|None|
|CharacterLength|int32|false|true|Null represents the longest string length within the group.|
|RequiredDelimiters|string[]|false|true|None|
|ValueMappings|object|false|true|None|

```json
{
  "Type": "Unspecified",
  "Value": "string",
  "Name": "string",
  "CharacterType": "Any",
  "CharacterLength": 0,
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

#### Enumerated Values

|Property|Value|
|---|---|
|Unspecified|Unspecified|
|Group|Group|
|Wildcard|Wildcard|
|Literal|Literal|
|Delimiter|Delimiter|

---

### CharacterType

<a id="schemacharactertype"></a>
<a id="schema_CharacterType"></a>
<a id="tocScharactertype"></a>
<a id="tocscharactertype"></a>

#### Enumerated Values

|Property|Value|
|---|---|
|Any|Any|
|Letter|Letter|
|Digit|Digit|
|Alphanumeric|Alphanumeric|

---

### RuleOutput

<a id="schemaruleoutput"></a>
<a id="schema_RuleOutput"></a>
<a id="tocSruleoutput"></a>
<a id="tocsruleoutput"></a>

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Field|string|false|true|None|
|Value|any|false|true|None|

```json
{
  "Field": "string",
  "Value": null
}

```

---

