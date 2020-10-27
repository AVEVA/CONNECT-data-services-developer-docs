---
uid: min-sys-reqmnts
---

# Minimum system requirements

The following system requirements are needed to transfer data from your on-premises PI Server to OCS using the PI to OCS Agent:

| System component | Requirement | 
| ------------- | ----------------- | 
| PI Server | <ul><li>PI Data Archive 2016 R2 (v. 3.4.405.1198) or later.</li><li>See the PI Data Archive Release notes for all other minimum system requirements.</li></ul> |
| PI to OCS Agent | <ul><li> Install on a different computer than your PI Data Archive deployment.</li><li>Operating system: 64-bit version of Windows (v. 1809) or 64-bit version of Windows Server 2016 Standard (v. 1803)<br>**Note.** 32-bit operating systems are not supported.</li><li>A computer with adequate CPU performance and 8 GB RAM</li><li>An Internet connection and a secure network connection to the PI Data Archive computer</li></ul> |

## Administrative privileges

Use an account with administrative privileges to log on to the OCS customer portal, and install the PI to OCS agent.  The PI to OCS agent must be installed on the local machine using an account with Administrative privileges.

The PI to OCS Agent requires the Windows service to "run as user". You must have read access to the following data on PI Data Archive:

* Archive data (the PIARCDATA Security table)
* The PI points configuration table (PIPOINT Security table)
* All PI points and data being transferred