---
uid: omf-ingress-validation

---

# Validation

## `Validate`

<a id="opIdValidator_Validate"></a>

<h3>Request</h3>

```text 
POST /api/v1/omf/validation
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[ValidationResult](#schemavalidationresult)|None|
|400|None|None|

<h4>Example response body</h4>

> 200 Response ([ValidationResult](#schemavalidationresult))

```json
{
  "IsValid": true,
  "ErrorMessage": "string",
  "Version": "string",
  "MessageType": "string"
}
```

---

## `Validate Any Message Type`

<a id="opIdValidator_Validate Any Message Type"></a>

<h3>Request</h3>

```text 
POST /api/v1/omf/validation/body
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[ValidationResult](#schemavalidationresult)|None|

<h4>Example response body</h4>

> 200 Response ([ValidationResult](#schemavalidationresult))

```json
{
  "IsValid": true,
  "ErrorMessage": "string",
  "Version": "string",
  "MessageType": "string"
}
```

---

## `Validate Any Header`

<a id="opIdValidator_Validate Any Header"></a>

<h3>Request</h3>

```text 
POST /api/v1/omf/validation/header
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[ValidationResult](#schemavalidationresult)|None|

<h4>Example response body</h4>

> 200 Response ([ValidationResult](#schemavalidationresult))

```json
{
  "IsValid": true,
  "ErrorMessage": "string",
  "Version": "string",
  "MessageType": "string"
}
```

---

## `Validate Header`

<a id="opIdValidator_Validate Header"></a>

<h3>Request</h3>

```text 
POST /api/v1/omf/validation/header/{omfVersion}
```

<h4>Parameters</h4>

`string omfVersion`
<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[ValidationResult](#schemavalidationresult)|None|
|400|None|None|

<h4>Example response body</h4>

> 200 Response ([ValidationResult](#schemavalidationresult))

```json
{
  "IsValid": true,
  "ErrorMessage": "string",
  "Version": "string",
  "MessageType": "string"
}
```

---

## `Validate Message Type`

<a id="opIdValidator_Validate Message Type"></a>

<h3>Request</h3>

```text 
POST /api/v1/omf/validation/body/{omfVersion}/{omfMessageType}
```

<h4>Parameters</h4>

`string omfVersion`
<br/><br/>`string omfMessageType`
<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[ValidationResult](#schemavalidationresult)|None|
|400|None|None|

<h4>Example response body</h4>

> 200 Response ([ValidationResult](#schemavalidationresult))

```json
{
  "IsValid": true,
  "ErrorMessage": "string",
  "Version": "string",
  "MessageType": "string"
}
```

---
## Definitions

### ValidationResult

<a id="schemavalidationresult"></a>
<a id="schema_ValidationResult"></a>
<a id="tocSvalidationresult"></a>
<a id="tocsvalidationresult"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|IsValid|boolean|false|false|None|
|ErrorMessage|string|false|true|None|
|Version|string|false|true|None|
|MessageType|string|false|true|None|

```json
{
  "IsValid": true,
  "ErrorMessage": "string",
  "Version": "string",
  "MessageType": "string"
}

```

---

