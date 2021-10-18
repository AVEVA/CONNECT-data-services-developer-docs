---
uid: EdgeSystemTemplates
---

# Edit a configuration template

You can create and manage edge system template configurations within AVEVA™ Data Hub. Once the configuration is complete, you can export configuration files by component or edge system to manually apply to the edge system. You can also use an exported configuration file as a template for configuring other edge systems by importing it during configuration. Default configurations are available for supported edge system types. The maximum size for a configuration file is 16 MB.

**Note:** You can create configuration templates for the following edge system types:

 - Edge Data Store

 - OPC UA adapter

 - Modbus TCP adapter

## Add a new template

Use the following procedure to modify an edge system configuration template and export it for use:

1. In the left pane, select **Data Management** > **Edge Systems**.

1. Verify that the **Edge Systems/Configuration Library** selector is set to **Configuration Library**.

1. Click **Add Template**.

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

## Edit an existing template

Use the following procedure to modify an edge system configuration template and export it for use:

1. In the left pane, select **Data Management** > **Edge Systems**.

1. Verify that the **Edge Systems/Configuration Library** selector is set to **Configuration Library**.

1. Find and click on the template to configure.

1. In the right pane, click **Edit Template** or ![Edit](images/pencil-icon.png).

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
