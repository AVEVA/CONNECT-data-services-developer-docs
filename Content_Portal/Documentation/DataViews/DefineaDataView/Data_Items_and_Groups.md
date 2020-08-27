---
uid: DataViewsDataItemsandGroups
---

# Identify data items

A `DataItem` is an SdsStream included in the data view. The collection of data items is specified by the data view queries, where the queries define the search criteria and the data items represent the results of the search. The data view can include one or more properties from each data item.


## Data Items

The collection of data items in the data view represents all SDS streams that match the [`.Queries`](xref:DataViewsQueries) field of the data view, excluding data items that are ineligible (see discussion of ineligible data items below). To add data items to a data view, either refine an existing query, or add a new query (refer to [queries](xref:DataViewsQueries) for which option to choose from). Similarly, to remove data items from a data view, either refine an existing query, or remove a query (this will remove all data items from the query).

Note: Each query is executed independently to generate the list of data items. It is thus possible to have duplicate data items resulting from different queries. This can be desirable or undesirable depending on the use case.

There is a maximum of 10,000 data items per query. You can add more than 10,000 data items to a data view by adding additional queries. Data items are ordered alphabetically by data item id within the data items collection.

### Adding Fields
Each data item contains information that can be optionally (and explicitly) added to the data view by setting the [`.DataFieldSets`](xref:DataViewsFieldSets) field of the data view. Currently, the only supported resource type is `stream` with the following available fields:
* Stream id
* Stream name
* Stream tags
* Stream metadata
* Data from each stream property


### Adding or Removing SDS Streams
When requesting for [resolved data items](xref:ResolvedDataViewAPI) or when [getting the data view data](xref:DataViewsDataAPI), the list of data items reflects the list of SDS streams that match one or more queries when the data view was last resolved. This means that if new streams were added or existing streams were removed from the Sequential Data Store, the list of data items will only reflect the latest changes if the data view is re-resolved. For more information, refer to the caching section in the resolved data view resource [page](xref:ResolvedDataView).


## Ineligible Data Items

The collection of ineligible data items represents SDS streams that match the queries but cannot be included in the data view. The criteria for ineligibility are:
* When the SDS stream's index type is different than the `IndexTypeCode` specified in the data view.
* When the SDS type of the stream contains compound indexes.
