---
uid: EdgeSystems
---

# Edge systems software management

Edge systems software management provides a centralized location to monitor the health and manage the software configuration of edge systems, including Edge Data Store and PI Adapters. This gives you visibility into the data collection software that is deployed on remote devices.

## Health monitoring

The `Edge Systems` page displays a list of edge system digital twins. Each edge system twin is a virtual representation of an actual edge system that is currently writing health data to the selected namespace. You can review health information for edge systems, including the current status of each system and when it last communicated with OCS. Use sort and filter functionality to navigate edge system twins to pinpoint problems and identify gaps in data collection. View detailed health information for your edge systems to understand their overall health. Digital twins are also created for PI Interfaces that send health data to OCS, which you can use to monitor PI Interface health. 

## Configuration management

Use the `Edge Systems` page to review detailed information about each edge system, its components, and its configurations. You can also manage, create, and edit edge system software configurations.

Use the Configuration Library to create and maintain a collection of configuration templates. Base each configuration template on either a default configuration or an imported configuration. The portal's built-in configuration editor identifies formatting errors as you work, helping you avoid problems later. Export a configuration template to manually apply it to a physical edge system.

In the field, you may customize a software configuration for a specific system. Once an edge system is writing data to OCS, the `Edge Systems` page shows its corresponding edge system twin. To store, review, and access configurations from a central location, import software configurations from the field to the corresponding edge system twins. 
