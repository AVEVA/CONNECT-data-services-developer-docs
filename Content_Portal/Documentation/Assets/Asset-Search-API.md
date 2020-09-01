# Assets Search API
The assets search API allows you to search for your assets with search criteria.

***
## `Get Assets by Search Criteria` 
Returns an array of assets that meet the search criteria.

### Searchable Properties
Assets can be searched on the following asset properties:

- Id
- Name
- Description
- Attributes
  - Name
  - Description
  - Value
- AssetTypeName
- AssetTypeId
- Measurement Name

Search criteria can be chained together using an **AND**. See examples below. 


### Request 
```text 

GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets?skip={skip}&count={count}&query={queryString} 

```

### Parameters  
`string tenantId` 

The tenant identifier

`string namespaceId` 

The namespace identifier

[Optional] `int skip` 

An optional parameter representing the zero-based offset of the first asset to retrieve. If not specified, a default value of 0 is used.

[Optional] `int count` 

An optional parameter representing the maximum number of assets to retrieve. If not specified, a default value of 100 is used.

`string queryString`
The asset query string

### Response 
The response includes a status code and an array of assets matching the search criteria.

| Status Code | Body Type | Description |
|--|--|--|
| 200 OK | `Asset[]` | An array of assets matching the search criteria. An empty array is returned if there are no matching assets. |
| 400 Bad Request | error | The request is not valid. See the response body for additional details. |
| 403 Forbidden | error | You are not authorized to view the requested asset. |

### Example Asset Queries

| Query String                   | Description                                                  |
| ------------------------------ | ------------------------------------------------------------ |
| Id:Id1                         | Returns the asset with ID equal to **Id1**.                  |
| Id:Id*                         | Returns all assets with ID matching **id*** wildcard. [QUESTION: Is search case-sensitive?] |
| Name:Name1                     | Returns all asset with a friendly name equal to **Name1**. [QUESTION: What is a friendly name?] |
| Id:Id AND Name:Name1           | Returns all assets with ID matching the **id*** wildcard and with a friendly name equal to **Name1**. |
| AssetTypeName:AssetType Heater | Returns all assets with an asset type name that is equal to **AssetTypeHeater**. |
| Description:floor1*            | Returns all assets with a description that starts with **floor1**. |
| floor1*                        | Returns all assets with a description that starts with **floor1**. |
| Attributes/Name:Building*      | Returns all assets with at least one attribute description that contains the string **Building**. |
| Attributes/Description:heater* | Returns all assets with at least one attribute description that starts with **heater**. |
| Attributes/Value:123           | Returns all assets with at least one attribute that equals **123**. |
| Id:X* AND Attributes/Name:B*   | Returns all assets with ID starting with **X** and containing at least one attribute with a name that starts with a **B**. |
| References/Name:measurement*   | Returns all assets with an ID starting with the string **measurement**. |
| References/Description: test*  | Returns all assets with at least one reference description that starts with the string **test**. |
| References/Value:PI            | Returns all assets with at least one reference value stream ID, stream view ID, or type ID containing the string **PI**. |
| References/Properties:code     | Returns all assets with at least one reference value's stream code object containing with the stream ID contains a stream property contain "code." [QUESTION: I don't understand this one.] |

