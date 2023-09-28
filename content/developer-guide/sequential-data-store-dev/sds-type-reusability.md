---
uid: sds-type-reusability
---

# Type reuse

Types can refer to other types by using their identifiers, which enables type reusability. For example, if there is a common index and value property for a group of types that may have additional properties, a base type can be created with those properties.

```json
{
  "Id": "Simple",
  "Name": "Simple",
  "SdsTypeCode": 1,
  "Properties": [
    {
      "Id": "Time",
      "Name": "Time",
      "IsKey": true,
      "SdsType": {
        "SdsTypeCode": 16
      }
    },
    {
      "Id": "Measurement",
      "Name": "Measurement",
      "SdsType": {
        "SdsTypeCode": 14
      }
    }
  ]
}
```

If you need to create a new type with properties in addition to the ones shown above, a reference to the base type can be added by simply specifying the base type's `Id`.

```json
{
  "Id": "Complex",
  "Name": "Complex",
  "SdsTypeCode": 1,
  "BaseType": {
    "Id": "Simple"
  },
  "Properties": [
    {
      "Id": "Depth",
      "Name": "Depth",
      "SdsType": {
        "SdsTypeCode": 14
      }
    }
  ]
}
```

The new type may also include the full type definition of the reference type instead of specifying only the `Id` as shown below:

```json
{
  "Id": "Complex",
  "Name": "Complex",
  "SdsTypeCode": 1,
  "BaseType": {
    "Id": "Simple",
    "Name": "Simple",
    "SdsTypeCode": 1,
    "Properties": [
      {
        "Id": "Time",
        "Name": "Time",
        "IsKey": true,
        "SdsType": {
          "SdsTypeCode": 16
        }
      },
      {
        "Id": "Measurement",
        "Name": "Measurement",
        "SdsType": {
          "SdsTypeCode": 14
        }
      }
    ]
  },
  "Properties": [
    {
      "Id": "Depth",
      "Name": "Depth",
      "SdsType": {
        "SdsTypeCode": 14
      }
    }
  ]
}
```

If the full definition is sent, the referenced types (base type "Simple" in the above example) should match the actual type that was initially created. If the full definition is sent and the referenced types do not exist, a new type is created automatically by SDS. Further type creations can reference them as shown above. Note that when trying to get types back from SDS, the results also include types that were automatically created by SDS.

Base types and properties of type `object`, `enum`, or user-defined collections such as `array`, `list` and `dictionary`, are treated as referenced types. Note that streams cannot be created using these referenced types. If a stream of a particular type is to be created, the type should contain at least one property with a valid index type as described in the [Indexes](xref:sdsIndexes) section. The index property may also be in the base type as shown in the example above.

You can do this using any programming languages. Here's an example in .NET:

```csharp
public class Basic
{
    [SdsMember(IsKey = true, Order = 0)]
    public DateTime Time { get; set; }

    public double Temperature { get; set; }
}

public class EngineMonitor : Basic
{
    public double PistonSpeed { get; set; }
}

public class WindShieldMonitor : Basic
{
    public double Luminance { get; set; }
}

SdsType engineType = SdsTypeBuilder.CreateSdsType<EngineMonitor>();
engineType.Id = "Engine";
engineType.BaseType.Id = "Basic";

SdsType windShieldType = SdsTypeBuilder.CreateSdsType<WindShieldMonitor>();
windShieldType.Id = "WindShield";
windShieldType.BaseType.Id = "Basic";

```

If needed, the base type's Id can also be changed to be more meaningful.
