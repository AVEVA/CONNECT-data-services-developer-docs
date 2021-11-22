---
uid: ccNamespaces
---

# Folders and namespaces

When you first subscribe and turn on AVEVA™ Data Hub for your organization, you create a folder in AVEVA™ Connect that is linked to a namespace. AVEVA™ Data Hub namespaces represent a logical unit of organization for data within a tenant. Each tenant may have more than one folder/namespace. Before AVEVA™ Data Hub can receive data for a given tenant, a namespace must exist within the scope of that tenant. When you create a folder in AVEVA™ Connect, you specify the region where data will be stored; for example, West US.

Data processing resources are allocated when you create a folder/namespace. For example, SDS and asset service, and the associated storage resources are allocated to support that namespace. Each namespace and its resources are distinct and separate from all other namespaces. The resources are scoped to the namespace. Which means, you can create an SdsType or an SdsStream object with the same name in two different namespaces.

Data stored within a folder/namespace is tied to a namespace and its region. You cannot directly transfer the data to any other namespace (or region). To move data between namespaces, you must export the data from the source namespace in AVEVA™ Data Hub, then import it into the destination namespace.

## PI Server counterpart

A namespace is similar to a full PI Server. Much like a PI Server, a namespace has its own resources and it is not typical or easy to use data from multiple namespaces at the same time. It is reasonable for a tenant to use only one namespace.

## Namespace IDs

The namespace ID must be unique across the tenant and meet these requirements:

- Contains 100 or fewer characters
- Can include alphanumeric characters, underscores (\_), dashes (-), spaces, and periods
- May not contain two consecutive periods or two consecutive underscores
- May not begin or end with a period
- May not start with two consecutive underscores
- May not include leading or trailing white spaces

## Querying data across namespaces

When querying API endpoints, the namespace ID is part of the URL. The API URL takes the form `https://{server}/api/{version}/Tenants/{tenant id}/Namespaces/{namespace id}`, followed by the API path, such as `/Streams`.  Because the URL contains the namespace, it is not possible to make a single API request for data across multiple namespaces.
