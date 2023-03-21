---
uid: gs-egress
---

# Step 6: Egress data

You can egress data from AVEVA Data Hub for use in other applications.

## Data Views

Data views allow you to access subsets of data items from AVEVA Data Hub in data-driven applications, where the items can be used for data science enablement. With data views, you can prepare your raw AVEVA Data Hub data for third-party applications like Microsoft Power BI, where it can be used for analytics, machine learning, and so on. Users can programmatically retrieve data view content using the AVEVA Data Hub API. Data views deliver shaped data that is ready for consumption because it is normalized, aligned, and contextualized.

1. [Create and configure data view](https://docs.aveva.com/bundle/data-hub/page/analytics/data-views/data-views-create-and-configure.html)

    First, you must create and configure a data view. The AVEVA Data Hub resources included in the data view are based on the result of one or more queries, which you must configure. Streams, assets, and other AVEVA Data Hub resources that can be included in a data view are known as _data items_. Streams shared to communities can also be included. Properties from data objects and information about the data items (such as Id and Metadata) can be included in the data view as _fields_.

## API Console

The API Console provides a graphical interface for using the REST API. When using the API Console, you select a GET, POST, PUT, DELETE, or PATCH action, select the objects for the action, and execute.

- [API console (aveva.com)](https://docs.aveva.com/bundle/data-hub/page/api-reference/api-console.html)
- [AVEVA Data Hub API reference](https://docs.aveva.com/bundle/data-hub/page/api-reference/ocs-api-reference.html)

## Microsoft Power BI

The AVEVA Data Hub Power BI Connector retrieves data views from AVEVA Data Hub and makes them available in Microsoft Power BI for advanced data visualization and analysis. You can also use Microsoft Power BI to edit the query generated from the connector to modify the dates, edit the interpolation interval, and enable an incremental refresh of data.

1. [Power BI Connector setup (aveva.com)](https://docs.aveva.com/bundle/data-hub/page/visualize-data/power-bi-connector/set-up-power-bi.html)
2. [Retrieve Data Views with Power BI Connector (aveva.com)](https://docs.aveva.com/bundle/data-hub/page/visualize-data/power-bi-connector/retrieve-data-views.html)