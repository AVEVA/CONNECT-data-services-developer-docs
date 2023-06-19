---
uid: gsStreams
---

# Get started: Streams

[Streams](https://docs.aveva.com/bundle/data-hub/page/developer-guide/sequential-data-store-dev/sds-streams-dev.html) are a collection of ordered events, or a series of events, where each event is an instance of the type you have defined. You create and write data to streams using a simple REST API. The streams you create can be used to store simple or complex data types to suit your application needs. You can define simple or complex [indexes](https://docs.aveva.com/bundle/data-hub/page/developer-guide/sequential-data-store-dev/sds-index.html) to arrange and relate your data.

[Streams best practices](https://docs.aveva.com/bundle/data-hub/page/add-organize-data/store-data/streams/streams-manage-streams.html#streams-best-practices)

1. [Sequential Data Store](https://docs.aveva.com/bundle/data-hub/page/add-organize-data/store-data/store-data-overview.html)

    The _Sequential Data Store_ (SDS) is a streaming database optimized for storing sequential data, typically time-series data. It can store any data that is indexed by an ordered sequence. For each namespace that is created, an SDS instance or SDS resources is created. Use SDS to store, retrieve, and analyze data.

1. [Create a Trend session](https://docs.aveva.com/bundle/data-hub/page/visualize-data/getting-started-trend.html)

    Using a _Trend session_, you can look for pattens in your streams over time. Trend sessions display property values from your streams with a given time range. You can view multiple streams in a Trend session, and you can view all property data for each stream.

1. [Create types](https://docs.aveva.com/bundle/data-hub/page/add-organize-data/store-data/types/types-procedure.html)

    A _type_ defines the shape and structure of events and how to associate events within a stream of data. A type is comprised of at least two properties. One property serves as the primary index, most commonly a timestamp or DateTime. In addition, it has one or more additional properties called value properties that describe the data in each stream event. Each value property can have a different property type. A wide variety of property types are supported.

    Additional documentation:

    - [Types](https://docs.aveva.com/bundle/data-hub/page/developer-guide/sequential-data-store-dev/sds-types-dev.html)
    - [Types best practices](https://docs.aveva.com/bundle/data-hub/page/add-organize-data/store-data/types/types-best-practices.html)

1. [Create stream metadata rules](https://docs.aveva.com/bundle/data-hub/page/add-organize-data/organize-data/metadata-rules/metadata-rules-procedure.html)

    When possible, you should explicitly include metadata when you create streams. However, when that is not possible, you can use metadata rules to leverage a consistent naming pattern for streams to embed metadata.

    Metadata, or data about data, is a collection of properties that asset instances of an asset type are expected to provide. The type and units of measure for the value can be defined. Metadata enriches sequential data in AVEVA Data Hub and it logically segregates and contextualizes data. It supports data analysis, visualization, organization, and search capabilities.

    A metadata rule is a user-defined stream name pattern in which each part is assigned a metadata type. Metadata rules capture any streams currently stored in an AVEVA Data Hub namespace, as well as matching streams that are subsequently added to the namespace.

    Additional documentation:

   - [Stream metadata rules](https://docs.aveva.com/bundle/data-hub/page/add-organize-data/organize-data/metadata-rules/metadata-rules-concept.html)
   - [Metadata rules](https://docs.aveva.com/bundle/data-hub/page/api-reference/rules/metadata-rules/metadata-rules-overview.html)

1. [Stream views](https://docs.aveva.com/bundle/data-hub/page/add-organize-data/organize-data/stream-views/stream-views-concept.html)

    A stream view is a logical overlay that enables you to customize your view of streaming data so it is most useful to you. While you cannot change the properties of types, stream views enable you to create a view of a stream, so it appears as if you had changed the type. You create a stream view by choosing a source and target type, and then defining mappings between the properties of the two types. The source type is the type associated with the stream. The target type includes the properties you want to include in the stream view. In effect, you can remove, rename, or add properties without altering the original stream type.