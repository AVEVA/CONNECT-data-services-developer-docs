---
uid: DataViewsOverview
---

# Data views

Data views allow you to access subsets of data items from AVEVA Data Hub in data-driven applications, where the items can be used for data science enablement. With data views, you can bridge your raw AVEVA Data Hub data to third-party applications like Microsoft Power BI, where it can be used for analytics, machine learning, and so on. Users can programmatically retrieve data view content using the AVEVA Data Hub API. Data views deliver shaped data that is ready for consumption because it is normalized, aligned, and contextualized.

Understanding how the data view resolves into content is important for both the user designing the data view and the user working with that view for data science. Data views provide extensive visibility into the data included in the view. The concept of "resolving" a data view is when the data view's queries and logic are executed to determine the data view's exact schema and content.

## Defining and refining a data view

There are several concepts and types used when defining data views. This is accomplished via the RESTful [data views API](xref:DataViewsAPIOverview). See the AVEVA Data Hub documentation for greater detail on these concepts:

- [Define queries](xref:DataViewsQueries)
- [Define data field sets](xref:DataViewsFieldSets)
- [Group data items](xref:DataViewsGrouping)
- [Data view shape](xref:DataViewShape)

Data views are meant to be designed interactively. Each modification you make to a data view is likely to affect how the data view [resolves](xref:ResolvedDataView) into concrete information. The [resolved API resources](xref:data-views-data-views-resolved) close the loop, showing you exactly what information is in the data view, and why.

Each data view can be individually [access-controlled](xref:DataViewsSecuringDataViews) using the [access control API resources](xref:data-views-access-control).

## Consuming a data view

[Data view data](xref:DataViewsQuickStartGetData) is available via queries to the RESTful data views [data API resource](xref:data-views-data-views-data). 

To understand the source of each data field, inspect how the data view [resolved](xref:ResolvedDataView).
