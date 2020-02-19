---
uid: DataViewsSectioning
---

# Sectioning

The data items of a data view may be organized by grouping them. This is called _sectioning_. It is one way of producing a meaningful, consumable shape of data.


## Purpose of sectioning
Without sectioning, all of the data items returned by a `Query` will appear side-by-side. If the view includes many data items, its data records will be enormous. The fields are also likely to be ambiguous.

"[Distinguishing](xref:DataViewsFieldSets)" the items within each field set is one way to disambiguate the fields, but only one `Field` may be a distinguisher. What if multiple metadata `Field`s are required to fully describe each data item? The [example below](xref:DataViewsSectioning#example-scenario) shows exactly that case: power inverters that are described by a Site, Meter, and number. Sectioning can organize the data items into shapes that are consumable and/or represent a physical asset.

## How it works
To section a data view, specify one or more `Field` objects as the `DataView`'s `.Sectioners`. 

### Eligible sectioner fields
Fields whose values come from data item `FieldSource.Id`, `FieldSource.Name`, `FieldSource.Metadata`, or `FieldSource.Tags` are eligible to be used as sectioners. 

### Displaying the sectioner values
If a data view has any sectioners specified, then a special type of field set is available: `FieldSetSourceType.SectionValue`. Its fields serve as robust pass-throughs to whatever the data view's sectioners currently are. It also avoids repetitive inclusion of sectioner values in the case where a section contains multiple data items.

## Uses of sectioning
Sectioning can be used to separate the data items from each other, and to join different types of data items together.

### Separating data items
Separating the data items from each other makes the data view's data records smaller and more granular. It is also possible to produce shapes that mimic physical or logical assets.

#### Example scenario
For the following examples, assume a subsection of the [example scenario](xref:DataViewsExampleScenario)'s power inverter streams, produced by a `Query` [value](xref:sdsSearching) such as `"TypeId:docs-pi-inverter AND (Site:Rosemont OR Site:Winterthur)"`. This is to keep the example succinct.


| Site | Meter | Inverter | Measurement | Stream Id |
|--|--|--|--|--|
| Rosemont | Primary | 0 | Power In | ROSE.Meter.Primary.Inverter.0.PwrIn |
| Rosemont | Primary | 0 | Power Out | ROSE.Meter.Primary.Inverter.0.PwrOut |
| Rosemont | Primary | 1 | Power In | ROSE.Meter.Primary.Inverter.1.PwrIn |
| Rosemont | Primary | 1 | Power Out | ROSE.Meter.Primary.Inverter.1.PwrOut |
| Winterthur | Primary | 0 | Power In | WINT.Meter.Primary.Inverter.0.PwrIn |
| Winterthur | Primary | 0 | Power Out | WINT.Meter.Primary.Inverter.0.PwrOut |
| Winterthur | Secondary | 0 | Power In | WINT.Meter.Secondary.Inverter.0.PwrIn |
| Winterthur | Secondary | 0 | Power Out | WINT.Meter.Secondary.Inverter.0.PwrOut |

#### Example: No sectioning
Let us start with a simple data view. It queries for the aforementioned streams, and includes the "Value" property of each stream.

```json
{
  "Id": "quickstart",
  "Queries": [
    { 
      Id: "inverters",
      Value: "TypeId:docs-pi-inverter AND (Site:Rosemont OR Site:Winterthur)"
    }
  ],
  "FieldSets": [
    {
      "SourceType": "Index",
      "Fields": [
        {
          "Label": "Timestamp"
        }
      ]
    },
    {
      "SourceType": "DataItem",
      "QueryId": "inverters",
      "Fields": [
        {
          "Source": "PropertyId",
          "Keys": [ "Value" ],
          "Label": "{DistinguisherValue} {FirstKey}"
        }
      ],
    }
  ]
}
```
Unfortunately, the initial result is not very usable. The fields are ambiguous (eight fields are simply labelled "Value"), and the size of each data record is tied to the number of inverter streams found by the query.

| Timestamp | Value | Value | Value | ... | 
|--|--|--|--|--|--|
| - | ROSE.Meter.Primary.Inverter.0.PwrIn/Value | ROSE.Meter.Primary.Inverter.0.PwrOut/Value | ROSE.Meter.Primary.Inverter.1.PwrIn/Value | ... |

#### Example: Complete uniqueness, sectioning by data item id

A simple way of disambiguating the data items is to section them by data item id. This example includes two actions:

- Add data item id as a sectioner
- Include fields for metadata: Site, Meter, Inverter, Measurement.

```json
{
  "Id": "quickstart",
  "Queries": [
    { 
      Id: "inverters",
      Value: "TypeId:docs-pi-inverter AND (Site:Rosemont OR Site:Winterthur)"
    }
  ],
  "Sectioners": [
    {
          "Source": "Id",
          "Label": "{DistinguisherValue} {FirstKey}"
    },
  ],
  "FieldSets": [
    {
      "SourceType": "Index",
      "Fields": [
        {
          "Label": "Timestamp"
        }
      ]
    },
    {
      "SourceType": "DataItem",
      "QueryId": "inverters",
      "Fields": [
        {
          "Source": "Metadata",
          "Keys": [ "Site" ],
          "Label": "{DistinguisherValue} {FirstKey}"
        },
        {
          "Source": "Metadata",
          "Keys": [ "Meter" ],
          "Label": "{DistinguisherValue} {FirstKey}"
        },
        {
          "Source": "Metadata",
          "Keys": [ "Inverter" ],
          "Label": "{DistinguisherValue} {FirstKey}"
        },
        {
          "Source": "Metadata",
          "Keys": [ "Measurement" ],
          "Label": "{DistinguisherValue} {FirstKey}"
        },
        {
          "Source": "PropertyId",
          "Keys": [ "Value" ],
          "Label": "{DistinguisherValue} {FirstKey}"
        }
      ],
    }
  ]
}
```
The result is much closer to being usable. The records are no longer ambiguous. However, they do not mirror any physical or logical asset.

| Timestamp | Site | Meter | Inverter | Measurement | Value |
|--|--|--|--|--|--|
| - | "Rosemont" | "Primary" | "0" | "Power In" |  ROSE.Meter.Primary.Inverter.0.PwrIn/Value |
| - | "Rosemont" | "Primary" | "0" | "Power Out" |ROSE.Meter.Primary.Inverter.0.PwrOut/Value |
| - | "Rosemont" | "Primary" | "1" | "Power In" |ROSE.Meter.Primary.Inverter.1.PwrIn/Value |
| - | "Rosemont" | "Primary" | "1" | "Power Out" |ROSE.Meter.Primary.Inverter.1.PwrOut/Value |
| - | "Winterthur" | "Primary" | "0" | "Power In" |WINT.Meter.Primary.Inverter.0.PwrIn/Value |
| - | "Winterthur" | "Primary" | "0" | "Power Out" |WINT.Meter.Primary.Inverter.0.PwrOut/Value |
| - | "Winterthur" | "Secondary" | "0" | "Power In" |WINT.Meter.Secondary.Inverter.0.PwrIn/Value |
| - | "Winterthur" | "Secondary" | "0" | "Power Out" |WINT.Meter.Secondary.Inverter.0.PwrOut/Value |

#### Example: Data records that reflect real-world assets
Instead of sectioning by data item id, let us section by metadata. This example uses:

- the `Field`s for Site, Meter, and Inverter metadata as the data view's `.Sectioners`
- a `FieldSet` of `.SourceType` `FieldSetSourceType.SectionValue`, with a `Field` to show each sectioner's value
- the `Field` for Measurement metadata as the data item `FieldSet`'s `.Distinguisher`

```json
{
  "Id": "quickstart",
  "Queries": [
    { 
      Id: "inverters",
      Value: "TypeId:docs-pi-inverter AND (Site:Rosemont OR Site:Winterthur)"
    }
  ],
  "Sectioners": [
        {
          "Source": "Metadata",
          "Keys": [ "Site" ],
          "Label": "{DistinguisherValue} {FirstKey}"
        },
        {
          "Source": "Metadata",
          "Keys": [ "Meter" ],
          "Label": "{DistinguisherValue} {FirstKey}"
        },
        {
          "Source": "Metadata",
          "Keys": [ "Inverter" ],
          "Label": "{DistinguisherValue} {FirstKey}"
        }
  ],
  "FieldSets": [
    {
      "SourceType": "Index",
      "Fields": [
        {
          "Label": "Timestamp"
        }
      ]
    },
    {
      "SourceType": "SectionValue",
      "Fields": [
        {
          "Source": "None",
          "Keys": [ "0" ],
          "Label": "{SectionerLabel}"
        },
        {
          "Source": "None",
          "Keys": [ "1" ],
          "Label": "{SectionerLabel}"
        },
        {
          "Source": "None",
          "Keys": [ "2" ],
          "Label": "{SectionerLabel}"
        }
      ]
    },
    {
      "SourceType": "DataItem",
      "QueryId": "inverters",
      "Distinguisher": {
          "Source": "Metadata",
          "Keys": [ "Measurement" ],
          "Label": "{DistinguisherValue} {FirstKey}"
        },
      "Fields": [
        {
          "Source": "PropertyId",
          "Keys": [ "Value" ],
          "Label": "{DistinguisherValue} {FirstKey}"
        }
      ],
    }
  ]
}
```
The resulting data mappings reflect the data on a per-inverter basis, mirroring the physical asset:

| Timestamp | Site | Meter | Inverter | Power In Value | Power Out Value |
|--|--|--|--|--|--|
| - | "Rosemont" | "Primary" | "0" |  ROSE.Meter.Primary.Inverter.0.PwrIn/Value | ROSE.Meter.Primary.Inverter.0.PwrOut/Value |
| - | "Rosemont" | "Primary" | "1" | ROSE.Meter.Primary.Inverter.1.PwrIn/Value |ROSE.Meter.Primary.Inverter.1.PwrOut/Value |
| - | "Winterthur" | "Primary" | "0" | WINT.Meter.Primary.Inverter.0.PwrIn/Value | WINT.Meter.Primary.Inverter.0.PwrOut/Value |
| - | "Winterthur" | "Secondary" | "0" | WINT.Meter.Secondary.Inverter.0.PwrIn/Value | WINT.Meter.Secondary.Inverter.0.PwrOut/Value |

**Note:** Sectioning by Meter and Inverter overcomes the differences across Sites: not every site has a Secondary meter, and not every Meter has the same number of Inverters. This is not a problem.

### Associating data items with each other
Another use of sectioning is to "join" the data items returned by different queries, such as adding weather data for each power inverter.

#### Example: Adding weather data to the real-world assets
This example includes two actions:

- Add a second `Query` for "site weather"
- Add a new `FieldSet` for the data items from the "site weather" query, with `Field`s for "SolarRadiation" and "Temperature"

```json
{
  "Id": "quickstart",
  "Queries": [
    { 
      Id: "inverters",
      Value: "TypeId:docs-pi-inverter AND (Site:Rosemont OR Site:Winterthur)"
    },
    { 
      Id: "site weather",
      Value: "TypeId:docs-omf-weather* AND (Site:Rosemont OR Site:Winterthur)"
    }
  ],
  "Sectioners": [
        {
          "Source": "Metadata",
          "Keys": [ "Site" ],
          "Label": "{DistinguisherValue} {FirstKey}"
        },
        {
          "Source": "Metadata",
          "Keys": [ "Meter" ],
          "Label": "{DistinguisherValue} {FirstKey}"
        },
        {
          "Source": "Metadata",
          "Keys": [ "Inverter" ],
          "Label": "{DistinguisherValue} {FirstKey}"
        }
  ],
  "FieldSets": [
    {
      "SourceType": "Index",
      "Fields": [
        {
          "Label": "Timestamp"
        }
      ]
    },
    {
      "SourceType": "SectionValue",
      "Fields": [
        {
          "Keys": [ "0" ],
          "Label": "{SectionerLabel}"
        },
        {
          "Keys": [ "1" ],
          "Label": "{SectionerLabel}"
        },
        {
          "Keys": [ "2" ],
          "Label": "{SectionerLabel}"
        }
      ]
    },
    {
      "SourceType": "DataItem",
      "QueryId": "inverters",
      "Distinguisher": {
          "Source": "Metadata",
          "Keys": [ "Measurement" ],
          "Label": "{DistinguisherValue} {FirstKey}"
        },
      "Fields": [
        {
          "Source": "PropertyId",
          "Keys": [ "Value" ],
          "Label": "{DistinguisherValue} {FirstKey}"
        }
      ],
    },
    {
      "SourceType": "DataItem",
      "QueryId": "site weather",
      "Fields": [
        {
          "Source": "PropertyId",
          "Keys": [ "SolarRadiation" ],
          "Label": "{DistinguisherValue} {FirstKey}"
        },
        {
          "Source": "PropertyId",
          "Keys": [ "Temperature", "AmbientTemperature" ],
          "Label": "{DistinguisherValue} {FirstKey}"
        }
      ]
    }
  ]
}
```

This "join" works because inverters and weather stations have common metadata: _Site_.

| Timestamp | Site | Meter | Inverter | Power In Value | Power Out Value | SolarRadiation | Temperature |
|--|--|--|--|--|--|--|--|
| - | "Rosemont" | "Primary" | "0" |  ROSE.Meter.Primary.Inverter.0.PwrIn/Value | ROSE.Meter.Primary.Inverter.0.PwrOut/Value | WS_ROSE/SolarRadiation | WS_ROSE/Temperature |
| - | "Rosemont" | "Primary" | "1" | ROSE.Meter.Primary.Inverter.1.PwrIn/Value |ROSE.Meter.Primary.Inverter.1.PwrOut/Value | WS_ROSE/SolarRadiation | WS_ROSE/Temperature |
| - | "Winterthur" | "Primary" | "0" | WINT.Meter.Primary.Inverter.0.PwrIn/Value | WINT.Meter.Primary.Inverter.0.PwrOut/Value | WS_WINT/SolarRadiation | WS_WINT/AmbientTemperature |
| - | "Winterthur" | "Secondary" | "0" | WINT.Meter.Secondary.Inverter.0.PwrIn/Value | WINT.Meter.Secondary.Inverter.0.PwrOut/Value | WS_WINT/SolarRadiation | WS_WINT/AmbientTemperature |
