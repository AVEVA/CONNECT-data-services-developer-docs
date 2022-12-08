---
uid: PItoDH
---

# PI to Data Hub

PI to Data Hub enables you to transfer both on-prem PI data and Asset Framework (AF) data to AVEVA Data Hub.  

## PI to Data Hub architecture

PI to Data Hub enables you to use one PI to Data Hub Agent to connect and transfer your on-prem data to AVEVA Data Hub from one PI Data Archive and one optional Asset Framework (AF) server. The PI to Data Hub Agent creates and sends a transfer that contains the requested PI point data (metadata and PI events) and assets (AF elements and attributes) to AVEVA Data Hub.

### Restrictions of PI to Data Hub architecture

These are some restrictions to the PI to Data Hub architecture:

* The connecting AF server must reference the connected PI Data Archive. The list of available PI Data Archive servers is based on what servers are referenced by elements on the AF server you selected.

* The same PI to Data Hub Agent is required to transfer data from the on-prem PI Data Archive and AF server.

## PI to Data Hub best practices

Only a single PI to Data Hub Agent can connect to a single PI server or optional AF server and transfer data to a single namespace. This restriction prevents multiple PI to Data Hub Agents from pulling data from a single PI Data Archive, which places an excessive load on the server. The following actions are recommended to address this issue:

- Install the PI to Data Hub Agent on a host computer that is separate from the PI Data Archive deployment, so it does not add to the load on the server.

- Keep the PI to Data Hub Agent software version up-to-date for the best performance. The portal indicates when an agent is out of date and needs to be updated. 

**Note:** Multiple PI to Data Hub Agents can connect to and transfer data from the same PI Server if the agents are installed on different machines and assigned to different namespaces within the same tenant.
