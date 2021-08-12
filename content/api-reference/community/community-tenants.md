---
uid: community-tenants

---

# Tenants
APIs for updating and removing community tenant information

## `Update a Community Tenant State (communitytenants path)`

<a id="opIdCommunityTenants_Update a Community Tenant State (communitytenants path)"></a>

Updates the state of a community tenant. The state can be activated, paused, or removed.

<h3>Request</h3>

```text 
PUT /api/v1-preview/tenants/{callerTenantId}/communities/{communityId}/communitytenants/{tenantIdtoUpdate}
```

<h4>Parameters</h4>

`string callerTenantId`
<br/>Owning tenant identifier<br/><br/>`string communityId`
<br/>Community identifier<br/><br/>`string tenantIdtoUpdate`
<br/>`CommunityTenant` in the community to update<br/><br/>

<h4>Request Body</h4>

CommunityTenant object that contains the attributes to use for the update<br/>

```json
{
  "Status": "None"
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Success. The community tenant was updated.|
|204|None|No Content. No operation was performed.|
|400|[ErrorResponse](#schemaerrorresponse)|Bad Request. The server could not understand the request due to invalid syntax.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized. The client has not been authenticated.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden. The client does not have the required permissions to make the request.|
|404|[ErrorResponse](#schemaerrorresponse)|Not Found. The requested community tenant was not found.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal Server Error. The server has encountered a situation it does not know how to handle.|

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Community Administrator</li>
</ul>

---

## `Update a Community Tenant State (membertenants path)`

<a id="opIdCommunityTenants_Update a Community Tenant State (membertenants path)"></a>

Updates the state of a community tenant. The state can be activated, paused, or removed.

<h3>Request</h3>

```text 
PUT /api/v1-preview/tenants/{callerTenantId}/communities/{communityId}/membertenants/{tenantIdtoUpdate}
```

<h4>Parameters</h4>

`string callerTenantId`
<br/>Owning tenant identifier<br/><br/>`string communityId`
<br/>Community identifier<br/><br/>`string tenantIdtoUpdate`
<br/>`CommunityTenant` in the community to update<br/><br/>

<h4>Request Body</h4>

CommunityTenant object that contains the attributes to use for the update<br/>

```json
{
  "Status": "None"
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Success. The community tenant was updated.|
|204|None|No Content. No operation was performed.|
|400|[ErrorResponse](#schemaerrorresponse)|Bad Request. The server could not understand the request due to invalid syntax.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized. The client has not been authenticated.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden. The client does not have the required permissions to make the request.|
|404|[ErrorResponse](#schemaerrorresponse)|Not Found. The requested community tenant was not found.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal Server Error. The server has encountered a situation it does not know how to handle.|

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Community Administrator</li>
</ul>

---

## `Remove a Community Tenant from a Community`

<a id="opIdCommunityTenants_Remove a Community Tenant from a Community"></a>

Removes a community tenant from a community

<h3>Request</h3>

```text 
DELETE /api/v1-preview/tenants/{callerTenantId}/communities/{communityId}/communitytenants/{tenantIdToRemove}
```

<h4>Parameters</h4>

`string callerTenantId`
<br/>Owning tenant identifier<br/><br/>`string communityId`
<br/>Community identifier<br/><br/>`string tenantIdToRemove`
<br/>`CommunityTenant` in the community to remove<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|None|
|400|[ErrorResponse](#schemaerrorresponse)|Bad Request. The server could not understand the request due to invalid syntax.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized. The client has not been authenticated.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden. The client does not have the required permissions to make the request.|
|404|[ErrorResponse](#schemaerrorresponse)|Not Found. The requested community tenant was not found.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal Server Error. The server has encountered a situation it does not know how to handle.|

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Community Administrator</li>
<li>Community Moderator</li>
</ul>

---
## Definitions

### ErrorResponse

<a id="schemaerrorresponse"></a>
<a id="schema_ErrorResponse"></a>
<a id="tocSerrorresponse"></a>
<a id="tocserrorresponse"></a>

Object returned when there is an error

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|true|false|OperationId of action that caused the error|
|Error|string|true|false|Error description|
|Reason|string|true|false|Reason for the error|
|Resolution|string|true|false|Resolution for the error|
|EventId|string|true|false|EventId for the error|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "EventId": "string",
  "property1": null,
  "property2": null
}

```

---

### UpdateCommunityTenantInput

<a id="schemaupdatecommunitytenantinput"></a>
<a id="schema_UpdateCommunityTenantInput"></a>
<a id="tocSupdatecommunitytenantinput"></a>
<a id="tocsupdatecommunitytenantinput"></a>

The UpdateCommunityTenantInput object

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Status|[CommunityTenantStatus](#schemacommunitytenantstatus)|false|false|New status of CommunityTenant in community|

```json
{
  "Status": "None"
}

```

---

### CommunityTenantStatus

<a id="schemacommunitytenantstatus"></a>
<a id="schema_CommunityTenantStatus"></a>
<a id="tocScommunitytenantstatus"></a>
<a id="tocscommunitytenantstatus"></a>

Represents a status of a community tenant

<h4>Enumerated Values</h4>

|Property|Value|Description|
|---|---|---|
|None|None|No community tenant status specified.|
|AwaitingConfirmation|AwaitingConfirmation|After invite, awaiting confirmation from owner.|
|Paused|Paused|Community Tenant paused from actively sharing.|
|Active|Active|Resume sharing from pause or after confirm.|
|Remove|Remove|Owner removes Tenant or Community Tenant leaves community.|

---

