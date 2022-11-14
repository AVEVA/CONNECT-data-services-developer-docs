---
uid: DeployModule
---

# Deploy an edge system module

After you export an edge system module configuration, use AVEVA Edge Management to add the configuration to the module and deploy it to edge devices in the field. For details on how to configure and deploy an edge module, see the [AVEVA Edge Management](https://docs.osisoft.com/bundle/pi-adapter-azure-event-hubs/page/configuration/configuration.html) documentation. 

For modules that require secrets, complete the secret store configuration in AVEVA Edge Management and copy the setup module secret command provided. After you deploy the module configuration, run the setup module secret command in a Linux terminal on the device.

After deploying the configuration, to have an accurate record of the configuration, import the configuration file, including any modifications made in the field, to the corresponding edge system twin in OCS.
