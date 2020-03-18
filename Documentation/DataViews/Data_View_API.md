---
uid: DataViewAPI
---

# Data View API

The `DataView` API provides mechanisms to create, read, update, and delete data views. This is one portion of the whole [data views API](xref:DataViewsAPIOverview).

For a description of the `DataView` object type, see the [DataView documentation](xref:DataView).

Other sections of documentation describe how to [secure data views](xref:DataViewsSecuringDataViews) by setting their ownership and permissions, and the corresponding [API](xref:DataViewsAccessControlAPI).


## `Get Data View`
Returns the specified data view.

### Request
```text
GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/{dataViewId}
```
### Parameters
`string tenantId`  
The tenant identifier

`string namespaceId`  
The namespace identifier

`string dataViewId`  
The data view identifier

### Response
The response includes a status code and a response body.

| Status code | Body Type | Description |
|--|--|--|
| 200 OK | `DataView` | The requested data view |
| 400 Bad Request | error | The request is not valid. See the response body for details |
| 403 Forbidden | error | You are not authorized to view the requested data view |
| 404 Not Found | error | The specified data view identifier is not found |
| 500 Internal Server Error | error | An error occurred while processing the request. See the response body for details |

#### Example response body
```json
HTTP 200 OK
Content-Type: application/json
{
  "Id": "demo",
  "Name": "demo",
  "Description": null,
  "Queries": [
    { 
      "Id": "weather",
      "Value":"*weather*" 
    }
  ],
  "DataFieldSets": [],
  "GroupingFields": [],
  "Shape": "Standard",
  "IndexField": { "Label": "Timestamp" },
  "IndexTypeCode": "DateTime"
}
```

## `Get Data Views`
Returns a list of data views.

### Request
```text
GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews?skip={skip}&count={count}
```
### Parameters
`string tenantId`  
The tenant identifier

`string namespaceId`  
The namespace identifier

`[optional] int skip`  
An optional parameter representing the zero-based offset of the first data view to retrieve. If not specified, a default value of 0 is used.

`[optional] int count`  
An optional parameter representing the maximum number of data views to retrieve. If not specified, a default value of 100 is used.

### Response
The response includes a status code and a body.

| Status code | Body Type | Description |
|--|--|--|
| 200 OK | `DataView[]` | A page of data views. A response header, `Total-Count`, indicates the total size of the collection. |
| 400 Bad Request | error | The request is not valid. See the response body for details |
| 500 Internal Server Error | error | An error occurred while processing the request. See the response body for details |

#### Response headers
Successful (200 OK) responses include:

| Header | Description |
|--|--|
| Total-Count | The total count of data views visible to the current user |

#### Example response body
```json
HTTP 200 OK
Content-Type: application/json
[
  {
    "Id": "demo view 1",
    ... etc.
  },
  {
    "Id": "demo view 2",
    ... etc.
  }
]
```

## `Create Data View`
Create a new data view with a system-generated identifier.
### Request
```text
POST api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews
```
### Parameters
`string tenantId`  
The tenant identifier

`string namespaceId`  
The namespace identifier

### Request body
A `DataView` object whose `Id` is `null` or unspecified.

#### Example request body
```json
{
  "Name": "demo",
  "Description": "demonstration",
  "Queries": [],
  "DataFieldSets": [],
  "GroupingFields": [],
  "Shape": "Standard",
  "IndexField": { "Label": "Timestamp" },
  "IndexTypeCode": "DateTime"
}
```

### Response
The response includes a status code and a body.

| Status code | Body Type | Description |
|--|--|--|
| 201 Created | `DataView` | The data view as persisted, including values for optional parameters that were omitted in the request. |
| 400 Bad Request | error | The request is not valid. See the response body for details |
| 403 Forbidden | error | You are not authorized to create a data view |
| 500 Internal Server Error | error | An error occurred while processing the request. See the response body for details |

#### Example response body
```json
HTTP 200 OK
Content-Type: application/json
{
  "Id": "c79630cc-21dc-483e-8b37-46880e92c456",
  "Name": "demo",
  "Description": "demonstration",
  "Queries": [],
  "DataFieldSets": [],
  "GroupingFields": [],
  "Shape": "Standard",
  "IndexField": { "Label": "Timestamp" },
  "IndexTypeCode": "DateTime"
}
```

## `Get or Create Data View`
This call creates the specified data view. If a data view with the same id already exists, the existing data view is compared with the specified data view. If they are identical, a redirect (`302 Found`) is returned with the `Location` response header indicating the URL where the stream may be retrieved using a Get function. If the data views do not match, the request fails with `409 Conflict`.

### Request
```text
POST api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/{dataViewId}
```
### Parameters
`string tenantId`  
The tenant identifier

`string namespaceId`  
The namespace identifier

`string dataViewId`  
The data view identifier

### Request body
A `DataView` object whose `Id` matches the `dataViewId` in the URL.

#### Example request body
```json
{
  "Id": "demo2",
  "Name": "demo2",
  "Description": "demonstration 2",
  "Queries": [],
  "DataFieldSets": [],
  "GroupingFields": [],
  "Shape": "Standard",
  "IndexField": { "Label": "Timestamp" },
  "IndexTypeCode": "DateTime"
}
```

### Response
The response includes a status code and, in most cases, a body.

| Status code | Body Type | Description |
|--|--|--|
| 201 Created | `DataView` | The data view as persisted, including values for optional parameters that were omitted in the request. |
| 302 Found | (empty) | The specified data view already exists. A response header, `Location`, indicates the URL where the data view may be retrieved with the `GET` verb
| 400 Bad Request | error | The request is not valid. See the response body for details |
| 403 Forbidden | error | You are not authorized for this operation
| 409 Conflict | error | The specified data view conflicts with an existing data view that is not identical. To forcibly update the data view, see *Create Or Update Data View*
| 500 Internal Server Error | error | An error occurred while processing the request. See the response body for details |

#### Example response body

```json
HTTP 201 Created
Content-Type: application/json
{
  "Id": "demo2",
  "Name": "demo2",
  "Description": "demonstration 2",
  "Queries": [],
  "DataFieldSets": [],
  "GroupingFields": [],
  "Shape": "Standard",
  "IndexField": { "Label": "Timestamp" },
  "IndexTypeCode": "DateTime"
}
```

## `Create or Update Data View`
If a data view with the same id already exists, it is updated to the specified value. Otherwise, a new data view is created.

### Request
```text
PUT api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/{dataViewId}
```
### Parameters
`string tenantId`  
The tenant identifier

`string namespaceId`  
The namespace identifier

`string dataViewId`  
The data view identifier

### Request body
A `DataView` object whose `Id` matches the `dataViewId` in the URL.

#### Example request body
```json
{
  "Id": "demo",
  "Name": "demo",
  "Description": "demonstration",
  "Queries": [],
  "DataFieldSets": [],
  "GroupingFields": [],
  "Shape": "Standard",
  "IndexField": { "Label": "Timestamp" },
  "IndexTypeCode": "DateTime"
}
```

### Response
The response includes a status code and, in some cases, a body.

| Status code | Body Type | Description |
|--|--|--|
| 201 Created | `DataView` | The data view as persisted, including values for optional parameters that were omitted in the request |
| 204 No Content | (empty) | Successfully updated the data view |
| 400 Bad Request | error | The request is not valid. See the response body for details |
| 403 Forbidden | error | You are not authorized for this operation |
| 500 Internal Server Error | error | An error occurred while processing the request. See the response body for details |

## `Delete Data View`
Delete the data view with the specified id.

### Request
```text
DELETE api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/{dataViewId}
```
### Parameters
`string tenantId`  
The tenant identifier

`string namespaceId`  
The namespace identifier

`string dataViewId`  
The data view identifier

### Response
The response includes a status code and, in some cases, a body.

| Status code | Body Type | Description |
|--|--|--|
| 204 No Content | (empty) | Successfully deleted the data view |
| 400 Bad Request | error | The request is not valid. See the response body for details |
| 403 Forbidden | error | You are not authorized for this operation |
| 404 Not Found | error | The specified data view identifier is not found |
| 500 Internal Server Error | error | An error occurred while processing the request. See the response body for details |
