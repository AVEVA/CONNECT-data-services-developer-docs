---
uid: DeployModule
---

# Deploy an edge system module

After you export an edge system module configuration, use AVEVA Edge Management to add the configuration to the module and deploy it to edge devices in the field. For details on how to configure and deploy an edge module, see the [AVEVA Edge Management](https://edgemanagement.connect.aveva.com/help/#/home/665922/10/11) documentation. 

For modules that require secrets, complete the secret store configuration in AVEVA Edge Management to define values for the secret variables. AVEVA Edge Management encrypts the values and provides the `Setup module secret command`. After you deploy the module configuration, run the `Setup module secret command` in a Linux terminal on the device to complete the secure transfer of secret values.

After deploying the configuration, import the configuration file, including any modifications made in the field, to the corresponding edge system twin in OCS. This provides an accurate record of the configuration.
