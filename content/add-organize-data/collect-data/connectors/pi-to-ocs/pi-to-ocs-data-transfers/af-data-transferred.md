---
uid: af-data-transferred
---

# Transfer AF data

PI to Data Hub supports replication of AF elements to AVEVA™ Data Hub, the rebranded version of OCS on the AVEVA™ Connect cloud platform. Existing PI to OCS users will need to migrate to PI to Data Hub to take advantage of this new feature. Please contact your account manager to learn how to switch from OCS to AVEVA Data Hub.

You can transfer the following AF element data into AVEVA Data Hub:

* Simple PI point attributes
* Static attribute values

A simple PI point attribute consists of only a server and tag name. This data does not include any data retrieval qualifiers. The associated event data contains simple PI point attributes with the same historical and streaming transfer mechanism as points not associated with AF. 

This table lists what AF objects can and cannot be included in a PI to Data Hub data transfer.

| AF Object                                                    | Included in a PI to Data Hub transfer?      |
| ------------------------------------------------------------ | -------------------------------------- |
| Elements                                                     | Yes                                    |
| Attributes                                                   | Yes                                    |
| PI point references                                          | Yes                                    |
| Constant values/string                                       | Yes<sup>1</sup>                        |
| Excluded attributes                                          | Yes                                    |
| Hidden attributes                                            | No                                     |
| Custom unit of measurements (UOMs)                           | No                                     |
| Formulas                                                     | No                                     |
| Event frames                                                 | No                                     |
| PI point arrays                                              | No                                     |
| Implicit PI points with multiple attributes on an AF element | Only one attribute will be transferred |
| Implicit PI points with attributes that reference other attributes | No                               |
| Attributes that reference a non-registered data source/PI Data Archive | No                 |

<sup>1</sup>Static AF Attributes configured as type 'Boolean' are not supported and will not be transferred.

## Performance metrics: AF data transfer

The average data transfer rate is approximately 120-150 assets per second, and 1,000 assets per minute. Streams are created first, followed by AF element and asset data. If you use the same stream for various elements, the transfer time may be shorter.

**Note:** There may be some variance to these numbers.
