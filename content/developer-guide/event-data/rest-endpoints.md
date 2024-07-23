---
uid: RESTEndpoints
--- 

# REST endpoints for event and reference data

Along with the GraphQL endpoint, there are also two REST endpoints for querying and mutating event and reference data. These are `/events` and `/referenceData`. They both work the same, except one works with Event Types and the other with Reference Data Types. The queries and results from these endpoints are simpler than GraphQL, but not as powerful.

Some of the advantages of REST endpoints versus GraphQL:

- POST body is a simple JSON object or object array.

- Responses are JSON objects or object arrays instead of the GraphQL Request/Response object type.

- Errors have an HttpStatus code instead of the GraphQL Error collection (mainly useful to detect 400 level errors).

The REST endpoints also have some limitations:

- There is no editor intellisense support; you need to know the typeIds and property names you are working with.

- Filters are limited to 2 object levels (ex: asset.id eq "123").

- Syntax errors can be cryptic because they may still come from GraphQL.

## GET

You can pass typeId, fields, filter, order by, count, and continuation token arguments to query these endpoints. These are then turned into GraphQL for execution. The results are returned in a simple JSON array of objects.

- typeId – This is the Type Id from the type in the TypeStore. It must be one of the defined types.

- id – This is a specific entity Id. If you pass an id, you will get a single object back, not an array.

- fields – If not provided, all non-collection fields are returned from the entities. Otherwise, this is a GraphQL field selection specification. For example: `fields=id name asset {id name}`

- filter – This allows you to write expressions that are turned into GraphQL filters. Only AND operations are supported. Here are some examples:

  - `id eq "id_001"`

  - `startTime ge "2022-02-21T05:17:00Z" AND endTime lt "2022-02-21T05:18:00Z"`

  - `quantity ge 99 AND quantity.uom "lbs"`

  - Assume that you have an event property called assetMember, and it references Asset. You can filter on the Asset properties as below:

     - `assetMember.Name eq "Asset1"`

     - `contains(assetMember.Name, "Asset")`

     - `contains(assetMember.Name, "Asset") AND startsWith(assetMember.TypeName, "Turbine")`

     - `assetMember.metadata.Site in ["Buffalo", "New York"]`

- orderBy – This specifies a single sort property and ASC or DESC. For example: `&orderBy=endTime desc`

- count – This specifies the number of rows to be returned.

- continuationToken – This specifies if you want paging or not. The paged results have a different format than the non-paged results. They include an extra level that can hold a continuationToken. You must specify a blank continuationToken to start a paging request. For example: `continuationToken=` 

## POST

You can pass a typeId argument and a body of JSON (array or single object) to upsert entities to these endpoints.

- typeId – This is the Type Id from the type in the TypeStore. It must be one of the defined types.

- fields – If not provided, all non-collection fields are returned from the entities. Otherwise, this is a GraphQL field selection specification. For example: `fields=id name asset {id name}`

  **Note**: If you are not using the response data from your POST, it is recommended that you pass `fields=id` to limit the amount of data returned.

## DELETE

You can pass a typeId and id arguments to delete entities using these endpoints.

- typeId – This is the Type Id from the type in the TypeStore. It must be one of the defined types.

- id – This is the id of a specific entity.
