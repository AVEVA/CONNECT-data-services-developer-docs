---
uid: min-sys-reqmnts
---

# PI to Data Hub minimum system requirements

The following table lists the system requirements of PI to Data Hub.

| System component | Requirement |
| ---------------- | ----------- |
| PI Server | <ul><li>Minimum version: PI Data Archive 2016 R2. For full support of PI to Data Hub features, use PI Data Archive 2017 R2 or later.</li><li>PI AF 2017 R2 or later<br>**Note:** PI AF is only required if you wish to connect to an AF server.</li></ul> |
| Operating system | <ul><li>Windows 10, Windows 11, Windows Server 2016, Windows Server 2019, or Windows Server 2022<br>CORE editions of the Windows Server operating systems are supported with silent installations.</li><li>Processor: 1 gigahertz (GHz) or faster compatible processor or System on a Chip (SoC)</li><li>RAM: 4GB</li><li>Hard drive size: 32GB or larger hard disk</li><li>An Internet connection that allows outbound connections over port 443 and a secure network connection to the PI Data Archive computer</li><li>Internet connectivity of at least 10Mbit/sec</li></ul> |
| Specific PI to Data Hub features | <ul><li>Transfer out of order (OOO) events: PI Data Archive 2017 R2 or later and PI AF 2017 R2 or later</li></ul> |

## Administrator privileges

| Privileges | Requirement |
| ---------- | ----------- |
| Installation privileges | To install a PI to Data Hub Agent, you must be an administrator on the agent host computer. |
| Configuration privileges | To configure a PI to Data Hub Agent after the installation is complete, you must have the Tenant Administrator role in AVEVA Data Hub. For silent installations, you have the option to create the requisite client ID and secret prior to the installation. |

## Ensure write access to stream and asset collections 

The PI to Data Hub Agent has write permission to the streams collection in AVEVA Data Hub. The configuration utility generates a client ID that has the Tenant Contributor role, which provides write permission by default.

If write access is removed, certain operations on the stream collection will fail, such as updates to Units of Measure (UOM).

For AF server transfers, write permission on the assets collection is also required to create assets in AVEVA Data Hub.

To remove items from a transfer and also the corresponding streams and/or assets from the portal via Edit transfer mode, the user account used to edit the transfer must be the owner with write permission on the items. 

## Configure access to PI Data Archive security tables and PI point data

The account you configure to run the PI to Data Hub Agent service on the host computer must have read access to the following PI Data Archive data:

* Archive data (the PIARCDATA Security table)
* The PI points configuration table (PIPOINT Security table)
* The PI points and data to be transferred
* Read permission to the AF server, elements, and AF attribute data

## Open firewall port for communication to PI to Data Hub

Port 443 must be opened for https communication to the PI to Data Hub gateway. The URL used for https communication depends on the namespace to which the agent is communicating, as indicated in the following table.

| Region          | URL                            |
| --------------- | ------------------------------ |
| West US         | uswe.datahub.connect.aveva.com |
| Northern Europe | euno.datahub.connect.aveva.com |
| East Australia  | auea.datahub.connect.aveva.com |

Although each of the above URLs currently corresponds to a public static IP Address, we recommended you use the URL rather than the IP address in firewall rules. If required, you can determine the IP Address by pinging the URL.
