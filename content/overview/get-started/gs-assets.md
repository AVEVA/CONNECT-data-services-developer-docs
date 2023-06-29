---
uid: gsAssets
---

# Get started: Assets

An _asset_ is a container for data streams and metadata associated with a real world device or object. Assets allow you to group related streams and provide context to the stream data.

For additional information about asset best practices, see <xref:ccAssets>.

1. [Asset Explorer](xref:AssetExplorers)

    Use the asset explorer to create assets and then visualize data streams and properties to troubleshoot and analyze the associated devices. You can create assets as needed, create them from an asset type (which acts as a template for creating similar assets), and generate them based on stream naming patterns using asset rules.

1. [Add asset](xref:CreateConfigureAsset)

    Assets are digital twins of real-world equipment. Using assets, you can apply:

    - Metadata: Add static metadata to your assets—information about the asset that does not change. For example, if you were adding metadata for a wind turbine, you could add information such as its region or manufacturer number.

    - Properties: Group stream reference properties about a single real world asset, allowing you to view each of its streams and properties from a single location in real-time. You can also provide friendly names for each property, providing an additional layer of context for your assets.

    - Status: Map statuses to a variety of values that indicate the asset status. Then use that status to filter through assets in the Asset Explorer using real-time measurements, viewing their current status based on a property value.

1. [Create asset types](xref:AssetTypes)

    An _asset type_ is a template for creating assets that share a common structure or type. When you create an asset type, you define the expected metadata and stream references for assets created from that asset type.

    Before working with asset types, review the following documentation: [Asset types best practices](xref:AssetTypes#asset-types-best-pratices)

    There are two ways to create an asset type:

   - [From scratch](xref:CreateAssetTypeWithEditor)
   - [(Recommended) From an existing asset](xref:ConvertAssetToAssetType)

1. [Create asset rules](xref:CreateAssetRules)

     Use asset rules to efficiently scale creation of assets. An asset rule identifies patterns in a stream name convention and uses this information to automatically create or update assets.

    **Additional documentation**:

   - [Asset rules](xref:AssetRulesCC)
