---
uid: DataRetrieval
---

# Retrieving Data with Data Views
Data Views shape SDS stream data into a tabular format for end users to use in data science tools. Essentially they are queries to be resolved against the SDS data store for a unique user. This implies the following:
* Per-user Stream permissions in SDS mean per-user Data View results. When a user consumes a Data View, the Data View’s definition is resolved into concrete SDS streams & types which the user has permissions in SDS. From the resultant streams the [resolved data resources](#metadata) are derived: datagroups, data items and data mappings.  These are unique for each user, as each user has unique permissions in SDS.
* Changes to the underlying  SDS Streams collection can affect how a Data View resolves. If a user is paging through data, the pages can be corrupted if the Data View starts to resolve differently midway through. This can happen when the underlying streams and types that comprise the Data View resources change.  

To address these issues the [Resolved Data View Resources](#metadata) are cached after the first call to retrieve data on a per Data View per user basis. The user can then [page](#paging) through the data using the convenient [First Page and Next Page](#paging) hyperlinks provided in the HTTPS response headers.  On the initial data call a cache parameter allows the user to control the refreshing or updating of the Resolved Data Resources backing the Data View. If a Data View is changed by any authorized user, then the Data View Resolved Data Resources are resolved again for each user's data view on the next data call. Statistics provide a summary of the Resolved Data Resources.  

## <a name="data">`Data View Data` </a>

API: 
```csharp
    GET Dataviews/{id}/data/interpolated
```

#### <a name="paging">Paging Data View Data</a>

Each GET Data call to retrieve Data View data results in two links stored in the HTTPS response headers that the user can use to show the first page or the next page of data.

* <a name="firstpage">FirstPage</a>: .../DataViews/DataViewId/Data/Interpolated?form=csv&count=100&cache=Preserve
* <a name="nextpage">NextPage</a>: ...DataViews/DataViewId/Data/Interpolated?form=csv&count=100&continuationToken=MjAxOC0wMS0wMVQwMDowMDoxMVo_MD90Yk1OblE_QUxXcEZBP1VEdGxIMWJROG9z

Using these links allows the user to get the first page of data or retrieve the next.  In the [FirstPage](#firstpage) link the cache parameter controls resolution of the backing data view resources with a default of preserve. All necessary parameters to generate the next page of data are included in the continuationToken.  The user can override the form and the count, parameters.  

## <a name="metadata">`Resolved Data View Resources` </a>

APIs to retrieve user specific resolved resources of a Data View:
```csharp
    GET Dataviews/{id}/datagroups
        Query parameters: skip, count, cache
    GET Dataviews/{id}/datagroup
        Query parameters: cache
    GET Dataviews/{id}/dataitems
        Query parameters: skip, count, cache
    GET Dataviews/{id}/datamappings
        Query parameters: cache
    GET Dataviews/{id}/statistics
        Query parameters: cache
```
#### <a name="paging">Paging Resolved Data View Resources</a>
Results from two API calls to get data groups and data items can be quite lengthy and are easier read in a page format.  Similar to the Data API, links to view the first page and next page of data are stored in the HTTPS response headers. Below are example links for paging through the data groups one by one.

* FirstPage: .../DataViews/DataViewId/DataGroups?skip=0&cache=preserve&count=2
* NextPage: .../DataViews/DataViewId/DataGroups?skip=2&cache=preserve&count=2
