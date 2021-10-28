---
uid: EdgeSystemTemplates
---

# Add and edit edge system configuration templates

You can create and edit edge system configuration templates in OCS. Once the configuration is complete, you can export the configuration file by each component or edge system to manually apply to the edge system in the field. You can also use an exported configuration file as a template for configuring other edge systems by importing it during configuration. Default configurations are available for supported edge system types. The maximum size for a configuration file is 16 MB.

**Note:** You can create configuration templates for the following edge system types:

 - Edge Data Store

 - PI Adapter for BACnet
 
 - PI Adapter for DNP3
 
 - PI Adapter for Modbus TCP
 
 - PI Adapter for OPC UA

## Add a new template

To create an edge system configuration template and export it for use, complete the following procedure:

1. In the left pane, select **Data Management** > **Edge Systems**.

1. Verify that the **Edge Systems/Configuration Library** selector is set to **Configuration Library**.

1. Select **Add Template**.

1. In the **Configuration Template Name** field, enter a name to identify the template.

1. In the **Type** and **Version** fields, select the edge system type and version to create the template for.

  The default configuration for the selected edge system type displays.

1. To import a configuration, select **Import Configuration**, then browse to the JSON file that contains the configuration, and select **Import**.

1. **Optional:** In the **Section Select** field, select the section of the configuration to modify or select `JSON Configuration` to see the entire configuration.

1. Modify the JSON as needed. For configuration guidelines, refer to the specific edge system documentation.

 Do not include secrets in the configuration. Secrets cannot be stored or exported in a configuration.

 Errors in the JSON syntax are underlined. Hold the mouse over the underlined text to see an explanation of the issue. The overall status of the JSON syntax is displayed over the right pane.  

1. To export the completed configuration, do one of the following:

 - To export just the selected section, click **Export Section** in the right pane. 

 - Click **Export Configuration** to export the entire configuration in one file.

 The JSON file is downloaded to your browser.

1. When you have finished configuring the edge system, click **Save & Close**.

1. Click **Save & Close** to confirm the changes. 

## Edit an existing template

Use the following procedure to modify an edge system configuration template and export it for use:

1. In the left pane, select **Data Management** > **Edge Systems**.

1. Verify that the **Edge Systems/Configuration Library** selector is set to **Configuration Library**.

1. Find and select the template to modify.

1. In the right pane, select the edit icon ![Edit](images/pencil-icon.png).

1. Modify the template name, **Type**, and **Version** as needed.

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
