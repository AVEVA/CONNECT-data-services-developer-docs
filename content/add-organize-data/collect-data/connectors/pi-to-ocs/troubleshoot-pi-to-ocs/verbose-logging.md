---
uid: VerboseLogging
---

# Verbose logging

If there are problems with a transfer, you can enable verbose logging from the `Transfer Settings` window to capture more detailed logs for specific PI points and AF elements.

Verbose logging records events for each step in the transfer process related to the tagged PI points and AF elements. These messages are classified as warnings. This information is found in the PI to Data Hub Agent logs, which are viewable in the Windows Event Viewer. See <xref:view-logs>.

The number of events recorded can be very large, so there is a limit of 10 PI points and 10 AF elements that can be tagged. The duration of the verbose logging should also be for a limited time. The default duration is a day and the maximum is 30 days.

To enable verbose logging:

1. In the `PI to Data Hub Agents` page, select the agent that contains the transfer you want to edit.

1. Select **View/Edit Transfer**.

1. In the transfer pane, select the **Edit Mode** toggle.

   Edit mode is enabled and the **Search** pane opens. 

1. To open the `Transfer Settings` window, select **Settings**, then select the **Enable Verbose Logging** option, and select **Ok**.

1. Select **Verbose Logging** to display the `Verbose Logging` pane.

1. To include PI points in the verbose logging, select the **PI Points** tab, select the PI points, then select **Add Points** in the `Verbose Logging` pane.

   **Note:** Up to 10 PI points can be added.

1. To include AF elements in the verbose logging, select the **AF Elements** tab, select the elements, then select **Add Elements** in the `Verbose Logging` pane.

   **Note:** Up to 10 AF elements can be added.

1. In the **Log until** field, enter an ending time for the verbose logging, up to a maximum of 30 days.

   **Note:** When the verbose logging time expires, it deselects the **Enable Verbose Logging** option in `Transfer Settings`.

1. Select **Save** to retain these changes and return to the `PI to Data Hub Agents` page.

## Removing PI points and AF elements

If you edit a transfer and remove PI points or AF elements from the `Verbose Logging` pane, any corresponding information is removed from the log.