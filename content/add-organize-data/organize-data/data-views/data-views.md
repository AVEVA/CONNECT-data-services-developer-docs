---
uid: Dataviews1
---

# Create a data view

Data views are subsets of data from one or more streams. You create a data view by defining the target namespace, and then specifying the source stream or streams, selected data fields, time period, and interpolation interval. 

## Procedure

1. In the left pane, select **Analytics** > **Data Views**.

1. In the `Data Views` pane, click **Add Data View** and enter a name and description for the data view.

1. Next to **Data View Shape**, select **Standard** or **Narrow** to enter the general shape of the data display. **Standard** for a typical wide table or **Narrow** to pivot your data into a Field, Value pair format. 

1. In the center pane, update the **Query Id** field to a new value or accept the default of *Query1*.

1. For **Query Type**, select **Streams** or **Assets** to indicate which objects to search for this query.

   **Note**: Assets are available for use through specific licensing only. If you are interested in using Assets, contact your account team for more details.

1. For the **Query Value** search field, type a portion of the name of any known stream or asset preceded or followed by the * wildcard symbol, and then click the `Search` button.

   **Note**: If you have created a metadata rule in the same namespace, you can enter a selected metadata key instead of a stream or asset name in the `Search` field to select a more specific set of streams or assets.

1. Select any stream or asset in the query results to display the individual data fields to the pane on the right.

1. **Optional:** Click **+ Add Query** to add additional data fields to the query.

1. Click **Save** to accept the query results as the basis of the data view.

   The `Add Data Fields` pane displays.
   
1. In the `Add Data Fields` pane, select each data field or **Select All** data fields to use as an identifying field. **Show Included Fields** highlights identifying fields already included in the data field.

1. **Optional:** Click **Next** to edit data field label. Enter `{` to display tokens to use as a data field label. 

1. Click **Apply** to accept the selected data fields.

   The `Filter Fields...` and `Generate Preview` panes display.

1. In the `Filter Fields...` pane, the **Index Field** and **Grouping Fields** sections are set by default. In the queries section, select each data field to use as an identifying field.

1. In the `Generate Preview` pane, click the **Auto Refresh** toggle button to enable or disable auto refresh. With auto refresh enabled, changes to any of the streams included in the data view is immediately reflected in the data view.

1. Click the **Generate preview** button to generate a preview of the data view with the selected settings.

1. Click the **Interpolated/Stored** dropdown list and select **Interpolated** or **Stored** for the data view.

1. Click the date and time display to set the **Start Index** and **End Index** to enter the time period of the data to include in the data view. For interpolated data views, enter a `Time Interval`.

1. Click **Apply** to accept the index configuration changes.

1. Click **Save** to create the data view and continue working, or click **Save and Close** to create and exit.

## Related links

To define a data view using the OCS API, see [Define a data view](xref:DataViewsQuickStartDefine).
