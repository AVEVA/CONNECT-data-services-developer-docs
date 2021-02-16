---
uid: DataViewsAssetExamples
---

# Asset examples

This section defines an asset example including the streams, assets, and data view for illustrating how assets can be used within a data view.

This example creates haul truck assets and the underlying types and streams containing data such as engine oil pressure and engine temperature.

## Sequential Data Store artifacts

### Type
```json
{
    "Id": "docs-sds-truck-type",
    "Name": "TruckType",
    "SdsTypeCode": 1,
    "Properties": [
        {
            "Id": "Timestamp",
            "Name": "Timestamp",
            "IsKey": true,
            "SdsType": {
                "SdsTypeCode": "DateTime"
            }
        },
        {
            "Id": "EngineOilPressure",
            "Name": "EngineOilPressure",
            "SdsType": {
                "SdsTypeCode": "Double"
            },
            "Uom": "psi"
        },
        {
            "Id": "EngineTemperature",
            "Name": "EngineTemperature",
            "SdsType": {
                "SdsTypeCode": "Double"
            },
            "Uom": "°F"
        },
        {
            "Id": "Latitude",
            "Name": "Latitude",
            "SdsType": {
                "SdsTypeCode": "Double"
            }
        },
        {
            "Id": "Longitude",
            "Name": "Longitude",
            "SdsType": {
                "SdsTypeCode": "Double"
            }
        }
    ]
}
```
### Stream IDs
10 truck streams are defined:
```text
"Truck102",
"Truck202",
"Truck273",
"Truck421",
"Truck474",
"Truck641",
"Truck745",
"Truck788",
"Truck820",
"Truck834",
```

## Asset artifacts

### Asset type
```json
{
    "Id": "docs-truck-type",
    "Name": "TruckAssetType",
    "Metadata": [
        {
            "Id": "Target Differential",
            "Name": "Target Differential",
            "Description": "Target engine pressure differential",
            "SdsTypeCode": "Double",
            "Value": 0.1,
            "Uom": "psi"
        }
    ],
    "TypeReferences": [
        {
            "StreamReferenceId": "truck-streams",
            "StreamReferenceName": "truck-streams",
            "TypeId": "docs-sds-truck-type"
        }
    ]
}
```

### Assets
(one to one match with streams)

Asset IDs:
```text
"Truck102",
"Truck202",
"Truck273",
"Truck421",
"Truck474",
"Truck641",
"Truck745",
"Truck788",
"Truck820",
"Truck834",
```

#### Asset metadata
Each truck asset contains metadata for the truck Model and Last Maintenance Date.

```json
"Metadata": [
    {
        "Id": "Model",
        "Name": "Model",
        "SdsTypeCode": "String",
        "Value": one of ("CAT 797", "960E-1", "Titan")
    },
    {
        "Id": "Last Maintenance Date",
        "Name": "Last Maintenance Date",
        "SdsTypeCode": "DateTime",
        "Value": past date
    }
]
```

#### Asset stream references
Each truck asset contains a stream reference to the SDS stream with the same name.

```json
"StreamReferences": [
    {
        "Id": "Truck",
        "Name": "Truck",
        "StreamId": one of ("Truck102", "Truck202", "Truck273", "Truck421", "Truck474", "Truck641", "Truck745", "Truck788", "Truck820", "Truck834")
    }
]
```

## Sample data view
```json
{
    "Id": "asset-quickstart",
    "Name": "asset-quickstart",
    "Queries": [
        {
            "Id": "trucks",
            "Kind": "Asset",
            "Value": "Truck*"
        }
    ],
    "DataFieldSets": [
        {
            "QueryId": "trucks",
            "DataFields": [
                {
                    "Source": "PropertyId",
                    "Keys": [
                        "EngineOilPressure"
                    ],
                    "StreamReferenceNames": [
                        "Truck"
                    ],
                    "Label": "{IdentifyingValue} Truck EngineOilPressure {SummaryType} {Uom}",
                    "SummaryType": "None",
                    "IncludeUom": false
                },
                {
                    "Source": "PropertyId",
                    "Keys": [
                        "EngineTemperature"
                    ],
                    "StreamReferenceNames": [
                        "Truck"
                    ],
                    "Label": "{IdentifyingValue} Truck EngineTemperature {SummaryType} {Uom}",
                    "SummaryType": "None",
                    "IncludeUom": false
                },
                {
                    "Source": "PropertyId",
                    "Keys": [
                        "Latitude"
                    ],
                    "StreamReferenceNames": [
                        "Truck"
                    ],
                    "Label": "{IdentifyingValue} Truck Latitude {SummaryType} {Uom}",
                    "SummaryType": "None",
                    "IncludeUom": false
                },
                {
                    "Source": "PropertyId",
                    "Keys": [
                        "Longitude"
                    ],
                    "StreamReferenceNames": [
                        "Truck"
                    ],
                    "Label": "{IdentifyingValue} Truck Longitude {SummaryType} {Uom}",
                    "SummaryType": "None",
                    "IncludeUom": false
                },
                {
                    "Source": "Metadata",
                    "Keys": [
                        "Last Maintenance Date"
                    ],
                    "StreamReferenceNames": [],
                    "Label": "{IdentifyingValue} Last Maintenance Date {Uom}",
                    "SummaryType": "None",
                    "IncludeUom": false
                },
                {
                    "Source": "Metadata",
                    "Keys": [
                        "Model"
                    ],
                    "StreamReferenceNames": [],
                    "Label": "{IdentifyingValue} Model {Uom}",
                    "SummaryType": "None",
                    "IncludeUom": false
                },
                {
                    "Source": "Metadata",
                    "Keys": [
                        "Target Differential"
                    ],
                    "MeasurementKeys": [],
                    "Label": "{IdentifyingValue} Target Differential {Uom}",
                    "SummaryType": "None",
                    "IncludeUom": false
                }
            ]
        }
    ],
    "GroupingFields": [
        {
            "Source": "Id",
            "Keys": [],
            "StreamReferenceNames": [],
            "Label": "{IdentifyingValue} Id",
            "SummaryType": "None",
            "IncludeUom": false
        }
    ],
    "IndexTypeCode": "DateTime",
    "Shape": "Standard"
}
```