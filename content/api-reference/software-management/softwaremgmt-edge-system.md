---
uid: softwaremgmt-edge-system

---

# Edge System
APIs for managing edge systems

## `List Edge Systems`

<a id="opIdEdgeSystem_List Edge Systems"></a>

Returns a list of Edge Systems.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/SoftwareManagement/Systems
?skip={skip}&count={count}&orderBy={orderBy}&query={query}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>
`[optional] integer skip`
<br/>Parameter representing the zero-based offset of the first Edge System to retrieve. If unspecified, a default value of 0 is used. Value must be greater than or equal to 0.<br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of objects to retrieve. If unspecified, a default value of 100 is used. Value cannot be less than 1 or greater than 1000.<br/><br/>`[optional] string orderBy`
<br/>Query parameter to specify sort order. Valid sort order properties are EdgeSystemId, DeviceName, Name, Type, Tags, Status, StatusDescription, LastContactedTime, and SoftwareVersion. If unspecified, a default value of 'name asc' is used.<br/><br/>`[optional] string query`
<br/>Query parameter to specify filter. Valid filter properties are EdgeSystemId, DeviceName, Name, Type, Tags, Status, StatusDescription, LastContactedTime, and SoftwareVersion.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[EdgeSystem](#schemaedgesystem)[]|List of edge systems.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

<h4>Response Headers</h4>

|Status|Header|Type|Description|
|---|---|---|---|
|200|Total-Count|integer|The total number of edge systems.|

<h4>Example response body</h4>

> 200 Response ([EdgeSystem](#schemaedgesystem)[])

```json
[
  {
    "Id": "string",
    "DeviceName": "string",
    "Name": "string",
    "Type": "string",
    "SoftwareVersion": "string",
    "CreatedDate": "2019-08-24T14:15:22Z",
    "LastContactedTime": "2019-08-24T14:15:22Z",
    "ModifiedDate": "2019-08-24T14:15:22Z",
    "ModifiedBy": "string",
    "ModifiedByType": 1,
    "Status": 1,
    "StatusDescription": "string",
    "SystemDiagnosticsStreamId": "string",
    "Components": [
      {
        "Id": "string",
        "Name": "string",
        "ComponentType": "string",
        "DeviceStatusStreamId": "string",
        "NextHealthMessageExpectedStreamId": "string",
        "DiagnosticsStreams": [
          {
            "Id": "string",
            "NamespaceId": "string",
            "TypeId": "string"
          }
        ],
        "Status": 1,
        "StatusDescription": "string",
        "Errors": [
          "string"
        ]
      }
    ],
    "Tags": [
      "string"
    ],
    "IsVisible": true
  }
]
```

---

## `Get Edge Systems Summary`

<a id="opIdEdgeSystem_Get Edge Systems Summary"></a>

Returns header information for Edge Systems.

<h3>Request</h3>

```text 
HEAD /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/SoftwareManagement/Systems
?query={query}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>
`[optional] string query`
<br/>Query parameter to specify a filter. Valid filter properties are EdgeSystemId, DeviceName, Name, Type, Tags, Status, StatusDescription, LastContactedTime, and SoftwareVersion.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|Headers for Edge Systems found.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

<h4>Response Headers</h4>

|Status|Header|Type|Description|
|---|---|---|---|
|204|Total-Count|integer|The total number of edge systems.|

---

## `Get Edge System`

<a id="opIdEdgeSystem_Get Edge System"></a>

Returns a specific Edge System.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/SoftwareManagement/Systems/{edgeSystemId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string edgeSystemId`
<br/>Edge System identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[EdgeSystem](#schemaedgesystem)|Edge System with the specified identifier.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|404|[ErrorResponse](#schemaerrorresponse)|Edge System not found.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

<h4>Example response body</h4>

> 200 Response ([EdgeSystem](#schemaedgesystem))

```json
{
  "Id": "string",
  "DeviceName": "string",
  "Name": "string",
  "Type": "string",
  "SoftwareVersion": "string",
  "CreatedDate": "2019-08-24T14:15:22Z",
  "LastContactedTime": "2019-08-24T14:15:22Z",
  "ModifiedDate": "2019-08-24T14:15:22Z",
  "ModifiedBy": "string",
  "ModifiedByType": 1,
  "Status": 1,
  "StatusDescription": "string",
  "SystemDiagnosticsStreamId": "string",
  "Components": [
    {
      "Id": "string",
      "Name": "string",
      "ComponentType": "string",
      "DeviceStatusStreamId": "string",
      "NextHealthMessageExpectedStreamId": "string",
      "DiagnosticsStreams": [
        {
          "Id": "string",
          "NamespaceId": "string",
          "TypeId": "string"
        }
      ],
      "Status": 1,
      "StatusDescription": "string",
      "Errors": [
        "string"
      ]
    }
  ],
  "Tags": [
    "string"
  ],
  "IsVisible": true
}
```

---

## `Show Or Hide System`

<a id="opIdEdgeSystem_Show Or Hide System"></a>

Reactivates a specific System.

<h3>Request</h3>

```text 
PUT /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/SoftwareManagement/Systems/{edgeSystemId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string edgeSystemId`
<br/>Edge System identifier.<br/><br/>

<h4>Request Body</h4>

object to reactivate.<br/>

```json
{
  "Id": "string",
  "DeviceName": "string",
  "Type": "string",
  "SoftwareVersion": "string",
  "CreatedDate": "2019-08-24T14:15:22Z",
  "LastContactedTime": "2019-08-24T14:15:22Z",
  "ModifiedDate": "2019-08-24T14:15:22Z",
  "ModifiedBy": "string",
  "ModifiedByType": 1,
  "Status": 1,
  "StatusDescription": "string",
  "SystemDiagnosticsStreamId": "string",
  "Components": [
    {
      "Id": "string",
      "Name": "string",
      "ComponentType": "string",
      "DeviceStatusStreamId": "string",
      "NextHealthMessageExpectedStreamId": "string",
      "DiagnosticsStreams": [
        {
          "Id": "string",
          "NamespaceId": "string",
          "TypeId": "string"
        }
      ],
      "Status": 1,
      "StatusDescription": "string",
      "Errors": [
        "string"
      ]
    }
  ],
  "Tags": [
    "string"
  ],
  "IsVisible": true
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Success.|
|204|None|No content.|
|400|[ErrorResponse](#schemaerrorresponse)|None|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|404|[ErrorResponse](#schemaerrorresponse)|None|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

---

## `List Tags`

<a id="opIdEdgeSystem_List Tags"></a>

Returns a list of tags present on Edge Systems.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/SoftwareManagement/Tags
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|List of tags|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

<h4>Response Headers</h4>

|Status|Header|Type|Description|
|---|---|---|---|
|200|Total-Count|integer|The total number of tags.|

---

## `Update Tags`

<a id="opIdEdgeSystem_Update Tags"></a>

Creates or updates the tags of a specific Edge System.

<h3>Request</h3>

```text 
PUT /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/SoftwareManagement/Systems/{edgeSystemId}/Tags
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string edgeSystemId`
<br/>Edge System identifier.<br/><br/>

<h4>Request Body</h4>

Serialized list of tags.<br/>

```json
[
  "string"
]
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|No content.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

---

## `Get Configuration`

<a id="opIdEdgeSystem_Get Configuration"></a>

Returns an Edge System Configuration.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/SoftwareManagement/Systems/{edgeSystemId}/Configuration
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string edgeSystemId`
<br/>Edge System identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Configuration for the specified Edge System.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|404|[ErrorResponse](#schemaerrorresponse)|Configuration not found.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

---

## `Create Configuration`

<a id="opIdEdgeSystem_Create Configuration"></a>

Creates an Edge System Configuration. Does not save any secrets supplied as part of the edge system configuration.

<h3>Request</h3>

```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/SoftwareManagement/Systems/{edgeSystemId}/Configuration
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string edgeSystemId`
<br/>Edge System identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|201|Inline|Configuration created.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|409|[ErrorResponse](#schemaerrorresponse)|Conflict.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

---

## `Update Configuration`

<a id="opIdEdgeSystem_Update Configuration"></a>

Updates an Edge System Configuration. Does not save any secrets supplied as part of the edge system configuration.

<h3>Request</h3>

```text 
PUT /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/SoftwareManagement/Systems/{edgeSystemId}/Configuration
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string edgeSystemId`
<br/>Edge System identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|No content.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

---

## `Delete Configuration`

<a id="opIdEdgeSystem_Delete Configuration"></a>

Deletes an Edge System Configuration.

<h3>Request</h3>

```text 
DELETE /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/SoftwareManagement/Systems/{edgeSystemId}/Configuration
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>`string namespaceId`
<br/>Namespace identifier.<br/><br/>`string edgeSystemId`
<br/>Edge System identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|No content.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|404|[ErrorResponse](#schemaerrorresponse)|Configuration not found.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

---
## Definitions

### ErrorResponse

<a id="schemaerrorresponse"></a>
<a id="schema_ErrorResponse"></a>
<a id="tocSerrorresponse"></a>
<a id="tocserrorresponse"></a>

Object returned whenever there is an error.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|true|false|Gets or sets operationId of action that caused the Error.|
|Error|string|true|false|Gets or sets error description.|
|Reason|string|true|false|Gets or sets reason for the Error.|
|Resolution|string|true|false|Gets or sets what can be done to resolve the Error.|
|DynamicProperties|object|false|true|Gets additional properties.|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "DynamicProperties": {
    "property1": null,
    "property2": null
  },
  "property1": null,
  "property2": null
}

```

---

### EdgeSystem

<a id="schemaedgesystem"></a>
<a id="schema_EdgeSystem"></a>
<a id="tocSedgesystem"></a>
<a id="tocsedgesystem"></a>

Edge system response model

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Edge system unique identifier.|
|DeviceName|string|false|true|Device name for this edge system.|
|Name|string|false|true|Edge system name.|
|Type|string|false|true|Type name for this edge system.|
|SoftwareVersion|string|false|true|Version for this edge system.|
|CreatedDate|date-time|false|false|Time at which the edge system was created.|
|LastContactedTime|date-time|false|false|Time at which the edge system was last contacted.|
|ModifiedDate|date-time|false|true|Time at which the edge system was last modified.|
|ModifiedBy|string|false|true|Identifier for who modified the edge system most recently.|
|ModifiedByType|[TrusteeType](#schematrusteetype)|false|true|Type identifier for who modified the edge system most recently.|
|Status|[StatusCategory](#schemastatuscategory)|false|false|Value of the component's status for the component with the highest priority status.|
|StatusDescription|string|false|true|Value of the component's status description for the component with the highest priority status description.|
|SystemDiagnosticsStreamId|string|false|true|System diagnostics stream identifier for this edge system.|
|Components|[[Component](#schemacomponent)]|false|true|List of components for this edge system.|
|Tags|string[]|false|true|List of tags for this edge system.|
|IsVisible|boolean|false|false|Whether the system should be visible to the user/client.|

```json
{
  "Id": "string",
  "DeviceName": "string",
  "Name": "string",
  "Type": "string",
  "SoftwareVersion": "string",
  "CreatedDate": "2019-08-24T14:15:22Z",
  "LastContactedTime": "2019-08-24T14:15:22Z",
  "ModifiedDate": "2019-08-24T14:15:22Z",
  "ModifiedBy": "string",
  "ModifiedByType": 1,
  "Status": 1,
  "StatusDescription": "string",
  "SystemDiagnosticsStreamId": "string",
  "Components": [
    {
      "Id": "string",
      "Name": "string",
      "ComponentType": "string",
      "DeviceStatusStreamId": "string",
      "NextHealthMessageExpectedStreamId": "string",
      "DiagnosticsStreams": [
        {
          "Id": "string",
          "NamespaceId": "string",
          "TypeId": "string"
        }
      ],
      "Status": 1,
      "StatusDescription": "string",
      "Errors": [
        "string"
      ]
    }
  ],
  "Tags": [
    "string"
  ],
  "IsVisible": true
}

```

---

### TrusteeType

<a id="schematrusteetype"></a>
<a id="schema_TrusteeType"></a>
<a id="tocStrusteetype"></a>
<a id="tocstrusteetype"></a>

<h4>Enumerated Values</h4>

|Property|Value|Description|
|---|---|---|
|User|1|undefined|
|Client|2|undefined|
|Role|3|undefined|

---

### StatusCategory

<a id="schemastatuscategory"></a>
<a id="schema_StatusCategory"></a>
<a id="tocSstatuscategory"></a>
<a id="tocsstatuscategory"></a>

Status category enumeration

<h4>Enumerated Values</h4>

|Property|Value|Description|
|---|---|---|
|Bad|1|Status category enumeration|
|Warning|2|Status category enumeration|
|Discovered|3|Status category enumeration|
|Good|4|Status category enumeration|
|Stopped|5|Status category enumeration|

---

### Component

<a id="schemacomponent"></a>
<a id="schema_Component"></a>
<a id="tocScomponent"></a>
<a id="tocscomponent"></a>

Component response model

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Component unique identifier.|
|Name|string|false|true|Component unique identifier.|
|ComponentType|string|false|true|Type name for this component.|
|DeviceStatusStreamId|string|false|true|Stream identifier used to retrieve the component's status.|
|NextHealthMessageExpectedStreamId|string|false|true|Stream identifier used to retrieve the next health message expected time.|
|DiagnosticsStreams|[[DiagnosticsStream](#schemadiagnosticsstream)]|false|true|List of diagnostics streams.|
|Status|[StatusCategory](#schemastatuscategory)|false|false|Last known status for this component.|
|StatusDescription|string|false|true|Last known status description for this component.|
|Errors|string[]|false|true|List of errors for this component.|

```json
{
  "Id": "string",
  "Name": "string",
  "ComponentType": "string",
  "DeviceStatusStreamId": "string",
  "NextHealthMessageExpectedStreamId": "string",
  "DiagnosticsStreams": [
    {
      "Id": "string",
      "NamespaceId": "string",
      "TypeId": "string"
    }
  ],
  "Status": 1,
  "StatusDescription": "string",
  "Errors": [
    "string"
  ]
}

```

---

### DiagnosticsStream

<a id="schemadiagnosticsstream"></a>
<a id="schema_DiagnosticsStream"></a>
<a id="tocSdiagnosticsstream"></a>
<a id="tocsdiagnosticsstream"></a>

Diagnostics stream response model

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Unique identifier for this diagnostics stream.|
|NamespaceId|string|false|true|Namespace identifier for this diagnostics stream.|
|TypeId|string|false|true|Type name for this diagnostics stream.|

```json
{
  "Id": "string",
  "NamespaceId": "string",
  "TypeId": "string"
}

```

---

### EdgeSystem2

<a id="schemaedgesystem2"></a>
<a id="schema_EdgeSystem2"></a>
<a id="tocSedgesystem2"></a>
<a id="tocsedgesystem2"></a>

Edge system request model

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Edge system unique identifier.|
|DeviceName|string|false|true|Device name for this edge system.|
|Type|string|false|true|Type name for this edge system.|
|SoftwareVersion|string|false|true|Version for this edge system.|
|CreatedDate|date-time|false|false|Time at which the edge system was created.|
|LastContactedTime|date-time|false|false|Time at which the edge system was last contacted.|
|ModifiedDate|date-time|false|true|Time at which the edge system was last modified.|
|ModifiedBy|string|false|true|Identifier for who modified the edge system most recently.|
|ModifiedByType|[TrusteeType](#schematrusteetype)|false|true|Type identifier for who modified the edge system most recently.|
|Status|[StatusCategory](#schemastatuscategory)|false|false|Value of the component's status for the component with the highest priority status.|
|StatusDescription|string|false|true|Value of the component's status description for the component with the highest priority status description.|
|SystemDiagnosticsStreamId|string|false|true|System diagnostics stream identifier for this edge system.|
|Components|[[Component2](#schemacomponent2)]|false|true|List of components for this edge system.|
|Tags|string[]|false|true|List of tags for this edge system.|
|IsVisible|boolean|false|false|Whether the system should be visible to the user/client.|

```json
{
  "Id": "string",
  "DeviceName": "string",
  "Type": "string",
  "SoftwareVersion": "string",
  "CreatedDate": "2019-08-24T14:15:22Z",
  "LastContactedTime": "2019-08-24T14:15:22Z",
  "ModifiedDate": "2019-08-24T14:15:22Z",
  "ModifiedBy": "string",
  "ModifiedByType": 1,
  "Status": 1,
  "StatusDescription": "string",
  "SystemDiagnosticsStreamId": "string",
  "Components": [
    {
      "Id": "string",
      "Name": "string",
      "ComponentType": "string",
      "DeviceStatusStreamId": "string",
      "NextHealthMessageExpectedStreamId": "string",
      "DiagnosticsStreams": [
        {
          "Id": "string",
          "NamespaceId": "string",
          "TypeId": "string"
        }
      ],
      "Status": 1,
      "StatusDescription": "string",
      "Errors": [
        "string"
      ]
    }
  ],
  "Tags": [
    "string"
  ],
  "IsVisible": true
}

```

---

### Component2

<a id="schemacomponent2"></a>
<a id="schema_Component2"></a>
<a id="tocScomponent2"></a>
<a id="tocscomponent2"></a>

Edge system component request model

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Component unique identifier.|
|Name|string|false|true|Component data source or the type itself|
|ComponentType|string|false|true|Type name for this component.|
|DeviceStatusStreamId|string|false|true|Stream identifier used to retrieve the component's status.|
|NextHealthMessageExpectedStreamId|string|false|true|Stream identifier used to retrieve the next health message expected time.|
|DiagnosticsStreams|[[DiagnosticsStream2](#schemadiagnosticsstream2)]|false|true|List of diagnostics streams.|
|Status|[StatusCategory](#schemastatuscategory)|false|false|Last known status for this component.|
|StatusDescription|string|false|true|Last known status description for this component.|
|Errors|string[]|false|true|List of errors for this component.|

```json
{
  "Id": "string",
  "Name": "string",
  "ComponentType": "string",
  "DeviceStatusStreamId": "string",
  "NextHealthMessageExpectedStreamId": "string",
  "DiagnosticsStreams": [
    {
      "Id": "string",
      "NamespaceId": "string",
      "TypeId": "string"
    }
  ],
  "Status": 1,
  "StatusDescription": "string",
  "Errors": [
    "string"
  ]
}

```

---

### DiagnosticsStream2

<a id="schemadiagnosticsstream2"></a>
<a id="schema_DiagnosticsStream2"></a>
<a id="tocSdiagnosticsstream2"></a>
<a id="tocsdiagnosticsstream2"></a>

Diagnostics stream request model

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Unique identifier for this diagnostics stream.|
|NamespaceId|string|false|true|Namespace identifier for this diagnostics stream.|
|TypeId|string|false|true|Type name for this diagnostics stream.|

```json
{
  "Id": "string",
  "NamespaceId": "string",
  "TypeId": "string"
}

```

---

