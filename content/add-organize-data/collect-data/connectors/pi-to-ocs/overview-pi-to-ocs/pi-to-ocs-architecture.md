---
uid: pi-to-ocs-architecture
---

# PI to Data Hub architecture

PI to Data Hub enables you to connect and transfer your on-prem data to AVEVA Data Hub from one PI Data Archive and one optional Asset Framework (AF) server using one PI to Data Hub Agent. The PI to Data Hub Agent creates and sends a transfer that contains the requested PI point data (metadata and PI events) and assets (AF elements and attributes) to AVEVA Data Hub. <!--What else do we want to say here?-->

## Restrictions of PI to Data Hub architecture

These are some restrictions to the PI to Data Hub architecture:

* The connecting AF server must reference the connected PI Data Archive. The list of available PI Data Archive servers is based on what servers are referenced by elements on the AF server you selected.

* The same PI to Data Hub Agent is required to transfer data from the on-prem PI Data Archive and AF server.
