---
uid: AssetStatus
---

# Asset and Asset Type Status

***

## `Get Asset Status`

Returns the status of an asset. 

The status of an asset is determined by an exact match of the SDS stream property value to the value of the `ValueStatusMappings`. If there are no exact matches, the status is a 0 (Unknown).


### Request

```text 
GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/Status/Last
```

### Parameters

`string tenantId`  
Tenant identifier

`string namespaceId`  
Namespace identifier

`string assetId`  
Asset identifier

### Response

The response includes a status code and a response body.
| Status Code       | Body Type    | Description                                                  |
| ----------------- | ------------ | ------------------------------------------------------------ |
| 200 OK            | Asset status | The asset status is returned.                                |
| 400 Bad Request   | error        | The request is not valid. See the response body for additional details. |
| 403 Forbidden     | error        | You are not authorized to view the requested asset.          |
| 404 Not Found     | error        | The specified asset with identifier is not found.            |
| 422 Invalid State | error        | See the response body for details.                           |

#### Example response body

```
HTTP 200 OK
Content-Type: application/json
{
	"AssetId": "TemperatureSensorAsset",
	"Status": 1,
	"Value": "85",
    "DisplayName": "TemperatureSensorBuild1InF",
    "DataRetrievalTime": "2020-05-04T16:55:26.3732693Z",
    "Index": "2020-05-04T16:55:28.00001Z"
}
```

***

## `Asset Status Range Summary`

Returns the status summary of an asset.

Statistics are computed using 'StepwiseContinuousLeading' for interpolation and ‘Forward’ for extrapolation with regard to the status stream property, without regard to the actual interpolation or extrapolation modes configured in SDS for that property.

### Request

```text 
POST api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/Status/Summary
?startIndex={startIndex}&endIndex={endIndex}&intervals={intervals}
```

### Parameters

`string tenantId`  
Tenant identifier

`string namespaceId`  
Namespace identifier

`string assetId`  
Asset identifier

`string startIndex`  
Start index

`string endIndex`  
End index

`string intervals`  
Number of intervals

### Response

The response includes a status code and a response body.

| Status Code       | Body Type    | Description                                                  |
| ----------------- | ------------ | ------------------------------------------------------------ |
| 200 OK            | Asset status summary | The asset status summary is returned.                                |
| 400 Bad Request   | error        | The request is not valid. See the response body for additional details. |
| 403 Forbidden     | error        | You are not authorized to view the requested asset.          |
| 404 Not Found     | error        | The specified asset with identifier is not found.            |
| 422 Invalid State | error        | See the response body for details.                           |

#### Example response body

```
HTTP 200 OK
Content-Type: application/json
{
  "RangeValues": [
    {
      "Index": "2019-01-02T00:00:00Z",
      "Status": "Warning",
      "Value": 2,
      "DisplayName": "AssetInWarning"
    },
    {
      "Index": "2019-01-02T00:30:00Z",
      "Status": "Bad",
      "Value": 4,
      "DisplayName": "AssetInBadState"
    }
  ],
  "Statistics": [
    {
      "Status": "Warning",
      "TotalInterval": "00:30:00",
      "Values": [
        {
          "Value": 2,
          "Interval": "00:30:00"
        }
      ]
    },
    {
      "Status": "Bad",
      "TotalInterval": "1246.06:30:00",
      "Values": [
        {
          "Value": 4,
          "Interval": "1246.06:30:00"
        }
      ]
    }
  ]
}
```


***

## `Bulk Asset Status`

Returns the status of multiple assets.

### Request

```text 
POST api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Bulk/Assets/Status/Last
```

### Parameters

`string tenantId`  
Tenant identifier

`string namespaceId`  
Namespace identifier

#### Example POST body

Lists the asset identifiers whose status you are interested in.

```
Content-Type: application/json
[
   "AssetId-1",
   "AssetId-2",
   "AssetId-3"
]
```

### Response

The response includes a status code and a response body.

| Status Code      | Body Type         | Description                                                  |
| ---------------- | ----------------- | ------------------------------------------------------------ |
| 200 OK           | Asset status list | Returns the status of multiple assets. |
| 207 Multi Status | Multi Status      | Partial success. Not all assets were able to be resolved. See response body for additional details. |

#### Example response body

```
HTTP 200 OK
Content-Type: application/json
{
   [
      {
         "AssetId": "AssetId-1",
         "Status": 1, 
         "Value": "85",
         "DisplayName": "TemperatureSensorBuild1InF",
         "DataRetrievalTime": "2020-05-04T16:55:26.3732693Z",
         "Index": "2020-05-04T16:55:28.00001Z"
      },
      {
         "AssetId": "AssetId-2",
         "Status": 2, 
         "Value": "185",
         "DisplayName": "DeviceMeasurement",
         "DataRetrievalTime": "2020-05-04T16:55:26.3732693Z"
         "Index": "2020-05-04T16:55:29.00001Z"
      },
      {
         "AssetId": "AssetId-3",
         "Status": 1, 
         "Value": "75",
         "DisplayName": "TemperatureSensorBuild5450InF",
         "DataRetrievalTime": "2020-05-04T16:55:26.3732693Z"
         "Index": "2020-05-04T16:55:30.00001Z"
      }
   ]
}
```
