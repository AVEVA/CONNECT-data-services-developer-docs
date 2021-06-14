---
uid: PowerBI
---

# The OSIsoft Cloud Services Power BI Connector

The OCS Power BI Connector retrieves data views from OSIsoft Cloud Services (OCS) and makes them available in Microsoft Power BI for advanced data visualizations and analysis.

To utilize the OSIsoft Cloud Services data connector, complete the following:

1.	From the Sales Force portal, download the OCSPowerBIConnector.exe file.
2.	Execute the OCSPowerBIConnector.exe file to run the Setup wizard for the OSIsoft Cloud Services Power BI Connector.
3.	In Microsoft Power BI, type OSI in the entry field of the **Get Data** window. The **OSIsoft Cloud Services Data Views** displays in the **All** pane.
4.	In the **OCS Power BI Data Connector** dialog, select the OCS tenant (currently tenant Id only) and namespace whose data views you want to access, and click **OK**. The OSIsoft Cloud Services sign-in dialog displays if you have not already signed into OCS.
5.	If you have not already signed into OCS, click **Sign in as different user** and complete the OCS user authentication process. The **OSIsoft Cloud Services Data Views** sign-in dialog displays again after you have completed the OCS user authentication process.
6.	Click **Connect** in the **OSIsoft Cloud Services Data Views** sign-in dialog. The **Navigator** pane displays.
7.	Select one or more data views from the **Navigator** pane.
8.	Specify a Start Index, End Index, and Interval for each of the selected data views, or accept the default values. Click **Apply** to apply the values you have specified to the selected data views.
9.	Click **Load** at the bottom of the **Navigator** pane to load the selected data view data.
10.	Use the Microsoft Power BI **Visualizations** pane to select the visualizations you want to create.
