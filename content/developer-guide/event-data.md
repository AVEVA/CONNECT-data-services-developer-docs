---
uid: EventData
--- 

# Event data (Preview)

You can store event data, such as manufacturing execution systems (MES) data, in AVEVA Data Hub, as well as related reference data. This allows you to store data from multiple site systems into AVEVA Data Hub to visualize, create reports, and work with data across the enterprise.  

## Event Types

Events are time-oriented operational data. All event data must have a type. You can create and manage a set of namespace-scoped Event Types, which are definitions for domain-specific events and surrounding metadata.

The [Event Type Store APIs](xref:EventTypeStore) allow you to set up the event types, reference data types, and enumerations. 

An Event Type is a collection of properties, each configured as:

- A scalar value (int, double, datetime, string, bool, ID, etc.)
- A custom enumeration
- A relationship to another Event Type
- A relationship to a type from an adjacent service (assets, stream, etc.)
- A collection of any of these things

Event Types have the following base properties:

- id
- eventStartTime
- eventEndTime
- eventDuration
- eventState
- createdDate
- modifiedDate
- createdByUser

## Reference Data Types

Reference data provides additional information that can be referenced in the context of an asset or event, and is useful for users and/or applications when data is consumed, analyzed, visualized, and reported on. Reference data is typically configuration or system definition information. 

Reference Data Types are collections of configurable properties that can include references to other Reference Data or Events.

Reference Data Types have the following base properties:

- id
- createdDate
- modifiedDate
- createdByUser

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
- Enumeration – these are defined using the Enumerations endpoint
  - PropertyTypeId is the enumeration Id

It is best practice to name types, properties and enumerations in a GraphQL friendly manner. If they are not in the proper format, a GraphQLName will be generated.

- Best Practice GraphQL naming
  - Name can use these characters: [_A-Za-z][_0-9A-Za-z]
  - Types and Enum types are pascal case (ex: MyType)
  - Properties are camelCase: (ex: myProperty)
  - Enum values are upper-case

## Relationships

Properties can point to other types you define to form relationships. Event Type relationship properties can point to Reference Data Types, but Reference Data Types cannot point to Event Types.

PropertyTypeCode:
- Event
  - PropertyTypeId is the event Id
- ReferenceData
  - PropertyTypeId is the reference data Id

Relationship properties can specify if the relationship should be created in both directions. This is done by specifying the ReverseLookup flag and a RemoteReferenceName. This should be the plural remote property name that points back to the current type.

For example, a `Type: Alarm` with `Property: asset` would specify `RemoteReferenceName: alarms`.

**Note:** A remote reference is always created as a searchable array.

Scalar and relationship properties can be made a collection by specifying the `IsCollection` flag.

**Note:** Collections are limited in the number of elements they can hold (ex: 64 elements).

Scalar and relationship properties can be made searchable by specifying the `Indexed` flag. They can be made required by specifying the `Required` flag. Required means it must be specified on a top-level ingress operation. It can also restrict a delete operation to maintain integrity.

## Generating the GraphQL schema

When types are written to the Type Store, an ontology manager detects the changes within 60 seconds and generates a GraphQL schema. The GraphQL schema represents a strongly-typed model and set of APIs for querying and modifying your Type data.

**Note:** Depending on your changes, you can break existing queries and ingress operations. It is usually safe to add new types and properties. Deleting or renaming properties is more dangerous.

The `State` property on each Type and Enum affects how the GraphQL is generated.

-	Active – schema generated for query and ingress
-	Deprecated – schema generated for query only
-	Deleted – not generated in schema; this is a soft-delete

Authorization Tag changes will also be detected within 60 seconds of changes and the new access policy will be pushed into the GraphQL server.

You can short-circuit the 60 second detection by calling the `…/graphql/schema` endpoint. POST a non-empty body using text/plain content-type.

## GraphQL endpoint and APIs

The generated GraphQL APIs are the entry point to use GraphQL. These are visible in the portal by navigating to **Developer Tools** > **GraphQL API Console**. The console adds a user-friendly interface to help you learn GraphQL and to build queries and mutations. You can also use GraphQL clients or even REST clients to interact with the GraphQL endpoint.

The APIs generated in the GraphQL schema are:

-	assets – allow you to query assets from the asset service
-	events – allow you to query and upsert/delete your event data
-	referenceData - allow you to query and upsert/delete your reference data

GraphQL APIs return a standard GraphQL response type. This has the basic JSON format of:

-	data
  -	apiCollection (ex: events)
    -	apiName (ex: queryMyEvent)
      -	array of requested data
-	errors
  -	array of errors
    -	message – error message
    -	path – specifies where in input the failure happened
    -	locations
    -	extensions
      -	code – specifies what went wrong (maps to HttpStatus)
      -	data
        -	id – specifies the id of the top-level item (for retry purposes)
-	extensions
  -	continuation – used for paging

## Mutations

Mutations allow you to upsert and delete data in the Graph Store. These APIs allow you to send in a collection of items to upsert or delete. If there are errors, it is not rolled back. Instead some may succeed and some may fail. You can use the <xref:graphQLConsole> to create queries and mutations.

-	Upsert – Creates the item node if it does not exist; else it updates it. 

  - The id property must always be provided. The eventStartTime is required when creating a new event.

  - Missing properties are ignored on update, set to null on create.

    - This can work like a REST PATCH.

  - Null property values will clear a value.

  - Required properties must be passed at the top-level of an upsert. However, this is not enforced on child nodes.

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

  - The first WHERE filter is the most important for performance. It is also used for sorting. If the first Sort property is different than the first WHERE property, performance may be compromised.

  - Although multiple Sort properties are possible, they are meant for small sets of data. Paging is not properly supported with multiple Sorts.

  - Queries have node limits at every level. As you go deeper, the limits are reduced based on the number of nodes at the parent level.

  -	Queries are limited to a certain number of levels (depth) and a certain number of relationships (complexity).

## Managing permissions

Permissions to view event data are managed with authorization tags.

Each event or reference data type has a default tag which is applied to any node of that type. Additional authorization tags can be written when a node is created or updated. Roles are given access to authorization tags.

Currently, a user must have read access to ALL authorization tags on an event to read the event.
