---
uid: DataViewsUnitsOfMeasure
---

# Display units of measure (coming soon)

*Note: This topic covers features that are not yet generally available. If you are interested in trialing these pre-release features, contact your account team for more details.*

Data views can be configured to show the units of measure (Uom) from the underlying data source. This topic describes how to expose units of measure in the resolved data view, as well as the different options to include them in the data set itself.


## Units of measure in resolved data view
In the [resolved data items](xref:DataViewsDataItemsandGroups), each data item field shows the unit of measure from the underlying data source. In addition, each data mapping in the [resolved field mapping](xref:DataViewsFieldMappings) shows the unit of measure. If a unit of measure is not present in the underying data source, the `Uom` property is null.

If the unit of measure is consistent across all groups, then that unit of measure is reported on the [field mapping](xref:DataViewsFieldMappings) itself. Otherwise, the `Uom` property of the field mapping is null.

Note that the [ids of the units of measure](xref:unitsOfMeasure) are shown in resolved resources.


## Units of measure in data view
Data views can be optionally configured to show units of measure within the data set or in labels. The [abbreviations of the units of measure](xref:unitsOfMeasure) are shown in the data view.

### Show units of measure within the data set
To show the units of measure within the data set, set the `IncludeUom` property of the field to `true`. This applies to both data fields and group fields. In this case, the field will resolve an additional, "sister" field mapping whose label is suffixed with the string "Uom'. 

#### Example
This simple example shows the `IncludeUom` property of a data field is set to `true`.
```json
{
  "Id": "quickstart",
  "Queries": [
    { 
      "Id": "inverters",
      "Kind": "Stream",
      "Value": "id:BILT.Meter.Primary.Inverter.0.PwrIn"
    }
  ],
  "DataFieldSets": [
    {
      "QueryId": "inverters",
      "DataFields": [
        {
          "Source": "PropertyId",
          "Keys": [ "Value" ],
          "Label": "{IdentifyingValue} {FirstKey}",
		  "IncludeUom": "true"
        }
      ]
    }
  ]
}
```

The resulting data view in standard mode:
| Timestamp            | Value | Value Uom |
|----------------------|-------|-----------|
| 2020-11-06T08:00:00Z | 1.21  | kW        |

The resulting data view in narrow mode:
| Timestamp            | Field | Value | Uom |
|----------------------|-------|-------|-----|
| 2020-11-06T08:00:00Z | Value | 1.21  | kW  |


### Show units of measure in field labels
The field label token {Uom} can be used to add field-level unit of measure to field labels. {Uom} is included in the default field label. If the unit of measure is consistent across all groups, {Uom} is resolved to the field-level unit of measure and displayed in the field label.

#### Example
The following example shows how the field label token {Uom} of a data field is resolved.
```json
{
  "Id": "quickstart",
  "Queries": [
    { 
      "Id": "inverters",
      "Kind": "Stream",
      "Value": "id:BILT.Meter.Primary.Inverter.0.PwrIn"
    }
  ],
  "DataFieldSets": [
    {
      "QueryId": "inverters",
      "DataFields": [
        {
          "Source": "PropertyId",
          "Keys": [ "Value" ],
          "Label": "{IdentifyingValue} {FirstKey} {Uom}",
		  "IncludeUom": "false"
        }
      ]
    }
  ]
}
```

The resulting data view in standard mode:
| Timestamp            | Value kW |
|----------------------|----------|
| 2020-11-06T08:00:00Z | 1.21     |

The resulting data view in narrow mode:
| Timestamp            | Field    | Value |
|----------------------|----------|-------|
| 2020-11-06T08:00:00Z | Value kW | 1.21  |

