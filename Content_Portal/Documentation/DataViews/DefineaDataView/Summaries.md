---
uid: DataViewsSummaries
---

# Display calculated summaries (coming soon)


*Note: This topic covers features that are not yet generally available. If you are interested in trialing these pre-release features, contact your account team for more details.*

Data views can be configured to show calculated summaries for streams and assets.  �Calculated summaries� is defined as the summary types enumerated in [SdsSummaryType](xref:sdsReadingDataApi#get-summaries#get-summaries). This topic describes how to include summaries in a data view. 

# Available summaries
Not all SDS properties will have summaries. For example a string property has no Mean value. If a data item field requests a summary that is unavailable these values will be null in the view data.  

# Including summaries in a dataview
Users may include any mix of interpolated or summary data fields in a data view. Multiple summary types for a stream property or an asset are requested by defining a field for each desired summary type. Units of measure can also be included for a summary, if applicable, not all summaries do (e.g. Kurtosis and Skewness).

In the data view a data field defines the type of summary with the SummaryType property as [SdsSummaryType](xref:sdsReadingDataApi#get-summaries#get-summaries). Another property, SummaryDirection, allows the �summary�s direction� to be defined as [SummaryDirection](xref:ResolvedDataView#SummaryDirection-enumeration). SummaryDirection controls whether the start or end index of the summary is used by the data view to calculate the summary values.
If the SummaryType is "None", the SummaryDirection (if specified) will be accepted but ignored. If the SummaryType is not "None", and SummaryDirection is not specified, it will be initialized to "Forward". 

The label tokens: \{SummaryType\} and \{SummaryDirection\} will resolve in the field mappings and show in dataview table header columns for a summary field.

# Example: Include summary in data view
This simple example shows the inclusion of a summary data field for a SummaryType set to "Mean" with "IncludeUom" set to "true". Since the SummaryDirection is not specified, the default value of "Forward" is used. The label includes two summary tokens that will resolve to the summary type and direction in the data view header.
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
          "IncludeUom": "true"
        }
      ]
    }
  ]
}
```
The resulting data view in standard mode:
| Timestamp            | Value Mean Forward | Value Mean Forward Uom |
|----------------------|-------|-----------|
| 2020-11-06T08:00:00Z | .899  | kW        |

The resulting data view in narrow mode:
| Timestamp            | Field | Value | Uom |
|----------------------|-------|-------|-----|
| 2020-11-06T08:00:00Z |  Value Mean Forward | .899  | kW  |

# Example: Impact of summary direction

This simple example shows the impact of SummaryDirection, and how changing it will shift the summary value calculation. Three mini data view results are shown, where SummaryType and SummaryDirection are varied.

Example #1: SummaryType = "None"

| Timestamp            | Value | 
|----------------------|-------|
|2020-11-01T00:01:00Z  | 10    | 
|2020-11-01T00:02:00Z | 100  | 
|2020-11-01T00:03:00Z | 1000  |

Example #2: SummaryType = "Mean" & SummaryDirection = "Forward"

In the "Forward" direction, the start index anchors the calculation direction. The first mean value of 55, is the mean of all the values between the first and second index. The second mean value of 550 is the mean of all the values between the second and third index.

| Timestamp            | Value Mean Forward |
|----------------------|-------|
|2020-11-01T00:01:00Z  | 55    | 
|2020-11-01T00:02:00Z | 550  | 
|2020-11-01T00:03:00Z | 1000  |

Example #3: SummaryType = "Mean" & SummaryDirection = "Backward"

In the "Backward" direction, the last index anchors the calculation direction. The last mean value of 550, is the mean value of all the values between the last and second index. The second mean value of 55 is the mean value of all the values between the second and first index. 

| Timestamp            | Value Mean Backward |
|----------------------|-------|
|2020-11-01T00:01:00Z  | 10    | 
|2020-11-01T00:02:00Z | 55  | 
|2020-11-01T00:03:00Z | 550