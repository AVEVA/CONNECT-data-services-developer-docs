---
uid: EditEdgeSystem
---

# Edit edge system configuration

You can edit edge system configurations within AVEVA™ Data Hub. You can create a configuration from scratch, use a default configuration or a configuration template, or import a configuration file. Once the configuration is complete, you can export the configuration file for each component or for the edge system to manually apply to the edge system. You can use an exported configuration file to configure other edge systems by importing it. The maximum size for a configuration file is 16 MB.

**Note:** Configuration is available for the following edge system types:

 - Edge Data Store

 - OPC UA adapter

 - Modbus TCP adapter

Use the following procedure to modify an edge system configuration and export it for use:

1. In the left pane, select **Data Management** > **Edge Systems**.

1. Verify that the **Edge Systems/Configuration Library** selector is set to **Edge Systems**.

1. Find and click on the edge device to configure.

1. In the right pane, click **Edit Edge System** or ![Edit](images/pencil-icon.png).

1. To manage the tags for an edge system, click **Add Tag** ![Add Tag](images/edge-system-add-tag.png) and then do the following:

 - To add a tag, enter the tag text in the **New Tag** field and press Enter.

 - To delete a tag, click **X** in the tag bubble.

1. To create the configuration, do one of the following:

 - Click **Start With Default** to use the default configuration for the edge system type.
 
 - Click **Import Configuration** to select a JSON file that contains the configuration.

1. In the **Section Select** field, select the section of the configuration to modify or select `JSON Configuration` to see the entire configuration.

1. Modify the JSON as needed. Refer to the specific edge system documentation for configuration guidelines.

 Do not include secrets in the configuration. Secrets cannot be stored or exported in a configuration.

 Errors in the JSON syntax are underlined. Hold the mouse over the underlined text to see an explanation of the issue. The overall status of the JSON syntax is displayed over the right pane.  

1. To export the completed configuration, do one of the following:

 - Click **Export Section** in the right pane to export just the selected section. 

 - Click **Export Configuration** to export the entire configuration in one file.

 The JSON file is downloaded to your browser.

1. When you have finished configuring the edge system, click **Save & Close**.

1. Click **Save & Close** to confirm the changes. 
