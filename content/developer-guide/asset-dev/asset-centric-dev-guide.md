---
uid: asset-centric-dev-guide
---

# Assets Data API

The asset data API provides a quick way to retrieve data stored in an asset's referenced streams. 

In order to retrieve stream data from an asset, you must first set up stream references for a given asset. The data that is retrieved is based on the resolved asset. By default, data calls return data for all stream references. 

If you are only interested in data from a subset of streams, you must specify the streams encoded as a URL parameter. The format is to add `stream={streamReferennceName}` for each stream reference separated by ampersands (&).

For example, if a given asset has the following definition and you are only interested in HeaterA and PressureB for the last data call, you would send:

```text 
GET ...Namespaces/{namespaceId}/Assets/AssetStreamFilter/Data/Last?Stream={HeaterA}&Stream={PressureB}
```

**Note:** Asset stream references can contain commas. In this case, the comma must be properly escaped.

```
{
    "Id": "AssetStreamFilter",
    "Name": "Demo",
    "Description": "Only for demoing stream filtering",
    "StreamReferences": 
    [
        {
            "Id": "StreamReferenceId1",
            "Name": "StreamReferenceWithEventsName"
            "StreamId": "PI_buildingMachine"
        },
        {
            "Id": "HeaterId1",
            "Name": "HeaterA"
            "StreamId": "PI_HeaterA"
        },
        {
            "Id": "PressureId1",
            "Name": "PressureB"
            "StreamId": "PI_PressureB"
        }
    ]
}
```
### Example Asset
The following asset is used in all of the sample output in the output below.
```
{
    "Id": "Idsample",
    "Name": "SampleForDemo",
    "Description": "This is a demo asset.",
    "Metadata": [
        {
            "Id": "b47c9529-7fbf-4b2d-810b-fe79d7fdb2b0",
            "Name": "RoomLocation",
            "Description": "This is what room number the asset is located.",
            "SdsTypeCode": "Double",
            "Value": 1.0
        }
    ],
    "StreamReferences": 
    [
        {
            "Id": "StreamReferenceId1",
            "Name": "StreamReferenceWithEventsName"
            "StreamId": "PI_buildingMachine_1112"
        }
    ]
}
```