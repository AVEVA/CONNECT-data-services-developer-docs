---
uid: IndexConfig
---

 
 # IndexConfig
The IndexConfig defines the index information for retrieving data, and lets the user specify start and end times with an interval time, and the mode for which how to retrieve the data. Currently, only interpolation mode is supported. 
### Properties

Property | Type | Requried | Descriptions
 --- | --- | --- | ---
StartIndex | string | True | The start index of data retrieval
EndIndex | string | True | The end index of data retrieval
Mode | string | True | The data retrieval mode
Interval | string | True | The data retrieval interval

## `Example` 
The following example shows an index config set for data to be indexed between the start and end index, and give interpolated data using an interval of 5 minutes.
```json
{
  "StartIndex": "2018-01-01T00:00:00Z",
  "EndIndex": "2018-01-02T00:00:00Z",
  "Mode": "Interpolated",
  "Interval": "00:05:00"
}
```
