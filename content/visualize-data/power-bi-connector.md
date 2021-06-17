---
uid: PowerBI
---

# The OSIsoft Cloud Services Power BI Connector

The OCS Power BI Connector retrieves data views from OSIsoft Cloud Services (OCS) and makes them available in Microsoft Power BI for advanced data visualization and analysis.

To use the OSIsoft Cloud Services data connector, complete the following steps:

1. From the Sales Force portal, download the OCSPowerBIConnector.exe file.
2. To run the Setup wizard for the OSIsoft Cloud Services Power BI Connector, execute the `OCSPowerBIConnector.exe` file.
3. In Microsoft Power BI, in the entry field of the **Get Data** window, type *OSI*. The **OSIsoft Cloud Services Data Views** displays in the **All** pane.
4. In the **OCS Power BI Data Connector** dialog, select the OCS tenant whose data views you want to access, and then click **OK**. The OSIsoft Cloud Services sign-in dialog displays if you have not already signed into OCS.
5. If you have not already signed into OCS, click **Sign in as different user** and complete the OCS user authentication process. The **OSIsoft Cloud Services Data Views** sign-in dialog displays again after you have completed the OCS user authentication process.
6. In the **OSIsoft Cloud Services Data Views** sign-in dialog, click **Connect**. The **Navigator** pane displays.
7. From the **Navigator** pane, select one or more data views.
8. For each of the selected data views, specify a Start Index, End Index, and Interval. To apply the values you have specified for the selected data views, click **Apply**.

   **Note**: If one of the selected data views has default values defined for Start Index, End Index, and Interval, enter new values or accept **Apply** to accept the defaults.

10.	To load the selected data view data, click **Load** at the bottom of the **Navigator** pane.
11.	To select the visualizations you want to create, use the Microsoft Power BI **Visualizations** pane.
