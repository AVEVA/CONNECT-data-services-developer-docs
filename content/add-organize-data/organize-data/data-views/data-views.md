---
uid: CreateDataView
---

# Create and configure a data view

You create and configure a data view by defining the target namespace, and then specifying the source stream or asset, data fields, time period, and interpolation interval.

To create a data view:

## Add data fields to display as identifying fields for the data view

1. In the `Add Data Fields` window, select each data field or **Select All** data fields to use as an identifying field. **Show Included Fields** highlights identifying fields already included in the data field.

1. (Optional) To edit data field label, select **Next** and enter `{` to display tokens to use as a data field label.

1. Select **Apply** to accept the selected data fields.

   The `Filter Fields` and `Generate Preview` panes display.

## Edit the identifying fields, time period, and interpolation interval for the data view

1. In the `Filter Fields` pane, the **Index Field** and **Grouping Fields** sections are set by default. In the queries section, each data field previously selected in the `Add Data Fields` pane is listed as an identifying field. To add, edit, or remove identifying fields, select **Add**, **Edit**, or **Remove**.

1. In the `Generate Preview` pane, turn the **Auto Refresh** toggle switch on to enable auto refresh. With auto refresh enabled, changes to any of the streams included in the data view are immediately reflected in the data view.

1. Select the date and time display to set the **Start Index** and **End Index** to enter the time period of the data to include in the data view. For interpolated data views, enter a `Time Interval`.

1. Select **Apply** to accept the index configuration changes.

1. Select the **Interpolated/Stored** dropdown list and select **Interpolated** or **Stored** for the data view.

## Generate a preview and save the data view

1. To generate a preview of the data view with the selected settings, select **Generate preview**.

1. Select **Save** to create the data view and to continue editing, or select **Save and Close** to create the data view and exit.

To define a data view using the OCS API, see [Define a data view](xref:DataViewsQuickStartDefine).
