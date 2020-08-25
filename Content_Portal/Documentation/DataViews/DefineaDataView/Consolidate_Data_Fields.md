---
uid: ConsolidateDataFields
---

# Consolidate data fields
Streams included in a data view may have slight differences in property naming, despite those properties representing the same logical thing. For example: data from one equipment manufacturer reports "Temperature", while another reports "AmbientTemperature" instead.

Data views can overcome property naming differences by consolidating these similar properties into a single data field. This applies to stream properties referenced by id (`FieldSource.PropertyId`) or by name (`FieldSource.PropertyName`), and to stream metadata keys (`FieldSource.Metadata`). For those cases, adding multiple match values to the field's `Keys` collection will allow alternate keys to match. See [Consolidate data fields](xref:DataViewsQuickStartDefine#consolidate-data-fields) in the Define a data view topic for details.


