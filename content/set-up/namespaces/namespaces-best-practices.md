---
uid: bpNamespaces
---

# Folder naming best practices

Use one of the following strategies when creating folders/namespaces in AVEVA™ Connect:

- Strategy 1 &ndash; Create a separate folder for each environment. For example, Production, Development, Staging, and so on.

- Strategy 2 &ndash; Create a separate folder/namespace for each of your business units or geographical regions.
 
    **Note:** Connect initiates the namespace creation. A namespace is created in Data Hub. 

Use the first strategy for tenants where all the data belongs to one organization. Keep in mind, if you need to use the data together, you should store it together in one namespace.

The second strategy makes it easier to avoid naming conflicts and to manage security and assign permissions. Note that objects and collections do not automatically inherit security from their folder/namespace. Create separate folders for each business unit or region and create another folder/namespace for internal use that includes your Production, Development, and Staging environments.
