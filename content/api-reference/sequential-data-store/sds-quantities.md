---
uid: sds-quantities

---

# Quantities
Controller handling requests that are routed to {namespaceId}/Quantities/

## `List Quantities`

<a id="opIdQuantity_List Quantities"></a>

Returns a list of all quantities available within a given namespace

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Quantities
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

#### Request Headers

|Header|Type|Required|Description|
|---|---|---|---|

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[SdsUomQuantity](#schemasdsuomquantity)[]|Returns a list of `SdsUomQuantity` objects|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

#### Example response body
> 200 Response

```json
[
  {
    "Id": "string",
    "Name": "string",
    "BaseUom": {
      "Id": "string",
      "Abbreviation": "string",
      "Name": "string",
      "DisplayName": "string",
      "QuantityId": "string",
      "ConversionFactor": 0,
      "ConversionOffset": 0
    },
    "Dimensions": [
      0
    ]
  }
]
```

---

## `Get Quantity`

<a id="opIdQuantity_Get Quantity"></a>

Returns the quantity corresponding to the specified quantityId within a given namespace

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Quantities/{quantityId}
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string quantityId`
<br/><br/>

#### Request Headers

|Header|Type|Required|Description|
|---|---|---|---|

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[SdsUomQuantity](#schemasdsuomquantity)|Returns the `SdsUomQuantity`|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

#### Example response body
> 200 Response

```json
{
  "Id": "string",
  "Name": "string",
  "BaseUom": {
    "Id": "string",
    "Abbreviation": "string",
    "Name": "string",
    "DisplayName": "string",
    "QuantityId": "string",
    "ConversionFactor": 0,
    "ConversionOffset": 0
  },
  "Dimensions": [
    0
  ]
}
```

---

## `List Quantity Units of Measure`

<a id="opIdQuantity_List Quantity Units of Measure"></a>

Returns the list of units of measure that belongs to the quantity with the specified quantityId

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Quantities/{quantityId}/Units
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string quantityId`
<br/><br/>

#### Request Headers

|Header|Type|Required|Description|
|---|---|---|---|

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[SdsUom](#schemasdsuom)[]|Returns a list of `SdsUom` objects|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

#### Example response body
> 200 Response

```json
[
  {
    "Id": "string",
    "Abbreviation": "string",
    "Name": "string",
    "DisplayName": "string",
    "QuantityId": "string",
    "ConversionFactor": 0,
    "ConversionOffset": 0
  }
]
```

---

## `Get Unit of Measure`

<a id="opIdQuantity_Get Unit of Measure"></a>

Returns the unit of measure associated with the specified uomId belonging to the quantity with the specified quantityId

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Quantities/{quantityId}/Units/{uomId}
```

#### Parameters

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string quantityId`
<br/><br/>`string uomId`
<br/><br/>

#### Request Headers

|Header|Type|Required|Description|
|---|---|---|---|

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[SdsUom](#schemasdsuom)|Returns the `SdsUom`|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Missing or invalid inputs|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden|
|404|[ErrorResponseBody](#schemaerrorresponsebody)|One of the resources specified was not found|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|An error occurred while processing the request|
|503|[ErrorResponseBody](#schemaerrorresponsebody)|Service Unavailable|

#### Example response body
> 200 Response

```json
{
  "Id": "string",
  "Abbreviation": "string",
  "Name": "string",
  "DisplayName": "string",
  "QuantityId": "string",
  "ConversionFactor": 0,
  "ConversionOffset": 0
}
```

---
## Definitions

### SdsUomQuantity

<a id="schemasdsuomquantity"></a>
<a id="schema_SdsUomQuantity"></a>
<a id="tocSsdsuomquantity"></a>
<a id="tocssdsuomquantity"></a>

DataContract representing a measurable quantity. i.e. A unit of measure 'meter' would measure a quantity 'length'

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Unique identifier for this quantity.|
|Name|string|false|true|Friendly name for this quantity|
|BaseUom|[SdsUom](#schemasdsuom)|false|true|The base unit of measurement for this quantity. All other uom's measuring this quantity will be calculated relative to the base uom.|
|Dimensions|[integer]|false|true|Powers of each dimension that define this quantity. This array must have a length of 7. Dimensions represented in index order are Length, Mass, Time, Electric Current, Thermodynamic Temperature, Amount of Substance, and Luminous Density i.e. A velocity quantity would have values [1,0,-1,0,0,0,0] for (length)/(time)|

```json
{
  "Id": "string",
  "Name": "string",
  "BaseUom": {
    "Id": "string",
    "Abbreviation": "string",
    "Name": "string",
    "DisplayName": "string",
    "QuantityId": "string",
    "ConversionFactor": 0,
    "ConversionOffset": 0
  },
  "Dimensions": [
    0
  ]
}

```

---

### SdsUom

<a id="schemasdsuom"></a>
<a id="schema_SdsUom"></a>
<a id="tocSsdsuom"></a>
<a id="tocssdsuom"></a>

DataContract representing a unit of measure

#### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Unique identifier for this unit of measure.|
|Abbreviation|string|false|true|Abbreviation for this unit of measure.|
|Name|string|false|true|Full name for this unit of measure.|
|DisplayName|string|false|true|Display name for this unit of measure.|
|QuantityId|string|false|true|The Id of the quantity that this unit is a measure of.|
|ConversionFactor|double|false|false|When a value of this unit is multiplied by the ConversionFactor and then incremented by the ConversionOffset, the value in terms of the base unit of the corresponding quantity is returned.|
|ConversionOffset|double|false|false|When a value of this unit is multiplied by the ConversionFactor and then incremented by the ConversionOffset, the value in terms of the base unit of the corresponding quantity is returned.|

```json
{
  "Id": "string",
  "Abbreviation": "string",
  "Name": "string",
  "DisplayName": "string",
  "QuantityId": "string",
  "ConversionFactor": 0,
  "ConversionOffset": 0
}

```

---

### ErrorResponseBody

<a id="schemaerrorresponsebody"></a>
<a id="schema_ErrorResponseBody"></a>
<a id="tocSerrorresponsebody"></a>
<a id="tocserrorresponsebody"></a>

Contains the error message format that follows the OCS error standards

#### Properties

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

