---
uid: EventData
--- 

# Event data

You can store event data, such as manufacturing execution systems (MES) data, in CONNECT data services. This allows you to store data from multiple site systems into CONNECT data services to visualize, create reports, and work with data across the enterprise.  

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

  This property is read-only. The state is `active` if an event only has a startTime, or `closed` if an event has a startTime and endTime.

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

Numeric properties can also be given a default UOM with the `uom` property. This would be the Id or abbreviation of the UOM as defined by SDS Streams `units` endpoint. Defining a default UOM specifies the UOM that will be used if one is not provided during ingress. It also restricts the possible set of ingress UOM's to the same dimension as the default UOM. 

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

**Note:** At this time, collections are not searchable properties.

You can make them required by specifying the `Required` flag. Required means the property must be specified on a top-level ingress operation. It can also restrict a delete operation to maintain integrity.

You can opt out of making numeric values aggregate properties or UOM properties by using the `NoAggregate` and `NoUom` flags. This means the properties will not have the extra GraphQL schema structure to hold aggregations or UOMs.

## Generating the GraphQL schema

An ontology manager detects types that are written to the Type Store within 60 seconds and generates a GraphQL schema. The GraphQL schema represents a strongly-typed model and set of APIs for querying and modifying your type data.

**Note:** Depending on your changes, you can break existing queries and ingress operations. It is usually safe to add new types and properties. Deleting or renaming properties is more dangerous.

The `State` property on each Type and Enum affects how the GraphQL is generated.

- Active – schema generated for query and ingress
- Deprecated – schema generated for query only

Authorization Tag changes will also be detected within 60 seconds of changes and the new access policy will be pushed into the GraphQL server.

You can short-circuit the 60 second detection by calling the `…/graphql/schema` endpoint. POST a non-empty body using text/plain content-type.

## Managing permissions

You manage permissions to view event data with authorization tags.

Each event or reference data type has an optional default tag, which is applied to any node of that type. By default, the type is given the BaseAuthorizationTag. Additional authorization tags can be written when a node is created or updated. Roles are given access to authorization tags.
