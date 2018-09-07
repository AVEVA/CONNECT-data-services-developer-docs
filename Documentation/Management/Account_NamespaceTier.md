---
uid: AccountNamespaceTier
---

NamespaceTier
=======================================================

An attribute that specifies namespace performance.

	For HTTP requests and responses, the NamespaceTier object has the following properties and JSON-serialized body: 

#### NamespaceTierObj 

``string Id``
	GUID for this Namespace Tier.
``string Description``
	Description of this Tier.
``int32 ThroughputUnits``
	The number of throughput units associated with this Tier.
``int32 StorageUnits``
	The number of Storage units associated with this Tier.

.. highlight:: C#

    	HTTP/1.1 200
    	Content-Type: application/json

     {
    	"Id": "id",
    	"Description": "description",
    	"ThroughputUnits": 0,
    	"StorageUnits": 0
     }

**********************

``GetNamespaceTier()``
--------------------------------------------------------------------

Retrieves a Namespace tier associated with a specified id

**Http**

    	GET api/NamespaceTiers/{namespaceTierId}

**Parameters**

``string namespaceTierId``
	The tier identifier for this request

**Security**  
Allowed by Account Member [Role](xref:accountRole#roleobj)

**Returns**  
A [NamespaceTier](#namespacetierobj) object with the specified namespaceTierId

**********************

``GetAllNamespaceTiers()``
--------------------------------------------------------------------

Retrieves a list of all available namespace tiers.

**Http**

    	GET api/NamespaceTiers

**Parameters**


**Security**  
Allowed by Account Member [Role](xref:accountRole#roleobj)

**Returns**  
An array of [NamespaceTier](#namespacetierobj) objects

**********************
