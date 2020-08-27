---
uid: DataViewsQuickStartDefine
---

# Define a data view
The `DataView` object is a declarative query and shape for stream data. This section describes the `DataView` object. See the [Data View API section](xref:DataViewAPI) for the corresponding API routes.  

At times, this section makes reference to ways the view *resolves* into further resources, such as the collection of data items found by each data item query. See the [Resolved Data View](xref:ResolvedDataView) and [Resolved Data View API](xref:ResolvedDataViewAPI) sections for details.

## General concepts
You define multiple aspects of a data view when you define it, including data items and their organization, grouping, and shaping. 

### Define a data view identifier
A data view must have a unique identifier. It may have a friendly name and description. If a friendly name is not specified, the identifier will be used as the data view's name.

### Include data items
One or more queries determine the set of data items (such as SDS streams) that the data view will include. Each [Query](xref:DataViewsQueries) should represent a collection of like streams. To include streams that represent very different items, such as power inverters and weather stations, use separate queries.

### Include data fields

Information from, or about, those data items must be included explicitly in the data view as Fields within [DataFields](xref:DataViewsFieldSets) or [GroupingFields](xref:DataViewsGrouping). By default, a data view includes no fields, except the default [IndexField](#include-the-index-field).

The fields that are available for use are exposed as a "resolved" resource, [Available Field Sets](xref:DataViewsAvailableFieldSets). It is recommended to use or adapt those fields instead of defining new fields. Individual fields are organized into [DataFieldSets](xref:DataViewsFieldSets) and [GroupingFields](xref:DataViewsGrouping).

### Group the data items

Data items may be [grouped](xref:DataViewsGrouping), which amounts to grouping or partitioning them by one or more field values. To group data items in a data view, define one or more fields as `.GroupingFields` of the data view. This is one way of producing a meaningful, consumable shape of data.

### Organize the data fields
Field sets and fields resolve in the order they are defined. They may be re-ordered.

Within each group, a field set may be associated with multiple data items. It is often necessary to disambiguate these items. If a group contains multiple data items from the same query, you may wish to identify those data items so that they are not ambiguous and so they will be aligned across groups. Items can be disambiguated by specifying an [`.IdentifyingField`](xref:DataViewsFieldSets#identifying-field). An identifying field is a field that differentiates the data items within a group, such as the value of _Measurement_ metadata (i.e., the data items are identified by what they measure). Identifying data items also allows the data views engine to "align" them across groups, since it is clear, for example, that streams measuring _Power Out_ and streams measuring _Power In_ are alike. Ensure that each data field's label includes the {IdentifyingValue} token so the field labels are unique. The default field labels already include it.

### Include the index field
The field used for indexing.  If not specified, a default value with a label of "Timestamp" is applied. If specified, a label is required. Field source and keys are not applicable for index field.

### Define index type and default range
Data views currently operate on timestamped data, which is data indexed by a DateTime property. This is reflected by the `.IndexTypeCode` of the DataView, whose value must be "DateTime". Default values may be defined for the start index, end index, and/or interval used when data view data is queried.

### Define data view shape
Data views may be set to resolve as standard shape or narrow shape. Standard shape resolves fields similar to how they are defined. Narrow shape pivots the fields vertically, resulting in a view whose schema is independent of what data items (streams) are resolved by the data view. Narrow shape may be used when an invariant output schema is required.

## Recommended workflow
This is an introduction to the recommended workflow for defining data views. The following sections show these concepts in action.

Designing and tweaking a data view is expected to be an iterative process. You are not expected to "get it right the first time," nor to be an expert at the streams available in the Sequential Data Store. Data views provide an interactive way to select, identify, and arrange the data you and your applications need.

There are three main steps required to define a data view: 
1. Including data items (streams)
2. Including specific data fields
3. Arranging them within the data view.

This is not a one-way street. You are likely to keep adjusting the data fields included in the view even after you have begun working on how the fields are arranged in the data view.


## Procedure: Define a data view

This section presents the main concepts behind creating data views.

It is assumed that you are working with streams as described in the [Stream examples](xref:DataViewsExampleScenario). The data views API uses the same authentication scheme as the Sequential Data Store.

### Create a data view
Very little information is required to create a new data view. In fact, if you request that the system generate an identifier for the new data view, no information at all is necessary. However, it is recommended to specify a meaningful `.Id`, because the identifier cannot be changed later without recreating the data view. All other properties are modifiable.

This data view does not accomplish anything yet, but it's a starting point.

#### Action
```json
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart
{ 
  "Id": "quickstart" 
}
```

#### Expected result
A data view with very few properties populated: `.Id`, `.Name`, `IndexField` (default: `{ "Label": "Timestamp" }`), `.IndexTypeCode` (default: `"DateTime"`), Shape (default: `DataViewShape.Standard`, which as a string is `"Standard"`).
```json
HTTP 201 Created
{
  "Id": "quickstart",
  "Name": "quickstart",
  "IndexField": { "Label": "Timestamp" },
  "Queries": [],
  "DataFieldSets": [],
  "GroupingFields": [],
  "IndexTypeCode": "DateTime",
  "Shape": "Standard"
}
```

The `.Queries` property is empty, `[ ]`. We will address that soon. 

### Retrieve the data view
To access the data view again, it is available via the `GET` verb:

#### Action
```text
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart
```

#### Expected result
```json
HTTP 200 OK
{
  "Id": "quickstart",
  "Name": "quickstart",
  "IndexField": { "Label": "Timestamp" },
  "Queries": [],
  "DataFieldSets": [],
  "GroupingFields": [],
  "IndexTypeCode": "DateTime",
  "Shape": "Standard"
}
```

### Add a query for data items

Creating a data view begins with including some data items: today, those are SDS Streams.

#### Action
Use the result of the previous step as the starting point. All following steps will involve modifying the data view definition, or seeing the effects of those modifications.

Add an item to the array of `.Queries`: `{ "Id": "weather", "Value":"*weather*" }`
```json
PUT /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart
{
  "Id": "quickstart",
  "Name": "quickstart",
  "IndexField": { "Label": "Timestamp" },
  "Queries": [
    { 
      "Id": "weather",
      "Value":"*weather*" 
    }
  ],
  "DataFieldSets": [],
  "GroupingFields": [],
  "IndexTypeCode": "DateTime",
  "Shape": "Standard"
}
```

#### Expected result
```text
HTTP 204 No Content
```

### View items found by the query

Data views resolve on a per user basis, executing the queries you defined. The results are available in several “resolved” resources.

#### Action – Page through the data items found by the query
```text
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart/Resolved/DataItems/weather
```

#### Expected result
An array of the data items matching the query, whose index type is "DateTime" (matching the Data View’s IndexTypeCode)

```json
HTTP 200 OK
{
    "TimeOfResolution": "(a timestamp in ISO8601 format)",
    "Items": [
        {
            "Id": "WS_BILT",
            "Name": "WS_BILT",
            "TypeId": "docs-omf-weather-gen1",
            "ResourceType": "Stream",
            "Tags": [
                "Weather",
                "High Resolution",
                "Gen1"
            ],
            "Metadata": {
                "Site": "Biltmore"
            },
            "DataItemFields": [
                {
                    "Id": "Timestamp",
                    "Name": "Timestamp",
                    "TypeCode": "DateTime",
                    "IsKey": true
                },
                {
                    "Id": "SolarRadiation",
                    "Name": "Solar Radiation",
                    "TypeCode": "Int32",
                    "IsKey": false
                },
                {
                    "Id": "Temperature",
                    "Name": "Temperature",
                    "TypeCode": "Double",
                    "IsKey": false
                }
            ]
        },
        {
            "Id": "WS_ROSE",
            "Name": "WS_ROSE",
            "TypeId": "docs-omf-weather-gen1",
            "ResourceType": "Stream",
            "Tags": [
                "Weather",
                "Low Resolution",
                "Gen1"
            ],
            "Metadata": {
                "Site": "Rosecliff"
            },
            "DataItemFields": [
                {
                    "Id": "Timestamp",
                    "Name": "Timestamp",
                    "TypeCode": "DateTime",
                    "IsKey": true
                },
                {
                    "Id": "SolarRadiation",
                    "Name": "Solar Radiation",
                    "TypeCode": "Int32",
                    "IsKey": false
                },
                {
                    "Id": "Temperature",
                    "Name": "Temperature",
                    "TypeCode": "Double",
                    "IsKey": false
                }
            ]
        },
        {
            "Id": "WS_WINT",
            "Name": "WS_WINT",
            "TypeId": "docs-omf-weather-gen2",
            "ResourceType": "Stream",
            "Tags": [
                "Weather",
                "High Resolution",
                "Gen2"
            ],
            "Metadata": {
                "Site": "Winterthur"
            },
            "DataItemFields": [
                {
                    "Id": "Timestamp",
                    "Name": "Timestamp",
                    "TypeCode": "DateTime",
                    "IsKey": true
                },
                {
                    "Id": "SolarRadiation",
                    "Name": "Solar Radiation",
                    "TypeCode": "Int32",
                    "IsKey": false
                },
                {
                    "Id": "AmbientTemperature",
                    "Name": "Ambient Temperature",
                    "TypeCode": "Double",
                    "IsKey": false
                },
                {
                    "Id": "CloudCover",
                    "Name": "Cloud Cover",
                    "TypeCode": "Int32",
                    "IsKey": false
                 }
             ]
         }
     ]
}
```

#### Action – Page through the ineligible data items found by the query
```text
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart/Resolved/IneligibleDataItems/weather
```

#### Expected result
An array of the data items matching the query, but whose index type is not "DateTime" and thus not eligible for inclusion in the data view.

With the example streams, this collection is empty.
```json
HTTP 200 OK
{
  "TimeOfResolution": "(a timestamp in ISO 8601 format)",
  "Items": []
}
```

### View fields available to include in the data view

#### Action
```text
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart/Resolved/AvailableFieldSets
```

#### Expected result
A field set with a source type of "DataItem" pointing to the query identified by "weather". Assuming some data items were retrieved, this field set shows that attributes of the streams (id, name, tags) are available, as well as the values of all metadata keys and properties.

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
                        "SolarRadiation"
                    ],
                    "Label": "{IdentifyingValue} {FirstKey}"
                },
                {
                    "Source": "PropertyId",
                    "Keys": [
                        "Temperature"
                    ],
                    "Label": "{IdentifyingValue} {FirstKey}"
                },
                {
                    "Source": "Metadata",
                    "Keys": [
                        "Site"
                    ],
                    "Label": "{IdentifyingValue} {FirstKey}"
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
                }
            ]
        }
    ]
}
```

### Include some of the available fields
At this point, if you query for data, the table only contains the `IndexField` – because no fields have been included in the data view. Including fields is a deliberate action, albeit one that is intended to be easy.

#### Action
For ease, grab all of the field sets that are available. 

Set the data view’s `DataFieldSets` property as the contents of the `AvailableFieldSets` response.
```json
PUT /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart
{
  "Id": "quickstart",
  "Name": "quickstart",
  "IndexField": { "Label": "Timestamp" },
  "Queries": [
    { 
      "Id": "weather",
      "Value":"*weather*" 
    }
  ],
  "DataFieldSets": [
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
                        "SolarRadiation"
                    ],
                    "Label": "{IdentifyingValue} {FirstKey}"
                },
                {
                    "Source": "PropertyId",
                    "Keys": [
                        "Temperature"
                    ],
                    "Label": "{IdentifyingValue} {FirstKey}"
                },
                {
                    "Source": "Metadata",
                    "Keys": [
                        "Site"
                    ],
                    "Label": "{IdentifyingValue} {FirstKey}"
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
                }
            ],
       },
  ],
  "GroupingFields": [],
  "IndexTypeCode": "DateTime",
  "Shape": "Standard"
}
```
#### Expected Result
```text
HTTP 204 No Content
```

Now, if we return to the available field sets, all data fields are used so none are available.

#### Action
```text
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart/Resolved/AvailableFieldSets
```

#### Expected result
No available data fields.

```json
{
    "TimeOfResolution": "(a timestamp in ISO 8601 format)",
    "Items": []
}
```
And if we request data, the table contains multiple fields in addition to the `IndexField`.

#### Action
```text
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart/Data/Interpolated
?startIndex={your_val_here}&endIndex={your_val_here}&interval={your_val_here}
```

#### Expected result
An array of json values similar to:
```json
[
    {
        "Timestamp.0": "2019-10-21T18:00:00Z",
        "Id.1": "WS_BILT",
        "Name.2": "WS_BILT",
        "AmbientTemperature.3": null,
        "CloudCover.4": null,
        "SolarRadiation.5": 165,
         "Temperature.6": 33.589619124193831,
        "Site.7": "Biltmore",
        "Tags.8": "Weather, High Resolution, Gen1",
        "Id.9": "WS_ROSE",
        "Name.10": "WS_ROSE",
        "AmbientTemperature.11": null,
        "CloudCover.12": null,
        "SolarRadiation.13": 132,
        "Temperature.14": 14.537369185607899,
        "Site.15": "Rosecliff",
        "Tags.16": "Weather, Low Resolution, Gen1",
        "Id.17": "WS_WINT",
        "Name.18": "WS_WINT",
        "AmbientTemperature.19": 1.0805517883941373,
        "CloudCover.20": 2,
        "SolarRadiation.21": 108,
        "Temperature.22": null,
        "Site.23": "Winterthur",
        "Tags.24": "Weather, High Resolution, Gen2"
    },
]
```

There was ambiguity in the field mapping identifiers, so the data views engine suffixed each field mapping id ordinally.

The suffixing (to ensure uniqueness) is done for the sake of client behavior, as it is not expected that ambiguity is an acceptable outcome. The remaining steps show two approaches for disambiguating the content of a data view. 

#### Action – Want csv?
Resubmit the data query with an additional query parameter, `&form=csvh`
```text
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart/Data/Interpolated
?startIndex={your_val_here}&endIndex={your_val_here}&interval={your_val_here}&form=csvh
```

#### Expected result
Rows of CSV values similar to:
```csv
Timestamp.0,Id.1,Name.2,AmbientTemperature.3,CloudCover.4,SolarRadiation.5,Temperature.6,Site.7,Tags.8,Id.9,Name.10,AmbientTemperature.11,CloudCover.12,SolarRadiation.13,Temperature.14,Site.15,Tags.16,Id.17,Name.18,AmbientTemperature.19,CloudCover.20,SolarRadiation.21,Temperature.22,Site.23,Tags.24
2019-10-21T18:00:00.0000000Z,WS_BILT,WS_BILT,,,165,33.58961912,Biltmore,"Weather, High Resolution, Gen1",WS_ROSE,WS_ROSE,,,132,14.53736919,Rosecliff,"Weather, Low Resolution, Gen1",WS_WINT,WS_WINT,1.080551788,2,108,,Winterthur,"Weather, High Resolution, Gen2"
2019-10-21T20:00:00.0000000Z,WS_BILT,WS_BILT,,,157,32.41209639,Biltmore,"Weather, High Resolution, Gen1",WS_ROSE,WS_ROSE,,,139,14.76498991,Rosecliff,"Weather, Low Resolution, Gen1",WS_WINT,WS_WINT,2.501105722,3,109,,Winterthur,"Weather, High Resolution, Gen2"
```

### Group the data view
One way to disambiguate the data items is to “group” them, which amounts to partitioning them based on a value. For example, metadata:Site as the grouping field might yield groups of Biltmore, Rosecliff, and Winterthur, each containing the data items associated with that Site.

You may use multiple grouping fields. This is effectively “group by X then Y then Z”

Grouping fields are a property of the data view, and are an array of `Field` objects. This means the same Field objects contained in the available or included field sets may be reused directly as grouping fields.

#### Action
To group by metadata, copy the field in the `DataView` object with `{ Source: “Metadata”, Keys: [ "Site" ] }`, and add it to the array of `.GroupingFields`.

```json
PUT /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart
{
  "Id": "quickstart",
  "Name": "quickstart",
  "IndexField": { "Label": "Timestamp" },
  "Queries": [
    { 
      "Id": "weather",
      "Value":"*weather*" 
    }
  ],
  "DataFieldSets": [
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
                        "SolarRadiation"
                    ],
                    "Label": "{IdentifyingValue} {FirstKey}"
                },                
		{
                    "Source": "PropertyId",
                    "Keys": [
                        "Temperature"
                    ],
                    "Label": "{IdentifyingValue} {FirstKey}"
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
                }
            ],
       },
  ],
  "GroupingFields": [
    {
      "Source": "Metadata",
      "Keys": [
        "Site" 
      ],
      "Label": "{IdentifyingValue} {FirstKey}"
    }
  ],
  "IndexTypeCode": "DateTime",
  "Shape": "Standard"
}
```

#### Expected result
```text
HTTP 204 No Content
```

#### Action
```text
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart/Data/Interpolated
?startIndex={your_val_here}&endIndex={your_val_here}&interval={your_val_here}
```

#### Expected result
Data that looks a bit different now. In table terms, the data table would be ultra-skinny instead of ultra-wide.

```json
HTTP 200 OK
[
    {
        "Timestamp": "2019-10-21T18:00:00Z",
        "Site": "Biltmore",
        "Id": "WS_BILT",
        "Name": "WS_BILT",
        "AmbientTemperature": null,
        "CloudCover": null,
        "SolarRadiation": 165,
        "Temperature": 33.589619124193831,
        "Tags": "Weather, High Resolution, Gen1"
    },
    ... 
    (rest of the values for Site:Biltmore), then
    ...
    {
        "Timestamp": "2019-10-21T18:00:00Z",
        "Site": "Rosecliff",
        "Id": "WS_ROSE",
        "Name": "WS_ROSE",
        "AmbientTemperature": null,
        "CloudCover": null,
        "SolarRadiation": 132,
        "Temperature": 14.537369185607899,
        "Tags": "Weather, Low Resolution, Gen1"
    },
    ... 
    (rest of the values for Site:Rosecliff), then
    ...
    {
        "Timestamp": "2019-10-21T18:00:00Z",
        "Site": "Winterthur",
        "Id": "WS_WINT",
        "Name": "WS_WINT",
        "AmbientTemperature": 1.0805517883941373,
        "CloudCover": 2,
        "SolarRadiation": 108,
        "Temperature": null,
        "Tags": "Weather, High Resolution, Gen2"
    },
    ... 
    (rest of the values for Site:Winterthur)
]
```

**Note:** The Data Views product does not assume an intention for ultra-skinny output.

### Identify data items

A different and complementary way of disambiguating the data items is to “identify” them within the field set.

This is also useful for aligning data items across groups. Imagine if each site had an additional stream from a backup weather station:

| Timestamp |	Site |	Primary Temperature | Primary SolarRadiation | Backup Temperature | Backup SolarRadiation
|--|--|--|--|--|--|
| | Biltmore						
| | Rosecliff
| | Winterthur						

The data views engine must be told how the streams align across sites. Here, it makes sense to align them by which measurement they represent: _Primary_ or _Backup_.

#### Action
Move the field used as `GroupingField` over to being the “.IdentifyingField” of the weather data items `FieldSet`.
```json
PUT /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart
{
  "Id": "quickstart",
  "Name": "quickstart",
  "IndexField": { "Label": "Timestamp" },
  "Queries": [
    { 
      "Id": "weather",
      "Value":"*weather*" 
    }
  ],
  "DataFieldSets": [
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
                    "Source": "PropertyId",
                    "Keys": [
                        "AmbientTemperature"
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
            ],
            "IdentifyingField": {
                "Source": "Metadata",
                "Keys": [
                    "Site"
                ],
                "Label": "{IdentifyingValue} {FirstKey}"
            }
       },
  ],
  "GroupingFields": [],
  "IndexTypeCode": "DateTime",
  "Shape": "Standard"
}
```

#### Expected result
```text
HTTP 204 No Content
```

#### Action
```text
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart/Data/Interpolated
?startIndex={your_val_here}&endIndex={your_val_here}&interval={your_val_here}
```

#### Expected result
We’re back to a wide table, but the field ids are now distinct. The suggested/default values of the Available Fields’ `.Label` property includes {IdentifyingValue}, so if using those defaults, the impact of adding an identifying field is immediately clear.

```json
HTTP 200 OK
[
    {
        "Timestamp": "2019-10-21T18:00:00Z",
        "Biltmore Id": "WS_BILT",
        "Biltmore Name": "WS_BILT",
        "Biltmore AmbientTemperature": null,
        "Biltmore CloudCover": null,
        "Biltmore SolarRadiation": 165,
        "Biltmore Temperature": 33.589619124193831,
        "Biltmore Tags": "Weather, High Resolution, Gen1",
        "Rosecliff Id": "WS_ROSE",
        "Rosecliff Name": "WS_ROSE",
        "Rosecliff AmbientTemperature": null,
        "Rosecliff CloudCover": null,
        "Rosecliff SolarRadiation": 132,
        "Rosecliff Temperature": 14.537369185607899,
        "Rosecliff Tags": "Weather, Low Resolution, Gen1",
        "Winterthur Id": "WS_WINT",
        "Winterthur Name": "WS_WINT",
        "Winterthur AmbientTemperature": 1.0805517883941373,
        "Winterthur CloudCover": 2,
        "Winterthur SolarRadiation": 108,
        "Winterthur Temperature": null,
        "Winterthur Tags": "Weather, High Resolution, Gen2"
    },
    ...
]
```

### Consolidate data fields

There is a problem with this data view: the Gen1 Weather streams have a "Temperature" property but the Gen2 Weather streams have  renamed it to "AmbientTemperature". The data view has fields for both, but for each stream "Temperature" or "AmbientTemperature" is null. This is undesirable since the fields are semantically identical and should not be separate fields in the data view.

Find the `Field` associated with "AmbientTemperature". To the `Field`'s `.Keys` array, add "Temperature":

```json
{
  "Source": "PropertyId",
  "Keys": [
    "AmbientTemperature",
    "Temperature"
  ],
  "Label": "{IdentifyingValue} {FirstKey}"
},
```
Now that field will match to either "Temperature" or "AmbientTemperature".  
Remove the `Field` associated only with "Temperature".

You can also remove the `Fields` associated with data item Id and Name. These are not providing any additional useful information.

```json
PUT /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart
{
  "Id": "quickstart",
  "Name": "quickstart",
  "IndexField": { "Label": "Timestamp" },
  "Queries": [
    { 
      "Id": "weather",
      "Value":"*weather*" 
    }
  ],
  "DataFieldSets": [
        {
            "QueryId": "weather",
            "DataFields": [
                {
                    "Source": "PropertyId",
                    "Keys": [
                        "AmbientTemperature",
                        "Temperature"
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
                        "SolarRadiation"
                    ],
                    "Label": "{IdentifyingValue} {FirstKey}"
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
                }
            ],
            "IdentifyingField": {
                "Source": "Metadata",
                "Keys": [
                    "Site"
                ],
                "Label": "{IdentifyingValue} {FirstKey}"
            }
       },
  ],
  "GroupingFields": [],
  "IndexTypeCode": "DateTime",
  "Shape": "Standard"
}
```
#### Expected Result
```text
HTTP 204 No Content
```

#### Action
```text
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/DataViews/quickstart/Data/Interpolated
?startIndex={your_val_here}&endIndex={your_val_here}&interval={your_val_here}
```

#### Expected Result
```json
HTTP 200 OK
[
    {
        "Timestamp": "2019-10-21T18:00:00Z",
        "Biltmore AmbientTemperature": 33.589619124193831,
        "Biltmore CloudCover": null,
        "Biltmore SolarRadiation": 165,
        "Biltmore Tags": "Weather, High Resolution, Gen1",
        "Rosecliff AmbientTemperature": 14.537369185607899,
        "Rosecliff CloudCover": null,
        "Rosecliff SolarRadiation": 132,
        "Rosecliff Tags": "Weather, Low Resolution, Gen1",
        "Winterthur AmbientTemperature": 1.0805517883941373,
        "Winterthur CloudCover": 2,
        "Winterthur SolarRadiation": 108,
        "Winterthur Tags": "Weather, High Resolution, Gen2"
    }
    ...
]
```
### Further steps
The API is designed to encourage trial-and-error. We encourage you to experiment with other ways to represent this data, and to incorporate information about the solar inverters at each site.

## Data view properties
The following table lists the properties of a `DataView`:

| Property |Type    |Optionality  | Default | Details  |
|----------|--------|-------------|---------|----------|
| Id       | string | Required |  | Unique indentifier
| Name | string | Optional | value of Id | Friendly name
| Description | string | Optional  | null | Longer description of the view
| IndexField | Field | Optional | { Label:"Timestamp" } | The field used for indexing.  If unspecified a field labeled "Timestamp" is included.
| Queries     | Query[] | Optional | [ ] | Queries for SDS Streams to include in the view. This is the starting point when defining a data view. Each Query should represent a collection of like streams. To include streams that represent very different items (e.g. solar inverters and weather), use separate queries.
| DataFieldSets   | FieldSet[] | Optional | [ ] | The sets of fields included in the data view. Often copied or adapted from the view's available field sets, which are exposed in a resolved resource.
| GroupingFields  | Field[] | Optional | [ ] | Fields by which the data items are partitioned/grouped.
| DefaultStartIndex | string | Optional | null | The default value of StartIndex used when querying the data view data if none is specified.
| DefaultEndIndex | string | Optional | null | The default value of EndIndex used when querying the data view data if none is specified.
| DefaultInterval | string | Optional | null | The default value of Interval used when querying the data view data if none is specified.
| IndexTypeCode | SdsTypeCode | Optional | DateTime | The name of the index data type. DateTime is the currently supported index type.
| Shape | DataViewShape | Optional | Standard | Data views may be set to resolve as standard shape or narrow shape. Narrow shape may be used when an invariant output schema is required.

### Rules for Id property
- Is not case sensitive, but case is preserved
- Can contain spaces
- Cannot contain forward slash ("/")
- Can contain a maximum of 100 characters

## Related object types
The following sections describe the classes and enumerations used when defining data views.

### Query
A query for SDS Streams to include in the view.
|Property| Type | Optionality  | Default  | Details |
|--|--|--|--|--|
| Id  | string | Required |  | Unique identifier. Used by FieldSet to link to the query's results. |
| Value | string | Optional | null | A query for streams in SDS query syntax. A null or empty query will not match any streams.

### FieldSet
A set of fields included in the data view, sharing a common role or source (`.SourceType`). One `DataView` is likely to include one `FieldSet` per query.
|Property | Type | Optionality  | Default  | Details |
|--|--|--|--|--|
| QueryId | string | Required | | Must correspond to a query defined in the data view. 
| DataFields | Field[] | Optional | [ ] | Data fields to include in the data view. Often copied or adapted from the view's available field sets, which are exposed in a resolved resource.
| IdentifyingField | Field | Optional | null | A field by which to tell the data items apart, within each group. Any field from field sources `FieldSource.Id`, `FieldSource.Name`, `FieldSource.Metadata` and `FieldSource.Tags` can be used as an identifying field.

### Field
Individual piece of information, such as a property of an SDS stream or metadata of that stream.
|Property | Type | Optionality  | Default  | Details |
|--|--|--|--|--|
| Source | FieldSource | Optional | NotApplicable | Identifies the `.Source` of the field's values (not applicable for an index field). See the FieldSource enumeration section in this topic for details.
All sources except `FieldSource.NotApplicable` can be used as data fields. Fields from sources `FieldSource.Id`, `FieldSource.Name`, `FieldSource.Metadata` and `FieldSource.Tags` can be used as grouping fields and identifying fields. Some sources are used in conjunction with the Keys property (see below).
| Keys | String[] | Optional | [ ] | Used for sources `FieldSource.PropertyId`, `FieldSource.PropertyName`, `FieldSource.Metadata` and `FieldSource.Tags`, e.g. to map to specific stream properties by id. If more than one key is specified, they are matched as exclusive-or. A key has to be a non-null value.
| Label | string | Optional | null | Friendly name for the field. Certain tokens have special meaning: one of these, {IdentifyingValue}, is included in the suggested labels of AvailableFieldSets. Tokens that do not resolve are "" (empty string). The label is required in a field for all usages except in an identifying field. Label is trimmed of whitespace when used to identify field mappings. 

### FieldSource enumeration
For fields that derive data from a data item (e.g. an SDS stream), the `FieldSource` enumeration specifies the part of that data item that a Field resolves to. Some sources require one or more `.Keys` to be specified on the field, such as `PropertyId`, in which a key is the id of a desired property.

|Name | Enumeration Id | Keyed | Details |
|--|--|--|--|
|NotApplicable | 0 | No | FieldSource is not applicable for an index field
|Id | 1 | No | The id of the data item (stream)
|Name | 2 | No | The name of the data item (stream)
|PropertyId | 3 | Yes | Data from a stream property, found by id
|PropertyName | 4 | Yes | Data from a stream property, found by name
|Metadata | 5 | Yes | Value of the data item metadata, found by key
|Tags | 6 | Yes | Data item tags matching the collection provided

### SdsTypeCode enumeration
`SdsTypeCode` enumeration is the name of a data type. It is used when defining a data view, where the only supported `.IndexTypeCode` is "DateTime".

See [Sds documentation](xref:sdsTypes#sdstypecode) for details.

### DataViewShape enumeration
`DataViewShape` enumeration describes possible output shapes for a data view.
|Name| Enumeration Id | Description  |
|--|--|--|
|Standard | 0 | Fields are resolved into a shape similar to how they were defined. This is the recommended shape unless specific needs dictate.
|Narrow | 1 | Fields are pivoted vertically, resulting in a view whose schema is independent of what data items (streams) are resolved by the data view.
