---
uid: AssetsSearchAPI
---

# Assets search API
The assets search API allows you to search for your assets with search criteria.

***

## `Search Assets` 
Searches and returns assets matching the search criteria.

### Request 
```text 
GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets?skip={skip}&count={count}&orderby={orderby}&query={queryString}&{filterString}
```

### Parameters  
`string tenantId`  
Tenant identifier.

`string namespaceId`  
Namespace identifier.

`string queryString`  
Asset query string. Search strings are not case sensitive.

`string filterString`  
String used to filter the asset search results. Filter strings are not case sensitive. The strings on which you can filter results are limited to the asset `AssetTypeName` property and the asset metadata properties (using the syntax filter[*property_name*]=*property_value*).

[optional] `int skip`   
Optional parameter representing the zero-based offset of the first asset to retrieve. If not specified, a default value of 0 is used.

[optional] `int count`   
Optional parameter, between 1 and 1000 (inclusive), that represents the maximum number of assets to retrieve. If not specified, the default is 100.

[optional] `[id|name] [asc|desc|] orderby`  
Optional parameter which returns assets ordered either by the asset `Id` or the asset `Name`. Specify `asc` or `desc` to return the results in ascending or descending order. If not specified, the default is ascending order.

### Response 
Returns an array of assets matching the search query and the total number of assets returned specified as `Total-Count` in the HTTP response header. 

| Status Code | Body Type | Description |
|--|--|--|
| 200 OK | Asset list | A list of assets matching the search criteria. An empty array is returned if there are no matching assets. |
| 204 OK | empty | No assets match your search criteria. |
| 400 Bad Request | error | The request is not valid. See the response body for additional details. |
| 403 Forbidden | error | You are not authorized to view the requested asset. |


## `Search Matched Fields Asset` 
Searches all assets and returns a list of asset identifiers and their matched fields. Use this API to identify the fields in the asset that match your query string.

### Request 
```text 
GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Search/Assets?skip={skip}&count={count}&orderby={orderby}&query={queryString}&{filterString}
```

### Parameters  
`string tenantId`  
Tenant identifier

`string namespaceId`  
Namespace identifier

`string queryString`  
Asset query string. Search strings are not case-sensitive.

`string filterString`  
String used to filter the asset search results. Filter strings are not case sensitive. The strings on which you can filter results are limited to the asset `AssetTypeName` property and the asset metadata properties (using the syntax filter[*property_name*]=*property_value*).

[optional] `int skip`   
Optional parameter representing the zero-based offset of the first asset to retrieve. If not specified, a default value of 0 is used.

[optional] `int count`   
Optional parameter, between 1 and 1000 (inclusive), representing the maximum number of retrieved assets. If not specified, the default is 100.

[optional] `[id|name] [asc|desc|] orderby`  
Optional parameter which returns assets ordered either by the asset `Id` or the asset `Name`. Specify `asc` or `desc` to return the results in ascending or descending order. If not specified, the default is ascending order.

### Response 
A list of asset Ids and their matched fields.

| Status Code | Body Type | Description |
|--|--|--|
| 200 OK | Asset list | A list of assets matching the search criteria. An empty array is returned if there are no matching assets. |
| 204 OK | empty | No assets match your search criteria. |
| 400 Bad Request | error | The request is not valid. See the response body for additional details. |
| 403 Forbidden | error | You are not authorized to view the requested asset. |

## `Asset Faceted Search` 

Asset faceted search allows for searching using asset facets. Asset facets are not case sensitive.  Only asset metadata can be used in asset faceted searches.

### Request 

```text 
GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Search/Assets/Facets?name={category}&count={count}
```

### Parameters  

`string tenantId`  
Tenant identifier

`string namespaceId`  
Namespace identifier

`string name`  
Name of the asset metadata for which you want to retrieve the facet values.

[optional] `int count`   
Optional parameter, between 1 and 1000 (inclusive), representing the maximum number of retrieved assets. If not specified, the default is 100.

### Response 

A list of asset Ids and their matched fields.

| Status Code     | Body Type        | Description                                                  |
| --------------- | ---------------- | ------------------------------------------------------------ |
| 200 OK          | Asset facet list | A list of asset facet values that match the search criteria. An empty array is returned if there are no matching asset metadata with the supplied category. |
| 204 OK          | empty            | No assets match your search criteria.                        |
| 400 Bad Request | error            | The request is not valid. See the response body for additional details. |


## `Asset Autocomplete` 

Asset autocomplete allows you to query assets and retrieve a list of suggested assets based on your search criteria. The autocomplete feature can be used with the following asset properties:

-  Name
-  Description
-  AssetTypeName
-  Metadata

### Request 

```text 
GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Search/Assets/Autocomplete?term={term}&facetCount={facetCount}&termCount={termCount}
```

### Parameters  

`string tenantId`  
Tenant identifier

`string namespaceId`  
Namespace identifier

`string term`  
Search term that you want to search for.

[optional] `int facetCount`  
Maximum number of facet autocompleted items to return. The default is 0 which means you will not get any facet suggestions.

[optional] `int termCount`  
Maximum number of token autocompleted items to return. The default is 0 which means you will not get any token suggestions.