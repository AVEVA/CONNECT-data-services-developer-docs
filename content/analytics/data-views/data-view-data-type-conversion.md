---
uid: data-view-data-type-conversion
---

# Data view data type conversion

When requesting a data view that includes multiple data types in a single column by [linking data fields](xref:data-view-link-fields), the data view will:

1. Convert two or more SDS data types into a compatible SDS data type wide enough to accommodate all types without losing information.

    **Note:** This SDS data type conversion occurs for all data view output formats, not only Parquet.

1. When requesting a data view in the Parquet format, an additional conversion takes place. The compatible SDS data type referenced in step 1 is converted to a Parquet data type. This conversion occurs to accommodate the strongly-typed data in the Parquet format.

## SDS data type conversion

When requesting a data view that includes multiple data types in a single column, the data view will convert two or more SDS data types into a compatible SDS data type wide enough to accommodate all types without losing information.

The following table lists the resulting SDS data type when two are converted:

| Type1  | Type2  | Becomes |
|--------|--------|---------|
| SByte  | Byte   | Int16   |
| SByte  | Int16  | Int16   |
| SByte  | UInt16 | Int32   |
| SByte  | Int32  | Int32   |
| SByte  | UInt32 | Int64   |
| SByte  | Int64  | Int64   |
| SByte  | UInt64 | Decimal |
| SByte  | Single | Single  |
| SByte  | Double | Double  |
| SByte  | Decimal| Decimal |
| Byte   | Int16  | Int16   |
| Byte   | UInt16 | UInt16  |
| Byte   | Int32  | Int32   |
| Byte   | UInt32 | UInt32  |
| Byte   | Int64  | Int64   |
| Byte   | UInt64 | UInt64  |
| Byte   | Single | Single  |
| Byte   | Double | Double  |
| Byte   | Decimal| Decimal |
| Int16  | UInt16 | Int32   |
| Int16  | Int32  | Int32   |
| Int16  | UInt32 | Int64   |
| Int16  | Int64  | Int64   |
| Int16  | UInt64 | Decimal |
| Int16  | Single | Single  |
| Int16  | Double | Double  |
| Int16  | Decimal| Decimal |
| UInt16 | Int32  | Int32   |
| UInt16 | UInt32 | UInt32  |
| UInt16 | Int64  | Int64   |
| UInt16 | UInt64 | UInt64  |
| UInt16 | Single | Single  |
| UInt16 | Double | Double  |
| UInt16 | Decimal| Decimal |
| Int32  | UInt32 | Int64   |
| Int32  | Int64  | Int64   |
| Int32  | UInt64 | Decimal |
| Int32  | Single | Double  |
| Int32  | Double | Double  |
| Int32  | Decimal| Decimal |
| UInt32 | Int64  | Int64   |
| UInt32 | UInt64 | UInt64  |
| UInt32 | Single | Single  |
| UInt32 | Double | Double  |
| UInt32 | Decimal| Decimal |
| Int64  | UInt64 | Decimal |
| Int64  | Decimal| Decimal |
| UInt64 | Decimal| Decimal |
| Single | Double | Double  |

Nullable types and non-nullable types convert into a nullable type. If AVEVA Data Hub cannot convert two data types into a compatible type, it will convert them into strings. When you request a data view in the Parquet format with the **Narrow** data view shape selected, AVEVA Data Hub usually converts combined columns into strings.

## SDS to Parquet data type conversion

When requesting a data view in the Parquet format, an additional conversion takes place. The compatible SDS data type referenced in step 1 is converted to a Parquet data type. This conversion occurs to accommodate the strongly-typed data in the Parquet format.

| CLR Type | Parquet Type | Parquet Annotation |
|--|--|--|
| System.Byte (byte) | INT32 | UNIT_8 |
| System.SByte (sbyte) | INT32 | UINT_8 |
| byte[] | BYTE_ARRAY |  |
| System.Int16 (short) | INT_32 | INT_16 |
| System.UInt16 (ushort) | INT_32 | UINT_16 |
| System.Int32 (int) | INT32 |  |
| System.Boolean (bool) | BOOLEAN |  |
| System.String (string) | BYTE_ARRAY | UTF8 |
| System.Single (float) | FLOAT |  |
| System.Int64 (long) | INT64 |  |
| System.Double (double) | DOUBLE |  |
| System.Decimal (decimal) | BYTE_ARRAY | DECIMAL |
| System.DateTimeOffset (DateTimeOffset) | INT96 |  |
| System.DateTime (DateTime) | INT96 |  |
