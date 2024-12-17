---
title: SDS data query methods
uid: SdsDataQueryMethods
---

# SDS data query methods

When using <xref:sds-stream-data#list-values-account-path> or <xref:sds-stream-data#list-values-tenants-path> to query for data, there are several methods of retrieval:

- [Find distinct value](#find-distinct-value)
- [Filtered](#filtered)
- [Range](#range)
- [Window](#window)

## Find distinct value

Returns a stored event based on the specified `index` and `searchMode`.

### Request

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data?index={index}&searchMode={searchMode}
```

#### Parameters

`string index`<br>
The index.

`string searchMode`<br>
The [SdsSearchMode](xref:sdsReadingData#sdssearchmode). The default is `exact`.

### Response

The response includes a status code and a response body containing a serialized collection with one event.

Depending on the request `index` and `searchMode`, it is possible to have an empty collection returned.

#### Example request

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data?index=2017-11-23T13:00:00Z&searchMode=Next
```

The request has an index that matches the index of an existing event, but since a `SdsSearchMode` of `next` was specified, the response contains the next event in the stream after the specified index.

#### Example response body

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

#### Example request

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data?index=2017-11-23T13:30:00Z&searchMode=Next
```

The request specifies an index that does not match an index of an existing event. The next event in the stream is retrieved.

#### Example response body

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

## Filtered

Returns a collection of stored values as determined by a `filter`. The `filter` limits results by applying an expression against event fields. Filter expressions are explained in detail in the [Filter expressions](xref:sdsFilterExpressions) section.

### Request

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data?filter={filter}
```

#### Parameters

`string filter`<br>
Filter expression (see [Filter expressions](xref:sdsFilterExpressions)).

#### Example request

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data?filter=Measurement gt 10
```

The events in the stream with `Measurement` greater than 10 are returned.

#### Example response body

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

## Range

Returns a collection of stored values as determined by a `startIndex` and `count`. Additional optional parameters specify the direction of the range, how to handle events near or at the start index, whether to skip a certain number of events at the start of the range, and how to filter the data.

### Request

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data?startIndex={startIndex}&count={count}[&skip={skip}&reversed={reversed}&boundaryType={boundaryType}&filter={filter}]
```

#### Parameters

`string startIndex`<br>
Index identifying the beginning of the series of events to return.

`int count`<br>
The number of events to return.

`int skip`<br>
Optional value specifying the number of events to skip at the beginning of the result.

`bool reversed`<br>
Optional specification of the direction of the request. By default, range requests move forward from `startIndex`, collecting events after `startIndex` from the stream. A reversed request will collect events before `startIndex` from the stream.

`SdsBoundaryType boundaryType`<br>
Optional SdsBoundaryType specifies the handling of events at or near `startIndex`.

`string filter`<br>
Optional filter expression.

### Response

The response includes a status code and a response body containing a serialized collection of events.

#### Example request

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data?startIndex=2017-11-23T13:00:00Z&count=100
```

This request will return a response with up to 100 events starting at 13:00 and extending forward toward the end of the stream:

#### Example response body

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

#### Example request

To reverse the direction of the request, set reversed to true. The following request will return up to 100 events starting at 13:00 and extending back toward the start of the stream:

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data?startIndex=2017-11-23T13:00:00Z&count=100&reversed=true
```

#### Example response body

```json
HTTP/1.1 200
Content-Type: application/json

[
    {
        "Time": "2017-11-23T13:00:00Z",
        "Measurement": 10
    },
    {
        "Time": "2017-11-23T12:00:00Z"
    }
]
```

Note that `State` is not included in the JSON as its value is the default value.

Further, `Measurement` is not included in the second, 12:00:00, event as zero is the default value for numbers.

The following request specifies a boundary type of Outside for a reversed-direction range request. The response will contain up to 100 events. The boundary type Outside indicates that up to one event outside the boundary will be included in the response. For a reverse direction range request, this means one event forward of the specified start index. In a default direction range request, it would mean one event before the specified start index.

#### Example request

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data?startIndex=2017-11-23T13:00:00Z&count=100&reversed=true&boundaryType=2
```

#### Example response body

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

The event outside of the index is the next event or the event at 14:00 because the request operates in reverse.

#### Example request

Adding a filter to the request means only events that meet the filter criteria are returned:

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data?startIndex=2017-11-23T13:00:00Z&count=100&reversed=true&boundaryType=2&filter=Measurement gt 10
```

#### Example response body

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

For handling events at and near the boundaries of the window, a single SdsBoundaryType that applies to both the start and end indexes can be passed with the request, or separate boundary types may be passed for the start and end individually.

Paging is supported for window requests with a large number of events.

To retrieve the next page of values, include the `continuationToken` from the results of the previous request. For the first request, specify a null or empty string for the `continuationToken`.

### Requests

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data?startIndex={startIndex}&endIndex={endIndex}

GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data?startIndex={startIndex}&endIndex={endIndex}&boundaryType={boundaryType}

GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data?startIndex={startIndex}&startBoundaryType={startBoundaryType}&endIndex={endIndex}&endBoundaryType={endBoundaryType}

GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data?startIndex={startIndex}&endIndex={endIndex}&count={count}&continuationToken={continuationToken}

GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data?startIndex={startIndex}&startBoundaryType={startBoundaryType}&endIndex={endIndex}&endBoundaryType={endBoundaryType}&filter={filter}&count={count}&continuationToken={continuationToken}
```

#### Parameters

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
Optional [filter expression](xref:sdsFilterExpressions)

`string continuationToken`<br>
Optional token used to retrieve the next page of data. If `count` is specified, a `continuationToken` must also be specified.

### Response

The response includes a status code and a response body containing a serialized collection of events.

A continuation token can be returned if specified in the request.

#### Example request

The following requests all stored events between 12:30 and 15:30:

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data?startIndex=2017-11-23T12:30:00Z&endIndex=2017-11-23T15:30:00Z
```

The response will contain the event stored at the specified index:

#### Example response body

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

#### Example request

When the request is modified to specify a boundary type of Outside, the value before 13:30 and the value after 15:30 are included:

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data?startIndex=2017-11-23T12:30:00Z&endIndex=2017-11-23T15:30:00Z&boundaryType=2
```

#### Example response body

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

#### Example request

With a start boundary of Inside, only values inside the start boundary (after 13:30) are included in the result. With an end boundary of Outside, one value outside the end index (after 15:30) is included:

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data?startIndex=2017-11-23T12:30:00Z&&startBoundaryType=1&endIndex=2017-11-23T15:30:00Z&endBoundaryType=2
```

#### Example response body

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

#### Example request

In order to page the results of the request, a continuation token may be specified. This requests the first page of the first two stored events between `startIndex` and `endIndex` by indicating count is 2 and `continuationToken` is an empty string:

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data?startIndex=2017-11-23T12:30:00Z&endIndex=2017-11-23T15:30:00Z&count=2&continuationToken=
```

##### Example response body

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

#### Example request

This request uses the continuation token from the previous page to request the next page of stored events:

```text
GET api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/Simple/Data?startIndex=2017-11-23T12:30:00Z&endIndex=2017-11-23T15:30:00Z&count=2&continuationToken=2017-11-23T14:00:00Z
```

#### Example response body

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
