---
uid: ""

---

# Bulk Access
Defines the public API endpoints for bulk updating ACLs.

## `List Bulk Access Job Summaries`

<a id="opIdBulkAccess_List Bulk Access Job Summaries"></a>

Retrieves the status of all bulk access update jobs for a given Namespace.

<h3>Request</h3>

```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/bulk/accesscontrol/jobs
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant unique identifier.<br/><br/>`string namespaceId`
<br/>Namespace tenant unique identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[BulkAccessJobSummary](#schemabulkaccessjobsummary)[]|OK. The jobs were successfully retrieved.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized. The client has not been authenticated.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden. The client does not have the required permissions to make the request.|
|408|[ErrorResponse](#schemaerrorresponse)|Request Timeout. The request has timed out.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal Server Error. The server has encountered a situation it doesn't know how to handle.|

<h4>Example response body</h4>

> 200 Response ([BulkAccessJobSummary](#schemabulkaccessjobsummary)[])

```json
[
  {
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "OperationId": "string",
    "StartTime": "2019-08-24T14:15:22Z",
    "EndTime": "2019-08-24T14:15:22Z",
    "Status": 0,
    "Requester": {
      "Type": 1,
      "ObjectId": "string",
      "TenantId": "string"
    },
    "StepsSucceeded": 0,
    "StepsFailed": 0,
    "StepsProcessed": 0,
    "TotalSteps": 0
  }
]
```

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `Create Bulk Access Job`

<a id="opIdBulkAccess_Create Bulk Access Job"></a>

Creates a new bulk access job.

<h3>Request</h3>

```text 
POST /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/bulk/accesscontrol/jobs
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant unique identifier.<br/><br/>`string namespaceId`
<br/>Namespace unique identifier.<br/><br/>

<h4>Request Body</h4>

Input containing information for ACL update operation.<br/>

```json
{
  "AccessControlList": {
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
  "Operation": 0,
  "Scope": 0,
  "ResourceIds": [
    "string"
  ],
  "RoleIds": [
    "string"
  ],
  "ResourceType": 0,
  "Description": "string"
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[BulkAccessJobSummary](#schemabulkaccessjobsummary)|OK. The service bus message was successfully sent.|
|400|[ErrorResponseBody](#schemaerrorresponsebody)|Bad Request. The server could not understand the request.|
|401|[ErrorResponseBody](#schemaerrorresponsebody)|Unauthorized. The client has not been authenticated.|
|403|[ErrorResponseBody](#schemaerrorresponsebody)|Forbidden. The client does not have the required permissions to make the request.|
|408|[ErrorResponseBody](#schemaerrorresponsebody)|Request Timeout. The request has timed out.|
|500|[ErrorResponseBody](#schemaerrorresponsebody)|Internal Server Error. The server has encountered a situation it doesn't know how to handle.|

<h4>Example response body</h4>

> 200 Response ([BulkAccessJobSummary](#schemabulkaccessjobsummary))

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "OperationId": "string",
  "StartTime": "2019-08-24T14:15:22Z",
  "EndTime": "2019-08-24T14:15:22Z",
  "Status": 0,
  "Requester": {
    "Type": 1,
    "ObjectId": "string",
    "TenantId": "string"
  },
  "StepsSucceeded": 0,
  "StepsFailed": 0,
  "StepsProcessed": 0,
  "TotalSteps": 0
}
```

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `Get Bulk Access Job Summary`

<a id="opIdBulkAccess_Get Bulk Access Job Summary"></a>

Retrieves the summary of an existing bulk access job.

<h3>Request</h3>

```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/bulk/accesscontrol/jobs/{jobId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant unique identifier.<br/><br/>`string namespaceId`
<br/>Namespace unique identifier.<br/><br/>`string jobId`
<br/>Job unique identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[BulkAccessJobSummary](#schemabulkaccessjobsummary)|OK. The Job was successfully retrieved.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized. The client has not been authenticated.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden. The client does not have the required permissions to make the request.|
|408|[ErrorResponse](#schemaerrorresponse)|Request Timeout. The request has timed out.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal Server Error. The server has encountered a situation it doesn't know how to handle.|

<h4>Example response body</h4>

> 200 Response ([BulkAccessJobSummary](#schemabulkaccessjobsummary))

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "OperationId": "string",
  "StartTime": "2019-08-24T14:15:22Z",
  "EndTime": "2019-08-24T14:15:22Z",
  "Status": 0,
  "Requester": {
    "Type": 1,
    "ObjectId": "string",
    "TenantId": "string"
  },
  "StepsSucceeded": 0,
  "StepsFailed": 0,
  "StepsProcessed": 0,
  "TotalSteps": 0
}
```

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `List Bulk Access Job Steps`

<a id="opIdBulkAccess_List Bulk Access Job Steps"></a>

Retrieves the job steps of an existing bulk access job.

<h3>Request</h3>

```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/bulk/accesscontrol/jobs/{jobId}/jobsteps
?filterBy={filterBy}&skip={skip}&count={count}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant unique identifier.<br/><br/>`string namespaceId`
<br/>Namespace unique identifier.<br/><br/>`string jobId`
<br/>Job unique identifier.<br/><br/>
`[optional] any filterBy`
<br/>Filter to determine if successful, failed, or all job steps are returned.<br/><br/>`[optional] integer skip`
<br/>Parameter representing the zero-based offset of the first object to retrieve. If unspecified, a default value of 0 is used.<br/><br/>`[optional] integer count`
<br/>Maximum number of job steps to be returned.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[BulkAccessJobStep](#schemabulkaccessjobstep)[]|OK. The Job was successfully retrieved.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized. The client has not been authenticated.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden. The client does not have the required permissions to make the request.|
|408|[ErrorResponse](#schemaerrorresponse)|Request Timeout. The request has timed out.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal Server Error. The server has encountered a situation it doesn't know how to handle.|

<h4>Example response body</h4>

> 200 Response ([BulkAccessJobStep](#schemabulkaccessjobstep)[])

```json
[
  {
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "StartTime": "2019-08-24T14:15:22Z",
    "EndTime": "2019-08-24T14:15:22Z",
    "Status": 0,
    "Errors": [
      {
        "OperationId": "string",
        "Error": "string",
        "Reason": "string",
        "Resolution": "string"
      }
    ],
    "ResourceId": "string"
  }
]
```

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---
## Definitions

### BulkAccessJobSummary

<a id="schemabulkaccessjobsummary"></a>
<a id="schema_BulkAccessJobSummary"></a>
<a id="tocSbulkaccessjobsummary"></a>
<a id="tocsbulkaccessjobsummary"></a>

Summary object of a Job.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Identifier of the Job.|
|Name|string|false|true|Name of the Job.|
|Description|string|false|true|Description of the Job.|
|OperationId|string|false|true|Operation ID of the Job.|
|StartTime|date-time|false|true|Start time of the Job.|
|EndTime|date-time|false|true|End time of the Job.|
|Status|[Status](#schemastatus)|false|false|Status of the Job.|
|Requester|[Trustee](#schematrustee)|false|true|Requester of the Job.|
|StepsSucceeded|int32|false|false|Number of succeeded steps of the Job.|
|StepsFailed|int32|false|false|Number of failed steps of the Job.|
|StepsProcessed|int32|false|false|Number of steps of the Job that have finished, regardless of status.|
|TotalSteps|int32|false|false|Total count of steps of the Job.|

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "OperationId": "string",
  "StartTime": "2019-08-24T14:15:22Z",
  "EndTime": "2019-08-24T14:15:22Z",
  "Status": 0,
  "Requester": {
    "Type": 1,
    "ObjectId": "string",
    "TenantId": "string"
  },
  "StepsSucceeded": 0,
  "StepsFailed": 0,
  "StepsProcessed": 0,
  "TotalSteps": 0
}

```

---

### Status

<a id="schemastatus"></a>
<a id="schema_Status"></a>
<a id="tocSstatus"></a>
<a id="tocsstatus"></a>

<h4>Enumerated Values</h4>

|Property|Value|Description|
|---|---|---|
|Invalid|0||
|NotStarted|1||
|InProgress|2||
|Succeeded|3||
|Cancelled|4||
|Failed|5||
|PartiallySucceeded|6||

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

### ErrorResponseBody

<a id="schemaerrorresponsebody"></a>
<a id="schema_ErrorResponseBody"></a>
<a id="tocSerrorresponsebody"></a>
<a id="tocserrorresponsebody"></a>

```json
{}

```

---

### BulkAccessUpdateInput

<a id="schemabulkaccessupdateinput"></a>
<a id="schema_BulkAccessUpdateInput"></a>
<a id="tocSbulkaccessupdateinput"></a>
<a id="tocsbulkaccessupdateinput"></a>

Input to endpoint for bulk resource Access Control List updating.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|AccessControlList|[AccessControlList](#schemaaccesscontrollist)|false|true|If RoleIds are absent, this Access Control List will be assigned to each resource. If RoleIds are present, it will replace only the Access Control Entries whose trustees match those specified in RoleIds.|
|Operation|[Operation](#schemaoperation)|false|false|Operation type of the request.|
|Scope|[Scope](#schemascope)|false|false|Scope of the request.|
|ResourceIds|string[]|false|true|Identifiers of resources whose AccessControlList is being updated.|
|RoleIds|string[]|false|true|Role identifiers of trustee whose ACEs are being updated. Required for the UpdateRoleAccess operation.|
|ResourceType|[ResourceType](#schemaresourcetype)|false|false|Type of resource being updated.|
|Description|string|false|true|Description for the bulk access update operation. This will be used to populate the description for the corresponding BulkAccessJobSummary object.|

```json
{
  "AccessControlList": {
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
  "Operation": 0,
  "Scope": 0,
  "ResourceIds": [
    "string"
  ],
  "RoleIds": [
    "string"
  ],
  "ResourceType": 0,
  "Description": "string"
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

### Operation

<a id="schemaoperation"></a>
<a id="schema_Operation"></a>
<a id="tocSoperation"></a>
<a id="tocsoperation"></a>

Operation being performed during a bulk access update request.

<h4>Enumerated Values</h4>

|Property|Value|Description|
|---|---|---|
|UpdateRoleAccess|0|Operation being performed during a bulk access update request.|
|UpdateAll|1|Operation being performed during a bulk access update request.|

---

### Scope

<a id="schemascope"></a>
<a id="schema_Scope"></a>
<a id="tocSscope"></a>
<a id="tocsscope"></a>

Scope of a bulk access update operation.

<h4>Enumerated Values</h4>

|Property|Value|Description|
|---|---|---|
|Namespace|0|Scope of a bulk access update operation.|
|Resource|1|Scope of a bulk access update operation.|

---

### ResourceType

<a id="schemaresourcetype"></a>
<a id="schema_ResourceType"></a>
<a id="tocSresourcetype"></a>
<a id="tocsresourcetype"></a>

Type of resource whose access is being bulk updated.

<h4>Enumerated Values</h4>

|Property|Value|Description|
|---|---|---|
|Stream|0|Type of resource whose access is being bulk updated.|

---

### ErrorResponse

<a id="schemaerrorresponse"></a>
<a id="schema_ErrorResponse"></a>
<a id="tocSerrorresponse"></a>
<a id="tocserrorresponse"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|true|false|None|
|Error|string|true|false|None|
|Reason|string|true|false|None|
|Resolution|string|true|false|None|
|DynamicProperties|object|false|true|None|

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

### BulkAccessJobStep

<a id="schemabulkaccessjobstep"></a>
<a id="schema_BulkAccessJobStep"></a>
<a id="tocSbulkaccessjobstep"></a>
<a id="tocsbulkaccessjobstep"></a>

Job Step for the bulk access operation.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|None|
|Name|string|false|true|None|
|Description|string|false|true|None|
|StartTime|date-time|false|true|None|
|EndTime|date-time|false|true|None|
|Status|[Status](#schemastatus)|false|false|None|
|Errors|[[ErrorResponse2](#schemaerrorresponse2)]|false|true|None|
|ResourceId|string|false|true|ID of resource being updated.|

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "StartTime": "2019-08-24T14:15:22Z",
  "EndTime": "2019-08-24T14:15:22Z",
  "Status": 0,
  "Errors": [
    {
      "OperationId": "string",
      "Error": "string",
      "Reason": "string",
      "Resolution": "string"
    }
  ],
  "ResourceId": "string"
}

```

---

### ErrorResponse2

<a id="schemaerrorresponse2"></a>
<a id="schema_ErrorResponse2"></a>
<a id="tocSerrorresponse2"></a>
<a id="tocserrorresponse2"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|false|true|None|
|Error|string|false|true|None|
|Reason|string|false|true|None|
|Resolution|string|false|true|None|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string"
}

```

---

### JobStepFilter

<a id="schemajobstepfilter"></a>
<a id="schema_JobStepFilter"></a>
<a id="tocSjobstepfilter"></a>
<a id="tocsjobstepfilter"></a>

Filter to be applied to bulk access job steps.

<h4>Enumerated Values</h4>

|Property|Value|Description|
|---|---|---|
|Success|0|Returns job steps with status of success.|
|Failure|1|Returns job steps with status of failed.|
|All|2|Returns all job steps.|

---

