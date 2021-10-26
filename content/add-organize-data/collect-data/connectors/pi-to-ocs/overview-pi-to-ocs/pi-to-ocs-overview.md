---
uid: pi-to-ocs-overview
---

# Overview of PI to Data Hub

PI to Data Hub enables data transfer from an on-premises PI Server to OSIsoft Cloud Services (OCS). Transferring PI System data allows your organization to have data available wherever you go, so you can connect with the best in-class analytics, and with your community of vendors, service providers, and business partners. PI to Data Hub includes the following features:

* Transfer of a selection of Data Archive PI points and AF elements from PI Servers to OCS Sequential Data Store (SDS) [streams](xref:sdsStreams). Some of the PI point attributes and asset information is transferred as SDS stream [metadata](xref:sds-streams-metadata) and properties.

* AF elements and attributes are transferred as assets and metadata and properties.

* Simultaneous transfer of both historical and streaming data from Data Archive and an AF server to SDS for a selection of PI points.

* Configuration of a PI points and assets selection and data transfer management from the portal

PI to Data Hub has the following components:

- *PI to Data Hub Agent* - an on-premises component that serves as a bridge between the data source(s) and the OCS destination. The agent runs as a service and performs fast, secure data transfers.

- *PI System connection* - a cloud component which resides within OCS and receives data from the on-premises PI to Data Hub Agent and stores it in SDS.

**Note:** Storage in SDS is partitioned by namespace.

The deployment of a PI to Data Hub Agent establishes a one-to-one connection from an on-premises Data Archive and optional AF server to AVEVA™ Data Hub. The following diagram shows a deployment of PI to Data Hub Agents that transfer data to AVEVA™ Data Hub.

![PI to Data Hub](../../images/ocs-diagram.png)
