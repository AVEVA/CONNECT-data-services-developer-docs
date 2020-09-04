---
uid: AssetCentricDataAPI
---

# Asset Centric Data API
The Asset Centric Data API provides a quick way to take the dynamic data stored in SDS streams and store it as references within a given asset.

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
HTTP 200 OK
Content-Type: application/json
{
    "SampleStream": {
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
{
    "SampleStream": [
        {
            "Timestamp": "2019-07-15T00:00:00Z",
            "Value": 75.000336
        },
        {
            "Timestamp": "2019-07-15T02:15:56Z",
            "Value": 19.240202
        },
        {
            "Timestamp": "2019-07-15T02:15:57Z",
            "Value": 19.234468
        },
        {
            "Timestamp": "2019-07-15T11:54:15Z",
            "Value": 77.140495
        },
        {
            "Timestamp": "2019-07-15T14:18:48Z",
            "Value": 18.263603
        },
        {
            "Timestamp": "2019-07-15T14:18:49Z",
            "Value": 18.257984
        },
        {
            "Timestamp": "2019-07-16T12:00:01Z",
            "Value": 74.9938
        }
    ],
    "SampleView": [
        {
            "Timestamp": "2018-10-03T00:00:00Z",
            "Value": 24.0
        },
        {
            "Timestamp": "2018-10-03T01:00:00Z",
            "Value": 25.0
        },
        {
            "Timestamp": "2018-10-03T02:00:00Z",
            "Value": 23.0
        },
        {
            "Timestamp": "2018-10-03T03:00:00Z",
            "Value": 26.0
        },
        {
            "Timestamp": "2018-10-03T04:00:00Z",
            "Value": 22.0
        },
        {
            "Timestamp": "2019-08-20T19:15:37Z",
            "Value": 229.283447265625
        }
    ]
}
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
{
    "SampleStream": [
        {
            "Start": {
                "Timestamp": "2019-07-15T00:00:00Z",
                "Value": 75.000336
            },
            "End": {
                "Timestamp": "2019-07-15T12:00:00Z",
                "Value": 75.0001
            },
            "Summaries": {
                "Count": {
                    "Timestamp": 43201,
                    "Value": 43201,
                    "IsQuestionable": 43201
                },
                "Minimum": {
                    "Value": 2.3134134607971646E-09,
                    "IsQuestionable": 0.0
                },
                "Maximum": {
                    "Value": 100.0,
                    "IsQuestionable": 0.0
                },
                "Range": {
                    "Value": 99.99999999768659,
                    "IsQuestionable": 0.0
                },
                "Total": {
                    "Value": 2160002.348559387,
                    "IsQuestionable": 0.0
                },
                "Mean": {
                    "Value": 50.000054364801215,
                    "IsQuestionable": 0.0
                },
                "StandardDeviation": {
                    "Value": 35.35575171468018,
                    "IsQuestionable": 0.0
                },
                "PopulationStandardDeviation": {
                    "Value": 35.35534250222275,
                    "IsQuestionable": 0.0
                },
                "WeightedMean": {
                    "Value": 50.000054364801215,
                    "IsQuestionable": 0.0
                },
                "WeightedStandardDeviation": {
                    "Value": 35.355751714679954,
                    "IsQuestionable": 0.0
                },
                "WeightedPopulationStandardDeviation": {
                    "Value": 35.35534250222253,
                    "IsQuestionable": 0.0
                },
                "Skewness": {
                    "Value": -4.870436631192324E-06,
                    "IsQuestionable": "NaN"
                },
                "Kurtosis": {
                    "Value": -1.500001916843267,
                    "IsQuestionable": "NaN"
                }
            }
        }
    ],
    "SampleView": [
        {
            "Start": {
                "Timestamp": "2018-10-03T00:00:00Z",
                "Value": 24.0
            },
            "End": {
                "Timestamp": "2019-07-15T12:00:00Z",
                "Value": 205.8877037170768
            },
            "Summaries": {
                "Count": {
                    "Timestamp": 5,
                    "Value": 5,
                    "IsQuestionable": 5
                },
                "Minimum": {
                    "Value": 22.0,
                    "IsQuestionable": 0.0
                },
                "Maximum": {
                    "Value": 26.0,
                    "IsQuestionable": 0.0
                },
                "Range": {
                    "Value": 4.0,
                    "IsQuestionable": 0.0
                },
                "Total": {
                    "Value": 120.0,
                    "IsQuestionable": 0.0
                },
                "Mean": {
                    "Value": 24.0,
                    "IsQuestionable": 0.0
                },
                "StandardDeviation": {
                    "Value": 1.5811388300841898,
                    "IsQuestionable": 0.0
                },
                "PopulationStandardDeviation": {
                    "Value": 1.4142135623730951,
                    "IsQuestionable": 0.0
                },
                "WeightedMean": {
                    "Value": 22.001459427904262,
                    "IsQuestionable": 0.0
                },
                "WeightedStandardDeviation": {
                    "Value": 0.07396074789184506,
                    "IsQuestionable": 0.0
                },
                "WeightedPopulationStandardDeviation": {
                    "Value": 0.06615250398115592,
                    "IsQuestionable": 0.0
                },
                "Skewness": {
                    "Value": 0.0,
                    "IsQuestionable": "NaN"
                },
                "Kurtosis": {
                    "Value": -1.3,
                    "IsQuestionable": "NaN"
                }
            }
        }
    ]
}
```
