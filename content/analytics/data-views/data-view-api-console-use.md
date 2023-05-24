---
uid: data-view-api-console-use
---

# Data view API Console use

While creating or editing a data view, you can use the AVEVA Data Hub API Console to build, edit, and preview the data view endpoint configuration before specifying its URI in your application code or Microsoft Power BI.

## Response forms

When requesting data views from the API Console, the REST API is capable of returning requests in a variety of file formats. Select a form from the dropdown. Supported response forms include:

| Form | Description |
|--|--|
| default (JSON) | Object-style JSON. |
| table (Table) | Table-style JSON. |
| tableh (Table with headers) | Table-style JSON with header row. |
| csv (Comma separated values) | Comma-separated values. |
| csvh (Comma separated values with headers) | Comma-separated values with header row. |
| parquet | Parquet format. For more information on the Parquet format, see <xref:data-views-parquet-format>. |
