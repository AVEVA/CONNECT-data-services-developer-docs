---
uid: DataViewsAvailableFieldSets
---

# Available Field Sets

Available [field sets](xref:DataViewsFieldSets) include fields not currently included in the data view, which are available to be added. 

The list of field sets is generated based on the `.Queries`, `.GroupingFields`, and `.IndexTypeCode` of the defined data view. These fields and field sets can be readily added to the data view `.DataFieldSets`. Once the field is added, it is omitted from the list of available field sets. Similarly, if the field is removed from the data view, it is added back to the available field sets. This allows an iterative approach to building the data view by easily adding and removing fields from the data view. 

## Example
The example uses the following data view and the streams from the [SDS Example Scenario](xref:DataViewsExampleScenario). Note that the field sets and the grouping fields arrays are empty:
```json
{
  "Id": "example_without_grouping_fields",
  "Name": "example_without_grouping_fields",
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

Accessing the ```Get Available Field Sets``` endpoint will show available fields corresponding to stream id, name, tags, metadata, and each property. Since the index field set is not included in the data view, it is also shown as available.

```json
HTTP 200 OK
{
    "TimeOfResolution": "(a timestamp in ISO 8601 format)",
    "Items": [
        {
            "QueryId": "weather",
            "DataFields": [
                {
                    "Source": "Id",
                    "Keys": [],
                    "Label": "{IdentifyingValue} Id"
                },
                {
                    "Source": "Name",
                    "Keys": [],
                    "Label": "{IdentifyingValue} Name"
                },
                {
                    "Source": "Tags",
                    "Keys": [
                        "Weather",
                        "Low Resolution",
                        "High Resolution",
                        "Gen1",
                        "Gen2",
                    ],
                    "Label": "{IdentifyingValue} Tags"
                },
                {
                    "Source": "Metadata",
                    "Keys": [
                        "Site"
                    ],
                    "Label": "{IdentifyingValue} {FirstKey}"
                },
                {
                    "Source": "PropertyId",
                    "Keys": [
                        "Timestamp"
                    ],
                    "Label": "{IdentifyingValue} {FirstKey}"
                },
                {
                    "Source": "PropertyId",
                    "Keys": [
                        "SolarRadiation"
                    ],
                    "Label": "{IdentifyingValue} {FirstKey}"
                },
                {
                    "Source": "PropertyId",
                    "Keys": [
                        "AmbientTemperature"
                    ],
                    "Label": "{IdentifyingValue} {FirstKey}"
                },
                {
                    "Source": "PropertyId",
                    "Keys": [
                        "CloudCover"
                    ],
                    "Label": "{IdentifyingValue} {FirstKey}"
                },
                {
                    "Source": "PropertyId",
                    "Keys": [
                        "Temperature"
                    ],
                    "Label": "{IdentifyingValue} {FirstKey}"
                }
            ]
        }
    ]
}
```


