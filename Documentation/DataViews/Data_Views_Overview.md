---
uid: DataViewsOverview
---

# Data Views (Preview)

Data views are subsets of data from one or more streams, which can serve as a bridge between raw stream data and data-driven applications. A data view is a declarative query and shape for stream data. Within a target namespace, you specify the selected data by specific time period and interpolation interval.

The ability to create data views in OCS will mesh directly with OSIsoft's Data Science Enablement efforts, whereby users will be able to programmatically access data view content via an API for the purposes of advanced analytics. The ultimate goal is to deliver shaped data that is ready for consumption because it is normalized, aligned, and interpolated.

Understanding how the data view resolves into content is important both for the designer and the consumer. Data views provide extensive visibility into what data is included. The concept of "resolving" a data view is when the data view's queries and logic are executed to determine the data view's exact schema and content.

The collection(s) of streams that a data view acts on is the result of one or more queries. Streams (and any future data source types) are collectively known as *data items*. Values from the data items' properties can be included in the data view as *fields*, as can information about the data items (such as Id and Metadata). 

There are two primary means of controlling how the data items will be organized. One or more fields may be designated to *section* the data view, effectively grouping or partitioning the data items on some value. Within a set of fields, one field may be designated to *distinguish* or align the items.

Data view data is available in several formats, including JSON and CSV, with a user-specified range and granularity. Data is obtained by querying the REST API.

## Defining and refining a data view
There are several [concepts and types](xref:DataView) used when defining data views. This is accomplished via the RESTful [data views API](xref:DataViewsAPIOverview). See the OCS documentation for greater detail on these concepts:
* [Queries](xref:DataViewsQueries)
* [Field Sets](xref:DataViewsFieldSets)
* [Sectioning](xref:DataViewsSectioning)

Data views are meant to be designed interactively. Each modification you make to a data view is likely to affect how the data view [resolves](xref:ResolvedDataView) into concrete information. The [resolved API resources](xref:ResolvedDataViewAPI) close the loop, showing you exactly what information is in the data view, and why.

Each data view can be individually [access-controlled](xref:DataViewsSecuringDataViews) using the [access control API resources](xref:DataViewsAccessControlAPI).

## Consuming a data view
[Data view data](xref:DataViewsGettingData) is available via queries to the RESTful data views [data API resource](xref:DataViewsDataAPI). 

To understand the source of each data field, inspect how the data view [resolved](xref:ResolvedDataView).
