---
uid: DataViewsQuickStartDefine
---

# Define a data view
The `DataView` object is a declarative query and shape for stream data. This section describes the `DataView` object. See the [Data View API section](xref:DataViewAPI) for the corresponding API routes.  

At times, this section makes reference to ways the view *resolves* into further resources, such as the collection of data items found by each data item query. See the [Resolved Data View](xref:ResolvedDataView) and [Resolved Data View API](xref:ResolvedDataViewAPI) sections for details.

## General concepts
You define multiple aspects of a data view when you define it, including data items and their organization, grouping, and shaping. 

### Define a data view identifier
A data view must have a unique identifier. It may have a friendly name and description. If a friendly name is not specified, the identifier will be used as the data view's name.

### Include data items
One or more queries determine the set of data items (such as SDS streams) that the data view will include. Each [Query](xref:DataViewsQueries) should represent a collection of like streams. To include streams that represent very different items, such as power inverters and weather stations, use separate queries.

### Include data fields

Information from, or about, those data items must be included explicitly in the data view as Fields within [DataFields](xref:DataViewsFieldSets) or [GroupingFields](xref:DataViewsGrouping). By default, a data view includes no fields, except the default [IndexField](#include-the-index-field).

The fields that are available for use are exposed as a "resolved" resource, [Available Field Sets](xref:DataViewsAvailableFieldSets). It is recommended to use or adapt those fields instead of defining new fields. Individual fields are organized into [DataFieldSets](xref:DataViewsFieldSets) and [GroupingFields](xref:DataViewsGrouping).

### Group the data items

Data items may be [grouped](xref:DataViewsGrouping), which amounts to grouping or partitioning them by one or more field values. To group data items in a data view, define one or more fields as `.GroupingFields` of the data view. This is one way of producing a meaningful, consumable shape of data.

### Organize the data fields
Field sets and fields resolve in the order they are defined. They may be re-ordered.

Within each group, a field set may be associated with multiple data items. It is often necessary to disambiguate these items. If a group contains multiple data items from the same query, you may wish to identify those data items so that they are not ambiguous and so they will be aligned across groups. Items can be disambiguated by specifying an [`.IdentifyingField`](xref:DataViewsFieldSets#identifying-field). An identifying field is a field that differentiates the data items within a group, such as the value of _Measurement_ metadata (i.e., the data items are identified by what they measure). Identifying data items also allows the data views engine to "align" them across groups, since it is clear, for example, that streams measuring _Power Out_ and streams measuring _Power In_ are alike. Ensure that each data field's label includes the {IdentifyingValue} token so the field labels are unique. The default field labels already include it.

### Include the index field
The field used for indexing.  If not specified, a default value with a label of "Timestamp" is applied. If specified, a label is required. Field source and keys are not applicable for index field.

### Define index type and default range
Data views currently operate on timestamped data, which is data indexed by a DateTime property. This is reflected by the `.IndexTypeCode` of the DataView, whose value must be "DateTime". Default values may be defined for the start index, end index, and/or interval used when data view data is queried.

### Define data view shape
Data views may be set to resolve as standard shape or narrow shape. Standard shape resolves fields similar to how they are defined. Narrow shape pivots the fields vertically, resulting in a view whose schema is independent of what data items (streams) are resolved by the data view. Narrow shape may be used when an invariant output schema is required.

