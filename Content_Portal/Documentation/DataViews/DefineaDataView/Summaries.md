---
uid: DataViewsSummaries
---

# Display calculated summaries (coming soon)


*Note: This topic covers features that are not yet generally available. If you are interested in trialing these pre-release features, contact your account team for more details.*

Data views can be configured to show calculated summaries for streams and assets.  “Calculated summaries” is defined as the summary types enumerated in [SdsSummaryType](https://ocs-docs.osisoft.com/Content_Portal/Documentation/SequentialDataStore/Reading_Data_API.html#get-summaries). This topic describes how to include summaries in a data view. 

# Available summaries
Summary types are treated as a platform intrinsic, as is done by Sds and Assets. A stream and its properties provide no information about what summaries are available for each property; 
for example the caller simply requests summary data and is given whatever summaries are available.  Unavailable summaries are simply excluded from the result set. If a data item field requests a summary that is unavailable (e.g. Mean of a string property), 
the Mean summary values  in the data view data will be null.  

# Including summaries in a dataview
Users may include any mix of interpolated or summary data fields in a data view. Multiple summary types for a stream property or an asset are requested by defining a field for each desired summary type. Units of measure can also be included for a summary.

In the data view a field defines the type of summary with the SummaryType property as [SdsSummaryType](https://ocs-docs.osisoft.com/Content_Portal/Documentation/SequentialDataStore/Reading_Data_API.html#get-summaries). Another property, SummaryDirection, allows the “summary’s direction” to be defined as [SummaryDirection](xref:ResolvedDataView#SummaryDirection-enumeration). SummaryDirection controls whether the start or end index of the summary is used by the data view to calculate the summary values.
If the SummaryType is "None", the SummaryDirection (if specified) will be accepted but ignored. If the SummaryType is not "None", and SummaryDirection is not specified, it will be initialized to "Forward". 

The label tokens: \{SummaryType\} and \{SummaryDirection\} will resolve in the field mappings and show in dataview table header columns for a summary field.

# Example
This simple example shows the inclusion of a summary data field for a SummaryType set to "Mean", SummaryDirection set to "Backward" and "IncludeUom" is set to "true". The label includes two summary tokens that will resolve to the summary type and direction in the data view header.
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
          "Label": "{IdentifyingValue} {FirstKey} {SummaryType} {SummaryDirection}",
          "SummaryType": "Mean",
          "SummaryDirection": "Backward",
          "IncludeUom": "true"
        }
      ]
    }
  ]
}
```
The resulting data view in standard mode:
| Timestamp            | Value Mean Backward | Mean Backward Uom |
|----------------------|-------|-----------|
| 2020-11-06T08:00:00Z | .899  | kW        |

The resulting data view in narrow mode:
| Timestamp            | Field | Value | Uom |
|----------------------|-------|-------|-----|
| 2020-11-06T08:00:00Z |  Value Mean Backward | .899  | kW  |

