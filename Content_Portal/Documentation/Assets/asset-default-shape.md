---
uid: AssetDefaultShape
---

# Asset Default Shape

A shape describes the consumption-oriented aspects of an OCS resource, rather than describing how the resource is configured. For example, the shape of an asset corresponds to its metadata and measurements which define how the data is interpreted (that is, SdsTypeCode, InterpolationMode, UOM, and names that are meaningful in the context of an asset) rather than how the data is retrieved from the Sequential Data Store (that is, configuration information such as StreamId and TypeId).

***

## `Get Default Shape of an Asset`

Returns the default shape of an asset.

## Default Shape Metadata Value Rules

If an asset references an asset type, the following rules and examples apply for a given **metadata value**:

- If a metadata value with the same **id** exists on the asset type and asset, the metadata value  **Name**, **UOM**, and **SdsTypeCode** of the asset type take precedence over any values on the asset.
- If the metadata value with the same **id** exists on the asset type and asset, the **value** on the asset is used if it is not null. <! -- What is "it" referring to? The value on the asset type? --> The **value** of the metadata value on the asset will be coerced to the **SdsTypeCode** of the asset type if they do not match. If the **value** of the metadata value on the asset is null, then the **value** of the asset type's metadata value is used, unless that value is also null. In this instance, the **value** on the default shape is zero for numerical shapes and it is an empty string for strings.
- If the metadata value with the same **id** exists on the asset, but it does not exist on the asset type, then the asset's metadata value appears on the default shape, unless the **name** is null. In this instance, the metadata value does not appear on the default shape.

### Examples

The examples in the following table illustrate the default shape metadata value rules.

| Metadata value on asset type                 | Metadata value on asset                                | Metadata value on default shape                     | Details                                                      |
| -------------------------------------------- | ------------------------------------------------------ | --------------------------------------------------- | :----------------------------------------------------------- |
| id="md_id"<br> name="**m1**"<br>  value=null | id="md_id"<br> name=null<br>  value=null               | id="md_id"<br> name="**m1**"<br>  value=See Details | For numeric SdsTypeCode, the value for **m1** is 0. For string SdsTypeCode, the value for **m1** is an empty string. For both, the metadatum <! -- metadata **value**? --> is returned, along with UOM and SdsTypeCode from the asset type. |
| id="md_id"<br/> name="**m2**"<br/>  value=10 | id="md_id"<br/> name=null<br/>  value=null             | id="md_id"<br/> name="**m2**"<br/>  value=10        | m2 appears on the default shape with value=10, along with UOM and SdsTypeCode from the asset type. |
| id="md_id"<br/> name="**m3**"<br/>  value=10 | id="md_id"<br/> name=null<br/>  value=20               | id="md_id"<br/> name="**m3**"<br/>  value=20        | **m3** appears on the default shape with value=20, along with UOM and SdsTypeCode from the asset type. The value on the asset metadata value always overrides the value on the asset type. |
| Not present                                  | id="md_id"<br/> name="**m5**"<br/>  value=30           | id="md_id"<br/> name="**m5**"<br/>  value=30        | m5 appears on the default shape with value =30, along with UOM and SdsTypeCode from the asset. Since this metadatum <! -- **value**? --> does not exist on the asset type, the metadata value on the default shape takes the value of the asset. |
| Not present                                  | id="md_id"<br/> name=null<br/>  value=30               | Not present                                         | Because there is no metadata value with id = md_id on the asset type and the name of the metadata value on the asset is null, then this metadata value does not appear on the default shape. |
| id="md_id"<br/> name="**m7**"<br/>  value=10 | id="md_id"<br/> name=null<br/>  value="a string value" | id="md_id"<br/> name="**m7**"<br/>  value=10        | The metadata value with id "md_id" has different SdsTypeCodes. Therefore, the default shape's metadata value takes the value of the asset type's metadata value for id ("md_id"), along with the UOM and SdsTypeCode from the asset type. |
| id="md_id"<br/> name="**m8**"<br/>  value=10 | id="md_id"<br/> name=null<br/>  value="a string value" | id="md_id"<br/> name="**m8**"<br/>  value=0         | The metadata value with id "md_id" has different SdsTypeCodes. Therefore, the default shape's metadata value will coerce the overloaded value from the asset to the SdsTypecode on the asset type for the default shape, along with UOM and SdsTypeCode from the asset type. |
| id="md_id"<br/> name="**m9**"<br/>  value=10 | id="md_id"<br/> name=null<br/>  value="1.23"           | id="md_id"<br/> name="**m9**"<br/>  value=1         | The metadata value with id "md_id" has different SdsTypeCodes. Therefore, the default shape's metadata value will coerce the overloaded value from the asset to the SdsTypecode on the asset type for the default shape, along with UOM and SdsTypeCode from the asset type. |

### Default Shape Reference Rules

The following example illustrates the default shape reference rules. If an asset references an asset type, the the following rules apply for a given **Reference**:

Assume that the following is true for the asset and asset type:

- Id="reference1" is defined for both the asset and the asset type. The asset type has measurement mappings for "Temperature" and "Pressure". <! -- Is that correct? -->
- Id="reference2" is defined only on the asset, with one measurement mapping for "Temperature".
- Id="reference3" is defined only on the asset, but its **StreamReferenceName** is null, with one measurement mapping for "Pressure".

In this scenario, the default reference rules resolve as follows: 

- Measurement mappings for "reference1" are determined by the asset type. Any measurement mappings for "reference1" on the asset are ignored.
- The "Temperature" measurement mapping for "reference2" on the asset overrides the "Temperature" measurement mappings from "reference1".
- Any measurement mappings for "reference3" are ignored because Name on the asset is null. Note: **StreamReferenceName** on the asset type cannot be null. 

### Request

```
GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Assets/{assetId}/Shape
```

### Parameters

`string tenantId` 

The tenant identifier

`string namespaceId` 

The namespace identifier

`string assetID`

The asset identifier

### Response

The response includes a status code and a response body.

| Status Code     | Body Type | Description                                                  |
| --------------- | --------- | ------------------------------------------------------------ |
| 200 OK          | `Shape`   | The default shape of an asset                                |
| 400 Bad Request | error     | The request is not valid. See the response body for additional details. |
| 403 Forbidden   | error     | You are not authorized to view the requested asset.          |
| 404 Not Found   | error     | The asset with the specified identifier is not found.        |

#### Example response body

```
HTTP 200 OK
Content-Type: application/json
{
    "Id": "AssetTest",
    "Name": "AssetName",
    "Metadata": [
        {
            "Id": "metadataId_101",
            "Name": "DateTimeAttr",
            "SdsTypeCode": 16,
            "Value": "0001-01-01T00:00:00Z"
        }
    ],
    "Measurements": [
        {
            "Id": "3509f11f-8b51-4555-acca-8c7c7c8192c2",
            "Name": "measurementTemperature",
            "StreamId": "theSdsStreamId",
            "Properties": [
                {
                    "Id": "Timestamp",
                    "IsKey": true,
                    "ExtrapolationMode": 2,
                    "SdsType": {
                        "SdsTypeCode": 16
                    }
                },
                {
                    "Id": "Value",
                    "InterpolationMode": 4,
                    "ExtrapolationMode": 2,
                    "SdsType": {
                        "SdsTypeCode": 113
                    }
                }
            ]
        }
    ]
}
```