---
uid: bpNamespaces
---

# Folder best practices

When creating folders/namespaces in AVEVA Connect, create a separate folder for each environment. AVEVA Connect initiates the namespace creation in AVEVA Data Hub.

Identity resources, such as users, clients, and so on, are scoped globally across namespaces in AVEVA Data Hub. For example, it is not possible to have `User1` in the Production folder but not in the Staging folder. In AVEVA Connect, users are global across an AVEVA Connect account.

Create folders/namespaces for tenants when all the data belongs to one organization. If you need to use the data together, you should store it together in one namespace. Note that objects and collections do not automatically inherit security from their folder/namespace.
