---
uid: sds-sdstypes-props
---

# SdsType fields and properties

The table below lists required and optional fields in a type. Fields that are not included are reserved for internal SDS use. For more information on search including limitations, see <xref:sdsSearching>.

| Property Name | Data Type | Required | Searchable | Details |
| --- | --- | --- | --- | --- |
| Id | String | Yes | Yes | Identifier for referencing the type. For a list of identifier requirements, see [Rules for the type identifier](#rules-for-the-type-identifier-sdstypeid). |
| Name | String | No | Yes | Friendly name. |
| Description | String | No | Yes | Description text. |
| SdsTypeCode | SdsTypeCode | Yes | No | Numeric code identifying the base SdsType. |
| InterpolationMode | SdsInterpolationMode | No | No | Interpolation setting of the type. Default is Continuous. For more information, see [Interpolation](xref:sdsReadingData#interpolation). |
| ExtrapolationMode | SdsExtrapolationMode | No | No | Extrapolation setting of the type. For more information, see [Extrapolation](xref:sdsReadingData#extrapolation). |
| Properties | IList\<SdsTypeProperty\> | Yes | Yes, with limitations | List of SdsTypeProperty items. See [SdsTypeProperty](#sdstypeproperty) below. |
| CreatedDate | DateTime | Set by server | No | Timestamp in ISO 8601 extended format and UTC time standard when the SdsType was created. Cannot be modified by users. |
| ModifiedDate | DateTime | Set by server | No | Timestamp in ISO 8601 extended format and UTC time standard when the SdsType was last modified. Cannot be modified by users. |

## Rules for the type identifier (SdsType.Id)

1. Is not case sensitive.
2. Cannot just be whitespace.
3. Cannot contain leading or trailing whitespace.
4. Cannot contain forward slash ("/").
5. Can contain a maximum of 100 characters.

Type management using the .NET SDS client libraries methods is performed through `ISdsMetadataService`. You can create `ISdsMetadataService` using one of the `SdsService.GetMetadataService()` factory methods. .NET client libraries provide `SdsTypeBuilder` to help build SdsTypes from .NET types. SdsTypeBuilder is discussed in greater detail in [SDS Types in .NET Framework](#sdstypes-in-net-framework).

## SdsTypeCode

The SdsTypeCode is a numeric identifier used by SDS to identify SdsTypes. An SdsTypeCode exists for every supported type.

Atomic types (such as strings, floats, and arrays) are defined entirely by the SdsTypeCode and do not need other fields to define the type.

Types that require additional definition (enumerations and objects, for example) are identified with a generic SdsTypeCode (`ByteEnum`, `Int32Enum`, `NullableInt32withEnum`, or `Object`, for example) _and_ additional SdsTypeProperty fields.

**Supported Types**

The following types are supported and defined by the SdsTypeCode:

| Type                   | SdsTypeCode |
| ---------------------- | ----------- |
| Array                  | 400         |
| Boolean                | 3           |
| BooleanArray           | 203         |
| Byte                   | 6           |
| ByteArray              | 206         |
| ByteEnum               | 606         |
| Char                   | 4           |
| CharArray              | 204         |
| DateTime               | 16          |
| DateTimeArray          | 216         |
| DateTimeOffset         | 20          |
| DateTimeOffsetArray    | 220         |
| DBNull                 | 2           |
| Decimal                | 15          |
| DecimalArray           | 215         |
| Double                 | 14          |
| DoubleArray            | 214         |
| Empty                  | 0           |
| Guid                   | 19          |
| GuidArray              | 219         |
| IDictionary            | 402         |
| IEnumerable            | 403         |
| IList                  | 401         |
| Int16                  | 7           |
| Int16Array             | 207         |
| Int16Enum              | 607         |
| Int32                  | 9           |
| Int32Array             | 209         |
| Int32Enum              | 609         |
| Int64                  | 11          |
| Int64Array             | 211         |
| Int64Enum              | 611         |
| NullableBoolean        | 103         |
| NullableByte           | 106         |
| NullableByteEnum       | 706         |
| NullableChar           | 104         |
| NullableDateTime       | 116         |
| NullableDateTimeOffset | 120         |
| NullableDecimal        | 115         |
| NullableDouble         | 114         |
| NullableGuid           | 119         |
| NullableInt16          | 107         |
| NullableInt16Enum      | 707         |
| NullableInt32          | 109         |
| NullableInt32Enum      | 709         |
| NullableInt64          | 111         |
| NullableInt64Enum      | 711         |
| NullableSByte          | 105         |
| NullableSByteEnum      | 705         |
| NullableSingle         | 113         |
| NullableTimeSpan       | 121         |
| NullableUInt16         | 108         |
| NullableUInt16Enum     | 708         |
| NullableUInt32         | 110         |
| NullableUInt32Enum     | 710         |
| NullableUInt64         | 112         |
| NullableUInt64Enum     | 712         |
| Object                 | 1           |
| SByte                  | 5           |
| SByteArray             | 205         |
| SByteEnum              | 605         |
| Single                 | 13          |
| SingleArray            | 213         |
| String                 | 18          |
| StringArray            | 218         |
| TimeSpan               | 21          |
| TimeSpanArray          | 221         |
| UInt16                 | 8           |
| UInt16Array            | 208         |
| UInt16Enum             | 608         |
| UInt32                 | 10          |
| UInt32Array            | 210         |
| UInt32Enum             | 610         |
| UInt64                 | 12          |
| UInt64Array            | 212         |
| UInt64Enum             | 612         |
| Version                | 22          |
| VersionArray           | 222         |

### SdsTypeProperty

The `Properties` collection defines the fields in a type. Type properties appear in every stream that is created from a given type.

The following table shows the required and optional `SdsTypeProperty` fields. Fields that are not included are reserved for internal SDS use.

| Property Name | Data Type | Required | Details |
| --- | --- | --- | --- |
| Id | String | Yes | Identifier for referencing the type. For more information, see [Rules for the SdsTypeProperty identifier](#rules-for-the-sdstypeproperty-identifier-sdstypepropertyid). |
| Name | String | No | Friendly name. |
| Description | String | No | Description text. |
| SdsType | SdsType | Yes | Field defining the property's SdsType. |
| IsKey | Boolean | Yes | Identifies the property as the index. For more information, see [IsKey](#iskey).|
| Value | Object | No | Value of the property. For more information, see [Value](#value). |
| Order | Int | No | Order of comparison within a compound index. |
| InterpolationMode | SdsInterpolationMode | No | Interpolation setting of the property. Default is null. For more information, see [InterpolationMode](#interpolationmode). |
| Uom | String | No | Unit of measure of the property. For more information, see [Uom](#uom). |

#### Rules for the SdsTypeProperty identifier (SdsTypeProperty.Id)

The SdsTypeProperty Id follows the same [rules as the type identifier](#rules-for-the-type-identifier-sdstypeid).

#### IsKey

Boolean value `IsKey` identifies the primary index of a type in a single index. An index that is defined by more than one SdsTypeProperty is called a compound index. The maximum number of properties that can define a compound index is three. In a compound index, each `SdsTypeProperty` that is included in the index is specified as `IsKey`. The `Order` field marks the order of comparison within a compound index.

#### Value

The `Value` field is used for the properties of enumeration types. An enumeration is a collection of named constants with associated constant values. Each named constant is defined by the `Id` of the SdsTypeProperty. The associated constant value is defined by the `Value` of the SdsTypeProperty. For more information, see the enumeration `State` definitions in the sample code below.

#### InterpolationMode

`InterpolationMode` is assigned when the SdsTypeProperty of the event should be interpolated in a specific way that differs from the interpolation mode of the SdsType. `InterpolationMode` is only applied to an SdsTypeProperty that is not part of the index. If the `InterpolationMode` is not set, the SdsTypeProperty is interpolated in the manner defined by the SdsType's `InterpolationMode`.

An SdsType with the `InterpolationMode` set to `Discrete` cannot also have the SdsTypeProperty with `InteroplationMode`. For more information on interpolation of events, see [Interpolation](xref:sdsReadingData#interpolation).

#### Uom

`Uom` is the unit of measure for the SdsTypeProperty. The `Uom` of the SdsTypeProperty may be specified by the name or the abbreviation. The names and abbreviations of `Uoms` are case sensitive.

The `InterpolationMode` and `Uom` of the SdsTypeProperty can be overridden on the SdsStream. For more information, see [SdsStreamPropertyOverride](xref:sds-stream-properties#sdsstreampropertyoverride).

### Supported units of measure

For a list of units of measures that are supported for an SdsTypeProperty, see [Units of measure](xref:unitsOfMeasure#supported-system-defined-units-of-measure).
