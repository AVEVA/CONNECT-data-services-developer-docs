---
uid: osisoftCloudServices
---

# CONNECT data services API reference guide

This guide provide detailed information about the functions, classes, methods, and endpoints exposed by the CONNECT data services REST API. It serves as a reference manual for developers who want precise information about how to interact with the software programmatically. It is written for developers who are already familiar with CONNECT data services and need specific information about its API endpoints, parameters, return values, and usage.

## Access to CONNECT data services

You must acquire an account before interacting with CONNECT data services. To request an account, contact us at the [AVEVA Knowledge and Support Center](https://softwaresupport.aveva.com/).

## API console

For information on the graphical interface for using the REST API within CONNECT data services, see [API console](xref:apiConsole).

### Response format

Supported response formats include JSON, verbose JSON, and SDS.

In the API Console for CONNECT data services Portal, the default value of the header `Accept-Verbosity` is `verbose` for the response format. Verbose JSON responses include all values in the returned JSON payload, including defaults. To specify verbose JSON return, add the header `Accept-Verbosity` with a value of `verbose` to the request.

Calls to the API from other sources do not include `Accept-Verbosity` as a standard. The `Accept-Verbosity` heading needs to be specified.  If you do not include the the `Accept-Verbosity` heading, all calls except for dataview calls will be `non-verbose` and dataview calls will be `verbose`.

When set to `non-verbose`, properties with null values are omitted from the response to reduce bandwidth. This behavior is only applicable to the JSON format, as all other formats represent a table which cannot have omitted values. Verbose has no impact on writes; writes return only error messages.

The default response format for SDS is JSON. Default JSON responses do not include any values that are equal to the default value for their type. Note that the `Accept-Verbosity` header for SDS differs as its default is set to `non-verbose`. Verbose has no impact on writes; writes return only error messages.

To specify SDS format, set the `Accept` header in the request to `application/sds`.

## Architecture

A tenant represents the set of services, applications, data, and configuration states available to a customer in CONNECT data services. Users are associated with a tenant via at least one configured identity provider, a database of user records that allows for authentication, and access to resources can be managed for those users via the assignment of roles.

Tenants are divided into one or more logical units called Namespaces. Each Namespace is distinct and separate from other Namespaces with its own instances of the various CONNECT data services and data stores. Namespaces provide isolation of resources.

Namespaces are provisioned within a region. The Namespace's services and data stores all exist in the Namespace's region. Resources allocated to a Namespace are isolated to the Namespace's region. For more information on regions see the [Namespaces](xref:tenant-namespaces) documentation.  Isolation provided by Tenants and Namespaces prevents accidental or malicious data access.

CONNECT data services provides data residency via namespaces in the following regions:

| CONNECT region label | CONNECT data services region label |
| ------------- | ------------- |
| US-West | (westus) |
| EU-West | (northeurope) |
| Australia | (australiaeast) |

Tenant account information is stored in all regions for read-only purposes. Write operations are only supported through the global base URL. See [Get regions](xref:tenant-tenants#list-regions) for information on how to access this data.

## CONNECT data services API versioning

New versions of the API are released when major changes occur in the CONNECT data services API. When a newer version of the API is released, the legacy version of the API will only be supported for a period of time. We encourage all users to switch to the newer version as soon as possible. Versions are inline in the routes, following the host:

```text
api/v{version}/Tenants/{tenantId}/Namespaces/{namespaceId}/...
```

Where:

* version is an incrementally (singular) increasing integer value
* v{version}-preview will be used to expose beta functionality

The currently supported versions are:

* v1
* v1-preview
* v2-preview
