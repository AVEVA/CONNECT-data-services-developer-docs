---
uid: regional-endpoints
---

# Regional endpoints

A regional endpoint is the URL host address referenced by API requests. The region represents the cluster where AVEVA Data Hub cloud resources and data are stored. 

The table lists the current AVEVA Data Hub region labels and corresponding endpoints.

| AVEVA Data Hub regional endpoints |  AVEVA Connect & AVEVA Data Hub region labels |
| ------------- | ----------------- |
| https://uswe.datahub.connect.aveva.com/  | US-West (westus) |
| https://euno.datahub.connect.aveva.com/ | EU-North (northeurope)  | 

**Note:** US-West is the primary region and only certain actions may be taken in this region. The region is selected at initial setup when an AVEVA Connect folder is created, and cannot be changed after folder creation.

## Endpoint usage guidelines

Reference the regional endpoint in READ, WRITE and DELETE requests. To retrieve a region's host URL for an object that belongs to a namespace, such as a stream, use the `Self` property within the context of the namespace.

In general, any AVEVA Data Hub object whose API route contains `/Namespaces` can use these actions:

* GET

* DELETE

* PATCH

* POST

* PUT

If an object's API route does not contain `/Namespaces`, follow these guidelines:

* Use the GET action for either region

* Use PUT, POST, PATCH, and DELETE actions for the US-West region only.  The table below provides a list of these objects and actions.

## List of objects and actions (US-West region only)

This table lists all the actions you can take on AVEVA Data Hub objects in the US-West region.

| AVEVA Data Hub Object |	GET |	POST |	PUT | PATCH |	DELETE |
| ------ | ------ | ------ | ------ | ------ | ------ |
| Automation Identities |	 | ✔ | ✔ |	✔ |	✔ |
|Blogs|	✔|	**N/A**|	**N/A**|	**N/A**|	**N/A**|
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
