---
uid: data-views-parquet-format-notes
---

# Parquet data format

AVEVA Data Hub can output your data view in Apache Parquet, an open source, column-oriented data file format designed for efficient data storage and retrieval. This binary file format allows you to easily upload AVEVA Data Hub data into data lakes and data warehouses. Parquet is a common format for working with data in technologies like Databricks, Snowflake, Azure, AWS, and others.

## Parquet data serialization

When you request a data view in Parquet format, AVEVA Data Hub serializes the data from text-based data to the Parquet binary file format, which is not human readable. To read the Parquet file, you will need to open it with a programming language or application capable of deserialization, such as Databricks, Snowflake, Azure, AWS, and so on.

## Handling multiple data types

When requesting a data view in the Parquet format that includes multiple data types in a single column, the data view will coalesce them into a compatible data type wide enough to accommodate all types without losing information. This coalescence occurs to accommodate the strongly-typed data in the Parquet format.

For example, AVEVA Data Hub will coalesce `UInt32` and `Sbyte` data types into a single Int64 column. Nullable types and non-nullable types coalesce into a nullable type. If AVEVA Data Hub cannot coalesce two data types into a compatible type, it will coalesce them into strings. When you request a data view in the Parquet format with the Narrow data view shape selected, AVEVA Data Hub usually coalesces combined columns into strings. Review the following table for examples of coalesced data type results.

| Types                     | Result   |
|---------------------------|----------|
| `Int16`, `Int32`, `Int64` | `Int64`  |
| `UInt64`, `Int64`         | `String` |
| `Float`, `Double`         | `Double` |
| `Double`, `Int64`         | `String` |
