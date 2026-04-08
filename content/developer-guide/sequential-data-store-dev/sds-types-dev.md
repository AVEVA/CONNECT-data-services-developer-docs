---
uid: sdsTypes
---

# Types

The Sequential Data Store (SDS) stores streams of data points and provides convenient ways to find and associate data points. Data points are stored in streams. A primitive type is available in CONNECT data services and is used within the API and REST definitions to identify a stream type.

You can define simple atomic types, such as integers, floats, strings, arrays, and dictionaries, or complex or nested types using the properties collection of SdsTypes. For more information, see <xref:sds-sdstypes-props#sdstypeproperty>.

A type that is used to define a stream must have a key. A _key_ is a SdsTypes property (or a combination or properties) that constitutes an ordered, unique identity. If the key is ordered so it functions as an index, it is known as the _primary index_. While a timestamp (`DateTime`) is a very common type of index, any type that can be ordered is permitted. Secondary and other indexes are defined in the stream. For more information, see <xref:sdsIndexes>.

Consider how the data points will be represented in a stream, as the type defines each data point in a stream. A data point is a single unit with properties whose values are related to the index; that is, each property of a type is related to the data point's index.

Reference a type by its identifier or `Id` field. Type identifiers must be unique within a namespace.

A type can also refer to other types by using their identifiers. This referencing enables type re-usability. Nested types and base types are automatically created as separate types. For more information, see <xref:sds-type-reusability>.

Types define how data points are read and associated within a collection of streams. The read characteristics when attempting to read non-existent indexes—indexes that fall between, before, or after existing indexes—are determined by the interpolation and extrapolation settings of the type. For more information about read characteristics, see [Interpolation](xref:sdsReadingData#interpolation) and [Extrapolation](xref:sdsReadingData#extrapolation).

Types are immutable. After a type is created, its definition cannot be updated. The type must be deleted and recreated if the definition is incorrect. You can delete a type only if no streams, stream views, or other types reference it.

Only the types that are used to define streams or stream views are required to be added to SDS. Types that define [properties](xref:sds-sdstypes-props#sdstypeproperty) or base types are contained within the parent type so they do not need to be added to SDS independently.
