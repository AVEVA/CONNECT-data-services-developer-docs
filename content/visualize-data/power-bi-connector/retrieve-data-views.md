---
uid: RetrieveDataViews
---

# Retrieve Data Views with Power BI Connector

## Authentication prerequisites

While retrieving a data view from AVEVA Data Hub, Power BI Connector prompts you to authenticate with Microsoft Power BI. You have two options for authentication:

- (**Recommended**) Client-credential client authentication:

    Use an AVEVA Data Hub client-credential client Id and client secret to authenticate with Microsoft Power BI. This authentication option is preferred over OAuth because it allows Microsoft Power BI to remain securely connected with AVEVA Data Hub without prompting you to reauthenticate every seven days.

    If you choose this option, you must create and configure a client-credential client for use during authentication while completing [To retrieve Data Views](#to-retrieve-data-views). For instructions on creating these credentials, see <xref:gpClientCredentialsClient>. While creating the credentials, record the **Client Id** and **Client Secret** to enter while retrieving a data view.

- OAuth authentication

    Use the same user account that you use to sign into AVEVA Data Hub to authenticate the connection between AVEVA Data Hub and  Microsoft Power BI. If you use this authentication option, Power BI Connector prompts you to reauthenticate the connection every seven days.

    If you choose this authentication option, you can begin [To retrieve Data Views](#to-retrieve-data-views) without completing any prerequisites.

## To retrieve Data Views

Use AVEVA Power BI Connector to retrieve AVEVA Data Hub data views for use in Microsoft Power BI.

1. In Microsoft Power BI Desktop, in the entry field of the `Get Data` window, type `AVEVA`.<br>The AVEVA Data Hub Data Views connector file displays in the `All` pane.

   ![Get Data](../../analytics/data-views/_images/get-data.png)

1. Select the `AVEVA Data Hub Data Views` connector file, and then select **Connect**.

1. Select **Continue** in the `Connecting to a third-party service` warning.

1. In the `AVEVA Data Hub Data Views` window, enter the tenant and namespace for the data views you want to access, and then select **OK**.

   The AVEVA Data Hub sign-in window displays if you have not already signed in.

   - If you have not already signed in, select **Sign in as different user** and complete the user authentication process.

1. In the `AVEVA Data Hub Data Views` sign-in window, select **Connect**.

1. In the `Navigator` pane, do one of the following:

   - To get data using the stored retrieval mode, select **Stored Data Views**, and then select the data view to work with in Microsoft Power BI.

   - To get data using the interpolated retrieval mode, select **Interpolated Data Views**, and then select the data view to work with in Microsoft Power BI.

   ![Select Data Views](../../analytics/data-views/_images/click-data-view-box.png)

1. For stored data views, specify a Start Index and End Index in `YYYY-MM-DDTHH:mm:ss` format for the selected data view, and select **Apply** to save the values. For interpolated data views, also specify an Interpolation Interval in `dd.hh:mm:ss` format. Repeat for each additional data view as needed.

   **Note**: If a data view has default values, enter new values and select **Apply** to accept the defaults.

   ![Specify Data View Values](../../analytics/data-views/_images/specify-values.png)

1. Select **Load** at the bottom of the `Navigator` pane to load all selected data views to Microsoft Power BI.
