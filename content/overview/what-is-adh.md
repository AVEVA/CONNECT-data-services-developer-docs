---
uid: WhatIsADH
---

# What is AVEVA Data Hub?

AVEVA Data Hub is a cloud data platform for storing, retrieving, and analyzing sequentially indexed data. AVEVA Data Hub creates a seamless, trustworthy data infrastructure to incorporate information from sensors, plants, enterprises, and communities of interested users. This infrastructure enables data sharing and usage within your organization, across locations, and even with external partners.

AVEVA Data Hub offers the following capabilities: 

  - [Easy data collection](#easy-data-collection)
    - [PI to Data Hub Agent](#pi-to-data-hub-agent)
    - [Open Message Format](#open-message-format)
    - [Edge Data Store](#edge-data-store)
    - [PI Adapters](#pi-adapters)
    - [REST API](#rest-api)
  - [Integration with external tools and applications](#integration-with-external-tools-and-applications)
  - [Secure and robust data infrastructure](#secure-and-robust-data-infrastructure)
  - [Elastic resource allocation](#elastic-resource-allocation)
  - [Interruption resilience](#interruption-resilience)
  - [Easy management and maintenance](#easy-management-and-maintenance)

## Easy data collection

AVEVA Data Hub provides a variety of methods to collect data into the system. You can ingress data from an external application or from PI Server directly to AVEVA Data Hub using any of the following methods: 

- PI to Data Hub Agent
- Open Message Format (OMF)
- Edge Data Store
- PI Adapters
- REST API

### PI to Data Hub Agent

The PI to Data Hub Agent transfers PI time-series data from an on-premises PI Server into AVEVA Data Hub. PI to Data Hub maps PI Data Archive PI points to SDS types and streams. 

### Open Message Format

Open Message Format (OMF) is a platform-independent format for passing JSON messages to AVEVA Data Hub using an HTTP client. Use OMF to achieve a high-throughput data feed into AVEVA Data Hub. 

### Edge Data Store

Edge Data Store (EDS) uses OMF messages to send data into AVEVA Data Hub from edge devices.

### PI Adapters 

PI Adapters use OMF messaging to send data into AVEVA Data Hub from a variety of data collection devices. 

### REST API 

Developer-friendly REST APIs provide programmatic access to read and write sequential data into AVEVA Data Hub. 

## Integration with external tools and applications

AVEVA Data Hub allows you to integrate data with many different partner applications, data pipelines and workflows, collaboration tools, and business intelligence (BI), data analytics, visualization, and custom software/applications. 

A few examples include these tools: 

- Power BI 
- Grafana

You can integrate and view AVEVA Data Hub data in the following ways: 

- Build applications with AVEVA Data Hub client libraries to read and write data to AVEVA Data Hub 
- Use the AVEVA Data Hub REST API to read and write data to AVEVA Data Hub 
- Retrieve tabular data with AVEVA Data Hub data views 

AVEVA Data Hub also offers opportunities for many new types of data consumers. For example, you could integrate AVEVA Data Hub with applications that perform machine learning or AI functions. 

## Secure and robust data infrastructure

AVEVA Data Hub is built from the ground up to ensure security. The AVEVA Data Hub platform is based on industry standard techniques to ensure the strongest possible data integrity. User authentication is handled through AVEVA Connect. Authenticated users can only perform actions for which their role is authorized. Machine access to AVEVA Data Hub is controlled through a variety of defensive strategies. All data in AVEVA Data Hub is fully encrypted in transit and at rest. 

## Elastic resource allocation

Due to its microservice-based architecture, AVEVA Data Hub dynamically adapts to workload changes by automatically provisioning and de-provisioning resources. Each microservice performs a subset of the system’s overall capabilities, and when orchestrated together, they function as a complete platform. 

When AVEVA Data Hub is turned on in a folder for a tenant in AVEVA Connect, a new set of microservices and all the necessary data storage is provisioned for that folder/namespace. As the tenant’s needs for the namespace grow, AVEVA Data Hub automatically provisions additional microservices and storage so the namespace can expand horizontally. Similarly, if requirements shrink, AVEVA Data Hub can reduce the number of required microservices and de-allocate storage. 

## Interruption resilience

To prevent data interruptions or loss, AVEVA Data Hub incorporates many safeguards and is designed for high availability. You are not required to perform any specific actions to ensure continuous access to reliable, distributed data storage.

AVEVA Data Hub is continuously tested to ensure the platform is performing reliably. Both the platform and the underlying operating systems are updated regularly. In addition, frequent threat analyses is conducted to thwart potential exploitations. Load balancing precludes distributed denial of service attacks. A gateway prevents unauthorized access to resources.

## Easy management and maintenance

AVEVA manages, operates, and maintains all aspects of the AVEVA Data Hub platform. AVEVA Data Hub is built and deployed on Microsoft Azure and operates outside the AVEVA corporate firewall. Currently, AVEVA Data Hub runs in three Azure regions: West US, West Europe, and Australia. By housing the platform in multiple regions, AVEVA Data Hub accommodates regulations that mandate where data must be stored.

Access your data infrastructure through the AVEVA Data Hub web-based portal or by using modern, secure, developer-friendly REST APIs.

## Service description

For more information on operational topics relating to AVEVA Data Hub, such as data ownership, data privacy, database backup and redundancy, see the [AVEVA Data Hub Service Description](https://www.aveva.com/en/legal/service-description/).