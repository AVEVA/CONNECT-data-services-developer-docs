---
uid: accountRootAccessControl
---

RootAccessControl
=======================================================

Apis to control default access to entities governed by an [AccessControlList](xref:accessControl#accesscontrollistobj).

**********************

``GetRootNamespaceAcl()``
--------------------------------------------------------------------

Get the [AccessControlList](xref:accessControl#accesscontrollistobj) that is used to authorize access to a [Namespace](xref:accountNamespace#namespaceobj) if none is specified during creation.

**Http**

    	GET api/Tenants/{tenantId}/AccessControl/Namespaces

**Parameters**

``string tenantId``
	The idenfifier for the account being accessed.

**Security**  
[CommonAccessRights.Read](xref:accessControl#commonaccessrightsenum)

**Returns**  
The root [AccessControlList](xref:accessControl#accesscontrollistobj) for [Namespaces](xref:accountNamespace#namespaceobj).

**********************

``SetRootNamespaceAcl()``
--------------------------------------------------------------------

Set the [AccessControlList](xref:accessControl#accesscontrollistobj) that is used to authorize access to a [Namespace](xref:accountNamespace#namespaceobj) if none is specified during creation.

**Http**

    	PUT api/Tenants/{tenantId}/AccessControl/Namespaces

**Parameters**

``string tenantId``
	The idenfifier for the account being modified.
``AccessControlList newAccessControlList``
	The new root [AccessControlList](xref:accessControl#accesscontrollistobj) for [Namespaces](xref:accountNamespace#namespaceobj).

**Security**  
[CommonAccessRights.ManageAccessControl](xref:accessControl#commonaccessrightsenum)

**Returns**  
The new root [AccessControlList](xref:accessControl#accesscontrollistobj) for [Namespaces](xref:accountNamespace#namespaceobj).

**********************
