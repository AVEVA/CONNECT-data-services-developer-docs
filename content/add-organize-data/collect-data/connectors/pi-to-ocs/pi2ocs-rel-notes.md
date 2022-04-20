---
uid: pi2ocs-rel-summary
---

# PI to Data Hub release summary

## Release 2.0: April 27, 2022


## Overview

This release covers the PI To Data Hub Agent, a component that is installed on-premises to replicate data and assets from the PI System to AVEVA Data Hub.

## Fixes and enhancements

### Enhancements

*AF element replication*

PI to Data Hub now supports replication of AF elements to AVEVA Data Hub. AF elements are created as assets in AVEVA Data Hub. For a complete list of supported AF objects, see ["What AF data is transferred to AVEVA Data Hub?"](https://docs.osisoft.com/bundle/data-hub/page/add-organize-data/collect-data/connectors/pi-to-ocs/pi-to-ocs-data-transfers/af-data-transferred.html).

*Edit a transfer*

PI to Data Hub now supports the ability to edit an existing transfer.  Once a transfer is created, you may add items to or remove items from your transfer such as AF elements (including implicit PI point references) and explicit PI point references. Additionally, you may edit the time range, data replication policy settings, and other general transfer settings.

*Health events*

PI to Data Hub makes it easier to understand if there are errors with a PI to Data Hub agent or transfer by raising health events. Health events are accessed from the PI to Data Hub Agents window in AVEVA Data Hub.

*Alternate display name*

Some customers require PI Server Name obfuscation in the cloud. This is now supported and configured in the Post-Installation Configuration Utility. There is a new field called, Alternate Display Name. If specified, this text will be used instead of any on-prem PI Data Archive names in the Stream Ids created in Data Hub.
 
You may also configure an alternate display name for your AF server. Although the AF server name is not used in Stream Ids, it is visible on the PI to Data Hub Agents and Transfer Details page.

**NOTE:** STREAM IDS ARE IMMUTABLE. IF YOU REQUIRE USE OF AN ALTERNATE DISPLAY NAME, PLEASE BE AWARE NEW STREAMS WILL BE CREATED, EVEN IF YOU HAVE ALREADY STARTED A TRANSFER. YOU MAY WISH TO DELETE ANY STREAMS PREVIOUSLY CREATED BY PI TO DATA HUB.

### Fixes

**Known issues**

* Query search results that contain a very large number of PI points (> 1 million) will generate an exception error and not be processed. 

* The AF Server must have a default Data Archive server specified for PI to Data Hub to operate properly.

## System requirements

This release supports Windows 10, Windows 11, Windows Server 2016, Windows Server 2019, and Windows Server 2022.

Minimum requirements:

* 4GB of RAM

* Internet connectivity of at least 10Mbit/sec

* Prior editions of Windows are not supported.

## Distribution Kit Files

| Product  | Software Version |
|------------- | ------------ |
| PI to Data Hub Agent Installation | 2.0 |

## Installation and upgrade

Run the `PIToDataHubAgent.exe` setup kit. Instructions are provided on-screen.

## Uninstallation

1. Select the Windows **Start** button, then select **Settings**.

1. In the `Settings` window, select **Apps**.

1. Under the **Apps & features** list, navigate to and select **PI to Data Hub**, then select **Uninstall** twice.

## Security information and guidance

### AVEVA's commitment

Because the PI System often serves as a barrier protecting control system networks and mission-critical infrastructure assets, AVEVA is committed to (1) delivering a high-quality product and (2) communicating clearly what security issues have been addressed. This release of PI to Data Hub Agent is the highest quality and most secure version of the PI to Data Hub Agent released to date. AVEVA's commitment to improving the PI System is ongoing, and each future version should raise the quality and security bar even further.

### Vulnerability communication

The practice of publicly disclosing internally discovered vulnerabilities is consistent with the [Common Industrial Control System Vulnerability Disclosure Framework](https://www.cisa.gov/uscert/sites/default/files/ICSJWG-Archive/ICSJWG_Vulnerability_Disclosure_Framework_Final_1.pdf) developed by the [Industrial Control Systems Joint Working Group (ICSJWG)](https://www.cisa.gov/uscert/ics/Industrial-Control-Systems-Joint-Working-Group-ICSJWG). Despite the increased risk posed by greater transparency, AVEVA is sharing this information to help you make an informed decision about when to upgrade to ensure your PI System has the best available protection.

To report a security vulnerability to AVEVA, contact productsecurity@aveva.com. Also see AVEVA's [Cyber Security Updates](https://www.aveva.com/en/support-and-success/cyber-security-updates/).

### Vulnerability scoring
AVEVA has selected the [Common Vulnerability Scoring System (CVSS)](https://www.first.org/cvss/v2/guide) to quantify the severity of security vulnerabilities for disclosure. To calculate the CVSS scores, AVEVA uses the [National Vulnerability Database (NVD)](https://nvd.nist.gov/vuln-metrics/cvss/v2-calculator?calculator&.0) calculator maintained by the National Institute of Standards and Technology (NIST). AVEVA uses High, Medium and Low categories to aggregate the CVSS Base scores. This removes some of the opinion related errors of CVSS scoring. As noted in the [CVSS specification](https://www.first.org/cvss/specification-document), base scores range from 0 for the lowest severity to 10 for the highest severity.

### Overview of new vulnerabilities found or fixed
This section is intended to provide relevant security-related information to guide your installation or upgrade decision. AVEVA is proactively disclosing aggregate information about the number and severity of the PI to Data Hub Agent security vulnerabilities that are fixed in this release.

No security-related information is applicable to this release.

### Documentation overview

See the [PI to Data Hub documentation](xref:main-lp) .

© 2022 AVEVA Group plc and its subsidiaries.
