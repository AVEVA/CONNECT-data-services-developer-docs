---
uid: export-missing-points
---


# Export a list of missing PI points

Sometimes, PI points cannot be transferred to OCS because they have been removed on the source PI Server. When this happens, PI to OCS flags the points as missing and displays a message. You can export a file that contains a list of these missing PI points for your records. The .CSV file contains the following information:

- Transfer name
- PI point IDs
- The name of the source PI Server

### Procedure

1. In the `PI to OCS Agents` window, select the transfer with the unresolved PI points.
2. Click the **View Transfer** button on the `Details` pane.
   **Result:** The `Transfer` window opens.
3. Click the **Export Missing PI Point Ids** button.
   **Result:** A .CSV file that contains a list of missing PI points is saved.