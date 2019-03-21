---
uid: GroupRules
---

 
 # GroupRules
The GroupRule lets users organize data items in the query, within or across streams, to form data groups in the resulting data set. By specifying the type to group on, optionally also token rules defining patterns that describe the group, users can retrieve organized data sets to compare results and examine the data easier. 
### Properties

Property | Type | Requried | Descriptions
 --- | --- | --- | ---
Id | string | True | Id of the rule
Type | GroupRuleType | False | Stream property to base grouping on
TokenRules | TokenRules | True | Token rules that create patterns to form groups



 ## `Type` 
 The Type can have the following values: 
Value | Type | Description
 --- | --- | ---
StreamId | string | Group on Stream ID
StreamName | string | Group on Stream Name
StreamTag | string | Group on Stream Tag
StreamMetadata | string | Group on Stream Metadata


## `Example` 
The following examples show group rule definitions, with the first example being a simple definition using only stream names to create data groups. 

The second example creates groups according to the name of streams and the specified pattern. Streams whose name property match the {state}_Stream pattern, where {state} is the token, would in this case create a data group. 

These groups could then be used as column mapping rules using a group rule mapping rule to get the value of the {state} token for the stream of the respective column. For example, using two streams named California_Stream and Pennsylvania_Stream with this group rule would result in two data groups being created, that, if used in a group rule mapping rule for a column representing the State, would result in the respective state, such as California, being the value for columns where the data item is contained in the California_Stream. (See the [mappings](xref:Mappings) page for more information about mapping rules). When working with large data sets, this allows users to group their data items and retrieve organized results.
```json
[
  {
    "Id": "DefaultGroupRule",
    "Type": "StreamName",
    "TokenRules": null
  }
]
```
```json
[
  {
    "Id": "group_rule",
    "Type": "StreamName",
    "TokenRules": {
      "Tokens": [
        "{state}"
      ],
      "Patterns": [
        {
          "QueryId": "*",
          "Name": "test_pattern",
          "Value": "{state}_Stream"
        }
      ]
    }
  }
]
```
```json
An example output using this group rule as described above could look like the following:
```
```json

[
    {
        "Timestamp": "2018-10-03T03:00:00Z",
        "State": "Pennsylvania",
        "FlowRate": "2",
        "Temperature": "5",
        "Volume": "100"
    },
    {
        "Timestamp": "2018-10-03T03:10:00Z",
        "State": "Pennsylvania",
        "FlowRate": "3",
        "Temperature": "5.3334",
        "Volume": "114.223"
    },
    {
        "Timestamp": "2018-10-03T03:00:00Z",
        "State": "California",
        "FlowRate": "44",
        "Temperature": "24.44",
        "Volume": "245.12"
    },
    {
        "Timestamp": "2018-10-03T03:10:00Z",
        "State": "California",
        "FlowRate": "42",
        "Temperature": "25.223",
        "Volume": "247.5"
    },
]
```
