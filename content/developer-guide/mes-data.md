---
uid: MesData
--- 

# Event data (Preview)

You can store and access event data, such as manufacturing execution systems (MES) data, in AVEVA Data Hub.

The event type store APIs allow you to set up the event types, reference data types, and enumerations for this data. When types are written to our event store, the ontology manager dynamically generates a GraphQL schema for your tenant based on these types.

The event GraphQL APIs allow you to execute a query or mutation of the event data. You can use the <xref:graphQLConsole> to create queries and mutations.

## Types

 - Base Types
   - Event Types
   - Reference Data Types
   - Enumerations
 - Relationships
 - How do types get converted to a GraphQL Schema & what are the implications
 - Flags on properties
 - GraphQL names

## GraphQL API

 - Entity Types
   - Events
   - Reference Data
   - Enumerations
   - Assets
 - Relationships
 - Queries
   - Filtering
     - What operators are available for different data types?
     - Special filters for events (e.g. activebetween)
     - Special filters for Assets
   - Top-level filtering on relationships
   - Filtering on child collections
   - Sorting
   - Counts
   - Paging
   - Limits
 - Mutations

## Authorization Tags & Permissions Management

 - Creating Authorization Tags
 - Authorization Tag permissions
 - Adding/Removing Authorization tags on an Event/Ref Data