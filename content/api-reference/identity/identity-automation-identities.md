---
uid: identity-automation-identities

---

# Automation Identities
APIs for automation identities.

## `List Automation Identities from a Tenant`

<a id="opIdAutomationIdentities_List Automation Identities from a Tenant"></a>

Returns automation identity objects.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/AutomationIdentities
?tag={tag}&query={query}&skip={skip}&count={count}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier<br/><br/>
`[optional] array tag`
<br/>Only return automation identities that have at least one of these tags<br/><br/>`[optional] string query`
<br/>(not supported) Search string identifier<br/><br/>`[optional] integer skip`
<br/>Number of automation identities to skip. Ignored if a list of Ids is passed.<br/><br/>`[optional] integer count`
<br/>Maximum number of automation identities to return. Ignored if a list of Ids is passed.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AutomationIdentity](#schemaautomationidentity)[]|List of automation identities found|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|404|[ErrorResponse](#schemaerrorresponse)|Not found|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

<h4>Example response body</h4>

> 200 Response ([AutomationIdentity](#schemaautomationidentity)[])

```json
[
  {
    "Id": "string",
    "Name": "string",
    "TenantId": "string",
    "RoleIds": [
      "string"
    ],
    "RoleTypeIds": [
      "string"
    ],
    "Tags": [
      "string"
    ]
  }
]
```

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `Get Total Count of Automation Identities from Tenant`

<a id="opIdAutomationIdentities_Get Total Count of Automation Identities from Tenant"></a>

Returns the total number of automation identities in tenant in the Total-Count header.

<h3>Request</h3>

```text 
HEAD /api/v1/Tenants/{tenantId}/AutomationIdentities
?tag={tag}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier<br/><br/>
`[optional] array tag`
<br/>Only count automation identities that have at least one of these tags.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Number of automation identities in Total-Count header only|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|404|[ErrorResponse](#schemaerrorresponse)|Automation identity or tenant not found|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `Create an Automation Identity`

<a id="opIdAutomationIdentities_Create an Automation Identity"></a>

Creates an automation identity. A non-administrator caller must have all roles being assigned to the new automation identity.

<h3>Request</h3>

```text 
POST /api/v1/Tenants/{tenantId}/AutomationIdentities
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier<br/><br/>

<h4>Request Body</h4>

New automation identity object<br/>

```json
{
  "Name": "string",
  "RoleIds": [
    "string"
  ],
  "Tags": [
    "string"
  ]
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|201|[AutomationIdentity](#schemaautomationidentity)|Automation identity created|
|400|[ErrorResponse](#schemaerrorresponse)|Bad Request|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden. A non-administrator caller must have all roles being assigned to the new automation identity.|
|404|[ErrorResponse](#schemaerrorresponse)|Not found|
|408|[ErrorResponse](#schemaerrorresponse)|Operation timed out|
|409|[ErrorResponse](#schemaerrorresponse)|Already exists|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

<h4>Example response body</h4>

> 201 Response ([AutomationIdentity](#schemaautomationidentity))

```json
{
  "Id": "string",
  "Name": "string",
  "TenantId": "string",
  "RoleIds": [
    "string"
  ],
  "RoleTypeIds": [
    "string"
  ],
  "Tags": [
    "string"
  ]
}
```

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `Get an Automation Identity`

<a id="opIdAutomationIdentities_Get an Automation Identity"></a>

Returns automation identity object.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/AutomationIdentities/{automationIdentityId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier<br/><br/>`string automationIdentityId`
<br/>Automation identity unique identifier<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AutomationIdentity](#schemaautomationidentity)|Automation identity specified|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|404|[ErrorResponse](#schemaerrorresponse)|Not found|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

<h4>Example response body</h4>

> 200 Response ([AutomationIdentity](#schemaautomationidentity))

```json
{
  "Id": "string",
  "Name": "string",
  "TenantId": "string",
  "RoleIds": [
    "string"
  ],
  "RoleTypeIds": [
    "string"
  ],
  "Tags": [
    "string"
  ]
}
```

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `Get Header for Automation Identity`

<a id="opIdAutomationIdentities_Get Header for Automation Identity"></a>

Validates that an automation identity exists in tenant.

<h3>Request</h3>

```text 
HEAD /api/v1/Tenants/{tenantId}/AutomationIdentities/{automationIdentityId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier<br/><br/>`string automationIdentityId`
<br/>Automation identity unique identifier<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Ok if the automation identity exists|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden|
|404|[ErrorResponse](#schemaerrorresponse)|Automation identity or tenant not found|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `Update Automation Identity`

<a id="opIdAutomationIdentities_Update Automation Identity"></a>

Updates an automation identity. A non-administrator caller must have all roles belonging to the existing automation identity, as well as any roles being added.

<h3>Request</h3>

```text 
PUT /api/v1/Tenants/{tenantId}/AutomationIdentities/{automationIdentityId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier<br/><br/>`string automationIdentityId`
<br/>Automation identity unique identifier<br/><br/>

<h4>Request Body</h4>

Automation identity object. Properties that are not set or are null will not be changed.<br/>

```json
{
  "Name": "string",
  "RoleIds": [
    "string"
  ],
  "Tags": [
    "string"
  ]
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AutomationIdentity](#schemaautomationidentity)|Updated automation identity|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden. A non-administrator caller must have all roles belonging to the existing automation identity, as well as any roles being added.|
|404|[ErrorResponse](#schemaerrorresponse)|Automation identity or tenant not found|
|408|[ErrorResponse](#schemaerrorresponse)|Operation timed out|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

<h4>Example response body</h4>

> 200 Response ([AutomationIdentity](#schemaautomationidentity))

```json
{
  "Id": "string",
  "Name": "string",
  "TenantId": "string",
  "RoleIds": [
    "string"
  ],
  "RoleTypeIds": [
    "string"
  ],
  "Tags": [
    "string"
  ]
}
```

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `Delete an Automation Identity`

<a id="opIdAutomationIdentities_Delete an Automation Identity"></a>

Deletes an automation identity. A non-administrator caller must have all roles belonging to the automation identity being deleted.

<h3>Request</h3>

```text 
DELETE /api/v1/Tenants/{tenantId}/AutomationIdentities/{automationIdentityId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier<br/><br/>`string automationIdentityId`
<br/>Automation identity unique identifier<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|No content|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden. A non-administrator caller must have all roles belonging to the automation identity being deleted.|
|404|[ErrorResponse](#schemaerrorresponse)|Automation identity or tenant not found|
|408|[ErrorResponse](#schemaerrorresponse)|Operation timed out|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error|

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---
## Definitions

### AutomationIdentity

<a id="schemaautomationidentity"></a>
<a id="schema_AutomationIdentity"></a>
<a id="tocSautomationidentity"></a>
<a id="tocsautomationidentity"></a>

Automation identity.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|guid|false|false|Automation identity unique identifier.|
|Name|string|false|true|Automation identity name.|
|TenantId|guid|false|false|Automation identity tenant unique identifier.|
|RoleIds|string[]|false|true|Role unique identifiers associated with this automation identity.|
|RoleTypeIds|string[]|false|true|Role type unique identifiers associated with this automation identity.|
|Tags|string[]|false|true|Tags associated with this automation identity.|

```json
{
  "Id": "string",
  "Name": "string",
  "TenantId": "string",
  "RoleIds": [
    "string"
  ],
  "RoleTypeIds": [
    "string"
  ],
  "Tags": [
    "string"
  ]
}

```

---

### ErrorResponse

<a id="schemaerrorresponse"></a>
<a id="schema_ErrorResponse"></a>
<a id="tocSerrorresponse"></a>
<a id="tocserrorresponse"></a>

Object returned whenever there is an error

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|true|false|Operation identifier of action that caused the error|
|Error|string|true|false|Error description|
|Reason|string|true|false|Reason for the error|
|Resolution|string|true|false|Resolution to resolve the error|
|DynamicProperties|object|false|true|Additional properties|

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

### AutomationIdentityCreate

<a id="schemaautomationidentitycreate"></a>
<a id="schema_AutomationIdentityCreate"></a>
<a id="tocSautomationidentitycreate"></a>
<a id="tocsautomationidentitycreate"></a>

The model for creating an Automation Identity.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|Automation identity name.|
|RoleIds|string[]|false|true|Role Ids associated with this automation identity.|
|Tags|string[]|false|true|Tags associated with this automation identity.|

```json
{
  "Name": "string",
  "RoleIds": [
    "string"
  ],
  "Tags": [
    "string"
  ]
}

```

---

### AutomationIdentityUpdate

<a id="schemaautomationidentityupdate"></a>
<a id="schema_AutomationIdentityUpdate"></a>
<a id="tocSautomationidentityupdate"></a>
<a id="tocsautomationidentityupdate"></a>

The model for updating an automation identity.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|The automation identity name.|
|RoleIds|string[]|false|true|Role Ids associated with this automation identity.|
|Tags|string[]|false|true|Tags associated with this automation identity.|

```json
{
  "Name": "string",
  "RoleIds": [
    "string"
  ],
  "Tags": [
    "string"
  ]
}

```

---

