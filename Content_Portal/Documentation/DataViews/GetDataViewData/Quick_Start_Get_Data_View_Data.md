---
uid: DataViewsQuickStartGetData
---

# Get data view data
You retrieve data view data with the [Data API](xref:DataViewsDataAPI). This topic explains the concepts and workflow to retrieve data view data.

## General concepts
The supported mode of retrieval is interpolated values within a user-specified range. Several formats are available, such as JSON and CSV.

### Index
All data in a data view is associated with an index value, i.e. a timestamp.
If there are multiple groups in the data view, the index and grouping field values together form a unique identifier for each data record.

#### Index type
The supported index type is `DateTime`, as noted in [Define a Data View](xref:DataViewsQuickStartDefine). Date times should use ISO 8601 format and can be in either UTC or local time. Data retrieved using the [Data API](xref:DataViewsDataAPI) will be returned in UTC.

Interval timespan values should be formatted using the standard timespan format, ie., d.hh:mm:ss.fffffff.

#### Index range
Three parameters control the range and granularity of data returned:

| Name | Query-time parameter | Default property | Description |
|--|--|--|--|
| Start index | `startIndex` | `DefaultStartIndex` | The inclusive start boundary of the data view data
| End index | `endIndex` | `DefaultEndIndex` | The inclusive end boundary of the data view data
| Interval | `interval` | `DefaultInterval` | The interval between index values

Default values may, optionally, be defined on the data view itself. It is not necessary to define defaults for all three properties. 

Index parameters may be specified at query time. These take precedence over any defaults that are set.

### Retrieval mode
The supported mode of retrieval is `interpolated`.

#### Interpolated retrieval
Required index parameters when requesting interpolated data are:
- Start index
- End index
- Interval
 
If one or more of these parameters is not specified at query time or as a default, the data query is not valid.

Streams in SDS may be configured to have non-default interpolation and extrapolation behavior. These behaviors are observed when stream data is included in data views. Data view data is always treated as dense, even if SDS returns sparse data. See the following section on empty or missing values for details.

#### Empty or missing values
SDS stream properties may be of nullable (e.g. `NullableInt32`) or non-nullable (e.g. `Int32`) types. Data views treats all fields as nullable, as is necessary for its fundamental goal of aligning large datasets.
| SDS property type  | Corresponding data view field type |
|--|--|
| Double | NullableDouble |
| NullableDouble | NullableDouble |

If there is no value in an SDS stream for a requested index, the value of the corresponding data view fields(s) will be `null`.

### Ordering
Data records are ordered
- first by group, in the order that the groups resolved
- then by index, ascending, within each group

### Format
The view data is available in several formats.

| Name | Id | Enumeration Id | Description |
|--|--|--|--|
| JSON  | `default` | 0 | JSON object representation. An array of objects, each describing one data record. (default) |
| Table | `table` | 1 | JSON row-column representation. Includes an array describing the `.Columns` (corresponding to field mappings of the data view) and an array of data `.Rows`. Each row describes one data record.
| Table with header | `tableh` | 2 | Similar to `table`. The first of the `.Rows` is an array of the field mapping identifiers, information that is also available in the `.Columns` of both table formats. |
| CSV | `csv` | 3 | Comma-separated values. Each row describes one data record. |
| CSV with header | `csvh` | 4 | Similar to `csv`. The first row contains the identifier of its corresponding field mapping. |

### Paging
Data retrieval operations are paged. Data for a requested index range may span multiple pages.

Optimal page size is dependent both on the client and on the shape of the data view. The size of each individual record is proportional to the "width" of the data view, i.e. how many field mappings are resolved. Clients retrieving data views that resolve into few field mappings may wish to use a page size close to the maximum.

#### Page size
Optimal page size is dependent both on the client and on the shape of the data view. The size of each individual record is proportional to the "width" of the data view, i.e. how many field mappings are resolved. Clients retrieving data views that resolve into few field mappings may wish to use a page size close to the maximum.

By default, data views will be returned with an optimized page size based on the size and layout of the data view. Users can see the calculated page size as a `count` query parameter in the `Link` response header (described below). The calculated page size will be included in both the first and the next page links. This default page size can be overridden, however, by providing a `count` query parameter.

The maximum page size is 250,000.

#### Hyperlinks
When paging through data view data via the REST API, hyperlinks to the first page and next page of data are provided in the `Link` header. The first page header is signified by relation type of first, `rel="first"`. The next page header is signified by `rel="next"`. Proper use of the hyperlinks is recommended.

##### Next page
If the requested data spans into another page, the response includes a hyperlink to the next page of data. Absence of a `rel="next"` link indicates that the data does not span past the current page.

The hyperlink preserves all request parameters, while adding or updating a `continuationToken`. For example:
```
Link: <.../dataViews/{dataViewId}/data/interpolated?continuationToken=MjAxOC0wMS0wMVQwMDowMDoxMVo_MD90Yk1OblE_QUxXcEZBP1VEdGxIMWJROG9z&count=1000>; rel="next"
```

To retrieve the entire requested range of data, clients should continue to follow next page hyperlinks until the response does not include a next page link. This indicates that the last page has been reached.

It is possible for the continuation token to become invalid during paging. This is unlikely in ordinary circumstances. However, if an independent operation triggers the data view to re-resolve differently, existing continuation tokens are no longer valid. Data requests with an invalid token are considered bad requests. Paging must be restarted from the first page.

##### First page
If the continuation token becomes invalid and paging must be restarted, clients may follow the first page hyperlink included in the `Link` header. The hyperlink preserves all request parameters, adding or updating the cache behavior to `Preserve`. This ensures that multiple parallel workers cannot endlessly "trip" each other.

For example:
```
Link: <.../dataViews/{dataViewId}/data/interpolated?cache=Preserve&count=1000>; rel="first"
```

#### .NET client library
Paging is handled automatically when using the .NET client library to retrieve data. Results are returned as an IAsyncEnumerable<string> where each value is one record of data in the requested format. The actual backend page size of the request is configurable using the backingPageSize parameter.
 
#### Index parameters
Index parameters, such as Start Index, must remain constant while paging through a range of data. If a different range of data is desired, restart the paging operation.

#### Parallelization
To parallelize one large data retrieval operation across multiple workers, assign each worker a portion of the desired index range. Each worker should follow standard recommended paging behavior within its assigned range. The client application must then concatenate the portions in correct order.

It is recommended to suppress [re-resolution](xref:ResolvedDataView#when-is-a-data-view-resolved) of the data view by specifying a cache behavior of "preserve" on each first-page request.

### Resolution behavior
By default, requests for a first page of data will cause the data view to re-resolve. See the documentation on [resolved data views](xref:ResolvedDataView#when-is-a-data-view-resolved). This ensures that the data view accounts for any streams that have been added to or removed from SDS. Re-resolution may be suppressed by explicitly specifying a cache behavior of "preserve".

Requests for subsequent pages include a `continuationToken`. This implictly suppresses re-resolution, akin to cache "preserve" behavior.

### Field mapping maximum count
Shape plays an important role in both the performance and usefulness of a data view. In order to retain this balance, a maximum threshold of 1,000 field mappings is imposed for each data view. OCS checks the field mapping count prior to constructing the data set and returns a message if the limit has been exceeded.

If your data view exceeds this limit, there are several ways to shape the data view to reduce the number of field mappings generated:

- Use grouping fields to pivot data for like-groups into their own rows.
- Use identifying fields to display useful information in headers, rather than as discrete field mappings.
- Deselect unneeded fields to remove them as field mappings.
- Toggle to the narrow shape option to pivot data fields into individual rows instead of columns.

## Recommended workflow
Getting data from a data view is straightforward. If you want to understand more about the source behind each data field, that information is available too. For detailed information, see the [Data API reference](xref:DataViewsDataAPI).

### Specify first page parameters
Complete the following to specify first page parameters:

1. Specify the index range (start index and end index) and granularity of data to be retrieved (interval).
2. Specify the desired response format as csv, table-style json, or object-style json. The default is object-style json.  Csv and table-style json are available with or without a header row.
3. Specify the page size.

### Request any remaining pages
Complete the following if data spans into additional page(s). The current page response will include an HTTP `Link` header with a hyperlink to the next page of data.
1. Follow the hyperlinks to retrieve the full requested dataset page by page, if the current page includes a next hyperlink in the `Link` header.
2. Follow the first page hyperlink in the `Link` header in the event that it is necessary to restart the paging operation from the first page. 

### [Optional] Investigate the source of the data
For precise information about the source of each field's data, see the data view's resolved field mappings.

## Procedure: Get Data View Data

It is assumed that you are working with streams as described in the [Stream examples](xref:DataViewsExampleScenario). The data views API uses the same authentication scheme as the Sequential Data Store.

### Get data using defaults
The default start index, end index, and interval are configured in the `DataView` object. If not null, the get data request must include the startIndex, endIndex, and interval query parameters.

#### Action
```text
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart/Data/Interpolated
```

#### Expected result
An array of json values similar to:
```json
[
    {
        "Timestamp.0": "2019-10-21T18:00:00Z",
        "Id.1": "WS_BILT",
        "Name.2": "WS_BILT",
        "AmbientTemperature.3": null,
        "CloudCover.4": null,
        "SolarRadiation.5": 165,
        "Temperature.6": 33.589619124193831,
        "Site.7": "Biltmore",
        "Tags.8": "Weather, High Resolution, Gen1",
        "Id.9": "WS_ROSE",
        "Name.10": "WS_ROSE",
        "AmbientTemperature.11": null,
        "CloudCover.12": null,
        "SolarRadiation.13": 132,
        "Temperature.14": 14.537369185607899,
        "Site.15": "Rosecliff",
        "Tags.16": "Weather, Low Resolution, Gen1",
        "Id.17": "WS_WINT",
        "Name.18": "WS_WINT",
        "AmbientTemperature.19": 1.0805517883941373,
        "CloudCover.20": 2,
        "SolarRadiation.21": 108,
        "Temperature.22": null,
        "Site.23": "Winterthur",
        "Tags": "Weather, High Resolution, Gen2",
    },
    ...
```

### Get data for a custom range

#### Action
```text
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart/Data/Interpolated
?startIndex={your_val_here}&endIndex={your_val_here}&interval={your_val_here}
```

#### Expected result
An array of json values similar to:
```json
[
    {
        "Timestamp.0": "2019-10-21T18:00:00Z",
        "Id.1": "WS_BILT",
        "Name.2": "WS_BILT",
        "AmbientTemperature.3": null,
        "CloudCover.4": null,
        "SolarRadiation.5": 165,
        "Temperature.6": 33.589619124193831,
        "Site.7": "Biltmore",
        "Tags.8": "Weather, High Resolution, Gen1",
        "Id.9": "WS_ROSE",
        "Name.10": "WS_ROSE",
        "AmbientTemperature.11": null,
        "CloudCover.12": null,
        "SolarRadiation.13": 132,
        "Temperature.14": 14.537369185607899,
        "Site.15": "Rosecliff",
        "Tags.16": "Weather, Low Resolution, Gen1",
        "Id.17": "WS_WINT",
        "Name.18": "WS_WINT",
        "AmbientTemperature.19": 1.0805517883941373,
        "CloudCover.20": 2,
        "SolarRadiation.21": 108,
        "Temperature.22": null,
        "Site.23": "Winterthur",
        "Tags.24": "Weather, High Resolution, Gen2"
    },
    ...
```

### Get data in a different format
By default, data is returned in object-style json. Other formats are available: csv and table-style json, each with an optional header row.

#### Action
Resubmit the data query with an additional query parameter, `&form=csvh` for csv-formatted data with a header row.
```text
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart/Data/Interpolated
?startIndex={your_val_here}&endIndex={your_val_here}&interval={your_val_here}&form=csvh
```

#### Expected result
Rows of CSV values similar to:

```csv
Timestamp.0,Id.1,Name.2,AmbientTemperature.3,CloudCover.4,SolarRadiation.5,Temperature.6,Site.7,Tags.8,Id.9,Name.10,AmbientTemperature.11,CloudCover.12,SolarRadiation.13,Temperature.14,Site.15,Tags.16,Id.17,Name.18,AmbientTemperature.19,CloudCover.20,SolarRadiation.21,Temperature.22,Site.23,Tags.24
2019-10-21T18:00:00.0000000Z,WS_BILT,WS_BILT,,,165,33.58961912,Biltmore,"Weather, High Resolution, Gen1",WS_ROSE,WS_ROSE,,,132,14.53736919,Rosecliff,"Weather, Low Resolution, Gen1",WS_WINT,WS_WINT,1.080551788,2,108,,Winterthur,"Weather, High Resolution, Gen2"
2019-10-21T20:00:00.0000000Z,WS_BILT,WS_BILT,,,157,32.41209639,Biltmore,"Weather, High Resolution, Gen1",WS_ROSE,WS_ROSE,,,139,14.76498991,Rosecliff,"Weather, Low Resolution, Gen1",WS_WINT,WS_WINT,2.501105722,3,109,,Winterthur,"Weather, High Resolution, Gen2"
...
```

### Get subsequent pages
By default, each page includes 1000 records. If the requested data spans into another page, the response includes a hyperlink to the next page of data.

#### Action
Use the "next" hyperlink from the Link header to request the next page.

```text
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart/Data/Interpolated
?startIndex={your_val_here}&endIndex={your_val_here}&interval={your_val_here}&form=csvh&continuationToken=MjAxOC0wMS0wMVQwMDowMDoxMVo_MD90Yk1OblE_QUxXcEZBP1VEdGxIMWJROG9z
```

#### Expected result
The next page of data:

```csv
Timestamp.0,Id.1,Name.2,AmbientTemperature.3,CloudCover.4,SolarRadiation.5,Temperature.6,Site.7,Tags.8,Id.9,Name.10,AmbientTemperature.11,CloudCover.12,SolarRadiation.13,Temperature.14,Site.15,Tags.16,Id.17,Name.18,AmbientTemperature.19,CloudCover.20,SolarRadiation.21,Temperature.22,Site.23,Tags.24
2019-10-21T22:00:00.0000000Z,WS_BILT,WS_BILT,,,165,33.58961912,Biltmore,"Weather, High Resolution, Gen1",WS_ROSE,WS_ROSE,,,132,14.53736919,Rosecliff,"Weather, Low Resolution, Gen1",WS_WINT,WS_WINT,1.080551788,2,108,,Winterthur,"Weather, High Resolution, Gen2"
2019-10-22T00:00:00.0000000Z,WS_BILT,WS_BILT,,,157,32.41209639,Biltmore,"Weather, High Resolution, Gen1",WS_ROSE,WS_ROSE,,,139,14.76498991,Rosecliff,"Weather, Low Resolution, Gen1",WS_WINT,WS_WINT,2.501105722,3,109,,Winterthur,"Weather, High Resolution, Gen2"
...
```

### Recover from an invalid paging session
It is possible, though unlikely, for the continuation token to become invalid during paging. When this happens, paging must be restarted from the first page.

#### Action
Use the "first" hyperlink from the Link header to request the first page.

```text
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart/Data/Interpolated
?startIndex={your_val_here}&endIndex={your_val_here}&interval={your_val_here}&form=csvh&cache=preserve
```

#### Expected result
The first page of data:

```csv
Timestamp.0,Id.1,Name.2,AmbientTemperature.3,CloudCover.4,SolarRadiation.5,Temperature.6,Site.7,Tags.8,Id.9,Name.10,AmbientTemperature.11,CloudCover.12,SolarRadiation.13,Temperature.14,Site.15,Tags.16,Id.17,Name.18,AmbientTemperature.19,CloudCover.20,SolarRadiation.21,Temperature.22,Site.23,Tags.24
2019-10-21T18:00:00.0000000Z,WS_BILT,WS_BILT,,,165,33.58961912,Biltmore,"Weather, High Resolution, Gen1",WS_ROSE,WS_ROSE,,,132,14.53736919,Rosecliff,"Weather, Low Resolution, Gen1",WS_WINT,WS_WINT,1.080551788,2,108,,Winterthur,"Weather, High Resolution, Gen2"
2019-10-21T20:00:00.0000000Z,WS_BILT,WS_BILT,,,157,32.41209639,Biltmore,"Weather, High Resolution, Gen1",WS_ROSE,WS_ROSE,,,139,14.76498991,Rosecliff,"Weather, Low Resolution, Gen1",WS_WINT,WS_WINT,2.501105722,3,109,,Winterthur,"Weather, High Resolution, Gen2"
...
```

### Explore what each data field maps to

#### Action

```text
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart/Resolved/FieldMappings
```

#### Expected result
An array of field mappings:

```json
{
    "TimeOfResolution": "(a timestamp in ISO8601 format)",
    "Items": [
        {
           "Id": "Timestamp.0",
           "Label": "Timestamp",
           "FieldKind": "IndexField",
           "TypeCode": "DateTime",
           "DataMappings":  [
               {
                 "TypeCode": "DateTime"
               }
           ]
        },
        {
           "Id": "Id.1",
           "Label": "Id",
           "FieldKind": "DataField",
           "TypeCode": "String",
           "DataMappings":  [
                {
                   "TargetId": "WS_BILT",
                   "TargetFieldKey": "WS_BILT",
                   "TypeCode": "String",
                   "FieldSetIndex": 0,
                   "FieldIndex": 0,
                }
             ]
          },
      ...
    ]
}
```

