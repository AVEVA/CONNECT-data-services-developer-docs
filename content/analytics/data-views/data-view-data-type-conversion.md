---
uid: data-view-data-type-conversion
---

# Data view data type conversion

When requesting a data view that includes multiple data types in a single column, the data view will:

1. Convert two or more SDS data types into a compatible SDS data type wide enough to accommodate all types without losing information. This conversion occurs to accommodate the strongly-typed data in the Parquet format.

1. When requesting a data view in the Parquet format, an additional conversion takes place. The compatible SDS data type referenced in step 1 is converted to a Parquet data type. This conversion occurs because the Parquet format does not support all data types natively.

## SDS data type conversion

When requesting a data view that includes multiple data types in a single column, the data view will convert two or more SDS data types into a compatible SDS data type wide enough to accommodate all types without losing information. This conversion occurs to accommodate the strongly-typed data in the Parquet format.

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

When requesting a data view in the Parquet format, an additional conversion takes place. The compatible SDS data type referenced in step 1 is converted to a Parquet data type. This conversion occurs because the Parquet format does not support all data types natively.

| SDS Type Code/CLR Type | Physical Type | Converted Type | Logical Type |
|--|--|--|--|
| Byte (Byte) | INT32 | UNIT_8 | INT (8, false) |
| SByte (Sbyte) | INT32 | INT_8 | INT (8, true) |
| Int16 (Short) | INT32 | INT_16 | INT (16, true) |
| UInt16 (Ushort) | INT32 | UINT_16 | INT (16, false) |
| Int32 (Int) | INT32 | INT_32 | INT (32, true) |
| UInt32 (Uint) | INT32 | UINT_32 | INT (32, false) |
| Boolean (Bool) | BOOLEAN | UTF8 |  |
| String (String) | BYTE_ARRAY | UTF8 | STRING |
| Single (Float) | FLOAT | UTF8 |  |
| Int64 (Long) | INT64 | INT_64 | INT (64, true) |
| UInt64 (Ulong) | INT64 | UINT_64 | INT (64, false) |
| Double (Double) | DOUBLE | UTF8 |  |
| Decimal (Decimal) | FIXED_LEN_BYTE_ARRAY | DECIMAL | DECIMAL |
| DateTime (DateTime) | INT64 | UTF8 | TIMESTAMP (false, MICROS) |
| DateTimeOffset (DateTimeOffset) | INT64 | UTF8 | TIMESTAMP (false, MICROS) |
| Char (char) | BYTE_ARRAY | UTF8 | STRING |
| Guid (Guid) | BYTE_ARRAY | UTF8 | STRING |
| Version (Version) | BYTE_ARRAY | UTF8 | STRING |
