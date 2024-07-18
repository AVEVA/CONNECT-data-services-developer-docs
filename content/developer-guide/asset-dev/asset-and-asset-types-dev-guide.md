---
uid: asset-and-asset-types-dev-guide
---

# Assets and asset types

The asset API allows you to programmatically model your on-premises assets in CONNECT data services. A single stream with its metadata can be used to model very simple assets. However, in most instances, an asset relates to dynamic data from several streams and to static information that describe the asset. This is better structured as an asset in CONNECT data services instead of any single stream. The assets feature allows users to create an asset, add static metadata, and reference streams in a standard, structured way. The asset API includes search capabilities and features to directly retrieve the values of dynamic data associated with a given asset. It also provides methods to configure determining the asset status and to configure different user views of an asset.

The asset type API provides methods to create, read, update, and delete asset types. An asset type can be used as a template to build many similar assets. Some of the key benefits of using an asset type as the base model for assets are:

- Multiple similar assets can be created more quickly and with less effort.
- Maintaining assets is simplified.

In many instances, you will have multiple assets of the same type. In this situation, an asset type can be used to create multiple similar assets. A change to the asset type is reflected in all assets that are derived from the asset type.

## Asset and asset type properties

| Property | Type | Searchable? | Description | Validation Requirements | Asset Property? | Asset Type Property? |
| --- | --- | --- | --- | --- | --- | --- |
| Id | String | Yes | Asset or Asset Type identifier. If the `Id` field is not specified, the system autogenerates a GUID. | <ul><li>Maximum length of 100 characters: `MaxStringLength = 100`.</li><li>Forward slash (`/`) and null characters (`\0`) are disallowed.</li><li>Must be able to parse as string.</li><li>Cannot contain invalid white space.</li></ul> | Yes | Yes |
| Name | String | Yes | User-friendly name. If not specified, name will be set to the same value as the `Id` field. | <ul><li>Maximum length of 100 characters: `MaxStringLength = 100`.</li><li>Must be able to parse as string.</li><li>Cannot contain invalid white space.</li></ul> | Yes | Yes |
| Description | String | Yes | User-provided description. | Must be able to parse as string. | Yes | Yes |
| AssetTypeId | String | No | Identifier for the asset type that this asset is derived from. To get the merged view of the asset, get the resolved asset through the /Assets/{assetId}/Resolved route. | <ul><li>Maximum length of 100 characters: `MaxStringLength = 100`.</li><li> Forward slash (`/`) and null characters (`\0`) are disallowed.</li><li>Must be able to parse as string.</li><li>Cannot contain invalid white space.</li></ul> | Yes | No |
| Metadata<sup>1</sup> | Metadata List | Yes | Asset and asset type metadata. | <ul><li>Metadata `Name` and `Id` have a maximum length of 100 characters: `MaxStringLength = 100`.</li><li>Metadata `Name` for an AssetType cannot be null or empty.</li><li>Metadata `Name` can be null for an asset.</li><li>Metadata `Id` can be null in a user request, but `Name` and `Id` cannot both be null.</li><li>SDSTypeCode for an AssetType's Metadata cannot be empty or zero.</li></ul> | Yes | Yes |
| StreamReferences | Stream Reference List | No | Asset stream references. | <ul><li>Stream references `Name` and `Id` have a maximum length of 100 characters: `MaxStringLength = 100`.</li><li>Cannot be null and must be an SDS reference stream.</li><li>Stream reference `Name` and `Id` must be unique within asset.</li><li>Stream reference `Name` and `Id` cannot both be null.</li></ul> | Yes | No |
| Status | Status | No | Asset and asset type status configuration. | <ul><li>Not null or empty with no leading or trailing space.</li><li>Requires valid status type definition.</li><li>Status mapping must be defined on status enum.</li></ul> | Yes | Yes |
| Tags | String list | Yes | Asset tag. | <ul><li>Cannot be null or white space.</li><li>Must be able to parse as type List\<string\>.</li></ul> | Yes | No |
| TypeReferences | Type Reference List. | No | Asset type type references. | <ul><li>Type references `Name` and `Id` have a maximum length of 100 characters: `MaxStringLength = 100`.</li><li>Cannot be null.</li><li>Type reference `Name` and `Id` must be unique.</li><li>Type reference `Name` and `Id` cannot both be null.</li></ul> | No | Yes |
| CreatedDate | DateTime | No<sup>2</sup> | System-generated timestamp of the asset or asset type's creation date. | Must be able to parse as a DateTime object. | Yes | Yes |
| LastModifiedDate | DateTime | No<sup>2</sup> | System-generated timestamp of the asset or asset type's last modified date. Upon creation, it will be set to the same value as the `CreatedDate` field. | Must be able to parse as a DateTime object. | No | Yes |

<sup>1</sup> Required for Asset metadata, but optional for AssetType metadata.

<sup>2</sup> The `CreatedDate` and `LastModifiedDate` are not searchable, but they can be queried via filter expressions.

## Asset and asset type name and id

The asset and asset type resource has name and Id properties. The Id property cannot be changed; it remains constant. All asset and asset type API calls depend on the Id. The purpose of the name is be a user-friendly way of displaying a given asset or asset type. This can be changed freely without effecting data egress from assets.

## Asset and asset type metadata properties

An asset or asset type metadata is static information associated with a given asset. A given metadata contains a list of individual metadata values. There is no limit on the number of metadata values defined by an asset. An asset or asset type metadata does not stand alone. It must be specified within an asset or asset type object; therefore, there are no direct API routes to asset or asset type metadata.

| Property | Type | Required? | Description | Validation Requirements |
| --- | --- | --- | --- | --- |
| Id | String | Required<sup>1</sup> | Metadata value identifier. | <ul><li>Maximum length of 100 characters: `MaxStringLength = 100`.</li><li>Cannot contain invalid white space. </li><li>If not null, must be unique within an asset or asset type.</li></ul> |
| Name | String | Optional | User-friendly name for the metadata value. If not null, must be unique within an asset or asset type. | <ul><li>Maximum length of 100 characters: `MaxStringLength = 100`.</li><li>Cannot contain invalid white space.</li><li>If not null, must be unique within an asset or asset type.</li></ul> |
| Description | String | Optional | User-provided description. | Must be able to parse as a string. |
| SdsTypeCode | Int | Required/Optional<sup>2</sup> | This integer corresponds to the SdsTypeCode. Asset metadata support the following integer or string values: 11 ("Int64"), 14 ("Double"), 16 ("DateTime"), and 18 ("String"). | <ul><li>Must be able to convert between integer and string values for: 11 ("Int64"), 14 ("Double"), 16 ("DateTime"), and 18 ("String")</li><li>SdsTypeCode for an AssetType's Metadata cannot be empty or zero.</li></ul> |
| Uom | String | Optional | Asset metadata unit of measure (UOM). Select from the list of supported UOM types. | Cannot contain invalid white space. |
| Value | String | Optional | String representation of the metadata. | Must be able to parse as a string. |

<sup>1</sup> The `Id` property is not required if the `Name` property matches a `Name` on the asset type metadata. In this case, the `Id` of the metadata on the asset is inherited from the metadata `Id` of the asset type. This also applies when an asset is updated.

<sup>1</sup> If the `Id` property is not specified, the `Name` property must be specified. In this case, a random GUID will be assigned as the `Id` on the metadata.

<sup>2</sup> Required for Asset metadata, but optional for AssetType metadata.

## Asset stream reference properties

An asset stream reference represents dynamic stream data associated with an asset. The references must be an SDS stream. Asset-centric data routes provide direct access to dynamic data for a given asset. There are no limitations on the number of references an asset may contain. However, an asset cannot contain multiple references to the same SDS stream. An asset stream reference does not stand alone. It must be specified within an asset object; therefore, asset references do not have direct API routes.

| Property | Type | Required? | Description | Validation Requirements |
| --- | --- | --- | --- | --- |
| Id | String | Required<sup>1</sup> | Identifier for the stream reference object. The identifier must be unique within the asset. | <ul><li>Maximum length of 100 characters: `MaxStringLength = 100`.</li><li>Cannot contain invalid white space.</li><li>Stream reference `Name` and `Id` cannot both be null or empty strings.</li></ul> |
| Name | String | Optional | User-friendly name for the stream reference object. If not null, must be unique within an asset. | <ul><li>Maximum length of 100 characters: `MaxStringLength = 100`.</li><li>Cannot contain invalid white space.</li><li>If not null, must be unique within an asset or asset type.</li><li>Stream reference `Name` and `Id` cannot both be null or empty strings.</li></ul> |
| Description | String | Optional | Description text. | Must be able to parse as a string. |
| StreamId | String | Required | The SDS stream `Id` of this stream reference. | <ul><li>Cannot be null.</li><li>Cannot contain invalid white space.</li></ul> |

<sup>1</sup> The `Id` property is not required if the `Name` property matches a `Name` on the asset type type reference. In this case, the `Id` of the stream reference on the asset is inherited from the type reference `Id` of the asset type. This also applies when an asset is updated.

<sup>1</sup> If the `Id` property is not specified, the `Name` property must be specified. In this case, a random GUID will be assigned as the `Id` on the stream reference.

## Asset type type reference properties

An asset type type reference represents dynamic stream data associated with an asset. The references must either be an SDS stream or an SDS stream view. Asset-centric data routes provide direct access to dynamic data for a given asset. There are no limitations on the number of references an asset may contain. However, an asset cannot contain multiple references to the same SDS stream. An asset reference does not stand alone. It must be specified within an asset object; therefore, asset references do not have direct API routes.

| Property | Type | Required? | Description | Validation Requirements |
| --- | --- | --- | --- | --- |
| StreamReferenceId | String | Required | The `Id` for this type reference. If an asset is derived from this asset type, this `Id` must be referenced in the asset reference type object. This `Id` must be unique within the asset type. | <ul><li>Maximum length of 100 characters: `MaxStringLength = 100`.</li><li>Cannot contain invalid white space. </li><li>Stream reference `Name` and `Id` cannot both be null or empty strings.</li></ul> |
| StreamReferenceName | String | Required | The user friendly name for this type reference. If not null, must be unique within an asset type. | <ul><li>Maximum length of 100 characters: `MaxStringLength = 100`.</li><li>Cannot contain invalid white space. </li><li>If not null, must be unique within an asset or asset type. </li><li>Type reference `Name` and `Id` cannot both be null or empty strings. |
| Description | String | Optional | Description text. | Must be able to parse as a string.</li></ul> |
| TypeId | String | Required | This string must be an SDS stream type `Id` in the referenced SDS stream. | <ul><li>Cannot be null.</li><li>Cannot contain invalid white space.</li></ul> |

## Asset type concordance

If the asset you are trying to create references an asset type (through the `AssetTypeId` property) and if the corresponding asset type has a metadata value with the same `Id`, then the name and SDS type code of the metadata value on the asset must be null. If the asset type does not have metadata value with a corresponding `Id`, the name and SDS type code on the asset cannot be null.

To support flexibility on creation, the following rules and behaviors are executed for metadata and stream references on a given asset when that asset is created from an asset type.

| Asset values | Metadata values on the asset type | How references are resolved |
| --- | --- | --- |
| `Id` = "Metadata Id"​ and `Name` = Not specified | `Id` matches the asset type's `Metadata` `Id` | Uses the matching asset type's `Metadata` `Name` |
|  | `Id` does not match any asset type `Metadata` `Id` | `Id` is used as `Name` |
| `Id` = Not specified​ and `Name` = "Metadata Name" | `Name` matches asset type `Metadata` `Name` | Use matching asset type `Metadata` `Id` |
|  | `Name` does not match any asset type `Metadata` `Name` | GUID is generated for`Id` |
| `Id` = "Metadata Id"​ and `Name` = "Metadata Name" | Either `Id` or `Name`, but not both, match asset type `Metadata` `Id` or `Name` | Error. |

To support flexibility, on update, the following rules and behaviors are executed for metadata and stream references on a given asset when that asset is from an asset type.

| Asset values | Metadata values on the asset type | How references are resolved |
| --- | --- | --- |
| `Id` = "Metadata Id"​ and `Name` = Not specified | `Id` matches the asset type's `Metadata` `Id` | Uses the matching asset type `Metadata` `Name` |
|  | `Id` matches the existing asset type's `Metadata` `Id` | Uses the existing matching `Metadata` `Name` |
|  | `Id` does not match any asset type `Metadata` `Id` | `Id` is used as `Name` |
| `Id` = Not specified​ and `Name` = "Metadata Name" | `Name` matches the asset type's `Metadata` `Name` | Uses the matching asset type `Metadata` `Id` |
|  | `Name` matches the existing asset type's `Metadata` `Name` | Uses the matching existing asset type `Metadata` `Id` |
|  | `Name` does not match any asset type `Metadata` `Name` | GUID is generated for `Id` |
| `Id` = "Metadata Id"​ and `Name` = "Metadata Name" | Only `Id` or `Name` (not both) matches asset type `Metadata` `Id` or `Name` | Error. |
|  | Only `Id` or `Name` (not both) matches existing asset type `Metadata` `Id` or `Name` | The non-matching `Id` or `Name` of the existing `Metadata` is updated |

# Asset and asset type ETag

The asset and asset type feature supports the HTTP entity tag (ETag) and If-Match for conditional requests. When a `GET` call is performed, the HTTP response header includes an Etag which indicates what version of the asset or asset type resource that was retrieved.

## Example Etag response header

This is version 7 of this particular asset or asset type.

```text
Etag: "7"
```

To edit or delete the asset or asset type, specify `If-Match` in the HTTP request header when calling `DELETE` or `PUT`.

## Example If-Match response header

Modify or delete only if the current asset or asset type matches version 7. Otherwise, do not perform this operation. If this condition fails, return a 412.

```text
If-Match : "7"
```

**Note:** `If-Match` is optional. If you want to delete or modify regardless of the version, do not specify an `If-Match`.
