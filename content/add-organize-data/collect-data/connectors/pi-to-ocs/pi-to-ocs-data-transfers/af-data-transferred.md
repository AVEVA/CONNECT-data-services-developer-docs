---
uid: af-data-transferred
---

# Transfer AF data

You can transfer the following AF element data into AVEVA Data Hub:

* Simple PI point attributes
* Static attribute values

A simple PI point attribute consists of only a server and tag name. This data does not include any data retrieval qualifiers. The associated event data contains simple PI point attributes with the same historical and streaming transfer mechanism as points not associated with AF. 

The table below lists the AF objects that can be included in a PI to Data Hub data transfer and what those objects appear as in AVEVA Data Hub.

| AF Object                                                 | AVEVA Data Hub Object |
| --------------------------------------------------------- | --------------------- |
| Elements                                                  | Assets |
| PI point data reference attributes                        | Asset stream reference properties |
| Static (aka "None") data reference attributes<sup>1</sup> | Asset metadata properties |

<sup>1</sup>Static AF attributes configured as type 'Boolean' are not supported and will not be transferred.

These AF objects are not included in a PI to Data Hub data transfer:

* Hidden attributes
* Custom units of measure (UOMs)
* Formula data reference attributes 
* Event frames 
* PI point arrays
* Implicit PI points with multiple attributes on an AF element (only one attribute will be transferred)
* Implicit PI points with attributes that reference other attributes
* Attributes that reference a non-registered data source/PI Data Archive
* Analysis data reference attributes
* Table lookup attributes
* AF enumeration sets
* AF models/layers/connections/ports
* Extended properties and annotations on assets not supporting AF versioning
* AF categories
* Weakly referenced elements, composition elements, and element templates
* AF tables

## Performance metrics: AF data transfer

The average data transfer rate is approximately 120-150 assets per second, and 1,000 assets per minute. Streams are created first, followed by AF element and asset data. If you use the same stream for various elements, the transfer time may be shorter.

**Note:** There may be some variance to these numbers.
