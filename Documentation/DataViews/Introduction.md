---
uid: Introduction
---

# Introduction to Data Views

### Data views quick start guide

This page will give an overview of the data view definition and how to create data views. The intention is get users started with the basic ways to use data views, for more in depth information about individual components, see their respective pages.

### Data sources

To illustrate the examples below, the following SdsStreams have been created and populated with test data; Arizona_Stream, California_Stream, and Pennsylvania_Stream. All streams have the same properties: FlowRate, Volume, and Temperature. For information on how to create such streams, see the Sequential Data Store, Sds, documentation. 

### Simple example

The following is an example of creating a data view definition with a query to retrieve data from streams whose id contain "_Stream", like the streams defined above. Queries can also use logical operators to create complex expressions, see the [queries](xref:Queries) page for more information. 

This is the simplest form of creating a data view and uses default settings for the all components, the result would include columns mapped to every property in every stream of the query.

```json
{
  "Id": "SimpleDataView",
  "Queries": [
    {
      "Id": "Query1",
      "Query": {
        "Resource": "Streams",
        "Field": "Id" ,
        "Value": "_Stream" ,
        "Operator": "Contains"
      }
    }
  ],
  "IndexDataType": "datetime"
}
```

Since such data might not be very friendly to work with, there are ways to shape the resulting data set by defining the output columns, grouping the data items, and configuring the index. The following parts will provide quick overviews of these parts, see their respective pages for more information.

### Defining the columns

To define the columns of the output, the Mappings object can be added. The following is an example of a mappings object that creates a Timestamp column to use as key, along with three columns to map certain properties of a stream. This is done using the mapping rule object of the column to define the data source by specifying the property path and an item identifier to identify its containing stream:

```json
    "Mappings": {
        "Columns": [
            {
                "Name": "Timestamp",
                "MappingRule": {
                    "PropertyPaths": [
                        "path"
                    ]
                },
                "IsKey": true,
                "DataType": "string"
            },
            {
                "Name": "Arizona flow rate",
                "MappingRule": {
                    "PropertyPaths": [
                        "FlowRate"
                    ],
                    "ItemIdentifier": {
                        "Resource": "Streams",
                        "Field": "Id",
                        "Name": null,
                        "Value": "Arizona_Stream",
                        "Operator": "Equals"
                    }
                }
            },
            {
                "Name": "Arizona volume",
                "MappingRule": {
                    "PropertyPaths": [
                        "Volume"
                    ],
                    "ItemIdentifier": {
                        "Resource": "Streams",
                        "Field": "Id",
                        "Name": null,
                        "Value": "Arizona_Stream",
                        "Operator": "Equals"
                    }
                }
            },
                        {
                "Name": "Arizona temperature",
                "MappingRule": {
                    "PropertyPaths": [
                        "Temperature"
                    ],
                    "ItemIdentifier": {
                        "Resource": "Streams",
                        "Field": "Id",
                        "Name": null,
                        "Value": "Arizona_Stream",
                        "Operator": "Equals"
                    }
                }
            }
        ]
    },
```
This mapping will create columns for the properties of the Arizona_Stream and display their values along with a timestamp, resulting in an output like the following:

```json
...
    {
        "Timestamp": "2019-03-16T17:24:30.5270905Z",
        "Arizona flow rate": 23,
        "Arizona volume": 120,
        "Arizona temperature": 9
    },
...
```

To more efficiently combine components, the mapping rule can also be linked to shared mapping rules and group rules, see the [mappings](xref:Mappings) page for more information.


### Adding grouping

The Group Rule object can organize data items into data groups within the view to generate more meaningful results and let users compare similar properties in the result. The following is an example of a group rule that creates data groups based on the name of the Sds stream:

```json
    "GroupRules": [
        {
            "Id": "SimpleGroupRule",
            "Type": "StreamName"
        }
    ],
```
Group rules can be more advanced and get applied using patterns across the properties of Sds streams, for more information see the [group rules](xref:GroupRules) page.

### Configuring the index

Users can define the index config for data views by setting the Start and End times, a time interval, and the mode, all to be used when retreiveing the data. See the [index config](xref:IndexConfig) page for information.

