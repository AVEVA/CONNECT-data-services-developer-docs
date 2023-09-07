---
uid: sds-units-of-measure

---

# Units Of Measure
The API in this section interacts with units of measure. Read/Get operations only. Update/Write operations interact through the quantity API.

## `List Units of Measure (Account path)`

<a id="opIdUnit_List Units of Measure (Account path)"></a>

Returns a list of all available units of measure in the system.

<h3>Request</h3>

```text 
GET /api/v1/Account/{accountId}/sds/{serviceInstanceId}/Units
?filter={filter}&skip={skip}&count={count}&orderby={orderby}
```

<h4>Parameters</h4>

`string accountId`
<br/><br/>`string serviceInstanceId`
<br/><br/>`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>
`[optional] string filter`
<br/>Filter expression.<br/><br/>`[optional] integer skip`
<br/>Parameter representing the zero-based offset of the first SdsUomQuantity to retrieve. If not specified, a default value of 0 is used<br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of SdsUomQuantity to retrieve. If not specified, a default value of 100 is used<br/><br/>`[optional] string orderby`
<br/>Parameter representing sorted order of returned objects. A field name is required. The sorting is based on the stored values for the given field.<br/>For example, ``orderby=name`` would sort the returned results by the ``name`` values (ascending by default).<br/>Additionally, a value can be provided along with the field name to identify whether to sort ascending or descending,<br/>by using values ``asc`` or ``desc``, respectively.<br/>For example, ``orderby=name desc`` would sort the returned results by the ``name`` values, descending.<br/>If no value is specified, there is no sorting of results.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[SdsUom](#schemasdsuom)[]|Returns a list of `SdsUom` objects|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was invalid or missing|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

<h4>Example response body</h4>

> 200 Response

```json
HTTP/1.1 200
Content-Type: application/json
[
{
    "Id":"count",
    "Abbreviation":"count",
    "Name":"count",
    "DisplayName":"count",
    "QuantityId":"Quantity",
    "ConversionFactor":1
},
{
    "Id":"Ampere hour",
    "Abbreviation":"Ah",
    "Name":"Ampere hour",
    "DisplayName":"Ampere hour",
    "QuantityId":"Electric Charge",
    "ConversionFactor":3600
},
{
    "Id":"coulomb",
    "Abbreviation":"C",
    "Name":"coulomb",
    "DisplayName":"coulomb",
    "QuantityId":"Electric Charge",
    "ConversionFactor":1
}
]
```
> 400 Response ([ErrorResponseBody](#schemaerrorresponsebody))

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  }
}
```

---

## `List Units of Measure (Tenants path)`

<a id="opIdUnit_List Units of Measure (Tenants path)"></a>

Returns a list of all available units of measure in the system.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Units
?filter={filter}&skip={skip}&count={count}&orderby={orderby}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>
`[optional] string filter`
<br/>Filter expression.<br/><br/>`[optional] integer skip`
<br/>Parameter representing the zero-based offset of the first SdsUomQuantity to retrieve. If not specified, a default value of 0 is used<br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of SdsUomQuantity to retrieve. If not specified, a default value of 100 is used<br/><br/>`[optional] string orderby`
<br/>Parameter representing sorted order of returned objects. A field name is required. The sorting is based on the stored values for the given field.<br/>For example, ``orderby=name`` would sort the returned results by the ``name`` values (ascending by default).<br/>Additionally, a value can be provided along with the field name to identify whether to sort ascending or descending,<br/>by using values ``asc`` or ``desc``, respectively.<br/>For example, ``orderby=name desc`` would sort the returned results by the ``name`` values, descending.<br/>If no value is specified, there is no sorting of results.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[SdsUom](#schemasdsuom)[]|Returns a list of `SdsUom` objects|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was invalid or missing|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

<h4>Example response body</h4>

> 200 Response

```json
HTTP/1.1 200
Content-Type: application/json
[
{
    "Id":"count",
    "Abbreviation":"count",
    "Name":"count",
    "DisplayName":"count",
    "QuantityId":"Quantity",
    "ConversionFactor":1
},
{
    "Id":"Ampere hour",
    "Abbreviation":"Ah",
    "Name":"Ampere hour",
    "DisplayName":"Ampere hour",
    "QuantityId":"Electric Charge",
    "ConversionFactor":3600
},
{
    "Id":"coulomb",
    "Abbreviation":"C",
    "Name":"coulomb",
    "DisplayName":"coulomb",
    "QuantityId":"Electric Charge",
    "ConversionFactor":1
}
]
```
> 400 Response ([ErrorResponseBody](#schemaerrorresponsebody))

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  }
}
```

---

## `Get Unit of Measure (Account path)`

<a id="opIdUnit_Get Unit of Measure (Account path)"></a>

Returns the unit of measure corresponding to the specified uomId within a given namespace.

<h3>Request</h3>

```text 
GET /api/v1/Account/{accountId}/sds/{serviceInstanceId}/Units/{uomId}
```

<h4>Parameters</h4>

`string accountId`
<br/><br/>`string serviceInstanceId`
<br/><br/>`string uomId`
<br/>The unit of measure identifier<br/><br/>`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[SdsUom](#schemasdsuom)|Returns the `SdsUom`|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was invalid or missing|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

<h4>Example response body</h4>

> 200 Response

```json
HTTP/1.1 200
Content-Type: application/json
{
    "Id":"ounce",
    "Abbreviation":"oz",
    "Name":"ounce",
    "DisplayName":"ounce",
    "QuantityId":"Mass",
    "ConversionFactor":0.028349523
}
```
> 400 Response ([ErrorResponseBody](#schemaerrorresponsebody))

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  }
}
```

---

## `Get Unit of Measure (Tenants path)`

<a id="opIdUnit_Get Unit of Measure (Tenants path)"></a>

Returns the unit of measure corresponding to the specified uomId within a given namespace.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Units/{uomId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string uomId`
<br/>The unit of measure identifier<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[SdsUom](#schemasdsuom)|Returns the `SdsUom`|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was invalid or missing|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

<h4>Example response body</h4>

> 200 Response

```json
HTTP/1.1 200
Content-Type: application/json
{
    "Id":"ounce",
    "Abbreviation":"oz",
    "Name":"ounce",
    "DisplayName":"ounce",
    "QuantityId":"Mass",
    "ConversionFactor":0.028349523
}
```
> 400 Response ([ErrorResponseBody](#schemaerrorresponsebody))

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  }
}
```

---
## Definitions

### SdsUom

<a id="schemasdsuom"></a>
<a id="schema_SdsUom"></a>
<a id="tocSsdsuom"></a>
<a id="tocssdsuom"></a>

DataContract representing a unit of measure.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Unique identifier for this unit of measure.|
|Abbreviation|string|false|true|Abbreviation for this unit of measure.|
|Name|string|false|true|Full name for this unit of measure.|
|DisplayName|string|false|true|Display name for this unit of measure.|
|QuantityId|string|false|true|The Id of the quantity that this unit is a measure of.|
|ConversionFactor|double|false|false|When a value of this unit is multiplied by the ConversionFactor and then incremented by the ConversionOffset, the value in terms of the base unit of the corresponding quantity is returned.|
|ConversionOffset|double|false|false|When a value of this unit is multiplied by the ConversionFactor and then incremented by the ConversionOffset, the value in terms of the base unit of the corresponding quantity is returned.|
|CreatedDate|date-time|false|false|The DateTime in ISO 8601 extended format and UTC time standard when the SdsUom was created. This value is set upon object creation and is immutable. The default value of the CreatedDate property of existing objects is DateTime.MinValue. This property cannot be modified by users.|
|ModifiedDate|date-time|false|false|The DateTime in ISO 8601 extended format and UTC time standard when the SdsUom was last modified. This value is initialized upon object creation and is updated each time an object's properties are successfully modified. The ModifiedDate property of an object will also update if the object's ACL or owner is modified. The default value of the ModifiedDate property of existing objects is DateTime.MinValue. This property cannot be modified by users.|

```json
{
  "Id": "string",
  "Abbreviation": "string",
  "Name": "string",
  "DisplayName": "string",
  "QuantityId": "string",
  "ConversionFactor": 0,
  "ConversionOffset": 0,
  "CreatedDate": "2019-08-24T14:15:22Z",
  "ModifiedDate": "2019-08-24T14:15:22Z"
}

```

---

### ErrorResponseBody

<a id="schemaerrorresponsebody"></a>
<a id="schema_ErrorResponseBody"></a>
<a id="tocSerrorresponsebody"></a>
<a id="tocserrorresponsebody"></a>

The error response contains standard details on the cause and resolution of the error.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|false|true|Operation unique identifier of action that caused the error|
|Error|string|false|true|Error description|
|Reason|string|false|true|Reason for the error|
|Resolution|string|false|true|Resolution to resolve the error|
|Parameters|object|false|true|IDs or values that are creating or are affected by the error|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  }
}

```

---

