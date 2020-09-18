---
uid: AssetCentricDataAPI
---

# Asset-Centric Data API
The Asset-Centric Data API provides a quick way to take the dynamic data stored in SDS streams and store it as references within a given asset.

### Example Asset
The following asset is used in all of the sample output in this topic.
```
{
    "Id": "IDsample",
    "Name": "SampleForDemo",
    "Description": "This is a demo asset.",
    "Attributes": [
        {
            "Name": "RoomLocation",
            "Description": "This is what room number the asset is located.",
            "SdsTypeCode": 14,
            "Value": 1.0
        }
    ],
    "References": [
            {
            "Id": "IDsample",
            "Name": "SampleForDemo",
            "Description": "This is a demo asset.",
            "Metadata": [
            {
            "Name": "RoomLocation",
            "Description": "This is what room number the asset is located.",
            "SdsTypeCode": 14,
            "Value": 1.0
            }
            ],
            "StreamReferences": [
            {
            {
            "Id": "StreamRefId",
            "Description": "This is the sample data from the room.",
            "StreamId": "PI_buildingMachine_1112"
            }
            }
            ]
            }
            "Value": {
                "StreamId": "PI_buildingMachine_1112",
                "TypeId": "PI-Float32"
            }
        },
        {
            "Name": "SampleView",
            "Description": "This is a sample view that just exposes a single stream property.",
            "ReferenceType": "StreamViewReference",
            "Value": {
                "StreamId": "PI_buildingMachine_165394",
                "StreamViewId": "StreamViewSample",
                "TargetTypeId": "PI-Float64"
            }
        }
    ]
}
```

***
## `Get Asset Last Data` 
Returns the last stored value for all referenced SdsStream objects.

### Request 
```text 

GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/Data/Last  

```

### Parameters  
`string tenantId` 

The tenant identifier

`string namespaceId` 

The namespace identifier

`string assetId`

The asset identifier

### Response 
The response includes a status code and a response body.

| Status Code | Body Type | Description |
|--|--|--|
| 200 OK | OK | Array of last values for all references. |
| 207 Multi-Status | partial success | Array of last values for references. Look at child errors for those that are unsuccessful. |
| 400 Bad Request | error | The request is not valid. See the response body for additional details. |
| 403 Forbidden | error | You are not authorized to view the requested asset. |
| 404 Not Found | error | The specified asset is not found. |

#### Example response body
``` 
[
    {
        "Measurement": "Temperature",
        "Result": [
            {
                "Timestamp": "2020-08-12T22:35:44Z",
                "Value": 73.165016
            }
        ]
    }
]
        "Timestamp": "2019-07-25T23:38:31Z",
        "Value": 82.63277
    },
    "SampleView": {
        "Timestamp": "2020-05-22T21:07:30Z",
        "Value": 96.81087493896484
    }
} 
```

***
## `Get Asset Sampled Data` 
Returns sampled data for all referenced SdsStream objects. 
Note: The inputs to this API matches the SdsStream Get Samples Values data call.  

### Request 
```text 

GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/Data/Sampled?startIndex={startIndex}&endIndex=(endIndex)&intervals={intervals} 

```

### Parameters  
`string tenantId` 

The tenant identifier 

`string namespaceId` 

The namespace identifier

`string assetId`

The asset identifier

`string startIndex` 

The start index for the intervals

`string endIndex` 

The number of requested intervals 


### Response 
The response includes a status code and a response body.

| Status Code | Body Type | Description |
|--|--|--|
| 200 OK | OK | Array of sampled values for all references. |
| 207 Multi-Status | partial success | Array of sampled values for  references. Look at child errors for those that are unsuccessful. |
| 400 Bad Request | error | The request is not valid. See the response body for additional details. |
| 403 Forbidden | error | You are not authorized to view the requested asset. |
| 404 Not Found | error | The specified asset with identifier is not found. |

```json 
HTTP 200 OK
Content-Type: application/json
[
    {
        "Measurement": "StreamPressure",
        "Result": [
            {
                "Timestamp": "2019-08-20T19:15:37Z",
                "Value": 218.13373
            },
            {
                "Timestamp": "2019-08-20T19:37:07Z",
                "Value": 201.36305
            },
            {
                "Timestamp": "2019-08-20T22:09:07Z",
                "Value": 247.73355
            },
            {
                "Timestamp": "2019-08-20T22:38:07Z",
                "Value": 216.15732
            },
            {
                "Timestamp": "2019-08-20T22:38:37Z",
                "Value": 217.88617
            },
            {
                "Timestamp": "2019-08-21T00:08:07Z",
                "Value": 185.70175
            },
            {
                "Timestamp": "2019-08-21T03:35:07Z",
                "Value": 249.77954
            },
            {
                "Timestamp": "2019-08-21T03:53:37Z",
                "Value": 232.56764
            },
            {
                "Timestamp": "2019-08-21T03:54:07Z",
                "Value": 234.20694
            },
            {
                "Timestamp": "2019-08-21T07:23:37Z",
                "Value": 249.29556
            },
            {
                "Timestamp": "2019-08-21T08:36:37Z",
                "Value": 202.4792
            },
            {
                "Timestamp": "2019-08-21T09:09:07Z",
                "Value": 205.28456
            },
            {
                "Timestamp": "2019-08-21T09:09:37Z",
                "Value": 203.7544
            },
            {
                "Timestamp": "2019-08-21T11:02:07Z",
                "Value": 178.63676
            },
            {
                "Timestamp": "2019-08-21T14:03:37Z",
                "Value": 228.6509
            },
            {
                "Timestamp": "2019-08-21T14:25:07Z",
                "Value": 209.00409
            },
            {
                "Timestamp": "2019-08-21T14:25:37Z",
                "Value": 211.80522
            },
            {
                "Timestamp": "2019-08-21T14:53:37Z",
                "Value": 235.39305
            },
            {
                "Timestamp": "2019-08-21T18:55:07Z",
                "Value": 147.43044
            },
            {
                "Timestamp": "2019-08-21T19:40:37Z",
                "Value": 169.46703
            }
        ]
    }
] 
```

***

## `Get Asset Summary Data` 
Returns summary data for all referenced SdsStream objects. 
Note: The inputs to this API matches the SdsStream Get Summaries data call.

### Request 
```text 

GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/Data/Summaries?startIndex={startIndex}&endIndex=(endIndex)&count={count}

```

###  Parameters  
`string tenantId` 

The tenant identifier 

`string namespaceId` 

The namespace identifier

`string assetId`

The asset identifier

`string startIndex` 

The start index for the intervals

`string endIndex` 

The end index for the intervals

`int count` 

The number of requested intervals


### Response 
The response includes a status code and a response body.

| Status Code | Body Type | Description |
|--|--|--|
| 200 OK | OK | Array of summary values for all references. |
| 207 Multi-Status | partial success | Array of summary values for  references. Look at child errors for those that are unsuccessful. |
| 400 Bad Request | error | The request is not valid. See the response body for additional details. |
| 403 Forbidden | error | You are not authorized to view the requested asset. |
| 404 Not Found | error | The specified asset with identifier is not found. |

```json 
HTTP 200 OK
Content-Type: application/json
[
    {
        "Measurement": "measurementPressure",
        "Result": [
            {
                "Start": {
                    "Timestamp": "2020-01-01T12:00:00Z",
                    "Value": 139.56558
                },
                "End": {
                    "Timestamp": "2021-01-01T12:00:00Z"
                },
                "Summaries": {
                    "Count": {
                        "Timestamp": 211615,
                        "Value": 211613
                    },
                    "Minimum": {
                        "Value": 47.00091552734375
                    },
                    "Maximum": {
                        "Value": 249.99899291992188
                    },
                    "Range": {
                        "Value": 202.99807739257812
                    },
                    "Mean": {
                        "Value": 136.30853664128998
                    },
                    "StandardDeviation": {
                        "Value": 57.04227640108317
                    },
                    "PopulationStandardDeviation": {
                        "Value": 57.04214162121664
                    },
                    "Total": {
                        "Value": 28844658.36427307
                    },
                    "Skewness": {
                        "Value": 0.3037505109882242
                    },
                    "Kurtosis": {
                        "Value": -2.7748546694726244
                    },
                    "WeightedMean": {
                        "Value": 112.71120677110477
                    },
                    "WeightedStandardDeviation": {
                        "Value": 55.216968157263885
                    },
                    "WeightedPopulationStandardDeviation": {
                        "Value": 55.21683769086423
                    }
                }
            }
        ]
    }
]
```
