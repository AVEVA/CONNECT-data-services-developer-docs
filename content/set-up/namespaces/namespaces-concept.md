---
uid: ccNamespaces
---

# Folders and namespaces

The following list contains several important points related to folders and namespaces in AVEVA Data Hub:
 
- When you enable a Data Hub tile and create a folder in AVEVA Connect, a namespace is automatically created in Data Hub. 

- A namespace is linked to an associated AVEVA Connect folder. 

- Namespaces represent a logical unit of organization for data within a tenant.

  - A Data Hub tenant is the equivalent of an AVEVA Connect account.

  - Each tenant may have more than one namespace, and each namespace is associated with a unique folder in an AVEVA Connect account.

- Before Data Hub can receive data for a given tenant, a namespace must exist within the scope of the AVEVA Data Hub tenant.

- The Connect folder specifies the region where data will be stored for Data Hub; for example, West US or Northern Europe.

Multiple folders in Connect can have Data Hub turned on.  Each folder represents an AVEVA Data Hub namespace, and all of the namespaces are part of one Data Hub tenant and one AVEVA Connect account.

Data processing resources are allocated to a namespace after you create a folder and turn on AVEVA Data Hub. For example, SDS and asset services, and the associated storage resources are allocated to support a namespace. Each namespace and its resources are distinct and separate from all other namespaces. For example, you can create an SdsType or an SdsStream object with the same name in two different namespaces.

Data stored within a folder and its namespace is tied to the namespace and its region. You cannot directly transfer this data to any other namespace (or region). To move data between namespaces, you must export the data from the source namespace in AVEVA Data Hub, then [import it](xref:transfer-data) into the destination namespace.

## PI Server counterpart

A namespace is similar to a full PI Server. Much like a PI Server, a namespace has its own resources and it is not typical or easy to use data from multiple namespaces at the same time. It is reasonable for a tenant to have only one namespace.

## Namespace IDs

An AVEVA Data Hub namespace ID is defined by the solution ID in the AVEVA Connect folder. You can view a namespace's ID by clicking the Change Namespace down arrow in the Data Hub portal. The namespace description is synchronized with the AVEVA Connect folder name.

## Querying data across namespaces

When querying API endpoints, the namespace ID is part of the URL. The API URL takes the form `https://{server}/api/{version}/Tenants/{tenant id}/Namespaces/{namespace id}`, followed by the API path, such as `/Streams`.  Because the URL contains the namespace, it is not possible to make a single API request for data across multiple namespaces.
