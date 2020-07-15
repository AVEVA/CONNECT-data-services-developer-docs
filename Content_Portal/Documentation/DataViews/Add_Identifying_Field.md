---
uid: AddIdentifyingField
---

# Add identifying field
If a field set resolves to multiple data items in any group, then one field should be designated as the `.IdentifyingField` of the field set. If a single criterion is not an effective way of disambiguating fields, then it may be necessary to [group](xref:DataViewsGrouping) by additional criteria.  Any field from field sources `FieldSource.Id`, `FieldSource.Name`, `FieldSource.Metadata`, `FieldSource.Tags` can be used as an identifying field.  

See [Add identifying field](xref:DataViewsFieldSets#Identifying field) for details.
