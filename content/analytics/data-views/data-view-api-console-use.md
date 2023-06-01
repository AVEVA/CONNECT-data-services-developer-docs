---
uid: data-view-api-console-use
---

# Data views and the API Console

While creating or editing a data view, you can launch it within the API Console by choosing the **View in API Console** button. Launching the data view in the API console allows you to refine the data view endpoint query before specifying its URI in your application code or Microsoft Power BI.

## Data view API console parameters

When viewing a data view from the API Console, you can edit the default parameters that you configured during initial creation of the data view. Additionally, you can provide continuation tokens (in support of data pagination), caching data, or choosing different support response formats.

| Field | Description |
|--|--|
| startIndex | The inclusive start boundary of the data view data. |
| endIndex | The inclusive end boundary of the data view data |
| count | The number of data points included in the request. |
| interval | The requested interval between index values. |
| continuationToken | The field for specifying a continuation token when a request returns. For more information on this field and the **Load from Response** ![load from response](../../_icons/branded/book-arrow-right-outline.svg) button, see [Continuation token](#continuation-token). |
| cache | The field for setting cache behavior. Values include: <ul><li><code>Preserve</code> (default): Uses cached information, if available.</li><li><code>Refresh</code>: Forces the resource to re-resolve.</li></ul> |
| form | The file format that request responses are returned. For information on the response forms available, see [Response forms](#response-forms). |

## Continuation token

The continuation token field is used in support of server-side pagination. A continuation token is a mechanism used to handle large amounts of data efficiently. When you request data from a data view using the AVEVA Data Hub REST API, there might be too many results to retrieve all at once. To address this, the API provides you with a subset of the data and a continuation token.

When the **Load from Response** ![load from response](../../_icons/branded/book-arrow-right-outline.svg) button is enabled, the continuation token from the last API console data view request is loaded into the `continuationToken` field automatically. For more information, see <xref:apiConsole#continuation-token>.

## Response forms

When requesting data views from the API Console, the REST API is capable of returning requests in a variety of file formats. Select a form from the dropdown. Supported response forms include:

| Form | Description |
|--|--|
| default (JSON) | Object-style JSON. |
| table (Table) | Table-style JSON. |
| tableh (Table with headers) | Table-style JSON with header row. |
| csv (Comma separated values) | Comma-separated values. |
| csvh (Comma separated values with headers) | Comma-separated values with header row. |
| parquet | Parquet format. For more information on the Parquet format, see <xref:data-views-parquet-format>. |
