---
uid: pi-to-ocs-rel-summary
---

# PI to OCS release summary
Release 1.6.1192: June x, 2020

## Overview

PI to OCS release 1.6.1192 contains enhancements to [what do we want to say here?]

## Fixes:

The following fixes were resolved in release 1.6.1192:

| Item | Description |
| ------------- | ----------------- |
|LogSender doesn’t stop sending when agent/namespace is deleted.|After deleting the data source, the PI To OCS Agent service continues to run. This fix will ensure the service is stopped after the data source is deleted.|
|Agent should handle deletes of Client ID|If the client id associated with the PI To OCS Agent is deleted, the agent services keeps trying to connect to the cloud. This fix ensures the agent service stops trying to connect if the client id is not valid anymore.|
|After the user stops the transfer, the transfer’s status continues to show as Sending Streaming Data|After the PI To OCS Agent has stopped all transfers, the status of these transfers will change to idle.|
|Some PI to OCS warnings spam Event Logger|Ensure the PI To OCS Agent doesn't flood the logs with duplicate messages.|
|                |                      |

## Enhancements:

The follow major improvements were made in release 1.6.1192:

| Item | Description |
| ------------- | ----------------- |
|Add ability for the Agent to send current values for tags that have compression off|The streaming transfer step should write snapshot data to SDS for points with compression off.|
|PI to OCS Agent should update Agent status in OCS to “Shutdown” to indicate when the Agent is shutdown.|	The PI To OCS Agent on a graceful shutdown will send a message that changes the status to Shutdown.|

 
### Security

#### **OSIsoft’s commitment**
Because the PI System often serves as a barrier protecting control system networks and mission-critical infrastructure assets, OSIsoft is committed to (1) delivering a high-quality product and (2) communicating clearly what security issues have been addressed. This release of PI to OCS is the highest quality and most secure version of PI to OCS released to date. OSIsoft's commitment to improving the PI System is ongoing, and each future version should raise the quality and security bar even further.

#### **Platform Requirements:**
The following system requirements are needed to transfer data from your on-premises PI Server to OCS using the PI to OCS Agent: 

| Item | Description | 
| ------------- | ----------------- | 
| PI Server | <ul><li>Minimum supported version of PI Data Archive: 2016 R2</li><li>For full suport of PI to OCS features: PI Data Archive 2017 R2 (v.3.4.405.1198) or later.</li><li> PI AF 2017 R2</li><li>See the PI Data Archive and PI AF release notes for all other minimum system requirements.</li></ul> |
| PI to OCS Agent | <ul><li> Install on a different computer than your PI Data Archive deployment.</li><li>Operating system: 64-bit version of Windows (v. 1809) or 64-bit version of Windows Server 2016 Standard (v. 1803)<br>**Note:** 32-bit operating systems are not supported.</li><li>Processor: 1 gigahertz (GHz) or faster compatible processor or System on a Chip (SoC)</li><li>RAM: 2 gigabyte (GB for 64-bit)</li><li>Hard drive size: 32 GB or larger hard disk</li><li>An Internet connection and a secure network connection to the PI Data Archive computer</li></ul> |
|Specific PI to OCS features| <ul><li>To transfer elements and out of order (OOO) events to OCS: PI AF 2017 R2 or later |
|Technical support and resources| For technical assistance, contact OSIsoft Technical Support at 1+510-297-5828 or through the [OSIsoft Customer Portal](https://www.osisoft.com).|



