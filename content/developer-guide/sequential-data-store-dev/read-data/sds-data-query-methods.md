---
title: SDS data query methods
uid: SdsDataQueryMethods
---

# SDS data query options

When using SDS data operations to query data from a stream, you can query for data in stream using different query options based upon the operation type. The following table lists the available query options and the operations that they can be used with.

| Query option | Description | [List values](xref:sds-stream-data#list-values) | [List interpolated values](xref:sds-stream-data#list-interpolated-values) | [Remove values](xref:sds-stream-data#remove-values) |
|--|--|--|--|--|
| [Find distinct value](#find-distinct-value) | Returns a stored event based on the specified `index` and `searchMode`. | &#x2714; | | |
| [Filtered](#filtered) | Returns a collection of stored values as determined by a `filter` expression. The filter limits results by applying an expression against event fields. | &#x2714; | |  |
| [Index collection](#index-collection) | Removes the event at each index from the specified stream. Different overloads are available to make it easier to indicate the index where you want to remove a data event. One or more indexes can be specified in the request. |  | &#x2714; | &#x2714; |
| [Interval](#interval) | Returns events at evenly spaced intervals based on the specified `startIndex`, `endIndex`, and `count`. If no stored event exists at an index interval, the read characteristics of the stream determine how the returned event is calculated. |  |  | &#x2714; |
| [Range](#range) | Returns a collection of stored values as determined by a `startIndex` and `count`. Additional optional parameters specify the direction of the range, how to handle events near or at the start index, whether to skip a certain number of events at the start of the range, and how to filter the data. | &#x2714; |  |  |
| [Window](#window) | Returns a collection of stored events based on the specified `startIndex` and `endIndex`. |  &#x2714; |  |  |

## Find distinct value

Returns a stored event based on the specified `index` and `searchMode`.

### Request

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data?index={index}&searchMode={searchMode}
```

### Parameters

The following parameters must be defined when querying an SDS stream for a distinct value.

`string index`<br>
The index.

`string searchMode`<br>
The [SdsSearchMode](xref:sdsReadingData#sdssearchmode). The default is `exact`.

### Response

The response includes a status code and a response body containing a serialized collection with one event.

```json
HTTP/1.1 200
Content-Type: application/json

[
    {
        "Time": "2017-11-23T14:00:00Z",
        "State": 0,
        "Measurement": 20
    }
]
```

Depending on the request `index` and `searchMode`, it is possible to have an empty collection returned.

## Filtered

Returns a collection of stored values as determined by a `filter`. The `filter` limits results by applying an expression against event fields. Filter expressions are explained in detail in the [Filter expressions](xref:sdsFilterExpressionsValues) section.

### Request

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data?filter={filter}
```

### Parameters

`string filter`<br>
Filter expression (see [Filter expressions](xref:sdsFilterExpressionsValues)).

### Response

```json
HTTP/1.1 200
Content-Type: application/json

[
    {
        "Time": "2017-11-23T14:00:00Z",
        "Measurement": 20
    },
    {
        "Time": "2017-11-23T15:00:00Z",
        "Measurement": 30
    },
    {
        "Time": "2017-11-23T16:00:00Z",
        "Measurement": 40
    }
]
```

Note that `State` is not included in the JSON as its value is the default value.

### Examples

In the following request example, The events in the stream with `Measurement` greater than 10 are returned.

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data?filter=Measurement gt 10
```

The response returns stream events with a `Measurement` greater than 10.

```json
HTTP/1.1 200
Content-Type: application/json

[
    {
        "Time": "2017-11-23T14:00:00Z",
        "Measurement": 20
    },
    {
        "Time": "2017-11-23T15:00:00Z",
        "Measurement": 30
    },
    {
        "Time": "2017-11-23T16:00:00Z",
        "Measurement": 40
    }
]
```

## Index collection

Returns events at the specified indexes. If no stored event exists at a specified index, the stream's read characteristics determine how the returned event is calculated. For more information, see [Interpolation](xref:sdsReadingData#interpolation) and [Extrapolation](xref:sdsReadingData#extrapolation).

### Request

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Interpolated?index={index}[&index={index}...]
```

### Parameters

``string index``  
One or more indexes.

### Examples

#### Simple stream with continuous interpolation and extrapolation

Consider a stream of type ``Simple`` with the default ``InterpolationMode`` of ``Continuous`` and ``ExtrapolationMode`` of ``All``. In the following request, the specified index matches an existing stored event:

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data/Interpolated?index=2017-11-23T13:00:00Z
```

The response will contain the event stored at the specified index.

```json
HTTP/1.1 200
Content-Type: application/json

[
    {
        "Time": "2017-11-23T13:00:00Z",
        "State": 0,
        "Measurement": 10
    }
]
```

#### Simple stream with an index with no stored event

The following request specifies an index for which no stored event exists:

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data/Interpolated?index=2017-11-23T13:30:00Z
```

Because the index is a valid type for interpolation and the stream has a ``InterpolationMode`` of ``Continuous``, this request receives a response with an event interpolated at the specified index:

```json
HTTP/1.1 200
Content-Type: application/json

[
    {
        "Time": "2017-11-23T13:30:00Z",
        "State": 0,
        "Measurement": 15
    }
]
```

#### Simple stream with discrete interpolation

Consider a stream of type ``Simple`` with an ``InterpolationMode`` of ``Discrete`` and ``ExtrapolationMode`` of ``All``. In the following request, the specified indexes only match two existing stored events:

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data/Interpolated?index=2017-11-23T12:30:00Z&index=2017-11-23T13:00:00Z&index=2017-11-23T14:00:00Z
```

For this request, the response contains events for two of the three specified indexes.

```json
HTTP/1.1 200
Content-Type: application/json

[
    {
        "Time": "2017-11-23T13:00:00Z",
        "State": 0,
        "Measurement": 10
    },
    {
        "Time": "2017-11-23T14:00:00Z",
        "State": 0,
        "Measurement": 20
    }
]
```

## `Interval`

Returns events at evenly spaced intervals based on the specified `startIndex`, `endIndex`, and `count`. If no stored event exists at an index interval, the stream's read characteristics determine how the returned event is calculated. For more information, see [Interpolation](xref:sdsReadingData#interpolation) and [Extrapolation](xref:sdsReadingData#extrapolation).

### Request

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data/Interpolated?startIndex={startIndex}&endIndex={endIndex}&count={count}
```

### Parameters

``string startIndex``  
The index defining the beginning of the window.

``string endIndex``  
The index defining the end of the window.

``int count``  
The number of events to return. Read characteristics of the stream determine how the events are constructed.

### Response

A serialized collection of events is returned with evenly spaced intervals as defined in the request.

```json
HTTP/1.1 200
Content-Type: application/json

[
    {
        "Time": "2017-11-23T13:00:00Z",
        "State": 0,
        "Measurement": 10
    },
    {
        "Time": "2017-11-23T14:00:00Z",
        "State": 0,
        "Measurement": 20
    },
    {
        "Time": "2017-11-23T15:00:00Z",
        "State": 0,
        "Measurement": 30
    }
]
```

## Range

Returns a collection of stored values as determined by a `startIndex` and `count`. Additional optional parameters specify the direction of the range, how to handle events near or at the start index, whether to skip a certain number of events at the start of the range, and how to filter the data.

### Request

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data?startIndex={startIndex}&count={count}[&skip={skip}&reversed={reversed}&boundaryType={boundaryType}&filter={filter}]
```

### Parameters

`string startIndex`<br>
Index identifying the beginning of the series of events to return.

`int count`<br>
The number of events to return.

`int skip`<br>
Optional value specifying the number of events to skip at the beginning of the result.

`bool reversed`<br>
Optional specification of the direction of the request. By default, range requests move forward from `startIndex`, collecting events after `startIndex` from the stream. A reversed request will collect events before `startIndex` from the stream.

`SdsBoundaryType boundaryType`<br>
Optional parameter that specifies the handling of events at or near `startIndex`.

`string filter`<br>
Optional filter expression.

### Response

The response includes a status code and a response body containing a serialized collection of events.

```json
HTTP/1.1 200
Content-Type: application/json

[
    {
        "Time": "2017-11-23T13:00:00Z",
        "Measurement": 10
    },
    {
        "Time": "2017-11-23T14:00:00Z",
        "Measurement": 20
    },
    {
        "Time": "2017-11-23T15:00:00Z",
        "Measurement": 30
    },
    {
        "Time": "2017-11-23T16:00:00Z",
        "Measurement": 40
    }
]
```

Note that `State` is not included in the JSON as its value is the default value.

### Examples

#### Range of 100 events extending forward

This request will return a response with up to 100 events starting at 13:00 and extending forward toward the end of the stream:

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data?startIndex=2017-11-23T13:00:00Z&count=100
```

The response returns the range of events starting from the `startIndex` timestamp. The response has its returned events truncated for brevity.

```json
HTTP/1.1 200
Content-Type: application/json

[
    {
        "Time": "2017-11-23T13:00:00Z",
        "Measurement": 10
    },
    {
        "Time": "2017-11-23T14:00:00Z",
        "Measurement": 10
    },
    ...
]
```

Note that `State` is not included in the JSON as its value is the default value. Further, `Measurement` is not included in the second, 12:00:00, event as zero is the default value for numbers.

#### Range of 100 events reversed

The following request specifies a boundary type of `outside` for a reversed-direction range request. The response will contain up to 100 events. The boundary type Outside indicates that up to one event outside the boundary will be included in the response. For a reverse direction range request, this means one event forward of the specified start index. In a default direction range request, it would mean one event before the specified start index.

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data?startIndex=2017-11-23T13:00:00Z&count=100&reversed=true&boundaryType=2
```

The response returns the 100 events after the start index. The event outside of the index is the next event or the event at 14:00 because the request operates in reverse.

```json
HTTP/1.1 200
Content-Type: application/json

[
    {
        "Time": "2017-11-23T14:00:00Z",
        "State": 0,
        "Measurement": 20
    },
    {
        "Time": "2017-11-23T13:00:00Z",
        "State": 0,
        "Measurement": 10
    },
    {
        "Time": "2017-11-23T12:00:00Z",
        "State": 0,
        "Measurement": 0
    }
]
```

#### Range with filter

Adding a filter to the request means only events that meet the filter criteria are returned:

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data?startIndex=2017-11-23T13:00:00Z&count=100&reversed=true&boundaryType=2&filter=Measurement gt 10
```

The range and order is still in effect, but only events that meet filter criteria are included.

```json
HTTP/1.1 200
Content-Type: application/json

[
    {
        "Time": "2017-11-23T14:00:00Z",
        "State": 0,
        "Measurement": 20
    }
]
```

## Window

Returns a collection of stored events based on the specified `startIndex` and `endIndex`.

For handling events at and near the boundaries of the window, a single `SdsBoundaryType` that applies to both the start and end indexes can be passed with the request, or separate boundary types may be passed for the start and end individually.

Paging is supported for window requests with a large number of events.

To retrieve the next page of values, include the `continuationToken` from the results of the previous request. For the first request, specify a null or empty string for the `continuationToken`.

### Requests

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data?startIndex={startIndex}&endIndex={endIndex}
```

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data?startIndex={startIndex}&endIndex={endIndex}&boundaryType={boundaryType}
```

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data?startIndex={startIndex}&startBoundaryType={startBoundaryType}&endIndex={endIndex}&endBoundaryType={endBoundaryType}
```

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data?startIndex={startIndex}&endIndex={endIndex}&count={count}&continuationToken={continuationToken}
```

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data?startIndex={startIndex}&startBoundaryType={startBoundaryType}&endIndex={endIndex}&endBoundaryType={endBoundaryType}&filter={filter}&count={count}&continuationToken={continuationToken}
```

### Parameters

`string startIndex`<br>
Index bounding the beginning of the series of events to return

`string endIndex`<br>
Index bounding the end of the series of events to return

`int count`<br>
Optional maximum number of events to return. If `count` is specified, a `continuationToken` must also be specified.

`SdsBoundaryType boundaryType`<br>
Optional [SdsBoundaryType](xref:sdsReadingData#sdsboundarytype) specifies handling of events at or near the start and end indexes

`SdsBoundaryType startBoundaryType`<br>
Optional [SdsBoundaryType](xref:sdsReadingData#sdsboundarytype) specifies the first value in the result in relation to the start index. If `startBoundaryType` is specified, `endBoundaryType` must be specified.

`SdsBoundaryType endBoundaryType`<br>
Optional [SdsBoundaryType](xref:sdsReadingData#sdsboundarytype) specifies the last value in the result in relation to the end index. If `startBoundaryType` is specified, `endBoundaryType` must be specified.

`string filter`<br>
Optional [filter expression](xref:sdsFilterExpressionsValues)

`string continuationToken`<br>
Optional token used to retrieve the next page of data. If `count` is specified, a `continuationToken` must also be specified.

### Response

The response includes a status code and a response body containing a serialized collection of events.

A continuation token can be returned if specified in the request.

### Examples

#### Window of events between two timestamps

The following requests all stored events between 12:30 and 15:30:

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data?startIndex=2017-11-23T12:30:00Z&endIndex=2017-11-23T15:30:00Z
```

The response will contain the event stored at the specified index:

```json
HTTP/1.1 200
Content-Type: application/json

[
    {
        "Time": "2017-11-23T13:00:00Z",
        "Measurement": 10
    },
    {
        "Time": "2017-11-23T14:00:00Z",
        "Measurement": 20
    },
    {
        "Time": "2017-11-23T15:00:00Z",
        "Measurement": 30
    }
]
```

Note that `State` is not included in the JSON as its value is the default value.

#### Window of events between two timestamps with a boundary of `Outside`

When the request is modified to specify a boundary type of `Outside`, the value before 13:30 and the value after 15:30 are included:

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data?startIndex=2017-11-23T12:30:00Z&endIndex=2017-11-23T15:30:00Z&boundaryType=2
```

The response includes the windowed events, as well as the two values outside of the `startIndex` and `endIndex`.

```json
HTTP/1.1 200
Content-Type: application/json

[
    {
        "Time": "2017-11-23T12:00:00Z"
    },
    {
        "Time": "2017-11-23T13:00:00Z",
        "Measurement": 10
    },
    {
        "Time": "2017-11-23T14:00:00Z",
        "Measurement": 20
    },
    {
        "Time": "2017-11-23T15:00:00Z",
        "Measurement": 30
    },
    {
        "Time": "2017-11-23T16:00:00Z",
        "Measurement": 40
    }
]
```

Note that `State` is not included in the JSON as its value is the default value.

Further, `Measurement` is not included in the second event (12:00:00) as zero is the default value for numbers.

#### Window of events between two timestamps with mixed boundaries

With a `startBoundary` of `Inside`, only values inside the start boundary (after 13:30) are included in the result. With an end boundary of `Outside`, one value outside the end index (after 15:30) is included:

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data?startIndex=2017-11-23T12:30:00Z&&startBoundaryType=1&endIndex=2017-11-23T15:30:00Z&endBoundaryType=2
```

Example response:

```json
HTTP/1.1 200
Content-Type: application/json

[
    {
        "Time": "2017-11-23T13:00:00Z",
        "State": 0,
        "Measurement": 10
    },
    {
        "Time": "2017-11-23T14:00:00Z",
        "State": 0,
        "Measurement": 20
    },
    {
        "Time": "2017-11-23T15:00:00Z",
        "State": 0,
        "Measurement": 30
    },
    {
        "Time": "2017-11-23T16:00:00Z",
        "State": 0,
        "Measurement": 40
    }
]
```

#### Pagination

To page the results of the request, a `continuationToken` may be specified. This requests the first page of the first two stored events between `startIndex` and `endIndex` by indicating count is 2 and `continuationToken` is an empty string

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data?startIndex=2017-11-23T12:30:00Z&endIndex=2017-11-23T15:30:00Z&count=2&continuationToken=
```

Response:

```json
HTTP/1.1 200
Content-Type: application/json

{
    "Results": [
        {
            "Time": "2017-11-23T13:00:00Z",
            "State": 0,
            "Measurement": 10
        },
        {
            "Time": "2017-11-23T14:00:00Z",
            "State": 0,
            "Measurement": 20
        }
    ],
    "ContinuationToken": "2017-11-23T14:00:00.0000000Z"
}
```

#### Pagination with ContinuationToken

This request uses the continuation token from the previous page to request the next page of stored events:

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data?startIndex=2017-11-23T12:30:00Z&endIndex=2017-11-23T15:30:00Z&count=2&continuationToken=2017-11-23T14:00:00Z
```

Response:

```json
HTTP/1.1 200
Content-Type: application/json

{
    "Results": [
        {
            "Time": "2017-11-23T15:00:00Z",
            "State": 0,
            "Measurement": 30
        }
    ],
    "ContinuationToken": null
}
```

In this case, the results contain the final event. The returned continuation token is null.