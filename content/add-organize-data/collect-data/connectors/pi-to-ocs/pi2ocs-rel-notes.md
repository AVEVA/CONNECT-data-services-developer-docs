---
uid: pi2ocs-rel-summary
---

# PI to Data Hub 2.1.0 Release Notes

## Overview

This release covers the PI to Data Hub Agent, a component that is installed on-premises to replicate data and assets from the PI System to AVEVA Data Hub. Version 2.1, released 11/14/2022, is a feature release addressing change synchronization. 

**Note:** PI to Data Hub Agent Version 2.1 is a required upgrade for existing PI to Data Hub users. Failure to upgrade will result in loss of ability to configure an AF Server for the PI to Data Hub Agent.

For more information on product features and functions, including system requirements and installation/uninstallation instructions, refer to [PI to Data Hub documentation](xref:main-lp).

## Enhancements

The following features were added:

### Change synchronization

PI to Data Hub now supports change synchronization. If you make a configuration change on your PI System to an item that is part of a transfer, PI to Data Hub will automatically detect and replicate this change to AVEVA Data Hub.

Examples include:

- Changing a PI Point Name

- Changing a PI Point Attribute 

- Changing an AF Element Name

- Changing an AF Element Attribute Name

- Changing a PI Point Reference in an AF Attribute

- Adding a PI Point Reference in an AF Element that is part of the transfer.

PI to Data Hub will also replicate changes in data in your PI Server. If you edit archived events in the Data Archive, and that event is part of a PI to Data Hub Transfer, the agent will replicate that change to AVEVA Data Hub.

**Note:** The PI to Data Hub Agent and transfer must be running to detect and replicate changes.

## Fixes

The following items were resolved:

- PI to Data Hub Agent 2.0 sometimes stopped allowing transfer edits. This has been fixed.

- PI to Data Hub Agent 2.0 sometimes did not allow the user to configure an AF Server. This has been fixed.

- If a transfer is creating a large number of streams, and the user decided to remove the transfer, PI to Data Hub would continue creating the streams. This has been fixed.

## Known issues

- Query search results that contain a very large number of PI points (> 1 million) will generate an exception error and may not be processed.

- The AF Server must have a default Data Archive server specified for PI to Data Hub to operate properly.

- Streams with AF elements and referenced PI points are not deleted even when the **Automatically remove Streams and Assets** option has been selected; this exception includes instances of assets not created for AF elements due to errors (for example, attribute errors).

- Configuring two transfers in the same namespace where the transfers references the same AF element(s) results in the asset properties of one transfer overridden/replaced by the second transfer.

## Security information and guidance

AVEVA is [committed to releasing secure products](https://docs.osisoft.com/bundle/security-commitment-and-disclosure-standards/page/securitycommitmentanddisclosurestandards.html). This section is intended to provide relevant security-related information to guide your installation or upgrade decision.  

AVEVA [proactively discloses](https://docs.osisoft.com/bundle/security-commitment-and-disclosure-standards/page/securitycommitmentanddisclosurestandards.html#vulnerability-communication) aggregate information about the number and severity of security vulnerabilities addressed in each release. The tables below provide an overview of security issues addressed and their relative severity based on [standard scoring](https://docs.osisoft.com/bundle/security-commitment-and-disclosure-standards/page/securitycommitmentanddisclosurestandards.html#vulnerability-scoring).

## Distribution Kits

| Product  | Software Version |
|------------- | ------------ |
| PI to Data Hub Agent Installation | 2.1 |

©2022 AVEVA Group plc and its subsidiaries. All rights reserved.