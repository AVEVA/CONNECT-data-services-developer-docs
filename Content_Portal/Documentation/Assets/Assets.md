---
uid: AssetsProperties
---
# Assets

The Assets API allows you to programmatically model your on-premises devices in OSIsoft Cloud Services (OCS). A single stream with its metadata can be used to model very simple assets. However, in most instances, an asset relates to dynamic data from several streams and to static information. This is better structured as an asset instead of any single stream. the assets feature is well suited to model these aspects of an asset. It allows users to create an asset, add static metadata, and reference streams in a standard, structured way. The asset API includes search capabilities and features to directly retrieve the values of dynamic data associated with a given asset. It also provides methods to configure determining the asset status and to configure different user views of an asset.

## Asset Types

In many instances, you will have multiple devices of the same type. 

In this situation, an asset type can be used to create multiple similar assets. A change to the asset type is reflected in all assets that are derived from the asset type.

### Asset and Asset Type Properties

| Property      | Type              | Required? | Searchable? | Description                                                  | Asset Property? | Asset Type Property? |
| ------------- | ----------------- | --------- | ----------- | ------------------------------------------------------------ | ----- | --------------- |
| ID            | String            | Required  | Yes         | Identifier for referencing this asset. If you do not provide an identifier, then the Name property is required. OCS automatically assigns the name as the identifier. | Yes  | Yes            |
| Name          | String            | Optional  | Yes         | User-friendly name. Required if Id is not provided. If Name is used as the Id, it must be unique within a given namespace. | Yes  | Yes            |
| Description   | String            | Optional  | Yes         | User-provided description.                                   | Yes  | Yes            |
| AssetTypeId   | String            | Optional  | No          | Identifier for the asset type that this asset is derived from. To get the merged view of the asset, get the default shape through the /Assets/{assetId}/Shape route. | Yes  | No            |
| Metadata      | Metadata List     | Optional  | Yes*       | Asset and AssetType Metadata                               | Yes  | Yes            |
| StreamReferences    | Stream Reference List | Optional  | No *       | Asset Stream References                                             | Yes  | No            |
| TypeReferences | Type Reference List | Optional  | No*        | Asset Type Type References                                     | No | Yes            |

For more information on search syntax, see [Add xref.]

## Asset and Asset Type Metadata Properties

An asset or asset type metadata is static information associated with a given asset. There are no limitations on the number of metadata contained (?) by an asset. An asset or asset type metadata does not stand alone. It must be specified within an Asset or AssetType object and, therefore, there are no direct API routes to asset or asset type metadata.

| Property    | Type   | Required? |  Description                                                  |
| ----------- | ------ | --------- |  ------------------------------------------------------------ |
| ID          | String | Required  |  Identifier for the metadatum.                        |
| Name        | String | Required  |  User-friendly name for the metadatum.   If not null, must be unique within an asset or asset type.                     |
| Description | String | Optional  |  User-provided description                                    |
| SdsTypeCode | Int    | Required  |  This integer corresponds to the SdsTypeCode. Asset attributes support the following integer values: 11 (Int64), 14 (Double), 16 (DateTime), and 18 (String). |
| Uom         | String | Optional  |  Asset attribute unit of measurement. Select from the list of supported Uom types. |
| Value       | String | Optional  |  String representation of the attribute.                      |

## Asset Stream Reference Properties

An asset reference represents dynamic stream data associated with an asset. The references must either be an SDS stream or an SDS stream view. Asset-centric data routes provide direct access to dynamic data for a given asset. There are no limitations on the number of references an asset may contain. However, an asset cannot contain multiple references to the same SDS stream. An asset reference does not stand alone. It must be specified within an asset object and, therefore, asset references do not have direct API routes. 

| Property      | Type   | Required? | Searchable? | Description                                                  |
| ------------- | ------ | --------- | ----------- | ------------------------------------------------------------ |
| ID            | String | Required  | No          | Identifier for this stream reference object.  This identifier must be unique within the asset.                    |
| Name          | String | Required  | No          | User-friendly name for the stream reference object. If not null, must be unique within an asset. |
| Description   | String | Optional  | No          | Description text.                                            |
| StreamId      | String | Required  | No          | The SDS stream ID of this stream reference. This SDS stream must exist at the time the asset is created. |

## AssetType Type Reference Properties

An asset type type reference represents dynamic stream data associated with an asset. The references must either be an SDS stream or an SDS stream view. Asset-centric data routes provide direct access to dynamic data for a given asset. There are no limitations on the number of references an asset may contain. However, an asset cannot contain multiple references to the same SDS stream. An asset reference does not stand alone. It must be specified within an asset object and, therefore, asset references do not have direct API routes. 

| Property    | Type   | Required? | Searchable? | Description                                                  |
| ----------- | ------ | --------- | ----------- | ------------------------------------------------------------ |
| StreamReferenceId | String | Required | No |The ID for this type reference. If an asset is derived from this asset type, this ID must be referenced in the asset reference type object. This ID must be unique within the asset type. |
| StreamReferenceName  | String | Required  | No          | The user friendly name for this type reference. If not null, must be unique within an asset type.|
| Description | String | Optional  | No          | Description text                                             |
| TypeId    | String | Required  | No          | This string must be an SDS stream type ID in the referenced SDS stream. |

The following is an example of an asset derived from an asset type.

Asset Type Example

```
Content-Type: application/json
{
  "Id": "ChargingStationType", 
  "Description": "Charging Station Type", 
  "Metadata": [{ 
     "Id":"d7368dc2-58f0-4669-8e6e-44ac2cc3f47c",
     "Name": "Location", 
     "SdsTypeCode": 18, 
     "Value": null 
     "Uom": null 
   }], 
  "TypeReferences": [{ 
     "StreamReferenceId": "Reference1", 
     "StreamReferenceName": "ReferenceName", 
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
      "Id": "d7368dc2-58f0-4669-8e6e-44ac2cc3f47c",   
      "Name": null,   
      "Value": "Houston",  
      "SdsTypeCode": 18,  
    }] 
} 
```