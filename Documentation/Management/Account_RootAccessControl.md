---
uid: accountRootAccessControl
---

RootAccessControl
=======================================================

Apis to control default access to entities governed by an [`AccessControlList`](xref:accessControl#accesscontrollistobj).

***

### `GetRootNamespaceAcl()`

Get the [`AccessControlList`](xref:accessControl#accesscontrollistobj) that is used to authorize access to a [`Namespace`](xref:AccountNamespace) if none is specified during creation.

**Http**

`GET api/Tenants/{tenantId}/AccessControl/Namespaces`

**Parameters**

```csharp
string tenantId
```
The idenfifier for the account being accessed.


**Security**

[`CommonAccessRights.Read`](xref:accessControl#accesscontrollistobj)

**Returns**

The root `AccessControlList` for `Namespaces`.

***

### `SetRootNamespaceAcl()`

Set the [`AccessControlList`](xref:accessControl#accesscontrollistobj) that is used to authorize access to a [`Namespace`](xref:AccountNamespace) if none is specified during creation.

**Http**

`PUT api/Tenants/{tenantId}/AccessControl/Namespaces`

**Parameters**

```csharp
string tenantId
```
The idenfifier for the account being modified.
```csharp
AccessControlList newAccessControlList
```
The new root `AccessControlList` for `Namespaces`.


**Security**

[`CommonAccessRights.ManageAccessControl`](xref:accessControl#accesscontrollistobj)

**Returns**

The new root `AccessControlList` for `Namespaces`.

***