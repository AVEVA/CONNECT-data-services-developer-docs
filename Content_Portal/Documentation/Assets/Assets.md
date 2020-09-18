---
uid: Assets
---
# Assets

The Assets API allows you to programmatically model your on-premises devices in OSIsoft Cloud Services (OCS). A single stream with its metadata can be used to model very simple assets. However, in most instances, an asset relates to dynamic data from several streams and to static information. This is better structured as an asset instead of any single stream. the assets feature is well suited to model these aspects of an asset. It allows users to create an asset, add static metadata, and reference streams in a standard, structured way. The asset API includes search capabilities and features to directly retrieve the values of dynamic data associated with a given asset. It also provides methods to configure determining the asset status and to configure different user views of an asset.

## Asset Types

In many instances, you will have multiple devices of the same type. In this situation, an asset type can be used to create multiple similar assets. A change to the asset type is reflected in all assets that are derived from the asset type.

The general structure of an asset type includes the following:

- ID
- Name
- Description
- Attributes
- TypeReferences
- Measurements

The general structure of an asset is nearly identical to an asset type. It includes all properties of an asset type, plus the addition of an asset type:

- ID
- Name
- AssetTypeId
- Description
- Attributes
- References
- Measurements

### Asset and AssetType Properties

| Property      | Type              | Required? | Searchable? | Description                                                  | Asset Property| Asset<br />Type<br />Property |
| ------------- | ----------------- | --------- | ----------- | ------------------------------------------------------------ | ----- | --------------- |
| Id            | String            | Required  | Yes         | Identifier for referencing this asset. If you do not provide an ID, then the Name property is required. OCS automatically assigns the Name as the Id. | X     | X               |
| Name          | String            | Optional  | Yes         | User-friendly name. Required if Id is not provided. If Name is used as the Id, it must be unique within a given namespace. | X     | X               |
| Description   | String            | Optional  | Yes         | User-provided description.                                   | X     | X               |
| Attributes    | Asset Attribute   | Optional  | Yes *       | Asset and Assettype Attributes                               | X     | X               |
| AssetTypeId   | String            | Optional  | No          | Identifier for the asset type that this asset is derived from. To get the merged view of the asset, get the default shape through the /Assets/{assetId}/Shape route. | X     | --              |
| References    | Reference List    | Optional  | Yes *       | Asset References                                             | X     | --              |
| TypeRefeences | TypeReferenceList | Optional  | Yes*        | AssetType TypeReferences                                     | --    | X               |

For more information on search syntax, see [Add xref.]

## Asset and AssetType Attribute Properties

An asset or asset type attribute is static metadata associated with a given asset. There are no limitations on the number of attributes contained (?) by an asset. An asset or asset type attribute does not stand alone. It must be specified within an Asset or AssetType object and, therefore, asset or asset type attributes do not have direct API routes. [WRITER'S NOTE: Can we say: ... and, therefore, there are no direct API routes to asset or asset type attributes.] 

| Property    | Type   | Required? | Searchable? | Description                                                  |
| ----------- | ------ | --------- | ----------- | ------------------------------------------------------------ |
| Name        | String | Required  | Yes         | User-friendly name for the attribute.                        |
| Description | String | Required  | Yes         | User-provided description                                    |
| SdsTypeCode | Int    | Required  | No          | This integer corresponds to the SdsTypeCode. Asset attributes support the following integer values: 11 (Int64), 14 (Double), 16 (DateTime), and 18 (String). |
| Uom         | String | Optional  | No          | Asset attribute unit of measurement. Select from the list of supported Uom types. |
| Value       | String | Required  | Yes         | String representation of the attribute.                      |



## Asset References Properties

An asset reference represents dynamic stream data associated with an asset. The references must either be an SDS stream or an SDS stream view. Asset-centric data routes provide direct access to dynamic data for a given asset. There are no limitations on the number of references an asset may contain. However, an asset cannot contain multiple references to the same SDS stream. An asset reference does not stand alone. It must be specified within an asset object and, therefore, asset references do not have direct API routes. 

| Property      | Type   | Required? | Searchable? | Description                                                  |
| ------------- | ------ | --------- | ----------- | ------------------------------------------------------------ |
| Name          | String | Required  | Yes         | User-friendly name for the asset reference                   |
| Description   | String | Optional  | Yes         | Description text                                             |
| ReferenceType | String | Required  | No          | Specify either StreamReference or StreamViewReference. Refer to [StreamReference ReferenceType](xref:Assets#streamreference-refeencetype) and [StreamViewReference ReferenceType](xref;Assets:#streamviewreference-referencetype) below for the object definitions. |

### StreamReference ReferenceType

| Property | Type   | Required? | Searchable? | Description                                                  |
| -------- | ------ | --------- | ----------- | ------------------------------------------------------------ |
| StreamID | String | Required  | Yes         | The ID of the SdsStream pertaining to this asset             |
| TypeID   | String | Optional  | Yes         | The SdsType of the SdsStream pertaining to this asset. If you specify the TypeId, it will be validated to ensure that the specific StreamId is the TypeId you specified. It this is not specified, then the system maps the correct SdsType. |

### StreamViewReference ReferenceType

| Property     | Type   | Required? | Searchable? | Description                                                  |
| ------------ | ------ | --------- | ----------- | ------------------------------------------------------------ |
| StreamViewId | String | Required  | Yes         | The ID of the SdsStreamView pertaining to this asset         |
| StreamId     | String | Requried  | Yes         | The ID of the SdsStream that will be interpreted by the specified StreamViewId. |
| TypeId       | String | Optional  | Yes         | The SdsType of the SdsStream pertaining to this asset. If you specify the TypeId, it will be validated to ensure that the specific StreamId is the TypeId you specified. It this is not specified, then the system maps the correct SdsType. |



## AssetType TypeReferences Properties

An asset type type reference represents dynamic stream data associated with an asset. The references must either be an SDS stream or an SDS stream view. Asset-centric data routes provide direct access to dynamic data for a given asset. There are no limitations on the number of references an asset may contain. However, an asset cannot contain multiple references to the same SDS stream. An asset reference does not stand alone. It must be specified within an asset object and, therefore, asset references do not have direct API routes. 

| Property    | Type   | Required? | Searchable? | Description                                                  |
| ----------- | ------ | --------- | ----------- | ------------------------------------------------------------ |
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
  "Attributes": [{ 
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
  "Attributes": [{ 
      "Name": "Location",   
      "Value": "Houston",  
      "SdsTypeCode": 18,  
      "Uom": null 
    }],   
    "StreamReferences": [{ 
      "Id": "Reference1", 
      "StreamId": "pi2ocs_stream1_inputpower", 
      "TypeId": "PI-Float32" 
    }] 
} 
```