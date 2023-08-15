---
uid: gs-egress
---

# Step 6: Egress data

You can egress data from AVEVA Data Hub for use in other applications.

## Data Views

Data views allow you to access subsets of data items from AVEVA Data Hub in data-driven applications, where the items can be used for data science enablement. With data views, you can prepare your raw AVEVA Data Hub data for third-party applications like Microsoft Power BI, where it can be used for analytics, machine learning, and so on. Users can programmatically retrieve data view content using the AVEVA Data Hub API. Data views deliver shaped data that is ready for consumption because it is normalized, aligned, and contextualized.

First, you must create and configure a data view. The AVEVA Data Hub resources included in the data view are based on the result of one or more queries, which you must configure. Streams, assets, and other AVEVA Data Hub resources that can be included in a data view are known as _data items_. Streams shared to communities can also be included. Properties from data objects and information about the data items (such as Id and Metadata) can be included in the data view as _fields_.

Refer to the following topic for a workflow of how to get started creating and configuring a data view.

<xref:data-views-create-and-configure>

## API Console

AVEVA Data Hub includes an API console that you can use to create and refine requests to the AVEVA Data Hub REST API. After building and refining your requests using the console GUI—including edits to the URI, query parameters, request headers, and request body—you can implement the request in your own application. For more information about the console, see <xref:apiConsole>.

For a list of service endpoints available within the API console, refer to the <xref:osisoftCloudServices>. This reference lists each service available within AVEVA Data Hub, their available endpoints, and their available parameters.

## Microsoft Power BI

The AVEVA Data Hub Power BI Connector retrieves data views from AVEVA Data Hub and makes them available in Microsoft Power BI for advanced data visualization and analysis. You can also use Microsoft Power BI to edit the query generated from the connector to modify the dates, edit the interpolation interval, and enable an incremental refresh of data.

1. <xref:SetUpPowerBI>
2. <xref:RetrieveDataViews>
