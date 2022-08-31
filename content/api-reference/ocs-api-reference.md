---
uid: osisoftCloudServices
---

# OCS API reference

The information in the sections that follow document the APIs and usage for each of the following:

* [Asset store](xref:Assets)—Use the information in this section to create or find assets of different types, along with their data and status.
* [Communities (Preview)](xref:communityOverview)—OCS Communities helps industrial companies share their operational data with external business partners, service providers, and analytics providers. 
* [Data collection](xref:dataIngress)—You use OSIsoft Message Format (OMF) to achieve high-throughput asynchronous data ingress into the OCS Sequential Data Store.
* [Data views](xref:DataViewsOverview)—Use the information in this section to create user-selected subsets of data stored in OSIsoft Cloud Services which are mapped into customizable table formats.
* [Identity and access management](xref:identityandaccessmanagement)—Use the information in this section to create, manage and administer users and clients.
* [Operations](xref:operationsOverview)—Use the information in this section to get metrics on OCS operation. 
* [Rules](xref:rules-lp)—The metadata rules feature in the OCS Portal simplifies the process of assigning metadata to streams.
* [Sequential Data Store (SDS)](xref:sds)—Use the information in this section to learn about the OSIsoft Cloud Services Sequential Data Store. The SDS is optimized for sequential data operations.
* [Tenant Management](xref:AccountManagementOverview)—Use the information in this section to create, manage, and administer your account by assigning users, roles, and namespaces to your tenant.

## Access to OCS

You must acquire an account before interacting with the OCS. 
Go to the [OCS page on OSIsoft website](https://www.osisoft.com/pi-system/pi-cloud/osisoft-cloud-services), select [Contact Us](https://www.osisoft.com/contact) and request an OCS account.


## API console

For information on the graphical interface for using the REST API within OCS, see [API console](xref:apiConsole).


## Architecture

A tenant represents the set of services, applications, data, and configuration states available to a customer in OSIsoft Cloud Services (OCS). Users are associated with a tenant via at least one configured identity provider, a database of user records that allows for authentication, and access to resources can be managed for those users via the assignment of roles. 

Tenants are divided into one or more logical units called Namespaces. Each Namespace is distinct and separate from 
other Namespaces with its own instances of the various OSIsoft Cloud Services and data stores. Namespaces provide isolation of resources. 

Namespaces are provisioned within a region. The Namespace's services and data stores all exist in the Namespace's region. Resources allocated to a Namespace are isolated to the Namespace's region. For more information on regions see the [Namespace](xref:AccountNamespace_1) documentation.  Isolation provided by Tenants and Namespaces prevents accidental or malicious data access. 

OSIsoft Cloud Services provides data residency via namespaces in the following regions:

| Supported Regions | Geographic Area | Location |
| --- | --- | ---  |
| WestUS | Americas | California |
| WestEurope | Europe | Netherlands |

Tenant account information is stored in all regions for read-only purposes. Write operations are only supported through the global base URL. See the [Tenant](xref:AccountTenant) documentation for information on how to access this data.


## OCS API versioning

New versions of the API are released when major changes occur in the OCS API. When a newer version of the API is released, 
the legacy version of the API will only be supported for a period of time. We encourage all users to switch to the 
newer version as soon as possible. Versions are inline in the routes, following the host:
```text
    api/v{version}/Tenants/{tenantId}/Namespaces/{namespaceId}/...  
```
Where:  
* version is an incrementally (singular) increasing integer value 

* v{version}-preview will be used to expose beta functionality

The currently supported versions are:
* v1
* v1-preview
