---
uid: troubleshoot-missing-pida
---

# Troubleshoot missing PI Data Archive configuration

If a PI to Data Hub agent's status appears as `No PI Data Archive Configured` in the `PI to Data Hub Agent` window, you may be missing a PI mapping from your Data Archive server to your agent service account. You can correct this issue in the PI to Data Hub Agent Configuration Utility.

**Note:** There may be different reasons why the `No PI Data Archive Configured` status appears under **Data Archive Connection Status** in the PI to Data Hub Agent Configuration Utility. This topic addresses troubleshooting due to a missing PI mapping.

To add a missing PI Data Archive mapping:

1. Open the [PI to Data Hub Agent Configuration Utility](xref:pi-to-ocs-utility) and connect to the portal.

1. After successful authentication, select the Data Archive tab, then select the pencil icon under **PI Mapping**.  

    **Result:** The `Configure Mapping` dialog box opens.

1. Under the **Identity** list, select the identity, group or user for the PI mapping.

1. Select **Create**.

    **Result:** The PI mapping is created for the selected identity, group or user.

1. Select **Close** to exit out of the `Configure Mapping` dialog box. 

1. Select **Remove Server**, then select **Yes** to remove the server and return to the first screen of the PI to Data Hub Configuration Utility.

1. Add the Data Archive server back to the configuration. See [Run the PI to Data Hub Configuration Utility](xref:pi-to-ocs-utility) for more information.  

1. After the Data Archive has been successfully added, select **Save** to save the newly added server configuration.
