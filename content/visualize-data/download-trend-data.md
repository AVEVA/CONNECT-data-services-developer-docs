---
uid: download-trend-data
---

# Download trend data

After you create a trend session that includes traces from assets, streams, or both, you can download the data depicted in the trend session as a .csv file.

1. In the left pane, select **Visualization** > **Trend**.

1. Create a trend session using the instructions available in <xref:CreateTrendSession>.

1. From the toolbar, select **Download CSV**.

1. Select the data from the trend session that you want to download. Each option is downloaded as a separate .csv file.

   - **Trend Data**: Downloads the data depicted in the [Trend pane](xref:TrendUserInterface).

   - **UOM/Summary Data** Downloads the data listed in the [Legend table](xref:TrendUserInterface).

1. Select **Download**.

The selected trend session data is downloaded as .csv files.

**Note:** When downloading trend session data, the data is not retrieved from the trend session—rather, the data is retrieved from the assets and streams. This approach allows the downloaded data be be more accurate, as the the data does not include interpolated or calculated data included in the trend session.
