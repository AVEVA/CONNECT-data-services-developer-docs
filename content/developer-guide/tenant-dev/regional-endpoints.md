---
uid: regional-endpoints
---

# Regional endpoints

A regional endpoint is the URL host address referenced by API requests. The region represents the cluster where AVEVA Data Hub cloud resources and data are stored, and is usually selected based on your company's geographic location. 

The table below lists the current AVEVA Data Hub region labels and corresponding endpoints.

| AVEVA Connect & AVEVA Data Hub region labels  | Corresponding AVEVA Data Hub regional endpoint|
| ------------- | ----------------- |
| US-West (westus) | https://uswe.datahub.connect.aveva.com/ |
| EU-West (northeurope) | https://euno.datahub.connect.aveva.com/ | 

**Note:** The region is selected at initial setup when an AVEVA Connect folder is created. The region cannot be changed after folder creation.

## Endpoint usage guidelines

You reference the regional endpoint in read, write and delete API requests.

To retrieve a region's host URL for an object that belongs to a namespace, for example, streams, use the `Self` property within the context of the namespace.

In general, any AVEVA Data Hub object whose API route contains `/Namespaces` can use these actions:

* GET

* PUT

* POST

* PATCH

If an object's API route does not contain `/Namespaces`, follow these guidelines:

* Use the GET action for either region

* Use PUT, POST, PATCH, and DELETE actions for the US-West region only.  See the table below for a full list of objects and actions you can use in the US-West region.

## List of objects and actions (US-West region only)

This table lists all the actions you can take on AVEVA Data Hub objects in the US-West region.

| AVEVA Data Hub Object |	GET |	POST |	PUT | PATCH |	DELETE |
| ------ | ------ | ------ | ------ | ------ | ------ |
| Automation Identities |	 | ✔ | ✔ |	✔ |	✔ |
|Blogs|	✔|	✔|	✔|	✔|	✔|
|Clients (all types)	|	|✔|	✔|	✔|	✔|
|Entitlements |  | ✔ |	✔ |	✔ |	✔ |
|Identity Providers |	|✔	|✔	|✔	|✔|
|Invitations | | ✔ | ✔ | ✔ | ✔ |
|Namespace ACL	|	|✔	|✔|	✔|	✔|
|Namespace Owner |  | ✔ | ✔ | ✔ | ✔ |
|Namespaces	| | ✔ |	✔|	✔|	✔|
|Persisted Grants| | **N/A** | **N/A** | **N/A** | ✔ |
|Roles	| | ✔ | ✔ | ✔ | ✔ |
|Root Access Control |	| **N/A** |	✔ |	✔ |	**N/A** |
|Secrets (all types) |	| ✔ | ✔| ✔ | ✔ |
|Tenant Entitlement Manual Block |   |	|	✔ | | |		
|Tenant Entitlements| |	✔ |	✔ |	✔ |	✔ |
|Tenants	| |✔	|✔	|✔	|✔|
|Users |	| ✔ | ✔| ✔ | ✔ |
