---
uid: AccountNamespace_1
---

# Namespaces

A `Namespace` is a collection of SDS types, streams, and stream views. Namespace identifiers are unique within an account. Requirements
for Namespace IDs are the following:
- Must contain 100 characters or fewer
- Must only contain alphanumeric characters, underscores, dashes, spaces, and periods
- Must not contain two consecutive periods
- Must not start or end with a period
- Must not start with two consecutive underscores

In practice, namespaces may correspond to a specific set of infrastructure assets, but more commonly correspond to virtual partitions within a single set of assets. You can create one or more namespaces within an SDS account. Each namespace is effectively an instance of SDS, within which you create SDS types and streams, stream views, data views, and metadata.

## Properties

For HTTP requests and responses, the Namespace object has the following properties and JSON-serialized body: 

| Property Name | Data Type | Description | 
 | --- | --- | ---  | 
| Id | string | Nme of this Namespace; unique within a Tenant's Namespaces. | 
| Region | string | The region that the namespace is provisioned in. | 
| Self | string | The namespace's URI. | 
| Description | string | Description of this Namespace. | 
| State | NamespaceProvisioningState | Current state of this Namespace. | 

```json
{
	"Id": "id",
	"Region": "region",
	"Self": "self",
	"Description": "description",
	"State": 0,
}
```

## Region ##

When a namespace is created, all resources are created in the namespace's region. Resources created in this namespace (for example: SDS types, streams, and stream views) will be created in the region of the namespace, and any data stored in the namespace will be stored in that region. Read and write operations at the namespace level and within a namespace utilize the base URL of the region in which the namespace resides. The ``Self`` property on each namespace provides the complete URL for all operations within that namespace.

***

## `Get All Namespaces`

Returns all `Namespaces` owned by the specified `Tenant` that the caller has access to.

### Http

`GET api/v1/Tenants/{tenantId}/Namespaces`


### Parameters

```csharp
[Required]
[FromRoute]
string tenantId
```

The identifier of the account to access.


### Security

A `Namespace` can only be retrieved if the current principal has Read access.

### Returns

| Status Code | Return Type | Description | 
 | --- | --- | ---  | 
| 200 | [Namespace] | Returns a list of all `Namespace` objects for the specified tenantId that the caller has access to. | 
| 400 | Nothing is returned | Could not retrieve `Namespaces` due to missing or invalid input. | 
| 403 | Nothing is returned | Unauthorized to access the tenant's `Namespaces`. | 


***

## `Get Namespace By Id`

Returns a `Namespace` with the specified Id.

### Http

`GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}`


### Parameters

```csharp
[Required]
[FromRoute]
string tenantId
```

The identifier of the account to access.
```csharp
[Required]
[FromRoute]
string namespaceId
```

The identifier of the `Namespace` to return.


### Security

A `Namespace` can only be retrieved if the current principal has Read access.

### Returns

| Status Code | Return Type | Description | 
 | --- | --- | ---  | 
| 200 | Namespace | Returns a `Namespace` object with the specified namespaceId. | 
| 400 | Nothing is returned | Could not retrieve the `Namespace` due to missing or invalid input. | 
| 403 | Nothing is returned | Unauthorized to access this `Namespace`. | 
| 404 | Nothing is returned | `Namespace` not found in the specified account. | 


***

## `Create New Namespace`

Creates a new `Namespace` in the specified `Tenant`.

### Http

`POST api/v1/Tenants/{tenantId}/Namespaces/{namespaceId?}`


### Parameters

```csharp
[Required]
[FromRoute]
string tenantId
```

The account identifier where the `Namespace` will be created.
```csharp
[Required]
[FromBody]
Namespace namespaceToCreate
```

The new `Namespace` to be created.
```csharp
[Optional]
[Default = ""]
[FromRoute]
string namespaceId
```

The Id of the new `Namespace`. The Id can also be specified in the namespaceToCreate. If it is omitted in both,
            the Id will be generated.


### Security

A `Namespace` can only be created if the current principal has Write access.

### Returns

| Status Code | Return Type | Description | 
 | --- | --- | ---  | 
| 201 | Namespace | Returns the created `Namespace` object. | 
| 302 | Nothing is returned | Returns the location of the existing `Namespace` object. | 
| 400 | Nothing is returned | Could not create the `Namespace` due to missing or invalid input. | 
| 403 | Nothing is returned | Unauthorized to create a `Namespace` in this account. | 
| 405 | Nothing is returned | Method not allowed at this base URL. Try the request again at the Global base URL. | 
| 409 | Nothing is returned | A `Namespace` already exists with different values. | 


***

## `Update Namespace`

Updates `Namespace` information: Description and TierId. The [AccessControlList](xref:accessControl) and Owner's [Trustee](xref:accessControl) can
            only be updated through their own routes.

### Http

`PUT api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}`


### Parameters

```csharp
[Required]
[FromRoute]
string tenantId
```

The identifier of the account to access.
```csharp
[Required]
[FromRoute]
string namespaceId
```

The identifier of the `Namespace` to update.
```csharp
[Required]
[FromBody]
Namespace newProperties
```

The new details to store for the `Namespace`.


### Security

A `Namespace` can only be updated if the current principal has Write access.

### Returns

| Status Code | Return Type | Description | 
 | --- | --- | ---  | 
| 200 | Namespace | Returns the updated `Namespace`. | 
| 400 | Nothing is returned | Could not update the `Namespace` due to missing or invalid input. | 
| 403 | Nothing is returned | Unauthorized to update the `Namespace`. | 
| 405 | Nothing is returned | Method not allowed at this base URL. Try the request again at the Global base URL. | 

***

## `Delete Namespace`

Deletes a `Namespace` in the specified `Tenant`.

### Http

`DELETE api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}`


### Parameters

```csharp
[Required]
[FromRoute]
string tenantId
```

The identifier of the account to access.
```csharp
[Required]
[FromRoute]
string namespaceId
```

The identifier of the `Namespace` to delete.


### Security

A `Namespace` can only be deleted if the current principal has Delete access.

### Returns

| Status Code | Return Type | Description | 
 | --- | --- | ---  | 
| 204 | Nothing is returned | The `Namespace` was deleted. | 
| 400 | Nothing is returned | Could not delete the `Namespace` due to an invalid state. | 
| 403 | Nothing is returned | Unauthorized to delete the `Namespace`. | 
| 405 | Nothing is returned | Method not allowed at this base URL. Try the request again at the Global base URL. | 


***

## `Get Namespace AccessControlList`

Returns the [AccessControlList](xref:accessControl) that is used to authorize access to a `Namespace`.

### Http

`GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/accesscontrol`


### Parameters

```csharp
[Required]
[FromRoute]
string tenantId
```

The identifier of the account to access.
```csharp
[Required]
[FromRoute]
string namespaceId
```

The identifier of the `Namespace` to access.


### Security

An [AccessControlList](xref:accessControl) can only be retrieved if the current principal has Read access.

### Returns

| Status Code | Return Type | Description | 
 | --- | --- | ---  | 
| 200 | AccessControlList | Returns the [AccessControlList](xref:accessControl) for the specified `Namespace`. | 
| 400 | Nothing is returned | Could not retrieve the [AccessControlList](xref:accessControl) of the specified `Namespace` due to missing or invalid input. | 
| 403 | Nothing is returned | Unauthorized to get the [AccessControlList](xref:accessControl) for the specified `Namespace`. | 


***

## `Set Namespace AccessControlList`

Updates the [AccessControlList](xref:accessControl) that is used to authorize access to a `Namespace`.

### Http

`PUT api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/accesscontrol`


### Parameters

```csharp
[Required]
[FromRoute]
string tenantId
```

The identifier of the account to access.
```csharp
[Required]
[FromRoute]
string namespaceId
```

The identifier of the `Namespace` to access.
```csharp
[Required]
[FromBody]
AccessControlList newAccessControlList
```

The updated [AccessControlList](xref:accessControl) for the `Namespace`.


### Security

An [AccessControlList](xref:accessControl) can only be updated if the current principal has ManageAccessControl access.

### Returns

| Status Code | Return Type | Description | 
 | --- | --- | ---  | 
| 200 | AccessControlList | Returns the updated [AccessControlList](xref:accessControl). | 
| 400 | Nothing is returned | Could not update the [AccessControlList](xref:accessControl) of the specified `Namespace` due to missing or invalid input. | 
| 403 | Nothing is returned | Unauthorized to update the [AccessControlList](xref:accessControl) for the specified `Namespace`. | 
| 405 | Nothing is returned | Method not allowed at this base URL. Try the request again at the Global base URL. | 



***

## `Get Namespace Owner`

Returns the Owner's [Trustee](xref:accessControl) for a given `Namespace`.

### Http

`GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/owner`


### Parameters

```csharp
[Required]
[FromRoute]
string tenantId
```

The identifier of the account to access.
```csharp
[Required]
[FromRoute]
string namespaceId
```

The identifier of the `Namespace` to access.


### Security

An Owner's [Trustee](xref:accessControl) can only be retrieved if the current principal has Read access.

### Returns

| Status Code | Return Type | Description | 
 | --- | --- | ---  | 
| 200 | Trustee | Returns the Owner's [Trustee](xref:accessControl) of the specified `Namespace`. | 
| 400 | Nothing is returned | Could not retrieve the Owner's [Trustee](xref:accessControl) of the specified `Namespace` due to missing or invalid input. | 
| 403 | Nothing is returned | Unauthorized to get the Owner's [Trustee](xref:accessControl) of the specified `Namespace`. | 


***

## `Set Namespace Owner`

Changes the Owner's [Trustee](xref:accessControl) for a given `Namespace`.

### Http

`PUT api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/owner`


### Parameters

```csharp
[Required]
[FromRoute]
string tenantId
```

The identifier of the account to access.
```csharp
[Required]
[FromRoute]
string namespaceId
```

The identifier of the `Namespace` to access.
```csharp
[Required]
[FromBody]
Trustee newOwner
```

The new Owner's [Trustee](xref:accessControl) of the `Namespace`.


### Security

An Owner's [Trustee](xref:accessControl) can only be changed if the current principal has ManageAccessControl access.

### Returns

| Status Code | Return Type | Description | 
 | --- | --- | ---  | 
| 200 | Trustee | Returns the new Owner's [Trustee](xref:accessControl) of the specified `Namespace`. | 
| 400 | Nothing is returned | Could not change the Owner's [Trustee](xref:accessControl) of the specified `Namespace` due to missing or invalid input. | 
| 403 | Nothing is returned | Unauthorized to change the Owner's [Trustee](xref:accessControl) of the specified `Namespace`. | 
| 405 | Nothing is returned | Method not allowed at this base URL. Try the request again at the Global base URL. | 


***

