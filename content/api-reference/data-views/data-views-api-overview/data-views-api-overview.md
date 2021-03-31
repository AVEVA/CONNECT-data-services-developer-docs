---
uid: DataViewsAPIOverview
---

# Data views API reference

The data views API is a RESTful surface for creating, securing, and consuming data views. 
The supported content type of request and response bodies is JSON unless otherwise noted.

The API is comprised of the following main areas:

## [Data view API](xref:DataViewAPI)
Resources to create, read, update, and delete `/DataViews`. For more information, see [Data View](xref:DataViewsOverview)

## [Resolved data view API](xref:ResolvedDataViewAPI)
For each `/DataViews/{dataViewId}`, these resources show how the data view `./Resolved/` for your user context.

## [Resolved data view preview API](xref:ResolvedDataViewPreviewAPI)
For each `/DataView` provided in the request body, resources to show how the data view `./Resolved/` for your user context. This provides the flexibility to change the data view on the fly without saving/updating it.

## [Data API](xref:DataViewsDataAPI)
For each `/DataViews/{dataViewId}`, resources for getting the `./Data/` for a particular time range

## [Preview data API](xref:DataViewsPreviewDataAPI)
For each `/DataView` provided in request body, resources for getting the preview `./Data/` for a particular time range. This provides the flexibility to change the data view on the fly without saving/updating it.

## [Access control API](xref:DataViewsAccessControlAPI)
For the `/DataViews` collection, resources for reading and updating the default `/AccessControl`.  
For each `/DataViews/{dataViewId}`, resources for reading and updating its `/Owner` and `/AccessControl`
