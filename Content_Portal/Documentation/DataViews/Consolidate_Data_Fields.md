---
uid: ConsolidateDataFields
---

# Consolidate data fields
Data views containing streams that refer to the same property by different names will return a null value for both. This typically arises from a stream used in a data view having an identical property named slightly differently than the corresponding property in the data view, such as "Temperature" vs "AmbientTemperature".

When identicial fields are incorrectly designated as separate fields in the data view, consolidate the data fields from the relevant streams to remedy this undesirable condition. See [Consolidate data fields](xref:DataViewsQuickStartDefine#Consolidate data fields) in the Define a data view topic for details.


