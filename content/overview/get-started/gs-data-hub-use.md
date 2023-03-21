---
uid: gs-data-hub-use
---

# Step 5: AVEVA Data Hub use

After configuring security and ingress, your options for using AVEVA Data Hub expand.

## Streams

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

## Assets

An _asset_ is a container for data streams and metadata associated with a particular device or object. Assets allow you to group related streams and provide context to the stream data.

[Asset best practices](https://docs.aveva.com/bundle/data-hub/page/add-organize-data/organize-data/assets/asset-concept.html#assets-best-practices)

1. [Asset Explorer](https://docs.aveva.com/bundle/data-hub/page/visualize-data/asset-explorer.html)

    Use the asset explorer to create assets, then visualize data streams and properties to troubleshoot and analyze the associated devices. You can create assets as needed, create them from an asset type, which acts as a template for creating similar assets, and generate them based on stream naming patterns using asset rules.

1. [Add asset](https://docs.aveva.com/bundle/data-hub/page/add-organize-data/organize-data/assets/create-an-asset.html)

    Assets are digital twins of real-world equipment.

1. [Create asset types](https://docs.aveva.com/bundle/data-hub/page/add-organize-data/organize-data/assets/asset-type-overview.html)

    An _asset type_ is a template for creating assets that share a common structure or type. When you create an asset type, you define the expected metadata and stream references for assets created from that asset type.

    Before working with asset types, review the following documentation: [Asset types best practices](https://docs.aveva.com/bundle/data-hub/page/add-organize-data/organize-data/assets/asset-type-overview.html#asset-types-best-practices)

    There are two ways to create an asset type:

   - [From stratch](https://docs.aveva.com/bundle/data-hub/page/add-organize-data/organize-data/assets/create-asset-type-asset-editor.html)
   - [(Recommended) From an existing asset](https://docs.aveva.com/bundle/data-hub/page/add-organize-data/organize-data/assets/convert-asset-to-asset-type.html)

1. [Create asset rules](https://docs.aveva.com/bundle/data-hub/page/add-organize-data/organize-data/assets/create-asset-rule.html)

    An asset rule identifies patterns in a stream name and uses this information to automatically create assets.

    Additional documentation:

   - [Asset rules](https://docs.aveva.com/bundle/data-hub/page/add-organize-data/organize-data/assets/asset-rules-concept.html)

## Connected Communities

Communities allow a tenant to create a private group where operational data can be shared and viewed across other tenants. Using communities, industrial companies can share their data streams externally with trusted business partners, service providers, and analytics providers.

To join a community, follow the applicable scenario below. Regardless of which scenario you follow, reviewing the following document is recommended: [Community user roles](https://docs.aveva.com/bundle/data-hub/page/communities/community-setup.html#community-user-roles).

### Scenario A: Create community and invite other tenants

To create a community, invite other tenants, and share streams into the community, complete the following workflow: [Workflow: Create community (aveva.com)](https://docs.aveva.com/bundle/data-hub/page/communities/community-workflow-create.html)

### Scenario B: Join an existing community

To join a community that another tenant has invited you to, complete the following workflow: [Workflow: Join community (aveva.com)](https://docs.aveva.com/bundle/data-hub/page/communities/community-workflow-join.html)
