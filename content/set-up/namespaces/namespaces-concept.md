---
uid: ccNamespaces
---

# Folders and namespaces

An AVEVA Data Hub tenant is the equivalent of an AVEVA Connect account. An AVEVA Connect account can only be associated with one AVEVA Data Hub tenant. Each tenant may have more than one namespace, and each namespace is associated with a unique folder in an AVEVA Connect account.

A namespace represents a logical unit of organization for data within a tenant. When you enable an AVEVA Data Hub tile and create a folder in AVEVA Connect, a namespace is automatically created in AVEVA Data Hub. Multiple folders in AVEVA Connect can have AVEVA Data Hub turned on. Each folder represents an AVEVA Data Hub namespace, and all of the namespaces are part of one tenant and one AVEVA Connect account.

Data processing resources are allocated to a namespace after you create a folder and turn on AVEVA Data Hub. For example, SDS and asset services, and the associated storage resources are allocated to support a namespace. Each namespace and its resources are distinct and separate from all other namespaces. For example, you can create an SdsType or an SdsStream object with the same name in two different namespaces.

Data stored within a folder and its namespace is tied to the namespace and its region. You cannot directly transfer this data to any other namespace (or region). To move data between namespaces, you must export the data from the source namespace in AVEVA Data Hub, then [import it](xref:transfer-data) into the destination namespace.

As the administrator or developer setting up folders and namespaces, consider the following important points:
 
* Before Data Hub can receive data for a given tenant, a namespace must exist within the scope of the AVEVA Data Hub tenant.

* A namespace is linked to an associated AVEVA Connect folder.

* The AVEVA Connect folder specifies the data storage region; for example, West US or Northern Europe.

* The folder name is saved as the namespace description. 

* A namespace's description can only be changed by editing the associated AVEVA Connect folder name.

## PI Server counterpart

A namespace is similar to a full PI Server. Much like a PI Server, a namespace has its own resources and it is not typical or easy to use data from multiple namespaces at the same time. It is reasonable for a tenant to have only one namespace.

## Namespace IDs

An AVEVA Data Hub namespace ID is defined by the solution ID in the AVEVA Connect folder. You can view a namespace's ID by selecting the Change Namespace dropdown list in the AVEVA Data Hub portal. The namespace description is synchronized with the AVEVA Connect folder name.

## Querying data across namespaces

When querying API endpoints, the namespace ID is part of the URL. The API URL takes the form `https://{server}/api/{version}/Tenants/{tenant id}/Namespaces/{namespace id}`, followed by the API path, such as `/Streams`.  Because the URL contains the namespace, it is not possible to make a single API request for data across multiple namespaces.

## Namespace deletion

A namespace gets suspended when the administrator turns off the AVEVA Data Hub tile in a Connect folder. The customer then has 30 days to get the namespace reactivated. During the 30-day suspension period, neither reading or writing to the namespace is permitted. After 30 days, the namespace is deleted.
