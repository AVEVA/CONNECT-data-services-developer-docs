---
uid: AccountRootAccessControl_1
---

# Root access control

APIs to manage default access to entities governed by an [AccessControlList](xref:accessControl).

***

## `Get Root Namespace AccessControlList`

|Status Code|Body Type|Description|
|---|---|---|
|200|[AccessControlList](#schemaaccesscontrollist)|The root `AccessControlList` for `Namespace`.|
|400|None|Missing or invalid inputs.<br/>|
|403|None|Forbidden.<br/>|

#### Example response body
> 200 Response ([AccessControlList](#schemaaccesscontrollist))

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

### HTTP

`GET api/v1/Tenants/{tenantId}/AccessControl/Namespaces`


### Parameters

```csharp
[Required]
[FromRoute]
string tenantId
```

The identifier of the tenant to access.


### Authorization

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

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[AccessControlList](#schemaaccesscontrollist)|The new `AccessControlList` for `Namespace`.|
|400|None|Missing or invalid inputs.<br/>|
|403|None|Forbidden.<br/>|
|405|None|Method not allowed at this base URL. Try the request again at the Global base URL.|

#### Example response body
> 200 Response ([AccessControlList](#schemaaccesscontrollist))

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
## Definitions

### AccessControlList

<a id="schemaaccesscontrollist"></a>
<a id="schema_AccessControlList"></a>
<a id="tocSaccesscontrollist"></a>
<a id="tocsaccesscontrollist"></a>

#### Properties

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

***

## `Set Root AccessControlList`

Modifies the [AccessControlList](xref:accessControl) that is used to authorize access to a `Namespace` if none is specified during creation.

### Request

`PUT api/v1/Tenants/{tenantId}/AccessControl/Namespaces`


### Parameters

```csharp
[Required]
[FromRoute]
string tenantId
```

The identifier of the tenant to modify.
```csharp
[Required]
[FromBody]
AccessControlList newAccessControlList
```

The new root [AccessControlList](xref:accessControl) for `Namespaces`.


### Authorization

A root [AccessControlList](xref:accessControl) can only be modified if the current principal has ManageAccessControl access.

### Response

| Status Code | Return Type | Description |
| --- | --- | ---  |
| 200 | AccessControlList | Returns the modified root [AccessControlList](xref:accessControl) for `Namespaces`. |
| 400 | Nothing is returned | Could not modify the root [AccessControlList](xref:accessControl) for `Namespaces` due to missing or invalid input. |
| 403 | Nothing is returned | Unauthorized to change the root [AccessControlList](xref:accessControl) for `Namespaces`. |
| 405 | Nothing is returned | Method not allowed at this base URL. Try the request again at the Global base URL. |


***

