

# Log Query
APIs related to querying logs.

## `Get Tenant Logs`

<a id="opIdLog_Get Tenant Logs"></a>

Get logs for a **Tenant**.

### Request
```text 
GET /api/v1/tenants/{tenantId}/logs
?start={start}&end={end}&source={source}&severity={severity}&skip={skip}&count={count}
```

#### Parameters

`string tenantId`
<br/>Id of the tenant.<br/><br/>
`[optional] string start`
<br/>Start timestamp of logs.<br/><br/>`[optional] string end`
<br/>End timestamp of logs.<br/><br/>`[optional] array source`
<br/>Filter the logs by one or more sources. This parameter can be repeated multiple times. Valid sources are: *Account Management* and *Identity Management*. Omit this parameter to retrieve all sources. Source values must be alphanumeric (case insensitive), underscore, and whitespace only, between 1 and 50 characters<br/><br/>`[optional] array severity`
<br/>Filter the logs by one or more severities. This parameter can be repeated multiple times. Valid severities are: *Critical*, *Error*, *Warning*, *Information*, and *Verbose*. Omit this parameter to retrieve all severities.<br/><br/>`[optional] integer skip`
<br/>Number of logs to skip.<br/><br/>`[optional] integer count`
<br/>Maximum number of logs to return.<br/><br/>

#### Enumerated Values

|Parameter|Value|
|---|---|
|severity|0|
|severity|1|
|severity|2|
|severity|3|
|severity|4|

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Customer facing logs for specified tenant.|
|400|None|Missing or invalid inputs.|
|401|None|Unauthorized|
|403|None|Forbidden.|
|500|None|Internal server error.|

---

## `Get Namespace Logs`

<a id="opIdLog_Get Namespace Logs"></a>

Get logs for a **Namespace**.

### Request
```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/logs
?start={start}&end={end}&source={source}&severity={severity}&skip={skip}&count={count}
```

#### Parameters

`string tenantId`
<br/>Id of the tenant.<br/><br/>`string namespaceId`
<br/>Id of the namespace.<br/><br/>
`[optional] string start`
<br/>Start timestamp of logs.<br/><br/>`[optional] string end`
<br/>End timestamp of logs.<br/><br/>`[optional] array source`
<br/>Filter the logs by one or more sources. This parameter can be repeated multiple times. Valid sources are: *Data Ingress*, *Data Storage*, *Data Views*, *Metadata*, *PI to OCS*. Omit this parameter to retrieve all sources. Source values must be alphanumeric (case insensitive), underscore, and whitespace only, between 1 and 50 characters<br/><br/>`[optional] array severity`
<br/>Filter the logs by one or more severities. This parameter can be repeated multiple times. Valid severities are: *Critical*, *Error*, *Warning*, *Information*, and *Verbose*. Omit this parameter to retrieve all severities.<br/><br/>`[optional] integer skip`
<br/>Number of logs to skip.<br/><br/>`[optional] integer count`
<br/>Maximum number of logs to return.<br/><br/>

#### Enumerated Values

|Parameter|Value|
|---|---|
|severity|0|
|severity|1|
|severity|2|
|severity|3|
|severity|4|

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Customer facing logs for specified tenant.|
|400|None|Missing or invalid inputs.|
|401|None|Unauthorized|
|403|None|Forbidden.|
|500|None|Internal server error.|

---
## Definitions

### SeverityLevel

<a id="schemaseveritylevel"></a>
<a id="schema_SeverityLevel"></a>
<a id="tocSseveritylevel"></a>
<a id="tocsseveritylevel"></a>

Object describing the Severity Level of customer logs.

#### Enumerated Values

|Property|Value|
|---|---|
|Verbose|0|
|Information|1|
|Warning|2|
|Error|3|
|Critical|4|

---

