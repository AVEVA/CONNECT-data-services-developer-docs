---
uid: EventData
--- 

# Event data

You can store event data, such as manufacturing execution systems (MES) data, in AVEVA Data Hub. This allows you to store data from multiple site systems into AVEVA Data Hub to visualize, create reports, and work with data across the enterprise.  

## Types

Events are time-oriented operational data. All event data must have a type. You can create and manage a set of namespace-scoped Event Types, which are definitions for domain-specific events and surrounding metadata. The [Event Type Store APIs](xref:EventTypeStore) allow you to set up the Event Types, Reference Data Types, and Enumerations. 

### Event Types

An Event Type is a collection of properties, each configured as:

- A scalar value (int, double, datetime, string, bool, ID, etc.)
- A custom enumeration
- A relationship to another Event Type
- A relationship to a type from an adjacent service (such as assets)
- A collection of any of these things

Event Types have the following auto-generated properties by default when they are created. Some properties can be populated by the user when creating an event. The rest will auto-populate.

- id
- name
   If a name is not provided, the id will be assigned to the name.
- description
- asset
- startTime
- endTime
- duration
- state
   This property is read-only. The state is active if an event only has a startTime, or closed if an event has a startTime and endTime.
- createdDate
   This property is read-only.
- modifiedDate
   This property is read-only.
- createdByUser
   This property is read-only.
- authorizationTags
   See [Managing Permissions](#managing-permissions).

### Reference Data Types

Reference data provides additional information for the context of an event, and is useful for users and/or applications when data is consumed, analyzed, visualized, and reported on. Reference data is typically configuration or system definition information. 

Reference Data Types are collections of configurable properties that can include references to other Reference Data or Events.

Reference Data Types have the following auto-generated properties by default when they are created. Some properties can be populated by the user when creating an event. The rest will auto-populate.

- id
- name
   If a name is not provided, the id will be assigned to the name.
- description
- createdDate
   This property is read-only.
- modifiedDate
   This property is read-only.
- createdByUser
   This property is read-only.
- authorizationTags
   See [Managing Permissions](#managing-permissions).

Reference Data Types that reference external data have the following additional default properties:

- sourceId
- resourceId

## Type properties

When modeling events and reference data, you give the types a name and add properties to the types. The properties have a name and an Id. The Id cannot be changed, but the name can. Properties can be any of the following scalar types:

PropertyTypeCode
- String
- Boolean
- Int32
- Int64
- Double
- TimeSpan
- DateTime
- Enumeration – defined using the Enumerations endpoint
  - PropertyTypeId is the enumeration Id

Ids and names must be unique across all types, Event Types, Reference Data Types and Enumerations. This includes any munging done to remove unsupported characters when generating the GraphQLName. 

It is best practice to name types, properties, and enumerations in a GraphQL-friendly manner. If the name is in the proper format, the generated GraphQLName will be the same as the name. Otherwise, the GraphQLName will not match the name field.

Best practices for GraphQL naming:
- Name can use these characters: [_A-Za-z][_0-9A-Za-z]
- Types and enum names are Pascal case (MyType)
- Property names are camel case (myProperty)

Numeric properties can also be given a default UOM with the `uom` property. This would be the Id or abbreviation of the UOM as defined by ADH Streams `units` endpoint. Defining a default UOM specifies the UOM that will be used if one is not provided during ingress. It also restricts the possible set of ingress UOM's to the same dimension as the default UOM. 

## Retrieval of types 

There are two parameters you can use when retrieving the collection of Enumerations, Reference Data Types, or Event Types. The boolean `includeDeleted` parameter allows the user to specify whether to include soft-deleted resources in the response body. The `filter` parameter allows the user to supply a comparison operator, the CreatedDate or ModifiedDate property, and a DateTime to indicate which resources to return. For example, the query string "CreatedDate gt 2023-06-01T00:00:00.00Z" will return resources created after the specified date. The following comparison operators can be used with the `filter` parameter. 

- Eq: Equal to 
- Ne: Not equal to 
- Lt: Less than 
- Gt: Greater than 
- Le: Less than or equal to 
- Ge: Greater than or equal to 

The filter string is case-insensitive. 

## Relationships

Properties can point to other types you define to form relationships. As a best practice, Event Type relationship properties can point to Reference Data Types, but Reference Data Types should not point to Event Types because if an event does not exist it will cause an error.

PropertyTypeCode:
- Event
  - PropertyTypeId is the event Type Id
- ReferenceData
  - PropertyTypeId is the reference data Type Id
- Asset

By default, relationship properties will be created in both directions. A RemoteReferenceName property will be automatically generated to specify the remote property name. It will usually be the current Type's name with an 's' added. If you do not like the generated name, you can set the RemoteReferenceName youself. If you do not want the remote relationship at all, you can specify the `NoReverseLookup` flag in the Flags property.

For example, a `Type: Alarm` with `Property: asset` would specify `RemoteReferenceName: alarms`.

**Note:** A remote reference is always created as a searchable array.

## Property flags

You can make scalar and relationship properties a collection by specifying the `IsCollection` flag.

**Note:** Collections are limited to 64 elements.

You can make scalar and relationship properties searchable by specifying the `Indexed` flag.

**Note:** At this time, collections are not a searchable property.

You can make them required by specifying the `Required` flag. Required means the property must be specified on a top-level ingress operation. It can also restrict a delete operation to maintain integrity.

You can opt out of making numeric values aggregate properties or UOM properties by using the `NoAggregate` and `NoUom` flags. This means the properties will not have the extra GraphQL schema structure to hold aggregations or UOMs.

## Generating the GraphQL schema

An ontology manager detects types that are written to the Type Store within 60 seconds and generates a GraphQL schema. The GraphQL schema represents a strongly-typed model and set of APIs for querying and modifying your type data.

**Note:** Depending on your changes, you can break existing queries and ingress operations. It is usually safe to add new types and properties. Deleting or renaming properties is more dangerous.

The `State` property on each Type and Enum affects how the GraphQL is generated.

- Active – schema generated for query and ingress
- Deprecated – schema generated for query only
- Deleted – not generated in schema; this is a soft-delete

Authorization Tag changes will also be detected within 60 seconds of changes and the new access policy will be pushed into the GraphQL server.

You can short-circuit the 60 second detection by calling the `…/graphql/schema` endpoint. POST a non-empty body using text/plain content-type.

## GraphQL endpoint and APIs

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

Mutations allow you to upsert and delete data in the Graph Store. These APIs allow you to send in a collection of items to upsert or delete. If there are errors, the operation does not roll back. Instead, some items may succeed and some may fail. You can use the <xref:graphQLConsole> to create queries and mutations.

- Upsert – Creates the item node if it does not exist; else it updates it. 

  - The id property must always be provided. The startTime is required when creating a new top-level event.

  - Single point-in-time events can be modeled by setting endTime=startTime.

  - Missing properties are ignored on update, set to null on create.

     - This can work like a REST PATCH.

  - Null property values will clear a value.

  - Required properties must be passed at the top-level of an upsert. However, this is not enforced on child nodes.

  - When writing a numeric property, the format varies depending on whether it supports UOM structure or not.
  
    **Note**: The default behavior is to support UOM structure. You need to opt-out of UOM structure support when creating the type with the NoUom property flag.

     - NoUom structure: `{ quantity: 99 }`

     - Uom structure: `{ quantity: { value: 99  uom: { id: tons } } }`

       **Note**: uom can be set to null, in which case it defaults to the uom defined on the type property.

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

Queries allow you to query data in the Graph Store. These APIs allow you to choose your response structure (fields and relationships). They also allow you to filter, sort and page. You can use the <xref:graphQLConsole> to create queries and mutations.

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

## Managing permissions

You manage permissions to view event data with authorization tags.

Each event or reference data type has an optional default tag, which is applied to any node of that type. By default, the type is given the BaseAuthorizationTag. Additional authorization tags can be written when a node is created or updated. Roles are given access to authorization tags.

## REST endpoints for querying and mutating event and reference data

Along with the GraphQL endpoint, there are also two REST endpoints for querying and mutating event and reference data. These are `/events` and `/referenceData`. They both work the same, except one works with Event Types and the other with Reference Data Types. The queries and results from these endpoints are simpler than GraphQL, but not as powerful.

Some of the advantages of REST endpoints versus GraphQL:

- POST body is a simple JSON object or object array.

- Responses are JSON objects or object arrays instead of the GraphQL Request/Response object type.

- Errors have an HttpStatus code instead of the GraphQL Error collection (mainly useful to detect 400 level errors).

The REST endpoints also have some limitations:

- There is no editor intellisense support; you need to know the typeIds and property names you are working with.

- Filters are limited to 2 object levels (ex: asset.id eq "123").

- Syntax errors can be cryptic because they may still come from GraphQL.

### GET

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

- orderBy – This specifies a single sort property and ASC or DESC.

- count – This specifies the number of rows to be returned.

- continuationToken – This specifies if you want paging or not. The paged results have a different format than the non-paged results. They include an extra level that can hold a continuationToken. You must specify a blank continuationToken to start a paging request. For example: `continuationToken=` 

### POST

You can pass a typeId argument and a body of JSON (array or single object) to upsert entities to these endpoints.

- typeId – This is the Type Id from the type in the TypeStore. It must be one of the defined types.

- fields – If not provided, all non-collection fields are returned from the entities. Otherwise, this is a GraphQL field selection specification. For example: `fields=id name asset {id name}`

  **Note**: If you are not using the response data from your POST, it is recommended that you pass `fields=id` to limit the amount of data returned.

### DELETE

You can pass a typeId and id arguments to delete entities using these endpoints.

- typeId – This is the Type Id from the type in the TypeStore. It must be one of the defined types.

- id – This is the id of a specific entity.
