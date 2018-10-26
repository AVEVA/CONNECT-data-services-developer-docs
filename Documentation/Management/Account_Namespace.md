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
Owner `Trustee <Trustee>` of this Namespace.

```csharp
AccessControlList AccessControl
```
The `AccessControlList <AccessControlList>` that defines Access Control for this `Namespace <Namespace>`

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

### `GetAll()`

Returns all `Namespaces <Namespace>` owned by the specified tenant that the caller has access to.

**Http**

`GET api/Tenants/{tenantId}/Namespaces`

**Parameters**

```csharp
string tenantId
```
The `Tenant <Tenant>` identifier for the request.
```csharp
string include
```
An optional parameter specifying which attatched properties to include


**Security**

A `Namespace <Namespace>` can only be retrieved if the current principal has Read access.

**Returns**

An array of all `Namespace <Namespace>` objects for the specified tenantId that the caller has access.


***
### `GetNamespaceById()`

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

A `Namespace <Namespace>` can only be retrieved if the current principal has Read access.

**Returns**

A `Namespace <Namespace>` object with the specified namespaceId


***
### `Create()`

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
The `Namespace <Namespace>` to be created.


**Security**

A `Namespace <Namespace>` can only be created if the current principal has Write access.

**Returns**

The created `Namespace <Namespace>` object.


***
### `Update()`

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


                A `Namespace <Namespace>` can only be updated if the current principal has `CommonAccessRights.Write <CommonAccessRights>` access.
                The `AccessControl <AccessControl>` and `OwnerTrustee <OwnerTrustee>` can only be updated if the current principal has `CommonAccessRights.ManageAccessControl <CommonAccessRights>` access.
            

**Returns**

The updated `Namespace <Namespace>`.


***
### `Delete()`

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

A `Namespace <Namespace>` can only be deleted if the current principal has Delete access.

**Returns**

Nothing is returned.


***
### `GetAccessControl()`

Gets the `AccessControlList <AccessControlList>` that is used to authorize access to a `Namespace <Namespace>`.

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
The identifier of the `Namespace <Namespace>` being accessed.


**Security**

 The current principal has Read access.

**Returns**

The `AccessControlList <AccessControlList>` for the `Namespace <Namespace>`.


***
### `SetAccessControl()`

Edits the `AccessControlList <AccessControlList>` that is used to authorize access to a `Namespace <Namespace>`.

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
The identifier of the `Namespace <Namespace>` being modified.
```csharp
AccessControlList newAccessControlList
```
The new `AccessControlList <AccessControlList>` for the `Namespace <Namespace>`.


**Security**

 The current principal has ManageAccessControl access.

**Returns**

The updated `AccessControlList <AccessControlList>` for the `Namespace <Namespace>`.


***
### `GetOwner()`

Gets the `OwnerTrustee <OwnerTrustee>` for a given `Namespace <Namespace>`.

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
The identifier of the `Namespace <Namespace>` being accessed.


**Security**

 The current principal has Read access.

**Returns**

The `OwnerTrustee <OwnerTrustee>` of the `Namespace <Namespace>`.


***
### `SetOwner()`

Changes the `OwnerTrustee <OwnerTrustee>` for a given `Namespace <Namespace>`.

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
The identifier of the `Namespace <Namespace>` being edited.
```csharp
OwnerTrustee newOwner
```
The new `OwnerTrustee <OwnerTrustee>` for the `Namespace <Namespace>`.


**Security**

 The current principal has ManageAccessControl access.

**Returns**

The new `OwnerTrustee <OwnerTrustee>` of the `Namespace <Namespace>`.

## Properties

**Notes**

For HTTP requests and responses, the OwnerTrustee object has the following properties and JSON-serialized body: 


```json

```


***
