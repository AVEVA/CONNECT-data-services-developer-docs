---
uid: PowerBI
---

# OSIsoft Cloud Services Power BI Connector

The OCS Power BI Connector retrieves data views from OSIsoft Cloud Services (OCS) and makes them available in Microsoft Power BI for advanced data visualization and analysis.

To use the OSIsoft Cloud Services Power BI Connector, complete the following steps:

1. From the [myOSIsoft portal](https://customers.osisoft.com/s/products), download the OCSPowerBIConnector.exe file.
2. To run the Setup wizard for the OSIsoft Cloud Services Power BI Connector, double click the `OCSPowerBIConnector.exe` file.
3. In Microsoft Power BI, in the entry field of the **Get Data** window, type *OSI*. The **OSIsoft Cloud Services Data Views** connector file displays in the **All** pane.

   ![Get Data](images/get-data.png width="50%" height="50%")

4. Click the **OSIsoft Cloud Services Data Views** connector file, and then click **Connect**.
5. Click **Continue** in the **Connecting to a third-party service** warning.
6. In the **OSIsoft Cloud Services Data Views** window, enter the OCS tenant and namespace for the data views you want to access, and then click **OK**. The OSIsoft Cloud Services sign-in window displays if you have not already signed into OCS.
7. If you have not already signed into OCS, click **Sign in as different user** and complete the OCS user authentication process. The **OSIsoft Cloud Services Data Views** sign-in window displays again after you have signed in to OCS.
8. In the **OSIsoft Cloud Services Data Views** sign-in window, click **Connect**. The **Navigator** pane displays.
9. In the **Navigator** pane, click the box for each data view you want to work with in Power BI.

![Select Data Views](images/click-data-view-box.png)

10. For each of the selected data views, specify a Start Index, End Index, and Interval. To apply the values you have specified for the selected data views, click **Apply**.

    **Note**: If one of the selected data views has default values defined for Start Index, End Index, and Interval, enter new values or click **Apply** to accept the defaults.

11. To load the selected data view data, click **Load** at the bottom of the **Navigator** pane.
12. To select the visualizations you want to create, use the Microsoft Power BI **Visualizations** pane.

    **Note**: Click the **Transform data** button in the Power BI menu to review and edit data types for a selected data view.
