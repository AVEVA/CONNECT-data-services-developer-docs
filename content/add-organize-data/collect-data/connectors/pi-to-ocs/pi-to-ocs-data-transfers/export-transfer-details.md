---
uid: export-transfer-details
---

# Export transfer details

You can export a list of all the AF elements and implicit/explicit PI points in a transfer for your records. Exported transfer details include the name of the transfer and contain all or some of the following information:

* The paths and names of AF elements
* The paths and names of implicit PI points
* The paths and names of explicit PI points

**Note:** During query retrieval, the **Export** button cannot be used until all PI points and AF elements have been retrieved.  To use the **Export** button while implicit PI points are being retrieved, turn off the **Show Implicit PI Points** toggle setting.  You can then use the **Export** button to begin exporting transfer details for explicit PI points.  

If implicit PI points cannot be loaded to a transfer, details for these points are not included in the export file.

#### Procedure

1. In the `PI to OCS Agents` window, select an agent.

2. Click the **View Transfer** button on the `Details` pane.

   **Result:** The transfer opens.

3. Click the **Export** button in the upper-right corner of the screen.

   **Result:** The `Export Transfer` dialog box opens.
   ![](..\..\images\export-db.png)
4. Under the **Select Export Options** list, click to select or deselect the transfer details you want to include or exclude in the .csv file:
   * **All** (default): The names and paths of all AF elements and implicit and explicit PI points
   * **AF Elements**: All AF elements
   * **PI Points (Implicit)**: All loaded implicit PI points
   * **PI Points (Explicit)**: All the explicit PI points
5. Click the **Export** button to open the **Save As** dialog box.
6. In the `Save As` dialog box, navigate to where you want to save the file, enter a name for the .csv file, then click **Save**.
   **Result:** A .csv file that contains a list of your selected transfer details is saved.