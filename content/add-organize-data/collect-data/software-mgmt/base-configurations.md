---
uid: AddBaseConfiguration
---

# Add and edit base configurations

You can create and edit base configurations for edge systems in OCS. Once the configuration is complete, export the configuration in a text file to manually apply it to the edge system in the field or to deploy it to the edge module using AVEVA Edge Management. You can also use an exported configuration text file as a template for configuring other edge systems by importing it. Default configurations are available for supported edge system types. The maximum size for a configuration file is 16 MB.

You can create configuration templates for the following edge system types:

 - PI Adapter for Azure Event Hubs
 
 - PI Adapter for BACnet 

 - PI Adapter for DNP3

 - Edge Data Store

 - Edge Data Store Module

 - PI Adapter for Modbus TCP
 
 - PI Adapter for MQTT

 - AVEVA Adapter for MQTT Module

 - PI Adapter for OPC UA

 - AVEVA Adapter for OPC UA Module

 - PI Adapter for RDBMS

 - PI Adapter for Structured Data Files

**Note:** You can only deploy edge modules using AVEVA Edge Management. 

The `namespaceId` in the data and health endpoint URLs defaults to the namespace where the base configuration is created. For example, if the namespace of the base configuration is MyData, the endpoint URL would be `https://website.com/api/v1/Tenants/{tenantId}/Namespaces/MyData/Omf`.

## Edge module configuration

For edge modules, use variables to denote secrets in configuration files. Variables must be used within the configuration file in place of actual secret and password values. Use the following variables as required for your specific configuration:

  - `{{EgressEndpointSecret}}` - Use this variable for the secret or password value to connect to the egress endpoint. When sending data to AVEVA Data Hub, use this variable in place of the client secret. When sending data to PI Web API, use this variable in place of the password.
  
  - `{{AdditionalEgressEndpointSecret}}` - Use this variable when egressing data to more than one endpoint, when the other endpoint requires a different secret or password. 
  
  - `{{DataSourceSecret}}` - Use this variable in place of a data source password when the data source you are connecting to requires a password in order to connect.
  
  - `{{AdditionalDataSourceSecret}}` - Use this variable when connecting to more than one data source, when the other data source requires a different password in order to connect.

When you deploy the configuration in AVEVA Edge Management, you define values for the variables and securely transfer those values to the device. For more information, see [Deploy an edge module](xref:DeployModule).

## Add a new base configuration

To create a edge system base configuration and export it for use:

1. In the left pane, select **Data Collection** > **Software Management**.

1. Verify that the **Edge Systems/Base Configurations** selector is set to **Base Configurations**.

1. Select **New Base Configuration**.

1. In the **Base Configuration Name** field, enter a name to identify the configuration.

1. In the **Type** and **Version** fields, select the edge system type and version for which to create the configuration.

   The default configuration for the selected edge system type displays.

1. To import a configuration, select **Import Configuration**, then browse to the JSON file that contains the configuration, and select **Import**.

1. (Optional) In the **Section Select** dropdown list, select the section of the configuration to modify. The default option of `JSON Configuration` shows the entire configuration.

1. Modify the JSON as needed. For configuration guidelines, refer to the specific edge system documentation.

   **WARNING:** For security reasons, do not include secrets in the configuration. Secrets cannot be stored or exported in a configuration. For edge modules, variables must be used within the configuration file in place of actual secret and password values. For more details, see the [Configure a Module](https://edgemanagement.connect.aveva.com/help/#/home/665922/10/11) topic in the AVEVA Edge Management documentation.

   Errors in the JSON syntax are underlined. To see an explanation of the issue, hold the mouse over the underlined text. The overall status of the JSON syntax is displayed over the right pane.  

1. To export the completed configuration, do one of the following:

   - To export just the selected section, select **Export Section** in the right pane. 

   - To export the entire configuration in one file, select **Export Configuration**.

   The JSON file is downloaded to your browser.

1. When you have finished, select **Save & Close**.

1. Select **Save & Close** to confirm the changes. 

## Edit an existing base configuration

To modify a base configuration and export it for use:

1. In the left pane, select **Data Collection** > **Software Management**.

1. Verify that the **Edge Systems/Base Configurations** selector is set to **Base Configurations**.

1. Find and select the base configuration to modify.

1. In the right pane, select the edit icon ![Edit](../../../_icons/default/pencil.svg).

1. Modify the base configuration name, **Type**, and **Version** as needed.

1. **Optional:** In the **Section Select** dropdown list, select the section of the configuration to modify. The default option of `JSON Configuration` shows the entire configuration.

1. Modify the JSON as needed. For configuration guidelines, refer to the specific edge system documentation.

  **WARNING:** For security reasons, do not include secrets or passwords in the configuration. Secrets and passwords cannot be stored or exported in a configuration. Client secrets and passwords must be applied directly on the device. For edge modules, variables must be used within the configuration file in place of actual secret and password values. For more details, see the [Configure a Module](https://edgemanagement.connect.aveva.com/help/#/home/665922/10/11) topic in the AVEVA Edge Management documentation

  Errors in the JSON syntax are underlined. To see an explanation of the issue, hold the mouse over the underlined text. The overall status of the JSON syntax is displayed over the right pane.  

1. To export the completed configuration, do one of the following:

   - To export just the selected section, select **Export Section** in the right pane. 

   - To export the entire configuration in one file, select **Export Configuration**. 

   The JSON file is downloaded to your browser.

1. When you have finished, select **Save & Close**.

1. To confirm the changes, select **Save & Close**. 
