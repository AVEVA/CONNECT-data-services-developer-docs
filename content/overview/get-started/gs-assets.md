---
uid: gsAssets
---

# Get started: Assets

An _asset_ is a container for data streams and metadata associated with a particular device or object. Assets allow you to group related streams and provide context to the stream data.

[Asset best practices](xref:sccAssets)

1. [Asset Explorer](xref:AssetExplorers)

    Use the asset explorer to create assets, then visualize data streams and properties to troubleshoot and analyze the associated devices. You can create assets as needed, create them from an asset type, which acts as a template for creating similar assets, and generate them based on stream naming patterns using asset rules.

1. [Add asset](xref:CreateConfigureAsset)

    Assets are digital twins of real-world equipment.

1. [Create asset types](xref:AssetTypes)

    An _asset type_ is a template for creating assets that share a common structure or type. When you create an asset type, you define the expected metadata and stream references for assets created from that asset type.

    Before working with asset types, review the following documentation: [Asset types best practices](xref:AssetTypes#asset-types-best-pratices)

    There are two ways to create an asset type:

   - [(Recommended) From an existing asset](xref:ConvertAssetToAssetType)
   - [From stratch](xref:CreateAssetTypeWithEditor)

1. [Create asset rules](xref:CreateAssetRules)

    An asset rule identifies patterns in a stream name and uses this information to automatically create assets.

    Additional documentation:

   - [Asset rules](xref:AssetRulesCC)
