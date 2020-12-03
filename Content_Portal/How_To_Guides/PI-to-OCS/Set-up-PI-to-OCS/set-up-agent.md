---
uid: set-up-agent
---

# Confirm the PI to OCS Agent is running

After installation, check that the PI to OCS Agent Windows service is running on the machine that you installed the agent. You also need to confirm the agent has successfully connected to and registered with your on-premises PI Data Archive.

## Procedure
1. Type `services.msc` in the text box next to the **Windows** menu button, then press [ENTER].
2. In the **Services** window, verify that that the PI to OCS Agent’s status is running.

![ ](../images/services-window.png "Services window")

_Services window – PI to OCS Agent service_

3. Navigate to the Connections page, then select the connection you just created.
4. On the Details tab, view the Data Source Status field.
5. Verify that Registered appears next to the Data Source Status field.

![ ](../images/regstrd-data-source.png "Registered data source")

_Registered data source_

**NOTE:** It may take a few minutes for your PI System to be registered. The following states may also appear next to the Data Source Status field to indicate a connection issue:



State | Description
---------|----------
 Data Source Connection Issue| Indicates the PI To OCS Agent isn’t able to connect to the PI Data Archive. Some reasons for this status include the PI Data Archive is turned off, a firewall issue is preventing connections or an incorrect name is configured for the Data Archive (for example, trying to connect to a machine that doesn’t exist/was renamed). There may be additional reasons for this status.
 Data Source Security Issue | Indicates the PI Data Archive connection is unsecure and security settings need to be addressed. 
 Not Registered | You need to troubleshoot your PI System connection. Contact OSIsoft Technical Support at +1 510-297-5828 or through the OSIsoft Customer Portal Contact Us page.