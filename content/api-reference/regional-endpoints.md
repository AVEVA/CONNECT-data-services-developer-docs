---
uid: regional-endpoints
---

# Regional endpoints

A regional endpoint is the URL host address referenced by API requests. The region represents the cluster where AVEVA Data Hub cloud resources and data are stored. 

The table lists the current AVEVA Data Hub region labels and corresponding endpoints.

| AVEVA Connect & AVEVA Data Hub region labels | AVEVA Data Hub regional endpoints |
| ------------- | ----------------- |
| US-West (westus) | https://uswe.datahub.connect.aveva.com/ |
| EU-North (northeurope) | https://euno.datahub.connect.aveva.com/ | 

**Note:** US-West is the primary region. The region is selected at initial setup when an AVEVA Connect folder is created, and cannot be changed after folder creation. If a region other than the primary region has been selected, calls may still be made to the US-West region.

## Endpoint usage guidelines

Reference the regional endpoint in GET,  POST,  PUT, PATCH, and DELETE requests. To retrieve a region's host URL for an object that belongs to a namespace, such as a stream, use the `Self` property within the context of the namespace.

In general, most AVEVA Data Hub API routes allow these actions:
 
* GET

* PATCH

* POST

* PUT

* DELETE

## List of objects and actions (US-West region only)

This table lists all the actions you can take on AVEVA Data Hub objects in the US-West (primary) region. 

| AVEVA Data Hub Object |	GET |	POST |	PUT | PATCH |	DELETE |
| ------ | ------ | ------ | ------ | ------ | ------ |
| Automation Identities |	 | ✔ | ✔ |	✔ |	✔ |
|Blogs|	✔|	**N/A**|	**N/A**|	**N/A**|	**N/A**|
|Clients (all types)	|	|✔|	✔|	✔|	✔|
|Invitations | | ✔ | ✔ | ✔ | ✔ |
|Namespace ACL	|	|✔	|✔|	✔|	✔|
|Namespace Owner |  | ✔ | ✔ | ✔ | ✔ |
|Namespaces	| | ✔ |	✔|	✔|	✔|
|Persisted Grants| | **N/A** | **N/A** | **N/A** | ✔ |
|Roles	| | ✔ | ✔ | ✔ | ✔ |
|Root Access Control |	| **N/A** |	✔ |	✔ |	**N/A** |
|Secrets (all types) |	| ✔ | ✔| ✔ | ✔ |
|Users |	| ✔ | ✔| ✔ | ✔ |
