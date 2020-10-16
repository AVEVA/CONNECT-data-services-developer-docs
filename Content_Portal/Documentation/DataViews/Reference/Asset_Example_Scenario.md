---
uid: DataViewsWithAssetsExampleScenario
---

# Asset examples (Coming soon)
_Note: This section covers features that are not yet generally available. If you are interested in trialing these pre-release features, contact your account team for more details._

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
            "Id": "Time",
            "Name": "Time",
            "IsKey": true,
            "SdsType": {
                "Id": "0573b425-368a-369b-95d9-71c863df45a5",
                "Name": "DateTime",
                "SdsTypeCode": 16
            }
        },
        {
            "Id": "EngineOilPressure",
            "Name": "EngineOilPressure",
            "SdsType": {
                "Id": "9144b7d6-3d5f-3b29-8131-ff0db551e17c",
                "Name": "Double",
                "SdsTypeCode": 14
            },
            "Uom": "psi"
        },
        {
            "Id": "EngineTemperature",
            "Name": "EngineTemperature",
            "SdsType": {
                "Id": "9144b7d6-3d5f-3b29-8131-ff0db551e17c",
                "Name": "Double",
                "SdsTypeCode": 14
            },
            "Uom": "°F"
        },
        {
            "Id": "Latitude",
            "Name": "Latitude",
            "SdsType": {
                "Id": "9144b7d6-3d5f-3b29-8131-ff0db551e17c",
                "Name": "Double",
                "SdsTypeCode": 14
            }
        },
        {
            "Id": "Longitude",
            "Name": "Longitude",
            "SdsType": {
                "Id": "9144b7d6-3d5f-3b29-8131-ff0db551e17c",
                "Name": "Double",
                "SdsTypeCode": 14
            }
        }
    ]
}
```
### Stream IDs
Ten truck streams are defined:
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
    "Name": "docs-truck-type",
    "Metadata": [
        {
            "Id": "Target Differential",
            "Name": "Target Differential",
            "Description": "Target engine pressure differential",
            "SdsTypeCode": 14,
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

### Asset type measurement mappings
```json
[
    {
        "Name": "Engine Oil Pressure",
        "StreamReferenceId": "truck-streams",
        "StreamPropertyIds": [
            "Time",
            "EngineOilPressure"
        ]
    },
    {
        "Name": "Engine Temp",
        "StreamReferenceId": "truck-streams",
        "StreamPropertyIds": [
            "Time",
            "EngineTemperature"
        ]
    },
    {
        "Name": "Location",
        "StreamReferenceId": "truck-streams",
        "StreamPropertyIds": [
            "Time",
            "Latitude",
            "Longitude"
        ]
    }
]
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
        "SdsTypeCode": 18,
        "Value": one of ("CAT 797", "960E-1", "Titan")
    },
    {
        "Id": "Last Maintenance Date",
        "Name": "Last Maintenance Date",
        "SdsTypeCode": 16,
        "Value": past date
    }
]
```

#### Asset stream references
Each truck asset contains a stream reference to the SDS stream with the same name.

```json
"StreamReferences": [
    {
        "Id": "truck-streams",
        "StreamId": one of ("Truck102", "Truck102", "Truck102", "Truck102", "Truck102", "Truck102", "Truck102", "Truck102", "Truck102", "Truck102")
    }
]
```


## Sample data view
```json
{
    "Id": "asset-quickstart",
    "Name": "asset-quickstart",
    "IndexField": {
        "Source": "NotApplicable",
        "Keys": [],
        "MeasurementKeys": [],
        "Label": "Timestamp",
        "SummaryType": "None",
        "IncludeUom": false
    },
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
                    "MeasurementKeys": [
                        "Engine Oil Pressure"
                    ],
                    "Label": "{IdentifyingValue} {MeasurementFirstKey} {SummaryType} {Uom}",
                    "SummaryType": "None",
                    "IncludeUom": false
                },
                {
                    "Source": "PropertyId",
                    "Keys": [
                        "EngineTemperature"
                    ],
                    "MeasurementKeys": [
                        "Engine Temp"
                    ],
                    "Label": "{IdentifyingValue} {MeasurementFirstKey} {SummaryType} {Uom}",
                    "SummaryType": "None",
                    "IncludeUom": false
                },
                {
                    "Source": "PropertyId",
                    "Keys": [
                        "Latitude"
                    ],
                    "MeasurementKeys": [
                        "Location"
                    ],
                    "Label": "{IdentifyingValue} {MeasurementFirstKey} {FirstKey} {SummaryType} {Uom}",
                    "SummaryType": "None",
                    "IncludeUom": false
                },
                {
                    "Source": "PropertyId",
                    "Keys": [
                        "Longitude"
                    ],
                    "MeasurementKeys": [
                        "Location"
                    ],
                    "Label": "{IdentifyingValue} {MeasurementFirstKey} {FirstKey} {SummaryType} {Uom}",
                    "SummaryType": "None",
                    "IncludeUom": false
                },
                {
                    "Source": "Metadata",
                    "Keys": [
                        "LastMaintenanceDate"
                    ],
                    "MeasurementKeys": [],
                    "Label": "{IdentifyingValue} {FirstKey} {SummaryType} {Uom}",
                    "SummaryType": "None",
                    "IncludeUom": false
                },
                {
                    "Source": "Metadata",
                    "Keys": [
                        "Model"
                    ],
                    "MeasurementKeys": [],
                    "Label": "{IdentifyingValue} {FirstKey} {SummaryType} {Uom}",
                    "SummaryType": "None",
                    "IncludeUom": false
                },
                {
                    "Source": "Metadata",
                    "Keys": [
                        "Target Differential"
                    ],
                    "MeasurementKeys": [],
                    "Label": "{IdentifyingValue} {FirstKey} {SummaryType} {Uom}",
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
            "MeasurementKeys": [],
            "Label": "{IdentifyingValue} Id",
            "SummaryType": "None",
            "IncludeUom": false
        }
    ],
    "IndexTypeCode": "DateTime",
    "Shape": "Standard"
}
```