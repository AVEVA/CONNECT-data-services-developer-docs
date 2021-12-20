---
uid: GettingStartedWithTrendData
---

# Get started with trend data

Use trace data in a trend session to monitor assets, anticipate problems, and proactively perform preventative maintenance.

Follow this procedure to create a trending session:

1. In the left pane, select **Visualization** > **Trend**.
   
1. In the `Trend` pane, add asset data or stream data.

    1. In the `Add Traces` pane, select the **Assets** or **Streams** tab.

    1. From the **Namespace** dropdown list (callout **1** in the image below), select a namespace or community that contains data that you want to visualize (callout **2**).

    **Note:** Communities are only available for selection from the the **Streams** tab because they are used to share stream data.

    ![Select namespace/community](images/select-namespace-community.png)

    1. Select the **Add** ![add](../_icons/plus-thick-alt.svg) icon to add a trace to the trend session.

    **Tip:** Specify the asset name, stream name, or description in the **Search** box to find the trace you are interested in.
    
    ![Add traces](images/add-traces.png)

    1. (Optional) Repeat these substeps to add more traces from different namespaces and communities to the trend session.  

    **Tip:** After you have finished adding traces, select the **Close** ![close](../_icons/window-close.svg) icon in the `Add Traces` pane to hide the pane and maximize the available area to display your trend session.
        
1. From the **Change Y-axis Mode** ![Trend views menu](images/trend-views-icon.png) menu, select a view:

    | Trend View | Icon | Description |
    |--|--|--|
    | Single mode |  ![single mode](../_icons/chart-line.svg) | Each trace is displayed in its own trend. |
    | Multiple mode | ![multiple mode](../_icons/chart-multiple.svg) | All measurements are plotted on the same scale. |
    | Stacked mode | ![stacked mode](../_icons/layers.svg) | All measurements are plotted on its own scale. |

1. From the **Time picker**, select the time range to view. 

    - Select the **Quick Ranges** tab to choose a predefined time range.
    
    - Select the **Custom Range** tab to choose your own time range.
    
    ![Time picker](images/Time-picker.png)
    
1. Select **Step backward** ![step backward](../_icons/skip-backward.svg) or **Step forward** ![step forward](../_icons/skip-forward.svg) to move the time range of the data displayed in the trend session.

   The trace will move in time increments displayed in the time range picker. For example, if the trend session displays the last 8 hours, **Step backward** ![step backward](../_icons/skip-backward.svg) shows the previous 8-hour period. If it displays the last 30 days, **Step forward** ![step forward](../_icons/skip-forward.svg) shows the next 30-day period. Select the triangle to select another time range or specify a custom range.

   The [legend table](xref:LegendTableReference) displays the [Trend view](xref:LegendTableReference#trend-view) ![trend](../_icons/chart-line.svg). It shows the legend for each trace, the last value, minimum, maximum, and average values in the displayed time range.

1. From the legend table, select a trace to select it for further analysis.

    The selected trace is highlighted and two cursors automatically mark the minimum and maximum values for the displayed time range. These cursors, called *easy cursors,* remain as long as the trace is highlighted.

    ![Maximum and minimum cursors](images/Max_min_cursors.png)

1. Select the **Add** ![add](../_icons/plus-thick.svg) icon above the trace to lock the cursors in place.
    
    The **Add** ![add](../_icons/plus-thick.svg) icon turns into a **Close** ![close](../_icons/window-close.svg) icon. To unlock the cursor, select the **Close** ![close](../_icons/window-close.svg) icon.

    **Note:** When two cursors are locked, the [legend table](xref:LegendTableReference) displays summary calculations for the values between the two cursors, known as the [Cursor view](xref:LegendTableReference#cursor-view) ![cursor](../_icons/map-marker.svg).

1. Select the **Share** ![share](../_icons/share.svg) icon in the menu bar to copy the URL of the trend session. 

    You can share this URL with colleagues to give them the same view of the trend session that they can use to troubleshoot problems.
