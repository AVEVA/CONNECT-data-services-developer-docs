---
uid: AssetsProperties
---
# Assets

The Assets API allows you to programmatically model your on-premises devices in OSIsoft Cloud Services (OCS). A single stream with its metadata can be used to model very simple assets. However, in most instances, an asset relates to dynamic data from several streams and to static information. This is better structured as an asset instead of any single stream. the assets feature is well suited to model these aspects of an asset. It allows users to create an asset, add static metadata, and reference streams in a standard, structured way. The asset API includes search capabilities and features to directly retrieve the values of dynamic data associated with a given asset. It also provides methods to configure determining the asset status and to configure different user views of an asset.

## Asset Types

In many instances, you will have multiple devices of the same type. In this situation, an asset type can be used to create multiple similar assets. A change to the asset type is reflected in all assets that are derived from the asset type.

The general structure of an asset type includes the following:

- ID
- Name

## Asset

The general structure of an asset is nearly identical to an asset type. It includes all properties of an asset type, plus the addition of an asset type:

- ID
- Name
- AssetTypeId

### Asset and AssetType Properties

| Property      | Type              | Required? | Searchable? | Description                                                  | Asset | Asset Type |
| ------------- | ----------------- | --------- | ----------- | ------------------------------------------------------------ | ----- | --------------- |
| Id            | String            | Required  | Yes         | Identifier for referencing this asset. If you do not provide an ID, then the Name property is required. OCS automatically assigns the Name as the Id. | X     | X               |
| Name          | String            | Optional  | Yes         | User-friendly name. Required if Id is not provided. If Name is used as the Id, it must be unique within a given namespace. | X     | X               |
| Description   | String            | Optional  | Yes         | User-provided description.                                   | X     | X               |
| Metadata    | Asset Metadata   | Optional  | Yes *       | Asset and AssetType Metadata                               | X     | X               |
| AssetTypeId   | String            | Optional  | No          | Identifier for the asset type that this asset is derived from. To get the merged view of the asset, get the default shape through the /Assets/{assetId}/Shape route. | X     | --              |
| StreamReferences    | Stream Reference List    | Optional  | No *       | Asset References                                             | X     | --              |
| TypeReferences | TypeReference List | Optional  | No*        | AssetType TypeReferences                                     | --    | X               |

For more information on search syntax, see [Add xref.]

## Asset and AssetType Metadata Properties

An asset or asset type metadata is static information associated with a given asset. There are no limitations on the number of metadata contained (?) by an asset. An asset or asset type metadata does not stand alone. It must be specified within an Asset or AssetType object and, therefore, there are no direct API routes to asset or asset type metadata.

| Property    | Type   | Required? |  Description                                                  |
| ----------- | ------ | --------- |  ------------------------------------------------------------ |
| Name        | String | Required  |  User-friendly name for the attribute.                        |
| Description | String | Required  |  User-provided description                                    |
| SdsTypeCode | Int    | Required  |  This integer corresponds to the SdsTypeCode. Asset attributes support the following integer values: 11 (Int64), 14 (Double), 16 (DateTime), and 18 (String). |
| Uom         | String | Optional  |  Asset attribute unit of measurement. Select from the list of supported Uom types. |
| Value       | String | Required  |  String representation of the attribute.                      |



## Asset StreamReferences

An asset reference represents dynamic stream data associated with an asset. The references must either be an SDS stream or an SDS stream view. Asset-centric data routes provide direct access to dynamic data for a given asset. There are no limitations on the number of references an asset may contain. However, an asset cannot contain multiple references to the same SDS stream. An asset reference does not stand alone. It must be specified within an asset object and, therefore, asset references do not have direct API routes. 

| Property      | Type   | Required? | Searchable? | Description                                                  |
| ------------- | ------ | --------- | ----------- | ------------------------------------------------------------ |
| Name          | String | Required  | Yes         | User-friendly name for the asset reference                   |
| Description   | String | Optional  | Yes         | Description text                                             |

## AssetType TypeReferences Properties

An asset type type reference represents dynamic stream data associated with an asset. The references must either be an SDS stream or an SDS stream view. Asset-centric data routes provide direct access to dynamic data for a given asset. There are no limitations on the number of references an asset may contain. However, an asset cannot contain multiple references to the same SDS stream. An asset reference does not stand alone. It must be specified within an asset object and, therefore, asset references do not have direct API routes. 

| Property    | Type   | Required? | Searchable? | Description                                                  |
| ----------- | ------ | --------- | ----------- | ------------------------------------------------------------ |
| StreamReferenceID | String | Required | No |The ID for this type reference. If an asset derives from this asset type, this ID must be referenced in the asset reference type object. |
| Name        | String | Required  | No          | The ID for this type reference. If an asset derives from this asset type, this ID must be referenced in the asset reference type object. |
| Description | String | Optional  | No          | Description text                                             |
| TypeID      | String | Required  | No          | This string must be an SDS type ID to which we expect the reference stream to be. |

The following is an example of an asset derived from an asset type.

Asset Type Example

```
Content-Type: application/json
{
  "Id": "ChargingStationType", 
  "Description": "Charging Station Type", 
  "Metadata": [{ 
     "Name": "Location", 
     "SdsTypeCode": 18, 
     "Value": null 
     "Uom": null 
   }], 
  "TypeReferences": [{ 
     "StreamReferenceId": "Reference1", 
     "TypeId": "PI-Float32" 
   }] 
}
```

Asset Example

```
{ 
  "Id": "ChargingStation1", 
  "Name": " ChargingStation1", 
  "Description": "Charging Station Instance", 
  "AssetTypeId": "ChargingStationType", 
  "Metadata": [{ 
      "Name": "Location",   
      "Value": "Houston",  
      "SdsTypeCode": 18,  
      "Uom": null 
    }],   
    }] 
} 
```
