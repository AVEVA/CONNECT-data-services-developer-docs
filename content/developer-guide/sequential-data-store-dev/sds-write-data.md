---
uid: sdsWritingData
---

# Write data

The SDS REST APIs provide programmatic access to read and write SDS data. This section describes things to note when writing to an SdsStream.

When working in .NET, convenient SDS Client libraries are available. The `ISdsDataService` interface, accessed using the `SdsService.GetDataService()` helper, defines the available functions.

All writes rely on a stream's key or primary index. The primary index determines the order of events in the stream. Secondary indexes are updated, but they do not contribute to the request. All references to indexes are to the primary index.

The maximum size of the payload for a single write request is 28.6 MB. Additionally, compressed requests are limited to a maximum inflated payload size of 190 MB. Requests that exceed these limits will be rejected with an HTTP status code of `413 Payload Too Large`.

> [!NOTE] Use the ISO 8601 representation of dates and times in SDS, `2020-02-20T08:30:00-08:00` for February 20, 2020 at 8:30 AM PST, for example. SDS returns timestamps in UTC if the timestamp is of property `DateTime` and in local time if it is of `DateTimeOffset`.

## Single stream writes

The following methods support writing a single or multiple values:

- [Insert Values](xref:sds-stream-data#insert-values) inserts a collection of events.
- [Patch Values](xref:sds-stream-data#patch-values) updates specific fields for a collection of events.
- [Remove Values](xref:sds-stream-data#remove-values) deletes the events based on the request parameters.
- [Update Values](xref:sds-stream-data#update-values) add or replaces a collection of events.

### Request body format

With the exception of Remove Values, all single stream write calls require a request body containing the events to insert or modify.

The events must be formatted as a serialized JSON array of the stream's type. JSON arrays are comma-delimited lists of a type enclosed within square brackets. The following code shows a list of three WaveData events that are properly formatted for insertion. See the [AVEVA Data Hub-Samples](https://github.com/osisoft/OSI-Samples-ADH) for the complete example.

```json
[
  {
    "Order": 2,
    "Tau": 0.25722883666666846,
    "Radians": 1.6162164471269089,
    "Sin": 1.9979373673043652,
    "Cos": -0.090809010174665111,
    "Tan": -44.003064529862513,
    "Sinh": 4.8353589272389,
    "Cosh": 5.2326566823391856,
    "Tanh": 1.8481468289554672
  },
  {
    "Order": 4,
    "Tau": 0.25724560000002383,
    "Radians": 1.6163217742567466,
    "Sin": 1.9979277915696148,
    "Cos": -0.091019446679060964,
    "Tan": -43.901119254534827,
    "Sinh": 4.8359100947709592,
    "Cosh": 5.233166005842703,
    "Tanh": 1.8481776000882766
  },
  {
    "Order": 6,
    "Tau": 0.25724560000002383,
    "Radians": 1.6163217742567466,
    "Sin": 1.9979277915696148,
    "Cos": -0.091019446679060964,
    "Tan": -43.901119254534827,
    "Sinh": 4.8359100947709592,
    "Cosh": 5.233166005842703,
    "Tanh": 1.8481776000882766
  }
]
```

You can serialize your data using one of many available JSON serializers available at [Introducing JSON](http://json.org/index.html).

## Indexes

Writing to the SDS relies on the primary index for positioning within the streams and locating existing events. Most writes use the index as specified by the value. Deletes are the exception to this rule. When deleting, indexes are specified as strings in the URI, or, when using the SDS Client Libraries, the index may be passed as-is to DELETE methods that take the index type as a generic argument. For more information on working with indexes, see [Indexes](xref:sdsIndexes). For information on compound indexes, see [Compound indexes](xref:sdsIndexes#compound-indexes).

## Out-of-Order Data

Sequential Data Store is optimized for sending and retrieving data in order of the data's index. When writing data, clients should take care to send it in a sequential manner. Failure to do so can drastically impact performance both when it is being written and when it is later retrieved. This is especially pertinent when backfilling large amounts of historical data. Note that "sequential order" is desirable not just within the context of one batch that is sent, but also in a general sense over time.

---
