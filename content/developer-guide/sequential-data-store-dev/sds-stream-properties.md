---
uid: sds-stream-properties
---

# Stream properties

The following table shows the required and optional stream fields. Fields not listed are reserved for internal SDS use.

| Property | Type | Optionality | Searchable | Details |
| --- | --- | --- | --- | --- |
| Id | String | Required | Yes | An identifier for referencing the stream. For identifier rules, see [Rules for the stream identifier](#rules-for-the-stream-identifier-sdsstreamid). |
| TypeId | String | Required | Yes | The SdsType identifier of the type to be used for this stream. |
| Name | String | Optional | Yes | Friendly name. |
| Description | String | Optional | Yes | Description text. |
| Indexes | IList\<SdsStreamIndex\> | Optional | No | Used to define secondary indexes for stream. For more information, see [Indexes](#indexes). |
| InterpolationMode | SdsInterpolationMode | Optional | No | Interpolation setting of the stream. Default is null. For more information, see [Interpolation and extrapolation](#interpolation-and-extrapolation). |
| ExtrapolationMode | SdsExtrapolationMode | Optional | No | Extrapolation setting of the stream. Default is null. |
| PropertyOverrides | IList\<SdsStreamPropertyOverride\> | Optional | No | Used to define unit of measure and interpolation mode overrides for a stream. For more information, see [SdsStreamPropertyOverride](#sdsstreampropertyoverride). |
| CreatedDate | DateTime | Set by server | No | Timestamp in ISO 8601 extended format and UTC time standard when the SdsStream was created. Cannot be modified by users. |
| ModifiedDate | DateTime | Set by server | No | Timestamp in ISO 8601 extended format and UTC time standard when the SdsStream was last modified. Cannot be modified by users. |
| [Tags](xref:sds-streams-tags)<sup>1</sup> | IList\<String\> | Optional | Yes | A list of tags denoting special attributes or categories. |
| [Metadata](xref:sds-streams-metadata)<sup>1</sup> | IDictionary\<String, String\> | Optional | Yes | A dictionary of string keys and associated string values. |

<sup>1</sup> You can access stream metadata and tags through Metadata API and Tags API respectively. Because stream metadata and tags are associated with SdsStream objects, you can use them as search criteria.

## Rules for the stream identifier (SdsStream.Id)

1. Is not case sensitive
2. Cannot just be whitespace
3. Cannot contain leading or trailing whitespace
4. Cannot contain forward slash ("/")
5. Can contain a maximum of 100 characters

## Indexes

While you define the primary index on the type, the stream is where you define secondary indexes. If the primary index defined on the type is a compound index, secondary indexes on the stream are allowed as long as that compound index does not have more than two properties. For more information on compound indexes, see [Indexes](xref:sdsIndexes#compound-indexes).

<!-- Secondary indexes apply to a single property. In other words, there are no compound secondary indexes.-->

You can only use the SdsTypeCodes of type properties that can be ordered (`DateTime` or numbers, for example) as a secondary index.

## Interpolation and extrapolation

You can use the `InterpolationMode`, `ExtrapolationMode`, and [SdsStreamPropertyOverride object](#sdsstreampropertyoverride) to determine how a specific stream reads data. If you do not define these read characteristics at the stream level, the stream inherits them from the type.

## SdsStreamPropertyOverride

Use the `SdsStreamPropertyOverride` object to override interpolation behavior and unit of measure (UOM) for individual SdsType properties for a specific SdsStream.

The `SdsStreamPropertyOverride` object has the following structure:

| Property | Type | Optionality | Details |
| --- | --- | --- | --- |
| SdsTypePropertyId | String | Required | SdsTypeProperty identifier. |
| InterpolationMode | SdsInterpolationMode | Optional | Interpolation setting. Default is null. |
| Uom | String | Optional | Unit of measure. |

You can override the unit of measure (UOM) for any SdsTypeProperty defined by the stream type, including primary and secondary indexes. For more information on SdsTypeProperty `Uom`, see [Types](xref:sds-sdstypes-props#sdstypeproperty).

Read characteristics of the stream are determined by the type and the `PropertyOverride` of the stream. You can define or override the interpolation mode for non-index properties at the stream level. For more information about type read characteristics, see [Types](xref:sds-sdstypes-props#sdstypeproperty).

If you set `InterpolationMode` of the type to `Discrete`, it cannot be overridden at any level. When `InterpolationMode` is set to `Discrete` and an event is not defined for the index, a null value is returned for the entire event.
