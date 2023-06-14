---
uid: lp-setup
---

# Set up PI to Data Hub Agent

The PI to Data Hub Agent setup occurs prior to data transfer and involves temporarily disabling Internet Explorer enhanced security, downloading and installing the PI to Data Hub Agent, and connecting to data sources.

## Downloading the Agent Setup Kit

There are two options for downloading and installing the PI to Data Hub Agent setup kit.  

### Direct download option

You can download the setup kit from the `PI to Data Hub Agents` page on the portal and then transfer it to the computer that will host the agent.

### PI Server installation kit option

The agent is available as an individual feature in the PI Server installation kit in PI Server 2023 and greater. When the PI to Data Hub feature is selected for installation, the PI Server setup kit will download and install the latest version of the agent setup kit from the portal.  

Be aware that, for a new installation, when the PI Data Archive server role is selected, the individual agent feature is also selected by default. If you are planning on transferring a large amount a data, you can choose to deselect this feature and install the agent on a separate host computer from PI Data Archive, as per the "heavy workloads recommendation" mentioned in [PI to Data Hub best practices](PItoDH#pi-to-Data-Hub-best-practices).

