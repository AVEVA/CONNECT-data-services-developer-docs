---
uid: DataViewsQuickStartGetData
---

# Get data view data
You retrieve data view data with the [Data API](xref:DataViewsDataAPI). This topic explains parameters, options and items you must define to retrieve data view data.

## General concepts
The supported mode of retrieval is interpolated values within a user-specified range. Several formats are available, such as JSON and CSV.

### Index
All data in a data view is associated with an index value, i.e. a timestamp.
If there are multiple groups in the data view, the index and grouping field values together form a unique identifier for each data record.

#### Index type
The supported index type is `DateTime`, as noted in the documentation on creating [Data Views](xref:DataViewsQuickStartDefine).

#### Index range
Three parameters control the range and granularity of data returned:

| Name | Query-time parameter | Default property | Description |
|--|--|--|--|
| Start index | `startIndex` | `defaultStartIndex` | The inclusive start boundary of the data view data
| End index | `endIndex` | `defaultEndIndex` | The inclusive end boundary of the data view data
| Interval | `interval` | `defaultInterval` | The interval between index values

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

Streams in SDS may be configured to have non-default interpolation and extrapolation behavior. These behaviors are observed when stream data is included in data views. Data view data is always treated as dense, even if SDS returns sparse data. See the following section on empty or missing values for details.

### Empty or missing values
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

| Name | Id | Description |
|--|--|--|
| JSON  | `default` | JSON object representation. An array of objects, each describing one data record. (default) |
| Table | `table` | JSON row-column representation. Includes an array describing the `.Columns` (corresponding to field mappings of the data view) and an array of data `.Rows`. Each row describes one data record.
| Table with header | `tableh` | Similar to `table`. The first of the `.Rows` is an array of the field mapping identifiers, information that is also available in the `.Columns` of both table formats. |
| CSV | `csv` | Comma-separated values. Each row describes one data record. |
| CSV with header | `csvh` | Similar to `csv`. The first row contains the identifier of its corresponding field mapping. |

## Paging
Data retrieval operations are paged. Data for a requested index range may span multiple pages.

### Page size
By default, each page includes 1000 records. The maximum page size is 250,000. 

Optimal page size is dependent both on the client and on the shape of the data view. The size of each individual record is proportional to the "width" of the data view, i.e. how many field mappings are resolved. Clients retrieving data views that resolve into few field mappings may wish to use a page size close to the maximum.

### Hyperlinks
When paging through data view data via the REST API, hyperlinks to the `FirstPage` and `NextPage` are provided. Proper use of the hyperlinks is recommended.

#### NextPage
If the requested data spans into another page, the response includes a hyperlink to the next page of data. Absence of a `NextPage` link indicates that the data does not span past the current page.

The hyperlink preserves all request parameters, while adding or updating a `continuationToken`. For example:
```
NextPage: ".../dataViews/{dataViewId}/data/interpolated?continuationToken=MjAxOC0wMS0wMVQwMDowMDoxMVo_MD90Yk1OblE_QUxXcEZBP1VEdGxIMWJROG9z&count=1000"
```

To retrieve the entire requested range of data, clients should continue to follow `NextPage` hyperlinks until the response does not include a `NextPage` link. This indicates that the last page has been reached.

It is possible for the continuation token to become invalid during paging. This is unlikely in ordinary circumstances. However, if an independent operation triggers the data view to re-resolve differently, existing continuation tokens are no longer valid. Data requests with an invalid token are considered bad requests. Paging must be restarted from the first page.

#### FirstPage
If the continuation token becomes invalid and paging must be restarted, clients may follow the `FirstPage` hyperlink. The hyperlink preserves all request parameters, adding or updating the cache behavior to `Preserve`. This ensures that multiple parallel workers cannot endlessly "trip" each other.

For example:
```
FirstPage: ".../dataViews/{dataViewId}/data/interpolated?cache=Preserve&count=1000"
```

### .NET client library
Paging is handled automatically when using the .NET client library to retrieve data. Results are returned as an IAsyncEnumerable<string> where each value is one record of data in the requested format. The actual backend page size of the request is configurable using the backingPageSize parameter.
 
### Index parameters
Index parameters, such as Start Index, must remain constant while paging through a range of data. If a different range of data is desired, restart the paging operation.

### Parallelization
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
Getting data from a data view is straightforward. If you want to understand more about the source behind each data field, that information is available too.

This is an introduction to the recommended workflow for getting data. For detailed information, see the [Data API reference](xref:DataViewsDataAPI).

### Specify first page parameters
Complete the following to specify first page parameters:

1. Specify the index range (start index and end index) and granularity of data to be retrieved.
2. Specify the desired response format as csv, table-style json, or object-style json. The default is object-style json.  Csv and table-style json are available with or without a header row.
3. Specify the page size.

### Request any remaining pages
Complete the following if data spans into additional page(s). The current page response will include an HTTP header linking to the next page.
1. Follow the hyperlinks to retrieve the full requested dataset page by page, if the current page includes a NextPage hyperlink.
2. Follow the `FirstPage` hyperlink in the event that it is necessary to restart the paging operation from the first page. 

### [Optional] Investigate the source of the data
For precise information about the source of each field's data, see the data view's resolved field mappings.

## Procedure: Get Data View Data

This section presents the main concepts behind consuming data view data.

It is assumed that you are working with streams as described in the [Stream examples](xref:DataViewsExampleScenario). The data views API uses the same authentication scheme as the Sequential Data Store.

### Get data using defaults

#### Action
```text
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart/Data/Interpolated
```

#### Expected result
An array of json values similar to:
```json
[
    {
        "Timestamp.0": "2019-10-21T18:00:00Z",
        "Id.1": "WS_WINT",
        "Name.2": "WS_WINT",
        "Tags.3": "Weather, High Resolution, Gen2",
        "Site.4": "Winterthur",
        "SolarRadiation.5": 108,
        "AmbientTemperature.6": 1.0805517883941373,
        "CloudCover.7": 2,
        "Temperature.8": null,
        "Id.9": "WS_ROSE",
        "Name.10": "WS_ROSE",
        "Tags.11": "Weather, Low Resolution, Gen1",
        "Site.12": "Rosecliff",
        "SolarRadiation.13": 132,
        "AmbientTemperature.14": null,
        "CloudCover.15": null,
        "Temperature.16": 14.537369185607899,
        "Id.17": "WS_BILT",
        "Name.18": "WS_BILT",
        "Tags.19": "Weather, High Resolution, Gen1",
        "Site.20": "Biltmore",
        "SolarRadiation.21": 165,
        "AmbientTemperature.22": null,
        "CloudCover.23": null,
        "Temperature.24": 33.589619124193831,
    },
    ...
```

### Get data for a custom range

#### Action
```text
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart/Data/Interpolated
?startIndex={your_val_here}&endIndex={your_val_here}&interval={your_val_here}
```

#### Expected result
An array of json values similar to:
```json
[
    {
        "Timestamp.0": "2019-10-21T18:00:00Z",
        "Id.1": "WS_WINT",
        "Name.2": "WS_WINT",
        "Tags.3": "Weather, High Resolution, Gen2",
        "Site.4": "Winterthur",
        "SolarRadiation.5": 108,
        "AmbientTemperature.6": 1.0805517883941373,
        "CloudCover.7": 2,
        "Temperature.8": null,
        "Id.9": "WS_ROSE",
        "Name.10": "WS_ROSE",
        "Tags.11": "Weather, Low Resolution, Gen1",
        "Site.12": "Rosecliff",
        "SolarRadiation.13": 132,
        "AmbientTemperature.14": null,
        "CloudCover.15": null,
        "Temperature.16": 14.537369185607899,
        "Id.17": "WS_BILT",
        "Name.18": "WS_BILT",
        "Tags.19": "Weather, High Resolution, Gen1",
        "Site.20": "Biltmore",
        "SolarRadiation.21": 165,
        "AmbientTemperature.22": null,
        "CloudCover.23": null,
        "Temperature.24": 33.589619124193831,
    },
    ...
```

### Get data in a different format
By default, data is returned in object-style json. Other formats are available: csv and table-style json, each with an optional header row.

#### Action
Resubmit the data query with an additional query parameter, `&form=csvh` for csv-formatted data with a header row.
```text
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart/Data/Interpolated
?startIndex={your_val_here}&endIndex={your_val_here}&interval={your_val_here}&form=csvh
```

#### Expected result
Rows of CSV values similar to:

```csv
Timestamp.0,Id.1,Name.2,Tags.3,Site.4,SolarRadiation.5,AmbientTemperature.6,CloudCover.7,Temperature.8,Id.9,Name.10,Tags.11,Site.12,SolarRadiation.13,AmbientTemperature.14,CloudCover.15,Temperature.16,Id.17,Name.18,Tags.19,Site.20,SolarRadiation.21,AmbientTemperature.22,CloudCover.23,Temperature.24
2019-10-21T18:00:00.0000000Z,WS_WINT,WS_WINT,"Weather, High Resolution, Gen2",Winterthur,108,1.080551788,2,,WS_ROSE,WS_ROSE,"Weather, Low Resolution, Gen1",Rosecliff,132,,,14.53736919,WS_BILT,WS_BILT,"Weather, High Resolution, Gen1",Biltmore,165,,,33.58961912
2019-10-21T20:00:00.0000000Z,WS_WINT,WS_WINT,"Weather, High Resolution, Gen2",Winterthur,109,2.501105722,3,,WS_ROSE,WS_ROSE,"Weather, Low Resolution, Gen1",Rosecliff,139,,,14.76498991,WS_BILT,WS_BILT,"Weather, High Resolution, Gen1",Biltmore,157,,,32.41209639
...
```

### Get subsequent pages
By default, each page includes 1000 records. If the requested data spans into another page, the response includes a hyperlink to the next page of data.

#### Action
Use the hyperlink in the NextPage header to request the next page.
```text
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart/Data/Interpolated
?startIndex={your_val_here}&endIndex={your_val_here}&interval={your_val_here}&form=csvh&continuationToken=MjAxOC0wMS0wMVQwMDowMDoxMVo_MD90Yk1OblE_QUxXcEZBP1VEdGxIMWJROG9z&cache=preserve
```

#### Expected result
The next page of data:

```csv
Timestamp.0,Id.1,Name.2,Tags.3,Site.4,SolarRadiation.5,AmbientTemperature.6,CloudCover.7,Temperature.8,Id.9,Name.10,Tags.11,Site.12,SolarRadiation.13,AmbientTemperature.14,CloudCover.15,Temperature.16,Id.17,Name.18,Tags.19,Site.20,SolarRadiation.21,AmbientTemperature.22,CloudCover.23,Temperature.24
2019-10-21T22:00:00.0000000Z,WS_WINT,WS_WINT,"Weather, High Resolution, Gen2",Winterthur,108,1.080551788,2,,WS_ROSE,WS_ROSE,"Weather, Low Resolution, Gen1",Rosecliff,132,,,14.53736919,WS_BILT,WS_BILT,"Weather, High Resolution, Gen1",Biltmore,165,,,33.58961912
2019-10-22T00:00:00.0000000Z,WS_WINT,WS_WINT,"Weather, High Resolution, Gen2",Winterthur,109,2.501105722,3,,WS_ROSE,WS_ROSE,"Weather, Low Resolution, Gen1",Rosecliff,139,,,14.76498991,WS_BILT,WS_BILT,"Weather, High Resolution, Gen1",Biltmore,157,,,32.41209639
...
```

### Recover from an invalid paging session
It is possible, though unlikely, for the continuation token to become invalid during paging. When this happens, paging must be restarted from the first page.

#### Action
Use the hyperlink in the FirstPage header to request the first page.

```text
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart/Data/Interpolated
?startIndex={your_val_here}&endIndex={your_val_here}&interval={your_val_here}&form=csvh&cache=preserve
```

#### Expected result
The first page of data:

```csv
Timestamp.0,Id.1,Name.2,Tags.3,Site.4,SolarRadiation.5,AmbientTemperature.6,CloudCover.7,Temperature.8,Id.9,Name.10,Tags.11,Site.12,SolarRadiation.13,AmbientTemperature.14,CloudCover.15,Temperature.16,Id.17,Name.18,Tags.19,Site.20,SolarRadiation.21,AmbientTemperature.22,CloudCover.23,Temperature.24
2019-10-21T18:00:00.0000000Z,WS_WINT,WS_WINT,"Weather, High Resolution, Gen2",Winterthur,108,1.080551788,2,,WS_ROSE,WS_ROSE,"Weather, Low Resolution, Gen1",Rosecliff,132,,,14.53736919,WS_BILT,WS_BILT,"Weather, High Resolution, Gen1",Biltmore,165,,,33.58961912
2019-10-21T20:00:00.0000000Z,WS_WINT,WS_WINT,"Weather, High Resolution, Gen2",Winterthur,109,2.501105722,3,,WS_ROSE,WS_ROSE,"Weather, Low Resolution, Gen1",Rosecliff,139,,,14.76498991,WS_BILT,WS_BILT,"Weather, High Resolution, Gen1",Biltmore,157,,,32.41209639
...
```

### Explore what each data field maps to

#### Action

```text
GET /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart/Resolved/FieldMappings
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
            "DataMappings": [
                {
                    "TypeCode": "DateTime"
                }
            ]
        },
        {
            "Id": "Id.1",
            "Label": "Id",
            "FieldKind": "DataField",
            "FieldSetIndex": 0,
            "FieldIndex": 0,
            "DataMappings": [
                {
                    "TargetId": "WS_BILT",
                    "TargetFieldKey": "WS_BILT",
                    "TypeCode": "String"
                }
            ]
        },
      ...
    ]
}
```

