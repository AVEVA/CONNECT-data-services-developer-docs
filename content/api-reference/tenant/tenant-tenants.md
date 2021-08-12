---
uid: tenant-tenants

---

# Tenants
APIs to manage an OCS Customer Tenant. A tenant represents the set of services, applications, data, and configuration state available to a customer. Users are associated with a tenant via at least one configured identity provider and access to resources can be managed for those users via the assignment of roles. Data and services provided by a tenant may also span geographical regions. A tenant has APIs to manage an OCS customer tenant. Unlike namespaces, tenants are not scoped to a region. Tenant level information, such as users and clients, is stored in all supported regions for read-only purposes. Write operations for tenant management and identity and access management are only supported through the global base URL, such as https://dat-b.osisoft.com/Tenants/{tenantId}. Requests to local URLs will return a status of Method Not Allowed (405). Tenant level information, such as users and clients, is stored in all supported regions for read-only purposes.

## `Get Tenant`

<a id="opIdTenant_Get Tenant"></a>

Returns a specific `Tenant` by the identifier.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[TenantWithProperties](#schematenantwithproperties)|The `Tenant` with Id `tenantId`.|
|400|None|Missing or invalid inputs.|
|403|None|Forbidden.|

<h4>Example response body</h4>

> 200 Response ([TenantWithProperties](#schematenantwithproperties))

```json
{
  "Id": "string",
  "CompanyName": "string",
  "State": 0,
  "Created": "2019-08-24T14:15:22Z",
  "LastUpdated": "2019-08-24T14:15:22Z",
  "Alias": "string",
  "Features": [
    {
      "Feature": {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "DefaultState": 0
      },
      "CurrentState": 0
    }
  ],
  "ExternalAccountId": "string",
  "TenantType": "string",
  "Entitlements": [
    {
      "EntitlementDefinitionId": "string",
      "EntitlementType": 0,
      "LimitType": 0,
      "Value": 0,
      "ManualBlockStatus": true
    }
  ]
}
```

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `Tenant Exists`

<a id="opIdTenant_Tenant Exists"></a>

Checks if a `Tenant` with a specific identifier exists.

<h3>Request</h3>

```text 
HEAD /api/v1/Tenants/{tenantId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|HTTP 200 status code if a `Tenant` with `tenantId` exists.|
|400|None|Missing or invalid inputs.|
|404|None|Client or tenant not found.|

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `Update Tenant`

<a id="opIdTenant_Update Tenant"></a>

Updates a specified `Tenant` object.

<h3>Request</h3>

```text 
PUT /api/v1/Tenants/{tenantId}
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>

<h4>Request Body</h4>

The updated details of the Tenant.<br/>

```json
{
  "Id": "string",
  "CompanyName": "string",
  "State": 0,
  "Created": "2019-08-24T14:15:22Z",
  "LastUpdated": "2019-08-24T14:15:22Z",
  "Alias": "string",
  "Features": [
    {
      "Feature": {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "DefaultState": 0
      },
      "CurrentState": 0
    }
  ],
  "ExternalAccountId": "string",
  "TenantType": "string"
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Tenant](#schematenant)|The updated `Tenant` with Id `tenantId`.|
|400|None|Missing or invalid inputs.|
|403|None|Forbidden.|
|405|None|Method not allowed at this base URL. Try the request again at the Global base URL.|

<h4>Example response body</h4>

> 200 Response ([Tenant](#schematenant))

```json
{
  "Id": "string",
  "CompanyName": "string",
  "State": 0,
  "Created": "2019-08-24T14:15:22Z",
  "LastUpdated": "2019-08-24T14:15:22Z",
  "Alias": "string",
  "Features": [
    {
      "Feature": {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "DefaultState": 0
      },
      "CurrentState": 0
    }
  ],
  "ExternalAccountId": "string",
  "TenantType": "string"
}
```

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Administrator</li>
</ul>

---

## `Get Tenant Icon`

<a id="opIdTenant_Get Tenant Icon"></a>

Returns an icon specified by its `Tenant` identifier.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Icon
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|string|The icon associated with the `Tenant`.|
|400|None|Missing or invalid inputs.|
|403|None|Forbidden.|

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---

## `Create Or Update Tenant Icon`

<a id="opIdTenant_Create Or Update Tenant Icon"></a>

Creates or updates the icon for a `Tenant`. Note that the icon size must be less than `65536`.

<h3>Request</h3>

```text 
PUT /api/v1/Tenants/{tenantId}/Icon
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>

<h4>Request Body</h4>

The Base64 encoded PNG icon for the Tenant.<br/>

```json
"string"
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|string|The updated icon associated with the `Tenant`.|
|400|None|Missing or invalid inputs.|
|403|None|Forbidden.|
|405|None|Method not allowed at this base URL. Try the request again at the Global base URL.|

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Administrator</li>
</ul>

---

## `Delete Tenant Icon`

<a id="opIdTenant_Delete Tenant Icon"></a>

Deletes the icon for a `Tenant`.

<h3>Request</h3>

```text 
DELETE /api/v1/Tenants/{tenantId}/Icon
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|string|HTTP status code: 200 on successful deletion or another HTTP status codes on failure.|
|400|None|Missing or invalid inputs.|
|403|None|Forbidden.|
|405|None|Method not allowed at this base URL. Try the request again at the Global base URL.|

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Administrator</li>
</ul>

---

## `Get Regions`

<a id="opIdTenant_Get Regions"></a>

Returns the `RegionBase` list for the specified `Tenant`.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Regions
```

<h4>Parameters</h4>

`string tenantId`
<br/>Tenant identifier.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[RegionBase](#schemaregionbase)|The `RegionBase` list associated with the `Tenant`.|
|403|None|Forbidden.|
|404|None|Client or tenant not found.|

<h4>Example response body</h4>

> 200 Response ([RegionBase](#schemaregionbase))

```json
{
  "Id": "string",
  "Name": "string",
  "AdministrativeEndpointsWritable": true,
  "BaseAddress": "string"
}
```

<h3>Authorization</h3>

Allowed for these roles: 
<ul>
<li>Tenant Member</li>
</ul>

---
## Definitions

### TenantWithProperties

<a id="schematenantwithproperties"></a>
<a id="schema_TenantWithProperties"></a>
<a id="tocStenantwithproperties"></a>
<a id="tocstenantwithproperties"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Identifier of this tenant.|
|CompanyName|string|false|true|Company name of this tenant.|
|State|[TenantProvisioningState](#schematenantprovisioningstate)|false|false|Current tenant provisioning state for this tenant.|
|Created|date-time|false|false|Date and time this tenant was added to the system.|
|LastUpdated|date-time|false|false|Date this tenant was last updated.|
|Alias|string|false|true|Specifies a unique alias for this tenant.|
|Features|[[FeatureState](#schemafeaturestate)]|false|true|List of feature states for this tenant. Returned during GET methods.|
|ExternalAccountId|string|false|true|External account identifier for this tenant.|
|TenantType|string|false|true|Gets or sets tenant type.|
|Entitlements|[[TenantEntitlementInstance](#schematenantentitlementinstance)]|false|true|[An instance of an entitlement.]|

```json
{
  "Id": "string",
  "CompanyName": "string",
  "State": 0,
  "Created": "2019-08-24T14:15:22Z",
  "LastUpdated": "2019-08-24T14:15:22Z",
  "Alias": "string",
  "Features": [
    {
      "Feature": {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "DefaultState": 0
      },
      "CurrentState": 0
    }
  ],
  "ExternalAccountId": "string",
  "TenantType": "string",
  "Entitlements": [
    {
      "EntitlementDefinitionId": "string",
      "EntitlementType": 0,
      "LimitType": 0,
      "Value": 0,
      "ManualBlockStatus": true
    }
  ]
}

```

---

### TenantProvisioningState

<a id="schematenantprovisioningstate"></a>
<a id="schema_TenantProvisioningState"></a>
<a id="tocStenantprovisioningstate"></a>
<a id="tocstenantprovisioningstate"></a>

Status codes describing a tenant's current provisioning state.

<h4>Enumerated Values</h4>

|Property|Value|Description|
|---|---|---|
|Creating|0|Provisioning cannot be completed until all the Product Services (AF, Sds, etc.) are provisioned successfully. In this state, the tenant is provisioned in Azure AD, and created in the System DB. The provisioning engine now sets the state to Creating, notifies all Services to Activate, and waits for a completion message from all of the services. The customer cannot access any Product Services yet.|
|Active|1|The tenant is successfully provisioned (a completion message has been received from all Services). This is now a fully Active, functional tenant with full access to all Services.|
|Deactivating|2|A currently Active tenant is being deactivated (perhaps they haven’t paid their bill). The provisioning engine sets the state to Deactivating and notifies the system services to Deactivate. Until the engine receives a completion message from these services, it will be in this state. The services may become partially non-functional and inaccessible.|
|Deactivated|3|The tenant is successfully Deactivated (a completion message has been received from all Services). The Services are non-functional and inaccessible to customers. The customer data is still intact and some background activities may still be active.|
|Reactivating|4|A currently Deactivated tenant needs to be reinstated. The provisioning engine sets the state to Reactivating, notifies the Services to Reactivate, and waits for the completion message from all of the Services. Once completed, the tenant will be Active again. Until they are Active again, the PICS Services may not be fully functional yet.|
|Deleting|5|The tenant no longer wants to use PICS services or needs to be decommissioned for some reason. The provisioning engine sets the state to Deleting, notifies the Services to Delete, and waits for the completion message from all of the Services. The PICS Services may become partially non-functional and inaccessible.|
|Deleted|6|The tenant is successfully Deleted. The customer data is marked as Deleted. The PICS Services are non-functional and inaccessible. Records may still need to be archived for a period of time determined by SLA, and may not be physically removed yet for possible auditing requirements.|
|Purging|7|All customer records from all PICS services, Azure resources, databases, etc., are permanently and physically removed. Data and other resources are now unrecoverable|
|IsHomeTenant|8|State of the home tenant so it does not return from GetAllTenants|

---

### FeatureState

<a id="schemafeaturestate"></a>
<a id="schema_FeatureState"></a>
<a id="tocSfeaturestate"></a>
<a id="tocsfeaturestate"></a>

Representation of a server-side database interpretation of a feature state.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Feature|[Feature](#schemafeature)|false|true|The feature to which the feature state corresponds.|
|CurrentState|int32|false|false|Current state of the feature.|

```json
{
  "Feature": {
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "DefaultState": 0
  },
  "CurrentState": 0
}

```

---

### Feature

<a id="schemafeature"></a>
<a id="schema_Feature"></a>
<a id="tocSfeature"></a>
<a id="tocsfeature"></a>

Representation of a server-side database interpretation of a feature.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Identifier of this feature.|
|Name|string|false|true|Name of the feature.|
|Description|string|false|true|Description of the feature.|
|DefaultState|int32|false|false|Default state of the feature.|

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "DefaultState": 0
}

```

---

### TenantEntitlementInstance

<a id="schematenantentitlementinstance"></a>
<a id="schema_TenantEntitlementInstance"></a>
<a id="tocStenantentitlementinstance"></a>
<a id="tocstenantentitlementinstance"></a>

An instance of an entitlement.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|EntitlementDefinitionId|string|false|true|Gets or sets the identifier of the corresponding entitlement definition.|
|EntitlementType|[EntitlementType](#schemaentitlementtype)|false|false|Gets or sets the EntitlementType.|
|LimitType|[LimitType](#schemalimittype)|false|false|Gets or sets the Limit type.|
|Value|int32|false|false|Gets or sets the value.|
|ManualBlockStatus|boolean|false|false|Gets or sets the status.|

```json
{
  "EntitlementDefinitionId": "string",
  "EntitlementType": 0,
  "LimitType": 0,
  "Value": 0,
  "ManualBlockStatus": true
}

```

---

### EntitlementType

<a id="schemaentitlementtype"></a>
<a id="schema_EntitlementType"></a>
<a id="tocSentitlementtype"></a>
<a id="tocsentitlementtype"></a>

The type of entitlement.

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|Feature|0|
|Resource|1|
|Usage|2|

---

### LimitType

<a id="schemalimittype"></a>
<a id="schema_LimitType"></a>
<a id="tocSlimittype"></a>
<a id="tocslimittype"></a>

The limit type of entitlement.

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|Hard|0|
|Soft|1|

---

### Tenant

<a id="schematenant"></a>
<a id="schema_Tenant"></a>
<a id="tocStenant"></a>
<a id="tocstenant"></a>

Representation of a server-side database interpretation of a tenant.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Identifier of this tenant.|
|CompanyName|string|false|true|Company name of this tenant.|
|State|[TenantProvisioningState](#schematenantprovisioningstate)|false|false|Current tenant provisioning state for this tenant.|
|Created|date-time|false|false|Date and time this tenant was added to the system.|
|LastUpdated|date-time|false|false|Date this tenant was last updated.|
|Alias|string|false|true|Specifies a unique alias for this tenant.|
|Features|[[FeatureState](#schemafeaturestate)]|false|true|List of feature states for this tenant. Returned during GET methods.|
|ExternalAccountId|string|false|true|External account identifier for this tenant.|
|TenantType|string|false|true|Gets or sets tenant type.|

```json
{
  "Id": "string",
  "CompanyName": "string",
  "State": 0,
  "Created": "2019-08-24T14:15:22Z",
  "LastUpdated": "2019-08-24T14:15:22Z",
  "Alias": "string",
  "Features": [
    {
      "Feature": {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "DefaultState": 0
      },
      "CurrentState": 0
    }
  ],
  "ExternalAccountId": "string",
  "TenantType": "string"
}

```

---

### RegionBase

<a id="schemaregionbase"></a>
<a id="schema_RegionBase"></a>
<a id="tocSregionbase"></a>
<a id="tocsregionbase"></a>

Represents a region within an OCS environment for OCS customers to see.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|Identifier for the region.|
|Name|string|false|true|Name associated with the region.|
|AdministrativeEndpointsWritable|boolean|false|false|Value indicating whether value indicating whether administrative endpoints are writable in the region.|
|BaseAddress|string|false|true|Base address for the region.|

```json
{
  "Id": "string",
  "Name": "string",
  "AdministrativeEndpointsWritable": true,
  "BaseAddress": "string"
}

```

---

