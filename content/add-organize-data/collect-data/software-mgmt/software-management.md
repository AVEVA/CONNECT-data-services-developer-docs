---
uid: SoftwareMgmt
---

# Edge data store & adapters (Preview)

`AVEVA Data Hub` provides a centralized location to monitor the health and manage the software configuration of edge modules and systems, including Edge Data Store and AVEVA Adapters. This shows you the data collection software that deploys to remote devices. To be available in `AVEVA Data Hub`, a system must have an AVEVA Data Hub health endpoint configured. For information on configuring health endpoints, see the specific system product documentation.

Systems have product executables that you install on devices in the field. Use `Edge Data Store & Adapters` to create configuration files that you then deploy directly on those devices.

Edge modules have the same functionality as their corresponding systems, but are deployed and managed through AVEVA Edge Management. Edge modules operate in Alpine Linux containers on devices. Each edge module deployment includes the container OS, the system, and its configuration files. For details, see the [AVEVA Edge Management](https://docs.aveva.com/bundle/pi-adapter-azure-event-hubs/page/configuration/configuration.html) documentation.

## Health monitoring

The `Edge Data Store & Adapters Systems` page displays a list of system digital twins. Each system twin is a virtual representation of an actual system that is currently writing health data to the selected namespace. You can review health information for systems, including the current status of each system and when it last communicated with AVEVA Data Hub. Use sort and filter functionality to navigate system twins to pinpoint problems and identify gaps in data collection. View detailed health information for your systems to understand their overall health. 

## Configuration management

Use the `Edge Data Store & Adapters Systems` page to review detailed information about each system, its components, and its configurations. You can also manage, create, and edit system software configurations.

Use the `Edge Data Store & Adapters Configuration Templates` page to create and maintain a collection of configuration templates that you can apply to systems. Create each configuration template from either a default configuration or an imported configuration. Then modify configurations using the portal's built-in editor, which identifies formatting errors as you work, helping you avoid problems later. Export a configuration template to manually apply it to a physical system in the field or to deploy it using AVEVA Edge Management. For more information, see the [AVEVA Edge Management](https://edgemanagement.connect.aveva.com/help/#/home/665916/10/11) documentation.

In the field, you may need to customize a configuration template for a specific system. Once a system configuration is complete and it is writing data to health data to AVEVA Data Hub, the `Edge Data Store & Adapters` page shows its corresponding system twin. To store, review, and access configurations from a central location, import the actual configurations from the field to the corresponding system twins. 
