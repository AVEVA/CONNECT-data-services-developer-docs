---
uid: data-views-retrieve
---

# Retrieve a data view

[!include[data-views-retrieve](../../_includes/data-views-retrieve.md)]

## Data retrieval options

To retrieve a data view, you can either use the OSIsoft Microsoft Power BI Plugin, or you can develop your own plugin using an example GitHub project as a starting point.

### Microsoft Power BI

You can retrieve a data view using Microsoft Power BI. Retrieving a data view in Microsoft Power BI requires installation of OCS Power BI Connector. For more information installing the connector and retrieving a data view, see <xref:PowerBI>.

### Develop your own connector

Alternatively, you can develop your own connector for third-party software. AVEVA offers sample projects on GitHub for the following technologies:

- [Jupyter](https://github.com/osisoft/sample-adh-data_views_jupyter-python)
- [Python](https://github.com/osisoft/sample-adh-data_views-python)
- [R](https://github.com/osisoft/sample-adh-data_views_r-r)
- [.NET](https://github.com/osisoft/sample-adh-data_views-dotnet)
- [Java](https://github.com/osisoft/sample-adh-data_views-java)

## Client-Credentials

To retrieve a data view from OSIsoft Cloud Services (OCS), you must authenticate using a valid Client Id and Client secret. You can obtain an Id and secret by creating a set of client-credentials. For more information, see <xref:gpClientCredentialsClient>.

## API Console

[!include[api-console](_includes/api-console.md)]

## Developer documentation

For more information on interacting with a data view using the API console, see the [Developer Guide](xref:DataViewsOverview).
