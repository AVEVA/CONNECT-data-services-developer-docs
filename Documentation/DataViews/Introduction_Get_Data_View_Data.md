---
uid: DataViewsIntroductionGetData
---

# Introduction - Get Data View Data

Getting data from a data view is straightforward. If you want to understand more about the source behind each data field, that information is available too.

This is an introduction to the recommended workflow for getting data. The [Quick Start - Get Data View Data](xref:DataViewsQuickStartGetData) shows these concepts in action. For detailed information, see [Getting Data](xref:DataViewsGettingData) and [Data API](xref:DataViewsDataAPI).


## Step 1. Request the first page
Specify the following parameters or use the default:
- Index range (start index and end index) and granularity of data to be retrieved. If you do not specify one or more of these parameters, the data view's corresponding default values will be used if defined.
- Desired response format. The default is object-style json. Other options include csv and table-style json. The latter two are available with or without a header row.
- Page size

## Steps 2+. Request the remaining pages, if any
If data spans into additional page(s), the current page response will include an HTTP header linking to the next page.
- If the current page of data includes a NextPage hyperlink, keep following the hyperlinks to retrieve the full requested dataset page by page.
- In rare circumstances it may be necessary to restart the paging operation from the first page. In this case, follow the FirstPage hyperlink.

## [Optional] Investigate the source of the data
- For precise information about the source of each field's data, see the data view's resolved field mappings.
