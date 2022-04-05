---
uid: edit-transfer
---

# Edit a transfer

You can edit saved transfers by adding or removing AF elements and/or PI points.

**Note:** Your transfer settings affect if streams and data get replicated or deleted from cloud storage after you have removed elements or explicit PI points from your transfer. See [Name the transfer and set data privacy settings](xref:transfer-data) for details.

<!-- VTT: Add note about how the Opt-in setting (Transfer Settings window) affects streams/assets being deleted from cloud storage or replicated, depnding on the client's preference/option selection.-->

To edit an existing transfer, follow these steps:

1. In the `PI to OCS Agents` window, select the agent that contains the transfer you want to edit.

1. Select **View/Edit Transfer**.

1. In the transfer pane, select the **Edit Mode** toggle.

   Edit mode is enabled and the **Search** pane opens. 

1. (Optional) To add PI points to a transfer, enter search criteria on the **PI Point Search** tab, select **Search**, select desired PI points, then select **Add PI Points to Transfer**. 

1. (Optional) To add AF elements to a transfer, enter search criteria on the **AF Elements Search** tab, click **Search**, select desired PI points, then click **Add AF Elements to Transfer**.

1. (Optional) To remove PI points from a transfer, select the **PI Points** tab, select the PI points you want removed, select **Remove Points**, then select **Remove** to confirm.
 
   **Note:** You can only remove explicit PI points from a transfer. To remove implicit PI points from a transfer, you will need to remove the associated AF element. 

1. (Optional) Click **Undo Last Point Removal** to add the removed PI points back to the transfer.

1. (Optional) To remove AF elements from a transfer, select the **AF Elements** tab, select the AF elements you want removed, select **Remove Elements**, then select **Remove**.

   The removed AF elements are marked as **Removed** in the **AF Elements** list. 

   **Note:** Any implicitly referenced PI points that are not referenced by another AF element will also be removed from the transfer.

1. (Optional) Click **Undo Last Element Removal** to add the removed PI points back to the transfer.

1. After transfer edits are done, click **Save** to retain these changes and return to the `PI to OCS Agents` window.

   **Note:** If a transfer was started and in progress when edits were made, these changes will be processed after the transfer is saved.
