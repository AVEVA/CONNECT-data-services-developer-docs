---
uid: WhatADHdoes
---

# Core functionality

AVEVA Data Hub consists of several areas of core functionality.

## Access management

You can customize AVEVA Data Hub access management to meet your organization's requirements and needs. Administrators can:

- Create and manage users (user accounts must exist first in AVEVA Connect)

- Create and manage clients

- Define and assign roles

- Manage folders/namespaces (through AVEVA Connect)

- Customize authentication and authorization (through AVEVA Connect)

Administrators can define the permissions to an AVEVA Data Hub resource by configuring the
access control list (ACL) for that resource. They can also perform tenant management using the AVEVA Data
Hub REST API or the AVEVA Data Hub portal.

## Data collection

AVEVA Data Hub provides a variety of methods to collect data. You can ingress data from an external application or from PI Server directly to AVEVA Data Hub using any of the following methods: 

- PI to Data Hub Agent: Transfers on-premises PI data and Asset Framework (AF) data into AVEVA Data Hub.

- Custom Open Message Format (OMF) applications: OMF is a platform-independent format for passing JSON messages to AVEVA Data Hub using an HTTP client. Use OMF to achieve a high-throughput data feed into AVEVA Data Hub. 

- Edge Data Store (EDS): Uses OMF messages to send data into AVEVA Data Hub from edge devices.

- PI Adapters: Use OMF messages to send data into AVEVA Data Hub from a variety of data collection devices. 

- REST APIs: Developer-friendly APIs provide programmatic access to read and write sequential data into AVEVA Data Hub.
 
## Data management 

The Sequential Data Store (SDS) is the storage layer of AVEVA Data Hub. It is used to store, retrieve, and organize any type of streaming data. Typically, developers use the SDS as part of their customized applications. It is primarily for time-series data, but also more complex data such as location, time/depth, etc.

The basic features of the SDS include: 

- Types: A type defines the structure of data to be collected in AVEVA Data Hub. A type is analogous to a template that defines each instance in a stream of data.

- Streams: A stream is a series of ordered events. Each event is an instance of a type. Collectively, the stream of data forms the structure that the type specifies.

- Stream views: A stream view is a logical overlay for stream data that allows you to create customized views of data streams that meet the needs of multiple users without changing the original data. With a stream view you can do things such as include a subset of the data in a stream, convert units of measure, and change names so terminology is appropriate for a particular audience.

## Community sharing

With Communities you can create a private group where operational data can be shared and viewed by trusted business partners, service providers, and analytics providers. Sharing data with AVEVA Data Hub allows real-time updating of data, full data granularity, and an automated data copy outside your organization. You can share data from a PI server without requiring your partners to have a PI system.

Sharing data streams allows you to:

- Collectively operate more efficiently and reduce waste.

- Detect hidden problems in your equipment and processes, helping to troubleshoot issues.

- Predict future failures before they occur.

- Share data across engineering and operational partners.

## Monitoring and analysis 

After defining types, streams, and stream views, use the analytical tools in AVEVA Data Hub to sort and visualize the data. Two analytical tools are available in AVEVA Data Hub: 

- Trend: The Trend feature converts stream data to a graphic view, which can reveal trends, high points, or trouble spots. Use Trend to select data streams in a namespace, specify a time range, and then render a graph of those data values. This allows for quick data exploration and troubleshooting within the portal that can be easily shared with colleagues.

- Assets: Assets are a digital twin of physical entities in the real world. An asset can consist of data from one or more streams. Assets are a useful way to organize and contextualize data streams. With PI to Data Hub data transfers, for example, you can organize multiple PI tags under a single asset. You could create an asset with streams measuring data for thermostats, ventilation equipment, lighting systems, and security.

## Data science enablement

You can group and organize operational PI, IoT, and AVEVA Data Hub data. By arranging data into forms that can be consumed by third-party data science applications, data scientists can conduct deep analysis to detect unrealized patterns and insights. Data science enablement efforts allow for better informed planning, predictive maintenance, and operational optimization. 

Data views allow you to order, index, and organize data from multiple streams to create curated data subsets. Data views serve as a bridge between raw AVEVA Data Hub data and data science applications. Use an API or the AVEVA Data Hub portal to create data views to arrange data for consumption by third-party data science applications.

The AVEVA Data Hub Power BI Connector retrieves data views from AVEVA Data Hub and makes them available in Microsoft Power BI for advanced data visualization and analysis. You can also use Microsoft Power BI to edit the query generated from the connector to modify the dates, edit the interpolation interval, and enable an incremental refresh of data.
