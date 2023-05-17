---
uid: data-view-api-console-use
---

# Data view API Console use

While creating or editing a data view, you can use the AVEVA Data Hub API Console to build, edit, and preview the data view endpoint configuration before specifying its URI in your application code or Microsoft Power BI.

## Data view API console parameters

When viewing a data view from the API Console, you can edit the default parameters that you configured during initial creation of the data view. Additionally, you can provide continuation tokens (in support of data pagination), caching data, or choosing different support response formats.

| Field | Description |
|--|--|
| startIndex | The inclusive start boundary of the data view data. |
| endIndex | The inclusive end boundary of the data view data |
| count | The number of data points included in the request. |
| interval | The requested interval between index values. |
| continuationToken | The field for specifying a continuation token when a request returns. For more information on this field and the **Load from Response** button, see [Continuation token](#continuation-token). |
| cache | The field for setting cache behavior. Values include: <ul><li><code>Preserve</code> (default): Uses cached information, if available.</li><li><code>Refresh</code>: Forces the resource to re-resolve.</li></ul> |
| form | The file format that request responses are returned. For information on the response forms available, see [Response forms](#response-forms). |

## Continuation token

The continuation token field is used in support of server-side pagination. A continuation token is a mechanism used to handle large amounts of data efficiently. When you request data from a data view using the AVEVA Data Hub REST API, there might be too many results to retrieve all at once. To address this, the API provides you with a subset of the data and a continuation token.

The continuation token serves as a marker or reference point that helps you keep track of your progress and indicates where you left off. When you want to fetch the next portion of the data, you include the continuation token in your subsequent API request. Continuation tokens are only supported for `GET` requests.

When the **Load from Response** button is enabled, the continuation token from the last API console data view request is loaded into the `continuationToken` field automatically. The continuation token will be loaded from the response when all of the following conditions are met:

- The request verb is `GET`.
- There is a response present.
- The current response verb, path, and query parameters (excluding the `continuationToken`) all match the current request.

## Response forms

<!-- TODO: define -->