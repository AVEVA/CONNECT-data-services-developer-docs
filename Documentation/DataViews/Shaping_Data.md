---
uid: DataViewsShapingData
---

# Shaping Data

Data views may be set to resolve as a standard shape or a "narrow" shape. Narrow shape may be used when an invariant output schema is required.

## Specify the shape
Set the `DataView`'s `Shape` property to either `DataViewShape.Standard` (default) or `DataViewShape.Narrow`.

#### Standard shape

The resultant schema resolves fields into a shape similar to how they are defined in the field sets.  This is the default shape.

##### Example: Get data response body for standard shape

```
Timestamp,Site,Id,SolarRadiation,Temperature,Tags
2018-11-13T18:19:00.0000000Z,Biltmore,WS_BILT,229,28.042327888795327,"Gen1, High Resolution, Weather"
2018-11-13T18:20:00.0000000Z,Biltmore,WS_BILT,229,28.042327888795327,"Gen1, High Resolution, Weather"
2018-11-13T18:19:00.0000000Z,Hearst Castle,WS_HRST,254,4.219790459247207,"Gen1, Low Resolution, Weather"
2018-11-13T18:20:00.0000000Z,Hearst Castle,WS_HRST,254,4.219790459247207,"Gen1, Low Resolution, Weather"
```
#### Narrow shape

The resultant schema resolves fields into a vertical table, essentially pivoting the standard shape table.  Columns included are: __Timestamp__, any group identifying columns, a __Field__ column which holds the property name, and a __Value__ column which holds the property value for the timestamp.

##### Example: Get data response body for narrow shape

```
Timestamp,Site,Field,Value
2018-11-13T18:19:00.0000000Z,Biltmore,Id,WS_BILT
2018-11-13T18:19:00.0000000Z,Biltmore,SolarRadiation,229
2018-11-13T18:19:00.0000000Z,Biltmore,Temperature,28.042327888795327
2018-11-13T18:19:00.0000000Z,Biltmore,Tags,"Gen1, High Resolution, Weather"
2018-11-13T18:20:00.0000000Z,Biltmore,Id,WS_BILT
2018-11-13T18:20:00.0000000Z,Biltmore,SolarRadiation,229
2018-11-13T18:20:00.0000000Z,Biltmore,Temperature,28.042327888795327
2018-11-13T18:20:00.0000000Z,Biltmore,Tags,"Gen1, High Resolution, Weather"
2018-11-13T18:19:00.0000000Z,Hearst Castle,Id,WS_HRST
2018-11-13T18:19:00.0000000Z,Hearst Castle,SolarRadiation,254
2018-11-13T18:19:00.0000000Z,Hearst Castle,Temperature,4.219790459247207
2018-11-13T18:19:00.0000000Z,Hearst Castle,Tags,"Gen1, Low Resolution, Weather"
2018-11-13T18:20:00.0000000Z,Hearst Castle,Id,WS_HRST
2018-11-13T18:20:00.0000000Z,Hearst Castle,SolarRadiation,254
2018-11-13T18:20:00.0000000Z,Hearst Castle,Temperature,4.219790459247207
2018-11-13T18:20:00.0000000Z,Hearst Castle,Tags,"Gen1, Low Resolution, Weather"
```