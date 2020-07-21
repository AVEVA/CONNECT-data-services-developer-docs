---
uid: DataViewsGettingData
---

# Getting Data

Data view data is retrieved by using the [Data API](xref:DataViewsDataAPI). The supported mode of retrieval is interpolated values within a user-specified range. Several formats are available, such as JSON and CSV.


## Index
All data in a data view is associated with an index value, i.e. a timestamp.
If there are multiple groups in the data view, the index and grouping field values together form a unique identifier for each data record.

### Index type
The supported index type is `DateTime`, as noted in the documentation on creating [Data Views](xref:DataView). Date times should use ISO 8601 format and can be in either UTC or local time. Data retrieved using the [Data API](xref:DataViewsDataAPI) will be returned in UTC.

Interval timespan values should be formatted using the standard timespan format, ie., d.hh:mm:ss.fffffff.

### Index range
Three parameters control the range and granularity of data returned:

| Name | Query-time parameter | Default property | Description |
|--|--|--|--|
| Start index | `startIndex` | `DefaultStartIndex` | The inclusive start boundary of the data view data
| End index | `endIndex` | `DefaultEndIndex` | The inclusive end boundary of the data view data
| Interval | `interval` | `DefaultInterval` | The interval between index values

Default values may, optionally, be defined on the data view itself. It is not necessary to define defaults for all three properties. 

Index parameters may be specified at query time. These take precedence over any defaults that are set.


## Retrieval mode
The supported mode of retrieval is `interpolated`.

### Interpolated retrieval
Required index parameters when requesting interpolated data are:
- Start index
- End index
- Interval
 
If one or more of these parameters is not specified at query time or as a default, the data query is not valid.

Streams in SDS may be configured to have non-default interpolation and extrapolation behavior. These behaviors are observed when stream data is included in data views. Data view data is always treated as dense, even if SDS returns sparse data. See the section on [empty or missing values](xref:DataViewsGettingData#empty-or-missing-values) for details.

## Empty or missing values
SDS stream properties may be of nullable (e.g. `NullableInt32`) or non-nullable (e.g. `Int32`) types. Data views treats all fields as nullable, as is necessary for its fundamental goal of aligning large datasets.
| SDS property type  | Corresponding data view field type |
|--|--|
| Double | NullableDouble |
| NullableDouble | NullableDouble |

If there is no value in an SDS stream for a requested index, the value of the corresponding data view fields(s) will be `null`.

## Ordering
Data records are ordered
- first by group, in the order that the groups resolved
- then by index, ascending, within each group

## Format
The view data is available in several formats.

| Name | Id | Enumeration Id | Description |
|--|--|--|--|
| JSON  | `default` | 0 | JSON object representation. An array of objects, each describing one data record. (default) |
| Table | `table` | 1 | JSON row-column representation. Includes an array describing the `.Columns` (corresponding to field mappings of the data view) and an array of data `.Rows`. Each row describes one data record.
| Table with header | `tableh` | 2 | Similar to `table`. The first of the `.Rows` is an array of the field mapping identifiers, information that is also available in the `.Columns` of both table formats. |
| CSV | `csv` | 3 | Comma-separated values. Each row describes one data record. |
| CSV with header | `csvh` | 4 | Similar to `csv`. The first row contains the identifier of its corresponding field mapping. |

## Paging
Data retrieval operations are paged. Data for a requested index range may span multiple pages.

### Page size
Optimal page size is dependent both on the client and on the shape of the data view. The size of each individual record is proportional to the "width" of the data view, i.e. how many field mappings are resolved. Clients retrieving data views that resolve into few field mappings may wish to use a page size close to the maximum.

By default, data views will be returned with an optimized page size based on the size and layout of the data view. Users can see the calculated page size as a `count` query parameter in the `Link` response header (described below). The calculated page size will be included in both the first and the next page links. This default page size can be overridden, however, by providing a `count` query parameter.

The maximum page size is 250,000.

### Hyperlinks
When paging through data view data via the REST API, hyperlinks to the first page and next page of data are provided in the `Link` header. The first page header is signified by relation type of first, `rel="first"`. The next page header is signified by `rel="next"`. Proper use of the hyperlinks is recommended.

#### Next page
If the requested data spans into another page, the response includes a hyperlink to the next page of data. Absence of a `rel="next"` link indicates that the data does not span past the current page.

The hyperlink preserves all request parameters, while adding or updating a `continuationToken`. For example:
```
Link: <.../dataViews/{dataViewId}/data/interpolated?continuationToken=MjAxOC0wMS0wMVQwMDowMDoxMVo_MD90Yk1OblE_QUxXcEZBP1VEdGxIMWJROG9z&count=1000>; rel="next"
```

To retrieve the entire requested range of data, clients should continue to follow next page hyperlinks until the response does not include a next page link. This indicates that the last page has been reached.

It is possible for the continuation token to become invalid during paging. This is unlikely in ordinary circumstances. However, if an independent operation triggers the data view to re-resolve differently, existing continuation tokens are no longer valid. Data requests with an invalid token are considered bad requests. Paging must be restarted from the first page.

#### First page
If the continuation token becomes invalid and paging must be restarted, clients may follow the first page hyperlink included in the `Link` header. The hyperlink preserves all request parameters, adding or updating the cache behavior to `Preserve`. This ensures that multiple parallel workers cannot endlessly "trip" each other.

For example:
```
Link: <.../dataViews/{dataViewId}/data/interpolated?cache=Preserve&count=1000>, rel="first"
```

### .NET client library
Paging is handled automatically when using the .NET client library to retrieve data. Results are returned as an IAsyncEnumerable<string> where each value is one record of data in the requested format. The actual backend page size of the request is configurable using the backingPageSize parameter.

### Index parameters
Index parameters, such as Start Index, must remain constant while paging through a range of data. If a different range of data is desired, restart the paging operation.

### Parallelization
To parallelize one large data retrieval operation across multiple workers, assign each worker a portion of the desired index range. Each worker should follow standard recommended paging behavior within its assigned range. The client application must then concatenate the portions in correct order.

It is recommended to suppress [re-resolution](xref:ResolvedDataView#when-is-a-data-view-resolved) of the data view by specifying a cache behavior of "preserve" on each first-page request.

## Resolution behavior
By default, requests for a first page of data will cause the data view to re-resolve. See the documentation on [resolved data views](xref:ResolvedDataView#when-is-a-data-view-resolved). This ensures that the data view accounts for any streams that have been added to or removed from SDS. Re-resolution may be suppressed by explicitly specifying a cache behavior of "preserve".

Requests for subsequent pages include a `continuationToken`. This implictly suppresses re-resolution, akin to cache "preserve" behavior.

## Field mapping maximum count
Shape plays an important role in both the performance and usefulness of a data view. In order to retain this balance, a maximum threshold of 1,000 field mappings is imposed for each data view. OCS checks the field mapping count prior to constructing the data set and returns a message if the limit has been exceeded.

If your data view exceeds this limit, there are several ways to shape the data view to reduce the number of field mappings generated:

- Use grouping fields to pivot data for like-groups into their own rows.
- Use identifying fields to display useful information in headers, rather than as discrete field mappings.
- Deselect unneeded fields to remove them as field mappings.
- Toggle to the narrow shape option to pivot data fields into individual rows instead of columns.
