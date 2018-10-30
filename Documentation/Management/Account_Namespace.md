---
uid: AccountNamespace
---

Namespace
=======================================================

A Namespace is a collection of Data Streams.

## Properties

For HTTP requests and responses, the Namespace object has the following properties and JSON-serialized body: 

```csharp
string Id
```
Name of this Namespace. Unique within a Tenant's Namespaces.

```csharp
string TenantId
```
GUID of the Tenant that this Namespace corresponds to

```csharp
string Region
```
The region that the namespace is provisioned in

```csharp
string Self
```
The namespace's URI

```csharp
string Description
```
Description of this Namespace.

```csharp
string TierId
```
Id of the Tier that this Namespace is associated with.

```csharp
int32 ThroughputUnits
```
Number of Throughput units for this Namespace.

```csharp
int32 StorageUnits
```
Number of Storage units for this Namespace.

```csharp
NamespaceProvisioningState State
```
Current state of this Namespace.

```csharp
OwnerTrustee Owner
```
Owner [`Trustee`](xref:accessControl#trusteeobj) of this Namespace.

```csharp
AccessControlList AccessControl
```
The [`AccessControl`](xref:accessControl#accesscontrollistobj) that defines Access Control for this [`Namespace`](xref:AccountNamespace)

```csharp
AccessControlList AccessControlList
```
Access Control List.


```json
{
	"Id": "id",
	"TenantId": "tenantid",
	"Region": "region",
	"Self": "self",
	"Description": "description",
	"TierId": "tierid",
	"ThroughputUnits": 0,
	"StorageUnits": 0,
	"State": 0,
	"Owner": {
		"Type": 2,
		"TenantId": "string",
		"ApplicationId": "string"
	},
	"AccessControl": {
		"RoleTrusteeAccessControlEntries": []
	},
	"AccessControlList": {
		"RoleTrusteeAccessControlEntries": []
	}
}
```
***

## `GetAll()`

Returns all [`Namespaces`](xref:AccountNamespace) owned by the specified tenant that the caller has access to.

**Http**

`GET api/Tenants/{tenantId}/Namespaces`

**Parameters**

```csharp
string tenantId
```
The [`Tenant`](xref:accountTenant) identifier for the request.
```csharp
string include
```
An optional parameter specifying which attatched properties to include


**Security**

A [`Namespace`](xref:AccountNamespace) can only be retrieved if the current principal has Read access.

**Returns**

An array of all [`Namespace`](xref:AccountNamespace) objects for the specified tenantId that the caller has access.


***
## `GetNamespaceById()`

Returns the Namespace with the specified Id.

**Http**

`GET api/Tenants/{tenantId}/Namespaces/{namespaceId}`

**Parameters**

```csharp
string tenantId
```
The account identifier for the request
```csharp
string namespaceId
```
The Namespace identifier for this request


**Security**

A [`Namespace`](xref:AccountNamespace) can only be retrieved if the current principal has Read access.

**Returns**

A [`Namespace`](xref:AccountNamespace) object with the specified namespaceId


***
## `Create()`

Creates a namespace.

**Http**

`POST api/Tenants/{tenantId}/Namespaces`

**Parameters**

```csharp
string tenantId
```
The identifier for the account the namespace is to be created for.
```csharp
Namespace namespaceObj
```
The [`Namespace`](xref:AccountNamespace) to be created.


**Security**

A [`Namespace`](xref:AccountNamespace) can only be created if the current principal has Write access.

**Returns**

The created [`Namespace`](xref:AccountNamespace) object.


***
## `Update()`

Updates Namespace information - Description, TierId, AccessControl, and Owner.

**Http**

`PUT api/Tenants/{tenantId}/Namespaces/{namespaceId}`

**Parameters**

```csharp
string tenantId
```
The identifier of Namespace's Account.
```csharp
string namespaceId
```
The identifier for the Namespace to update.
```csharp
Namespace newProperties
```
The new details to store for the Namespace.


**Security**

A [`Namespace`](xref:AccountNamespace) can only be updated if the current principal has Write access.

The [`AccessControl`](xref:accessControl#accessControlListobj) and [`OwnerTrustee`](xref:accessControl#trusteeobj) can only be updated if the current principal has Manage Access Control access.

**Returns**

The updated [`Namespace`](xref:AccountNamespace).

***

## `Delete()`

Deletes a namespace.

**Http**

`DELETE api/Tenants/{tenantId}/Namespaces/{namespaceId}`

**Parameters**

```csharp
string tenantId
```
The identifier of namespace's account
```csharp
string namespaceId
```
The identifier of the namespace to be deleted


**Security**

A [`Namespace`](xref:AccountNamespace) can only be deleted if the current principal has Delete access.

**Returns**

Nothing is returned.


***
## `GetAccessControl()`

Gets the [`AccessControl`](xref:accessControl#accesscontrollistobj) that is used to authorize access to a [`Namespace`](xref:AccountNamespace).

**Http**

`GET api/Tenants/{tenantId}/Namespaces/{namespaceId}/accesscontrol`

**Parameters**

```csharp
string tenantId
```
The idenfifier of the account being accessed.
```csharp
string namespaceId
```
The identifier of the [`Namespace`](xref:AccountNamespace) being accessed.


**Security**

 The current principal has Read access.

**Returns**

The [`AccessControl`](xref:accessControl#accesscontrollistobj) for the [`Namespace`](xref:AccountNamespace).


***
## `SetAccessControl()`

Edits the [`AccessControl`](xref:accessControl#accesscontrollistobj) that is used to authorize access to a [`Namespace`](xref:AccountNamespace).

**Http**

`PUT api/Tenants/{tenantId}/Namespaces/{namespaceId}/accesscontrol`

**Parameters**

```csharp
string tenantId
```
The idenfifier of the account being modified.
```csharp
string namespaceId
```
The identifier of the [`Namespace`](xref:AccountNamespace) being modified.
```csharp
AccessControlList newAccessControlList
```
The new [`AccessControlList`](xref:accessControl#accesscontrollistobj) for the [`Namespace`](xref:AccountNamespace).


**Security**

 The current principal has ManageAccessControl access.

**Returns**

The updated [`AccessControlList`](xref:accessControl#accesscontrollistobj) for the [`Namespace`](xref:AccountNamespace).


***
## `GetOwner()`

Gets the [`OwnerTrustee`](xref:accessControl#trusteeobj) for a given [`Namespace`](xref:AccountNamespace).

**Http**

`GET api/Tenants/{tenantId}/Namespaces/{namespaceId}/owner`

**Parameters**

```csharp
string tenantId
```
The idenfifier of the account being accessed.
```csharp
string namespaceId
```
The identifier of the [`Namespace`](xref:AccountNamespace) being accessed.


**Security**

 The current principal has Read access.

**Returns**

The [`OwnerTrustee`](xref:accessControl#trusteeobj) of the [`Namespace`](xref:AccountNamespace).


***
## `SetOwner()`

Changes the [`OwnerTrustee`](xref:accessControl#trusteeobj) for a given [`Namespace`](xref:AccountNamespace).

**Http**

`PUT api/Tenants/{tenantId}/Namespaces/{namespaceId}/owner`

**Parameters**

```csharp
string tenantId
```
The idenfifier of the account being edited.
```csharp
string namespaceId
```
The identifier of the [`Namespace`](xref:AccountNamespace) being edited.
```csharp
OwnerTrustee newOwner
```
The new [`OwnerTrustee`](xref:accessControl#trusteeobj) for the [`Namespace`](xref:AccountNamespace).


**Security**

 The current principal has ManageAccessControl access.

**Returns**

The new [`OwnerTrustee`](xref:accessControl#trusteeobj) of the [`Namespace`](xref:AccountNamespace).

***
