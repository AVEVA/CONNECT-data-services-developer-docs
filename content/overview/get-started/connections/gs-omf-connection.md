---
uid: gsOMF
---

# Get started with OMF connections

To send Open Message Format (OMF) data to AVEVA™ Data Hub, you must first configure an OMF connection. For more information about OMF connections, see [OMF best practices](xref:bpOMFConnection).

Use this get started procedure to become familiar with OMF connections.

1. In the left pane, select **Security** > **Clients**.

1. Verify that there is at least one client-credentials client to use in the OMF connection. If you need to create one, see [Add a client credentials client](xref:gpClientCredentialsClient).

1. In the left pane, select **Data Collection** > **OMF Connections**.

1. In the toolbar, select **Add Connection**.

   The `Add OMF Connection` window appears.

1. In the `Add OMF Connection window`, complete the following fields, and then select **Next**:

   * **Name** - Enter a name for the OMF connection.

   * **Description** - (Optional) Enter a description for the connection.

1. In the **Clients** tab, select each client that can be used in the connection from the **Available** list to add it to the **Selected** list.

1. Select **Next**.

1. In the **Namespaces** tab, verify that the MyData namespace appears in the **Selected** list, and then select **Next**.

1. In the **Review** tab, verify that the information is correct, and then select **Save**.

An application can now use the selected client credentials client to write OMF data to the specified namespace.

Follow these tips to learn more about OMF connections.

  **Tip:** Click **Manage Permissions** to open the `Manage Permissions` window. In this window, you configure permissions only on the connection object itself. Click **Cancel** to continue.

 **Tip:** Click **Edit Connection** to open the `Edit` window. Use this window to edit the name and description of the connection. Enter the new name *MyDataEdit* and enter the description *OMF Connection used by MyData*. When you are done, click **Next** until you get to the **Review** tab, and then click **Save**.

## Next step

If you have not already completed [Get started with PI to OCS connections](xref:gsPItoOCS), do this next. Otherwise, continue with [Get started with types](xref:gsTypes).
