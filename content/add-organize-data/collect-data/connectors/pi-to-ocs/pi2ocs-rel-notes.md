---
uid: pi2ocs-rel-summary
---

# PI to Data Hub release summary

## Release 1.8.2: January 28, 2022


## Overview

This release covers the PI To Data Hub Agent, a component that is installed on-premises to replicate data and assets from the PI System to AVEVA Data Hub.

## Fixes and enhancements

### Fixes

*PI to Data Hub Agent redirects user to a broken documentation page*

During installation, the user gets redirected to a broken documentation web page. In addition, the user is redirected to a broken web page when the help icon is clicked in the PI to Data Hub Configuration Utility. This issue has been fixed. 

*PI to Data Hub Agent installation pointed to development cloud servers.*

During installation of the PI to Data Hub Agent, the agent attempts to establish connectivity with internal development cloud servers by default instead of the public AVEVA Data Hub cloud servers. This issue has been resolved. 

**Known issues**

* Query search results that contain a very large number of PI points (> 1 million) will generate an exception error and not be processed. 

* The AF Server must have a default Data Archive server specified for PI to Data Hub to operate properly.

* The PI to Data Hub Configuration Utility can become unresponsive on some systems. There are two workaround options:

  1. Download and install a newer version of .NET Desktop Runtime (3.1.21 or later) from [here](https://dotnet.microsoft.com/download/dotnet/3.1).
   
  2. Change the compatibility settings:
    
     a. Navigate to `C:\Program Files\AVEVA\PIToDataHub`.
     
     b. Right-click the `PIToDataHubConfigurationUtility.exe` file, then select **Properties**.
     
     c. In the **Properties** dialog box, select the **Compatibility** tab.
     
     d. Select the **Change high DPI settings** button, then select the **Use this setting to fix scaling problems for this program instead of the one in Settings** checkbox.
     
     e. Select **OK**, select **Apply**, then close the dialog box.

## System requirements

This release supports Windows 10, Windows Server 2016, and Windows Server 2019.

Minimum requirements:

* 4GB of RAM

* Internet connectivity of at least 10Mbit/sec

* Prior editions of Windows are not supported.

## Distribution Kit Files

| Product  | Software Version |
|------------- | ------------ |
| PI to Data Hub Agent Installation | 1.8.2 |

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
