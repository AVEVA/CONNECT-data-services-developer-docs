---
uid: pi2ocs-rel-summary
---

# PI to Data Hub release summary

## Release 1.8.0: December 10, 2021


## Overview

This release covers the PI To Data Hub Agent, a component that is installed on-premises to replicate data and assets from the PI System to AVEVA Data Hub.

## Fixes and enhancements

This is a Lighthouse Release. Prior to this, select customers had access to the preview Lighthouse, early adopter access to this product.

### Fixes

*PI to Data Hub Configuration Utility Improvements*

**Respect AVEVA Data Hub feature flags**

If a user is not authorized for a specific AVEVA Data Hub feature, the PI to Data Hub configuration utility will respect that setting. Previously, it didn't check if a user was authorized to configure an AF server for PI to Data Hub.
 
**Improve experience when searching for referenced Data Archives**

The PI to Data Hub Configuration Utility now displays more information while the tool is searching for referenced Data Archives. Previously, that area was blank until one or more Data Archives were found. 

The 1.6.1204.0 and 1.7.0.0 versions of the PI To OCS Agent will fail to register and fail to appear in the OSIsoft Cloud Service portal on new installations. The PI to OCS Configuration Utility will also display an agent status of "Retrieving State".

The PI to Data Hub Configuration Utility could crash if a user attempted to edit a PI mapping from within the tool. This has been fixed.

*PI to Data Hub Transfer Improvements*

**PI to Data Hub transfer stops streaming data if a delete event is processed**

If an event was deleted from Sequential Data Store to which a stream PI to Data Hub wrote, the transfer would stop streaming data. This has been fixed.
Enhancements

**AF support added to PI to Data Hub**

PI to Data Hub is now able to transfer AF elements and attributes to AVEVA Data Hub and create them as assets and metadata. PI to Data Hub will transfer the following AF objects to AVEVA Data Hub:

*PI to OCS Configuration Utility Improvements*

Please consult the PI to Data Hub online documentation for more details on how to configure a transfer with AF elements and attributes.
 
**PI to Data Hub supports Data Privacy Settings**

When configuring a transfer, you may now select the data privacy level for stream metadata replication. Please consult the PI to Data Hub online documentation for more details on how to configure data privacy settings.

**Known issues**

* Query search results that contain a very large number of PI points (> 1 million) will generate an exception error and not be processed. 
* The AF Server must have a default Data Archive server specified for PI to Data Hub to operate properly.

## System requirements

This release supports Windows 10, Windows Server 2016 and Windows Server 2019.

Minimum requirements:

* 4GB of RAM
* Internet connectivity at least 10Mbit/sec
* Prior editions of Windows are not supported.

## Distribution Kit Files

| Product  | Software Version |
|------------- | ------------ |
| PI to Data Hub Agent Installation | 1.7.0 |

## Installation and upgrade

Run the PIToDataHubAgent.exe setup kit. Instructions are provided on-screen.

## Uninstallation

In Windows go to **Settings** > **Apps**.
Uninstall the package "PI To Data Hub Agent".

## Security information and guidance

### AVEVA's commitment

Because the PI System often serves as a barrier protecting control system networks and mission-critical infrastructure assets, AVEVA is committed to (1) delivering a high-quality product and (2) communicating clearly what security issues have been addressed. This release of PI to Data Hub Agent is the highest quality and most secure version of the PI to Data Hub Agent released to date. AVEVA's commitment to improving the PI System is ongoing, and each future version should raise the quality and security bar even further.

### Vulnerability communication

The practice of publicly disclosing internally discovered vulnerabilities is consistent with the [Common Industrial Control System Vulnerability Disclosure Framework](https://ics-cert.us-cert.gov/sites/default/files/ICSJWG-Archive/ICSJWG_Vulnerability_Disclosure_Framework_Final_1.pdf)  developed by the [Industrial Control Systems Joint Working Group (ICSJWG)](https://ics-cert.us-cert.gov/Industrial-Control-Systems-Joint-Working-Group-ICSJWG). Despite the increased risk posed by greater transparency, AVEVA is sharing this information to help you make an informed decision about when to upgrade to ensure your PI System has the best available protection.
For more information, refer to [AVEVA's Ethical Disclosure Policy](https://www.osisoft.com/ethical-disclosure-policy).

To report a security vulnerability to AVEVA, contact productsecurity@aveva.com. Also see AVEVA's [Cyber Security Updates](https://www.aveva.com/en/support-and-success/cyber-security-updates/).

### Vulnerability scoring
AVEVA has selected the [Common Vulnerability Scoring System (CVSS)](https://www.first.org/cvss/v2/guide) to quantify the severity of security vulnerabilities for disclosure. To calculate the CVSS scores, AVEVA uses the [National Vulnerability Database (NVD)](https://nvd.nist.gov/cvss.cfm?calculator&version=2) calculator maintained by the National Institute of Standards and Technology (NIST). AVEVA uses High, Medium and Low categories to aggregate the CVSS Base scores. This removes some of the opinion related errors of CVSS scoring. As noted in the [CVSS specification](https://www.first.org/cvss/specification-document), base scores range from 0 for the lowest severity to 10 for the highest severity.

### Overview of new vulnerabilities found or fixed
This section is intended to provide relevant security-related information to guide your installation or upgrade decision. AVEVA is proactively disclosing aggregate information about the number and severity of the PI to Data Hub Agent security vulnerabilities that are fixed in this release.

No security-related information is applicable to this release.

### Documentation overview

See the [PI to Data Hub documentation](https://docs.osisoft.com/bundle/data-hub/page/add-organize-data/collect-data/connectors/pi-to-ocs/main-landing-page.html).

©2021 OSIsoft, LLC
