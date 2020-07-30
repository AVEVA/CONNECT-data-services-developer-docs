---
uid: GettingStartedWithTrendData
---

Getting Started with Trend Data
=================================================

Trace data can be displayed in a trend and used to monitor assets, anticipate problems, and proactively perform preventative maintenance.

The following procedure describes how to display traces in your trend and glean useful information from your data.

Procedure
---------

1.  Log in to OSIsoft Cloud Services.

2.  Click the navigation icon ![](images\icon_navigation_bigger.png) (upper left corner) and click **Trend** (under Visualization). 
    
3. In the Add Traces blade, click the **+** sign to add the trace to the trend. 

   Tip: 

   - Use the Search box to find the OCS streams and properties you are interested in.

   - After you have finished adding the traces, click the **x** in the Add Traces blade to hide the blade and maximize the available area to display your trend.


    ![Search blade](images\Search_blade_75.png)

4. Click on the ![Trend views icon](images\Trend_mode_icon.png)icon to choose one of the three views:

   | Trend View                               | Description                                     |
   | ---------------------------------------- | ----------------------------------------------- |
   | ![](images\Single mode.png)              | Each trace is displayed in its own trend.       |
   | ![](images\Multiple mode.png)            | All measurements are plotted on the same scale. |
   | ![Stacked mode](images\Stacked mode.png) | All measurements are plotted on its own scale.  |

5. In the time range picker, click **Step backward** or **Step forward** to move the time range of the data displayed in the trend.

   The trace will move in time increments displayed in the time range picker. If the trend displays the last 8 hours, **Step backward** shows the previous 8-hour period. If it displays the last 30 days, **Step forward** shows the next 30-day period. Click the triangle to select another time range or specify a custom range.

   ![Step back and step forward](images\Step_back_forward.png)

   The Legend table displays the Trace view. It shows the legend for each trace, the last value, minimum, maximum, and average values in the displayed time range.

   ![Legend Table](images\Legend_Table_Med.png)

6. Click on a trace to select it for further analysis

   The selected trace is highlighted, and two cursors automatically mark the minimum and maximum values for the displayed time range. These *easy cursors* remain as long as the trace is highlighted.

   ![Maximum and minimum cursors](images\Max_min__cursors.png)

   Click the plus sign (+) above the trace to lock the cursors in place. The **+** turns into an **x**.  To unlock the cursor, click the **x**.

   Note: When two cursors are locked, the Legend table displays summary calculations for the values between the two cursors, known as the Cursor view.

   ![Cursor_view](images\Cursor_view.png)

7. Click the link icon ![Copy link icon](images\copy_url_link.png) in the menu bar to copy the URL of the workspace.

   This link, shared with colleagues, gives them the same view of the trend that they can then use to troubleshoot problems.

