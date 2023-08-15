---
uid: EventUsageExamples
--- 

# Event Type Store and GraphQL API usage examples 

The following sample types demonstrate how Event Types and Reference Data Types can be used together to facilitate the creation and querying of events in the GraphQL API.  

First, we create a Reference Data Type referencing an external asset: 

`POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/ReferenceDataTypes/assetReference`
<br>&nbsp;
```json
{
    "Id": "assetReference",
    "Name": "assetReference",
    "Properties":
    [
        {
            "Id": "SourceId",
            "PropertyTypeCode": "String"
        },
        {
            "Id": "ResourceId",
            "PropertyTypeCode": "String"
        }
    ]
}
```

Then, we create an Event Type with a property referencing the previously created Reference Data Type:

`POST /api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/EventTypes/LowProductionEvent`
<br>&nbsp;
```json
{
    "Id": "LowProductionEvent",
    "Name": "LowProductionEvent",
    "Properties":
    [
        {
            "Id": "eventStartTime",
            "PropertyTypeCode": "DateTime"
        },
        {
            "Id": "eventEndTime",
            "PropertyTypeCode": "DateTime"
        },
        {
            "Id": "eventDuration",
            "PropertyTypeCode": "TimeSpan"
        },
        {
            "Id": "referenceAssets",
            "PropertyTypeCode": "ReferenceData",
            "Flags": "IsCollection",
            "PropertyTypeId": "assetReference"
        },
        {
            "Id": "totalRevenueLoss",
            "PropertyTypeCode": "Double"
        }
    ]
}
```

Finally, once events of the above Event Type have been created, we use the GraphQL API to query these assets, allowing the user to gather data about related events.
<br>&nbsp;
```json
{
    events {
        LowProductionEvent {
            eventStartTime
            eventEndTime
            eventDuration
            referenceAssets {
                id
                name
            }
            totalRevenueLoss
        }
    }
}
```

A sample result of the query is shown below.<br>
<br>&nbsp;
```json
{
    "data": {
        "events": {
            "LowProductionEvent": [
                {
                    "eventStartTime": "2023-06-01T05:43:27.00Z",
                    "eventEndTime": "2023-06-01T06:43:27.00Z",
                    "eventDuration": "01:00:00",
                    "referenceAssets": [
                        {
                            "id": "Asset1",
                            "name": "Asset1"
                        },
                        {
                            "id": "Asset2",
                            "name": "Asset2"
                        }
                    ],
                    "totalRevenueLoss": 5.2
                },
                {
                    "eventStartTime": "2023-06-03T09:00:02.00Z",
                    "eventEndTime": "2023-06-03T10:00:02.00Z",
                    "eventDuration": "01:00:00",
                    "referenceAssets": [
                        {
                            "id": "Asset3",
                            "name": "Asset3"
                        }
                    ],
                    "totalRevenueLoss": 12.1
                },
                {
                    "eventStartTime": "2023-06-03T15:20:25.00Z",
                    "eventEndTime": "2023-06-03T16:20:25.00Z",
                    "eventDuration": "01:00:00",
                    "referenceAssets": [
                        {
                            "id": "Asset3",
                            "name": "Asset3"
                        }
                    ],
                    "totalRevenueLoss": 33.56
                }
            ]
        }
    }
}
```
