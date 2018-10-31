---
uid: AccountNamespaceTier
---

NamespaceTier
=======================================================

## Properties

For HTTP requests and responses, the NamespaceTier object has the following properties and JSON-serialized body: 

```csharp
string Id
```
GUID for this Namespace Tier.

```csharp
string Description
```
Description of this Tier.

```csharp
int32 ThroughputUnits
```
The number of throughput units associated with this Tier.

```csharp
int32 StorageUnits
```
The number of Storage units associated with this Tier.


```json
{
	"Id": "id",
	"Description": "description",
	"ThroughputUnits": 0,
	"StorageUnits": 0
}
```
***

## `GetNamespaceTier()`

Retrieves a Namespace tier associated with a specified id

**Http**

`GET api/NamespaceTiers/{namespaceTierId}`

**Parameters**

```csharp
string namespaceTierId
```
The tier identifier for this request

**Security**

Allowed by Account Member [`Role`](xref:AccountRole)

**Returns**

A `NamespaceTier` object with the specified namespaceTierId

***
## `GetAllNamespaceTiers()`

Retrieves a list of all available namespace tiers.

**Http**

`GET api/NamespaceTiers`

**Parameters**

This API call does not have any parameters.

**Security**

Allowed by Account Member [`Role`](xref:AccountRole)

**Returns**

An array of `NamespaceTier` objects

***