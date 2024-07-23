---
uid: GraphQLEndpoint
--- 

# GraphQL endpoint and APIs

The generated GraphQL APIs are the entry point to use GraphQL. These are visible in the portal by navigating to **Developer Tools** > **GraphQL API Console**. The console adds a user-friendly interface to help you learn GraphQL and to build queries and mutations. You can also use GraphQL clients or even REST clients to interact with the GraphQL endpoint.

The APIs generated in the GraphQL schema are:

- assets – allows you to query assets from the asset service
- events – allows you to query and upsert/delete your event data
- referenceData – allows you to query and upsert/delete your reference data

GraphQL APIs return a standard GraphQL response type. This has the basic JSON format of:

- data
  - apiCollection (ex: events)
     - apiName (ex: queryMyEvent)
       - array of requested data
- errors
  - array of errors
     - message – error message
     - path – specifies where in input the failure happened
     - locations
     - extensions
        - code – specifies what went wrong (maps to HttpStatus)
        - data
           - id – specifies the id of the top-level item (for retry purposes)
- extensions
  - continuation – used for paging

## Mutations

Mutations allow you to upsert and delete data in the Graph Store. These APIs allow you to send in a collection of items to upsert or delete. If there are errors, the operation does not roll back. Instead, some items may succeed and some may fail. You can use the [GraphQL Console](https://docs.aveva.com/bundle/connect-data-services/page/1263333.html) to create queries and mutations.

- Upsert – Creates the item node if it does not exist; else it updates it. 

  - The id property must always be provided. The startTime is required when creating a new top-level event.

  - Single point-in-time events can be modeled by setting endTime=startTime.

  - Missing properties are ignored on update and set to null on create.

     - This can work like a REST PATCH.

  - Null property values will clear a value.

  - Required properties must be passed at the top-level of an upsert. However, this is not enforced on child nodes.

  - When writing a numeric property, the format varies depending on whether it supports UOM structure or not.
  
    **Note**: The default behavior is to support UOM structure. You need to opt-out of UOM structure support when creating the type with the `NoUom` property flag.

     - NoUom structure: `{ quantity: 99 }`

     - Uom structure: `{ quantity: { value: 99  uom: { id: tons } } }`

       **Note**: You can set `uom` to null, in which case it defaults to the `uom` defined on the type property.

  - When writing a tree of item nodes, the writes are done from the leaf nodes up.

  - An error writing a node at any level of the tree will cause the upsert to cancel the current write, up to the top-level. It will then continue with the next top-level item.

     - Errors are reported in the GraphQL errors collection.

  - Writing a collection property always updates the entire collection. No partial collection changes can be made.

  - Passing modifiedTime can be used for an optimistic concurrency check. If passed, it must match the exact value of the existing node.

  - Upserts are limited to 1000 top-level items and 2000 total nodes (in one request).

- Delete – Deletes each item by id.

  - An error deleting a node will cause the delete to continue with the next item.

    - Errors are reported in the GraphQL errors collection.

  - Deletes are limited to 100 nodes (in one request).

## Queries

Queries allow you to query data in the Graph Store. These APIs allow you to choose your response structure (fields and relationships). They also allow you to filter, sort and page. You can use the [GraphQL Console](https://docs.aveva.com/bundle/connect-data-services/page/1263333.html) to create queries and mutations.

- Query – Returns the results as requested by the query.

  - Syntax errors are caught and reported with various error codes in the GraphQL errors collection. They should not be retried.

  - The first WHERE filter is the most important for performance. It is also used for sorting. If you provide a Sort property, it is automatically moved to be your first Where filter. If the first Sort property is different than the first WHERE property, performance may be compromised.

  - Although multiple Sort properties are possible, they are meant for small sets of data. Paging is not properly supported with multiple Sorts.

  - For large sets of data, you can page with a Count option and a Continuation token.

  - Queries have node limits at every level. As you go deeper, the limits are reduced based on the number of nodes at the parent level.

  - Queries are limited to a certain number of levels (depth) and a certain number of relationships (complexity).

- Aggregations – A query can also do aggregations on numeric or TimeSpan properties, unless you opt-out with the `NoAggregate` property flag.

  - Use the `aggregate` property on any query to aggregate all rows returned for that level.

  - Any properties selected outside the `aggregate` property will be used for grouping. You can group on relationship properties, but not collection properties.

  - The `aggregate.count` property specifies the total number of rows in the group. The `<property>.count` property specifies the total number of rows that went into the properties aggregated values. This can be different than the total count if null values exist. Ex: `aggregate { count length {count max} }`

- UOMs – A query can also view UOMs for numeric values, unless you opt-out with the `NoUom` property flag.

  - Where filters can request a UOM to apply as part of the Where operator. All values will be converted to that UOM before comparing to the value. Not specifying a UOM will use the default UOM. Ex: `where: { length: { lt: 1000 uom: "meters" } }`

  - Aggregations can request a UOM to apply before aggregating the values. This is passed as an argument to the aggregate.property. The result will be in the requested UOM. Not specifying a UOM will use the default UOM. Ex: `aggregate: { length( uom: "meters" ){ sum } }`

  - Property values can be requested in a specific UOM. This is done by passing the UOM as an argument to the property. Not specifying a UOM will result in the UOM being returned as written. Ex: `length( uom: "meters" ) { value uom: { id }}`

