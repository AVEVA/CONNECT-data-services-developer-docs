---
uid: data-views-retrieve
---

# Retrieve a data view

[!include[data-views-retrieve](../../_includes/data-views-retrieve.md)]

## Data retrieval options

To retrieve a data view, you can either use the OSIsoft Microsoft Power BI Plugin, or you can develop your own plugin using an example GitHub project as a starting point.

### Microsoft Power BI

You can retrieve a data view using Microsoft Power BI. Retrieving a data view in Microsoft Power BI requires installation of OCS Power BI Connector. You can download the Connector by clicking on the banner listed at the top of the **Data Views** page. If you dismiss the banner, it will return upon your next user session.

For more information installing the connector and retrieving a data view, see <xref:PowerBI>.

### Develop your own connector

Alternatively, you can develop your own connector for third-party software. AVEVA offers sample projects on GitHub for the following technologies:

- [Jupyter](https://github.com/osisoft/sample-adh-data_views_jupyter-python)
- [Python](https://github.com/osisoft/sample-adh-data_views-python)
- [R](https://github.com/osisoft/sample-adh-data_views_r-r)
- [.NET](https://github.com/osisoft/sample-adh-data_views-dotnet)
- [Java](https://github.com/osisoft/sample-adh-data_views-java)

## Workflow: Data view retrieval

To retrieve a data view in a third-party application, follow these steps:

### Step 1. Create Client-Credentials Client

To retrieve a data view from OSIsoft Cloud Services (OCS), you must authenticate using a valid Client Id and Client secret. You can obtain an Id and secret by creating a set of client-credentials. While creating the client-credentials, accept the default expiry of 3600 seconds. When you are presented with the client secret, keep it secure, as there is no way to see the secret again. If you lose it, create a new set of client-credentials.

For more information on creating client-credential clients, see <xref:gpClientCredentialsClient>.

### Step 2. Develop your own connector 

Use one of the starter projects listed in [Develop your own connector](#develop-your-own-connector) or develop your own. Pass your client-credentials to the connector for authentication purposes. 

### Step 3. Use the API Console to request your data view 

[!include[api-console](_includes/api-console.md)]

## Developer documentation

For more information on interacting with a data view using the API console, see the [Developer Guide](xref:DataViewsOverview).
