---
uid: pi2ocs-rel-summary
---

# PI to Data Hub 2.2.1163 Release Notes

## Overview

This release covers the PI to Data Hub Agent, a component that is installed on-premises to replicate data, assets, and licensed PI point counts from PI System to AVEVA Data Hub. 

Version 2.2.1163, released 06/21/2023, is a feature release adding the capability to send licensed PI point counts to AVEVA Data Hub, which allows customers to take advantage of a new offering, AVEVA PI Data Infrastructure - aggregate tag, available in small (100,000 tags), medium (250,000 tags), and large (500,000 tags). With this new offering, customers no longer need to worry about exceeding maximum PI point counts on individual PI Data Archive servers. Instead, customers purchase tags in aggregate, up to 500,000, and configure PI points as needed on individual PI Data Archive servers.

This is also the first release where the PI to Data Hub Agent is available as a feature in the PI Server installation kit. On a new installation, when the PI Data Archive server role is selected, the agent feature will also be selected by default. Adding the agent to the PI Server installation kit is part of a larger effort to support hybrid deployments of PI System, with the goal of enabling seamless integration between PI System and AVEVA Data Hub. With this release, customers can configure transfers of on-premises data immediately after installing PI Server.  

The PI to Data Hub Agent will also remain available as a separate download from the AVEVA Data Hub portal.

**Note:** PI to Data Hub Agent Version 2.2.1163 is an optional upgrade for existing PI to Data Hub users.

For more information on product features and functions, including system requirements and installation/uninstallation instructions, refer to [PI to Data Hub documentation](xref:PItoDH).

## Enhancements

The following features were added:

- For customers who are on AVEVA PI Data Infrastructure - aggregate tag, the PI to Data Hub Agent now sends license usage information to AVEVA Data Hub. If the PI Data Archive has a license file corresponding to the aggregate PI point model, then the actual PI point count of the PI Data Archive will be sent to AVEVA Data Hub. If PI Data Archive has a traditional PI point count limit, then the maximum PI point count associated with the license will be sent as the usage information. For customers on SRP or AVEVA PI Data Infrastructure (without aggregate tag), license usage information is discarded and not stored in the cloud.

- For a new installation of the PI to Data Hub Agent, the initial connection and registration to AVEVA Data Hub has been moved from the PI to Data Hub Agent installation kit into the PI to Data Hub Agent Configuration Utility. This change facilitates a consistent post-installation user experience whether the agent is installed with the PI Server installation kit or the standalone installer.

## Fixes

There were no fixes in this release.

## Security information and guidance

We are [committed to releasing secure products](https://docs.aveva.com/bundle/security-commitment-and-disclosure-standards/page/securitycommitmentanddisclosurestandards.html). This section is intended to provide relevant security-related information to guide your installation or upgrade decision.  

We [proactively disclose](https://docs.aveva.com/bundle/security-commitment-and-disclosure-standards/page/securitycommitmentanddisclosurestandards.html#vulnerability-communication) aggregate information about the number and severity of security vulnerabilities addressed in each release. The tables below provide an overview of security issues addressed and their relative severity based on [standard scoring](https://docs.aveva.com/bundle/security-commitment-and-disclosure-standards/page/securitycommitmentanddisclosurestandards.html#vulnerability-scoring).

## Distribution Kits

| Product                           | Software Version |
|---------------------------------- | ---------------- |
| PI to Data Hub Agent Installation | 2.2.1163         |

©`2023` AVEVA Group plc and its subsidiaries. All rights reserved.