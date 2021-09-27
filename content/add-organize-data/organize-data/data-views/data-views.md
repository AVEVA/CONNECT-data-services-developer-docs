---
uid: Dataviews1
---

# Create a data view

Data views are subsets of data from one or more streams. You create a data view by defining the target namespace, and then specifying the source stream or streams, selected data fields, time period, and interpolation interval. 

## Procedure

1. In the left pane, select **Analytics** > **Data Views**.

1. In the `Data Views` pane, click **Add Data View** and enter the data view name and description.

1. From **Data View Shape**, select **Standard** or **Narrow** to enter the general shape of the data display.

1. In the `Query Id` field in the center pane, update the field to a new value or accept the default of  *Query1*.

1. In the `Query Type` section, select **Streams** or **Assets** to indicate which objects you want this query to search.

   **Note**: Assets are available for use through specific licensing only. If you are interested in using Assets, contact your account team for more details.

1. In the `Search` field of the `Query Value` section, type a portion of the name of any known stream or asset preceded or followed by the * wildcard symbol, and then click the `Search` button.

    The query results populate and the `Index Configuration` pane displays.
    

   **Note**: If you have created a metadata rule in the same namespace, you can enter a selected metadata key instead of a stream name in the `Search` field to select a more specific set of streams.

1. Select any stream or asset in the query results to display the individual data fields of the stream in the `Data Item Details` pane.

1. Click the **Add** button to add additional data fields to the query.

1. Click **Save** to accept the query results as the basis of the new data view.<br>The `Field filter` pane displays.

1. The **Index field** and **Grouping fields** selections are set by default. In the **Identifying field** section of the `Field filter` pane, select each data field to use as an identifying field.

1. In the `Generate Preview` pane, click the **Auto Refresh** toggle button to enable or disable auto refresh. With auto refresh enabled, changes to any of the streams included in the data view is immediately reflected in the data view.

1. **Optional:** Click the **Generate preview** button to generate a preview of the data view with the selected settings.


1. Click the **Interpolated/Stored** dropdown list and select **Interpolated** or **Stored** for the data view.

1. Click the date and time display to set the **Start Index** and **End Index** to enter the time period of the data to include in the data view. For interpolated data views, enter a `Time Interval`.

1. Click **Apply** to accept the index configuration changes.


1. Click **Save** to create the data view and continue working, or click **Save and Close** to create and exit.

## Related links

To define a data view using the OCS API, see [Define a data view](xref:DataViewsQuickStartDefine).
