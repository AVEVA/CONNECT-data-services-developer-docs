---
uid: gsAssets
---

# Get started: Assets

An *asset* is a digital entity that can be used to model real-world entities. For example, a wind turbine or a mixing tank. An asset consists of three parts: metadata, property and status.

For additional information about asset best practices, see <xref:ccAssets>.

1. [Add asset](xref:CreateConfigureAsset)

    Assets are digital twins of real-world equipment. Using assets, you can apply:

    - *Metadata*: Add static metadata to your assets—information about the asset that does not change. This metadata provides contextual knowledge for assets. For example, if you are adding metadata for a wind turbine, you can add information such as its region or manufacturer number.

    - *Properties*: Properties are references that associate real-time data streams with an asset. They also add extra context, such as when a user adds a stream reference to an asset. Properties provide a user-friendly name for reference, such as "temperature" or "pressure", to add context to underlying streams that often have naming conventions that may be difficult to understand.

    - *Status*: Map statuses to a variety of values that indicate the asset status. Then use that status to filter through assets in the Asset Explorer using real-time measurements, viewing their current status based on a property value. You can choose an enumeration or integer property on the asset and map its values to "Good", "Warning", or "Bad" as the asset status. These statuses help you filter through assets and locate those that need immediate attention.

1. [Create asset types](xref:AssetTypes)

    An *asset type* is a template for creating assets that share a common structure or type. When you create an asset type, you define the expected metadata, stream references, and status for assets created from that asset type. With a defined asset type, you can easily replicate assets sharing common metadata and properties.

    Before working with asset types, review the following documentation: [Asset types best practices](xref:AssetTypes#asset-types-best-pratices).

    There are two ways to create an asset type:

   - [From nothing](xref:CreateAssetTypeWithEditor)
   - [From an existing asset](xref:ConvertAssetToAssetType)

1. [Create asset rules](xref:CreateAssetRules)

     Use asset rules to efficiently scale creation of assets. An asset rule identifies patterns in the naming convention for streams and uses this information to automatically create or update assets.

    *Additional documentation*:

   - [Asset rules](xref:AssetRulesCC)
