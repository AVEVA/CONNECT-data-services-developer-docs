---
uid: sdsStreams
---

# Streams

Streams are a container for a data type of sequentially occurring values indexed by a single property, typically time series data. You define streams to organize incoming data from another system into CONNECT data services. To define a stream, you must first define a type, which defines the structure of the data you want to stream into a selected namespace.

Sequential Data Store (SDS) stores collections of events and provides convenient ways to find and associate events. Events of consistent structure are stored in streams. Streams are referenced by their identifier or `Id` field. Stream identifiers must be unique within a namespace.

A stream must include a `TypeId` that references the identifier of an existing type. Stream management using the .NET SDS client libraries is performed through `ISdsMetadataService`. Create the `ISdsMetadataService` using one of the `SdsService.GetMetadataService()` factory methods.

## Streams API

[Streams API](xref:sds-streams)
