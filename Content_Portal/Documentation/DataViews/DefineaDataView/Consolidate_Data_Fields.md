---
uid: ConsolidateDataFields
---

# Consolidate data fields
Data items included in a data view may have slight differences in property naming, despite those properties representing the same logical thing. For example: data from one equipment manufacturer reports "Temperature", while another reports "AmbientTemperature" instead.

Data views can overcome property naming differences by consolidating these similar properties into a single data field. This applies to stream properties referenced by id (`FieldSource.PropertyId`) or by name (`FieldSource.PropertyName`), and to stream metadata keys (`FieldSource.Metadata`). For those cases, adding multiple match values to the field's `Keys` collection will allow alternate keys to match. See [Consolidate data fields](xref:DefineaDataViewRecommendedWorkflow#consolidate-data-fields) in the Define a data view topic for details.

### Consolidate asset data fields (Coming Soon)
*Note: This section covers features that are not yet generally available. If you are interested in trialing these pre-release features, contact your account team for more details.*

Asset properties can also be consolidated. Asset metadata (`FieldSource.Metadata`) and measurement property ids (`FieldSource.PropertyId`) can be consolidated using the `Keys` collection. Asset measurement names can be consolidated using the `MeasurementKeys` collection.
