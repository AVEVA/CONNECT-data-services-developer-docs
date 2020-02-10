---
uid: DataViewsAvailableFieldSets
---

# Available Field Sets

Available [field sets](xref:DataViewsFieldSets) include fields not currently included in the data view, which are available to be added. 

The list of field sets is generated based on the `.Queries`, `.Sectioners`, and `.IndexTypeCode` of the defined data view. These fields and field sets can be readily added to the data view `.FieldSets`. Once the field is added, it is omitted from the list of available field sets. Similarly, if the field is removed from the data view, it is added back to the available field sets. This allows an iterative approach to building the data view by easily adding and removing fields from the data view. 

## Field Set Source
Available fields are organized into field sets according to their sources:

```FieldSetSourceType.Index```

The index field set represents the index field of the data view. Exactly one index field set is available per data view. Currently, this field is not mapped to anything, since interpolation is the only supported index mode.

```FieldSetSourceType.SectionerValue```

The sectioner value field set represents the matching value for each section. If no sectioners are specified, this field set is not available. Exactly one section value field set is available per data view. The section value field set contains one field per section, with each sectioner referred to by its index: `{ ... Keys: ["0"] }` for the 0th sectioner.

```FieldSetSourceType.DataItem```

The data item field set contains fields from the data item resulted from the query. For each query, a field set with unused fields will be returned. The available fields for stream data item include:
    * Id, name
    * Tags: one field with union of all tags
    * Metadata, propertyId: one field for each metadata key or property id

## Data View without Sectioners
The example uses the following data view and the streams from the [SDS Example Scenario](xref:DataViewsExampleScenario). Note that the field sets and the sectioners arrays are empty:
```json
{
  "Id": "example_without_sectioners",
  "Name": "example_without_sectioners",
  "Description": null,
  "Queries": [
    { 
      Id: "weather",
      Value:"*weather*" 
    }
  ],
  "FieldSets": [],
  "Sectioners": [],
  "Shape": "Standard",
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
            "SourceType": "Index",
            "Fields": [
                {
                    "Source": "None",
                    "Keys": [],
                    "Label": "Timestamp"
                }
            ]
        },
        {
            "SourceType": "DataItem",
            "QueryId": "weather",
            "Fields": [
                {
                    "Source": "Id",
                    "Keys": [],
                    "Label": "{DistinguisherValue} Id"
                },
                {
                    "Source": "Name",
                    "Keys": [],
                    "Label": "{DistinguisherValue} Name"
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
                    "Label": "{DistinguisherValue} Tags"
                },
                {
                    "Source": "Metadata",
                    "Keys": [
                        "Site"
                    ],
                    "Label": "{DistinguisherValue} {FirstKey}"
                },
                {
                    "Source": "PropertyId",
                    "Keys": [
                        "Timestamp"
                    ],
                    "Label": "{DistinguisherValue} {FirstKey}"
                },
                {
                    "Source": "PropertyId",
                    "Keys": [
                        "SolarRadiation"
                    ],
                    "Label": "{DistinguisherValue} {FirstKey}"
                },
                {
                    "Source": "PropertyId",
                    "Keys": [
                        "AmbientTemperature"
                    ],
                    "Label": "{DistinguisherValue} {FirstKey}"
                },
                {
                    "Source": "PropertyId",
                    "Keys": [
                        "CloudCover"
                    ],
                    "Label": "{DistinguisherValue} {FirstKey}"
                },
                {
                    "Source": "PropertyId",
                    "Keys": [
                        "Temperature"
                    ],
                    "Label": "{DistinguisherValue} {FirstKey}"
                }
            ]
        }
    ]
}
```

## Data View with Sectioners
This data view is the same as in the first example, except it also has a `sectioner`, which defines sectioning by the metadata key "Site":

```json
{
  "Id": "example_with_sectioners",
  "Name": "example_with_sectioners",
  "Description": null,
  "Queries": [
    { 
      Id: "weather",
      Value:"*weather*" 
    }
  ],
  "FieldSets": []
  "Sectioners": [
    {
      "Source": "Metadata",
      "Keys": [
        "Site" 
      ],
      "Label": "{DistinguisherValue} Id"
    }
  ],
  "Shape": "Standard",
  "IndexTypeCode": "DateTime"
}
```

A field set with ```SourceType.SectionValue``` is now shown as one of the available field sets:
```json
HTTP 200 OK
{
    "TimeOfResolution": "2019-11-14T20:31:20.856826+00:00",
    "Items": [
        {
            "SourceType": "Index",
            "Fields": [
                {
                    "Source": "None",
                    "Keys": [],
                    "Label": "Timestamp"
                }
            ]
        },
        {
            "SourceType": "SectionValue",
            "Fields": [
                {
                    "Source": "None",
                    "Keys": [
                        "0"
                    ],
                    "Label": "{SectionerLabel}"
                }
            ]
        },
        {
            "SourceType": "DataItem",
            "QueryId": "weather",
            "Fields": [
                ...
            ]
        }
    ]
}
```

