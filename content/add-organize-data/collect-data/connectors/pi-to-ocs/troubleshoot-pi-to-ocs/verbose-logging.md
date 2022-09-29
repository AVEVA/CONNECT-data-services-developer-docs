---
uid: VerboseLogging
---

# Verbose logging

If there are problems with a transfer, you can enable verbose logging from the `Transfer Settings` window to capture more detailed logs for specified PI points and AF elements.

To enable verbose logging:

1. In the `PI to Data Hub Agents` page, select the agent that contains the transfer you want to edit.

1. Select **View/Edit Transfer**.

1. In the transfer pane, select the **Edit Mode** toggle.

   Edit mode is enabled and the **Search** pane opens. 

1. To open the `Transfer Settings` window, select **Settings**, then select the **Enable Verbose Logging** option, and select **Ok**.

1. Select **Verbose Logging** to display the `Verbose Logging` pane.

1. To include PI points in the verbose logging, select the **PI Points** tab, select the PI points you want to include, and select **Add Points** in the `Verbose Logging` pane.

   **Note:** Up to 10 PI points can be included.

1. To include AF elements in the verbose logging, select the **AF Elements** tab, select the elements you want to include, and select **Add Elements** in the `Verbose Logging` pane.

   **Note:** Up to 10 AF elements can be included.

1. In the **Log until** field enter an ending time for the verbose logging. The default duration is one day, and the maximum time is 30 days.

1. Select **Save** to retain these changes and return to the `PI to Data Hub Agents` page.

## Removing PI points and AF elements

If you edit a transfer and remove PI points or AF elements from the `Verbose Logging` pane, any corresponding information is removed from the log.

## Viewing the log

The verbose logging information is contained in the PI to Data Hub Agent logs that are viewable in the Windows Event Viewer. See <xref:view-logs>.
