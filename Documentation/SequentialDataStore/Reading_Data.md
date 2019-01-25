---
uid: sdsReadingData
---

Reading data
============

The .NET and REST APIs provide programmatic access to read and write data. This section identifies and describes 
the APIs used to read [Stream](xref:sdsStreams) data. Results are influenced by [Types](xref:sdsTypes),  
[Stream Views](xref:sdsViews), [Filter expressions](xref:sdsFilterExpressions), and [Table format](xref:sdsTableFormat).

If you are working in a .NET environment, convenient SDS Client libraries are available. 
The ``ISdsDataServiceinterface``, which is accessed using the ``SdsService.GetDataService()`` helper, 
defines the functions that are available.

The following methods for reading a single value are available:

* ``Get Value`` returns a value at a specified index, calculated if no stored value exists at that index. 
* ``Get First Value`` returns the first value in the stream.
* ``Get Last Value`` returns the last value in the stream.
* ``Get Distinct Value`` returns a value at the specified index, only if a stored value exists at that index.
* ``Find Distinct Value`` searches for a value based on a starting index and search criteria.

In addition, the following methods support reading multiple values:

* ``Get Values`` retrieves a collection of values at specified indexes, calculated if no stored 
  value exists at the index(es). ``Get values`` supports specifying the desired indexes as a list of indexes, 
  a filter expression and count, or a starting index, ending index, and count.
* ``Get Range Values`` retrieves a collection of stored values based on the specified start index and count.
* ``Get Window Values`` retrieves a collection of stored values based on specified start and end indexes.
* ``Get Intervals`` retrieves a collection of evenly spaced summary intervals based on a count 
  and specified start and end indexes.

All reads are HTTP GET actions. Reading data involves getting events from streams. The base reading URI is as follows:

``api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data``


**where:**

``string tenantId``  
The tenant identifier

``string namespaceId``  
The namespace identifier

``string streamId``  
The stream identifier


Response Format
---------------

Supported response formats include json, verbose json, and Sds. 

The default response format for is json, which is used in all examples in this document.  Default json 
responses do not include any values that are equal to the default value for their type.

Verbose json responses include all values, including defaults, in the returned json payload. To specify 
verbose json return, add the header ``Accept-Verbosity`` with a value of ``verbose`` to the request.  

To specify SDS format, set the ``Accept`` header in the request to ``application/Sds``.

Indexes and reading data
------------------------

Most read operations take at least one index as a parameter. Indexes may be specified as strings, or, 
when using the Sds Client libraries, the index may be passed as-is to read methods that take the index 
type as a generic argument. Additional details about working with indexes can be found on the [Indexes](xref:sdsIndexes) page.

Read Characteristics
--------------------

When data is requested at an index for which no stored event exists, the read characterisitics determine 
whether the result is an error, null event, interpolated event, or extrapolated event. The combination of 
the type of the index and the interpolation and extrapolation modes of the SdsType and the SdsStream 
determine the read characteristics. For more information on read characteristics, 
see [Types](xref:sdsTypes) and [Streams](xref:sdsStreams).

**Methods affected by Read Characteristics**

[`GetValueAsync`](xref:sdsReadingDataApi#get-value)  
Read characteristics are applied when the index is between, before, or after all data.

[`GetValuesAsync`](xref:sdsReadingDataApi#get-values)  
Read characteristics applied when an index determined by the call is between, before, or after all data.

[`GetWindowValuesAsync`](xref:sdsReadingDataApi#get-window-values)  
Read characteristics applied to indexes between, before, or after data when the calls Boundary parameter is set to ExactOrCalculated.

[`GetRangeValuesAsync`](xref:sdsReadingDataApi#get-range-values)  
Read characteristics applied to indexes between, before, or after data when the calls Boundary parameter is set to ExactOrCalculated.

SdsStreamView and reading data
------------------------

All reads support specifying an SdsStreamView identifier in the query string to shape the results of the read:

``streamViewId={streamViewId}``

Working with stream views is covered in detail in the [Stream Views](xref:sdsViews) section.

When data is requested with an SdsStreamView the read characteristics defined by the *target type* of the SdsStreamView 
determine what is returned. The read characteristics are discussed in the *Get Value*, 
*GetValues* and *GetWindowValues* code samples.

Filter Expressions
------------------

Filter expressions can be applied to any read that returns multiple values, including Get Values, Get Range Values, 
Get Window Values, and Get Intervals. The filter expression is applied to the collection events conditionally 
filtering events that do not meet the filter conditions.

Filter expressions are covered in detail in the [Filter expressions](xref:sdsFilterExpressions) section.

Table Format
------------

Results of a query can be organized into tables by directing the form parameter to return a table. 
Two forms of table are available: table and header table.

When the form parameter is specified as table, ``?form=table``, events are returned in row column form. 
Results include a collection named ``Columns`` that lists column name and type and a collection named 
``Rows`` containing a collection of rows matching the order of the columns.

Specifying a form of type ``table-headers``, ``?form=tableh``, results in a collection where the Rows collection 
contains a column header list.

Table formats are covered in detail in the [Table format](xref:sdsTableFormat) section.


SdsBoundaryType
--------------

SdsBoundaryType defines how data on the boundary of queries is handled: around the start index for range value queries, 
and around the start and end index for window values. The following are valid values for SdsBoundaryType:

| Boundary | Enumeration value | Operation |
| -------  | ----------------- | --------- |
| Exact    | 0                 | Results include the event at the specified index boundary if a stored event exists at that index. |
| Inside   | 1                 | Results include only events within the index boundaries |
| Outside  | 2                 | Results include up to one event that falls immediately outside of the specified index boundary. |
| ExactOrCalculated | 3        | Results include the event at the specified index boundary. If no stored event exists at that index, one is calculated based on the index type and interpolation and extrapolation settings. |

SdsSearchMode
-------------

The SdsSearchMode enum defines search behavior when seeking a stored event near a specified index. The following are 
available SdsSearchModes:

| Mode  | Enumeration value | Operation |
| ----- | ----------------- | --------- |
| Exact | 0                 | If a stored event exists at the specified index, that event is returned. Otherwise no event is returned. |
| ExactOrNext | 1           | If a stored event exists at the specified index, that event is returned. Otherwise the next event in the stream is returned. |
| Next | 2                  | Returns the stored event after the specified index. |
| ExactOrPrevious | 3       | If a stored event exists at the specified index, that event is returned. Otherwise the previous event in the stream is returned. |
| Previous | 4              | Returns the stored event before the specified index. |

## Unit conversion of data
SDS supports assigning [Units of Measure](xref:unitsOfMeasure) (Uom) to stream data. If stream data has Uom information associated, SDS supports reading data with unit conversions applied. On each read data request, unit conversions are specified by a user defined collection of `SdsStreamPropertyOverride` objects in read requests. The `SdsStreamPropertyOverride` object has the following structure:


| Property          | Type                 | Optionality | Details                                              |
| ----------------- | -------------------- | ----------- | ---------------------------------------------------- |
| SdsTypePropertyId | String               | Required    | Identifier for an SdsTypeProperty with a Uom assigned |
| Uom               | String               | Required    | Target unit of measure                               |
| InterpolationMode | SdsInterpolationMode | N/A         | Currently not supported in context of data reads     |

This is supported in the .NET API via overloads that accept a collection of `SdsStreamPropertyOverride` objects, and in the REST API via HTTP POST calls with a request body containing a collection of `SdsStreamPropertyOverride` objects. See [API calls for reading data](xref:sdsReadingDataApi) for more information.
