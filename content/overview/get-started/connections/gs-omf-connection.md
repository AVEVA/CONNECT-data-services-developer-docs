---
uid: gsOMF
---

# Get started with OMF connections

To send Open Message Format (OMF) data to AVEVA Data Hub, you must first configure an OMF connection. For more information about OMF connections, see [OMF best practices](xref:bpOMFConnection).

Use this get started procedure to become familiar with OMF connections.

To create an OMF connection:

1. In the left pane, select **Security** > **Clients**.

1. Verify that there is at least one client-credentials client to use in the OMF connection. If you need to create one, see [Clients](xref:ccClients).

1. In the left pane, select **Data Collection** > **OMF Connections**.

1. Select **Add OMF Connection** to open the `Add Connection` pane.

1. In the **Name** field, enter *MyData*.

1. Select **Add Client**.

1. Select a client in the list and select ![Assign](../../../_icons/default/plus.svg) to add it to the assigned clients.

   **Note:** For the purposes of this exercise, you may choose any client.

1. Select **Save**.

   An application can now use the selected client-credentials client to write OMF data to the `MyData` namespace.

1. To learn more about OMF connections, do the following:

   - In the `Connection` pane, select **More Options** ![more options](../../../_icons/default/dots-vertical.svg) > **Manage Permissions**.

     In this window, you configure permissions only on the connection object itself. Select **Cancel** to continue.

   - In the `Connection` pane, select **Edit Connection** ![edit connection](../../../_icons/default/pencil.svg) to open the `Edit Connection` pane.

     Use this window to edit the name, description, and assigned clients of the connection. Enter the new name *MyDataEdit* and enter the description *OMF Connection used by MyData*. When you are done, select **Save**.

## Next step

If you have not already completed [Get started with PI to Data Hub connections](xref:gsPItoOCS), do this next. Otherwise, continue with [Get started with types](xref:gsTypes).
