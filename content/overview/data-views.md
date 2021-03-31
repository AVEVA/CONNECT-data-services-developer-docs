---
uid: Dataviews
---

# Data views

The OCS Portal provides the ability to create and configure data views in a graphical user interface. You create a data view by defining the target namespace, the source stream or streams, the desired data fields, time period, and interpolation interval. 

## Create a data view

To create a new data view, complete the following:

1. In the **Data Views** pane of the OCS Portal, click **Add Data View8*.
2. Enter the data view **Name** and **Description** in the **Data View Information** pane.
3. Click **Standard** or **Narrow** to specify the general shape of the data display.
4. In the **Query ID** field in the center pane, enter a name for *Query1* in the **Query ID** field, or accept the default name. 
5. In the **Query Type** section, select **Streams** or **Assets** to indicate which objects you want this query to search.

   **Note**: Assets are available for use through specific licensing only. If you are interested in using Assets, contact your account team for more details. 
   
6. In the **Search** field of the **Query Value** section, type a portion of the name of any known stream or asset (preceded/followed by the * wildcard symbol). 

   **Note**: If you have created a metadata rule in the same namespace, you can enter a selected metadata key instead of a stream name in the **Search** field to select a more specific set of streams.
   
7. Click **Save**. The query results populate and the **Index Configuration** pane displays.

## Configure a data view

1. In the **Index Configuration** pane, select the date and time for the **Start Index** and **End Index** to specify the time period of the data to be included in the data view.
2. Enter a value in the **Time Interval** field to specify the time interval by which to display data. The **Time Interval** field provides entry spaces for Days, Hours, Minutes, and Seconds.
3. Select **Save Default with Data View** to save your settings with this data view.
4. In the **Field Management** pane, click **+ Add** to select available data fields from the query results to include in the data view. Select the data fields you want to add in the **Add Data Fields** dialog and click **Add**.
5. In the **Field Management** pane, use the Up and Down Arrows to move selected data fields up or down in the display, and click **Apply**.
6. Click **Save**.







