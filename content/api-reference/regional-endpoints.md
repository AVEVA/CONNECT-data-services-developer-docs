---
uid: regional-endpoints
---

# Regional endpoints

A regional endpoint is the URL host address referenced by API requests. The region represents the cluster where CONNECT data services cloud resources and data are stored. 

The following table lists the current CONNECT data services region labels and corresponding endpoints.

| CONNECT region label | CONNECT data services region label | CONNECT data services regional endpoints |
| ------------- | ------------- | ----------------- |
| US-West | (westus) | https://uswe.datahub.connect.aveva.com/ |
| EU-West | (northeurope) | https://euno.datahub.connect.aveva.com/ |
| Australia | (australiaeast) | https://auea.datahub.connect.aveva.com |

**Note:** US-West is the primary region. The region is selected at initial setup when a CONNECT folder is created, and cannot be changed after folder creation. If a region other than the primary region has been selected, calls may still be made to the US-West region.

## Endpoint usage guidelines

Reference the regional endpoint in GET, POST, PUT, PATCH, and DELETE requests. To retrieve a region's host URL for an object that belongs to a namespace, such as a stream, use the `Self` property within the context of the namespace.

In general, most CONNECT data services API routes allow these actions:
 
* GET

* PATCH

* POST

* PUT

* DELETE

## List of objects and actions (US-West region only)

The following table lists all the actions you can use on CONNECT data services objects in the US-West (primary) region. 

| CONNECT data services Object |	GET |	POST |	PUT | PATCH |	DELETE |
| ------ | ------ | ------ | ------ | ------ | ------ |
| Automation Identities |	 | ✔ | ✔ |	✔ |	✔ |
|Blogs|	✔|	**N/A**|	**N/A**|	**N/A**|	**N/A**|
|Clients (all types)	|	|✔|	✔|	✔|	✔|
|Invitations | | ✔ | ✔ | ✔ | ✔ |
|Namespace ACL	|	|✔	|✔|	✔|	✔|
|Namespace Owner |  | ✔ | ✔ | ✔ | ✔ |
|Persisted Grants| | **N/A** | **N/A** | **N/A** | ✔ |
|Roles	| | ✔ | ✔ | ✔ | ✔ |
|Root Access Control |	| **N/A** |	✔ |	✔ |	**N/A** |
|Secrets (all types) |	| ✔ | ✔| ✔ | ✔ |
|Users |	| ✔ | ✔| ✔ | ✔ |
