_Data views_ allow you to access subsets of data from OSIsoft Cloud Services (OCS) sources (such as streams and assets) in data-driven applications, where the data can be used for data science enablement. With data views, you can bridge your raw OCS data to third-party applications like Microsoft Power BI, where it can be used for analytics, machine learning, and so on. With data views, users can programmatically access data view content using an API for the purposes of advanced analytics. Data views deliver shaped data that is ready for consumption because it is normalized, aligned, and interpolated.

A data view is a declarative query and shape for OCS data. It includes the following components, which are further describes in the topics that follow:

- **Index field**: Determines the primary index type and label of the index. The index must be a timestamp and displays in the first column of the data view.

- **Query**: Determines what data items are available for a data view. Queries can include streams or assets. A data view can have multiple queries.

- **Data field set**: Collections of fields originating from the same query.

- **Data view shape**: Determines if the data should be returned in the standard grouped row format or a narrow view, which is a pivot of the standard table.

Data views also include other components such as grouping instructions and default data range and interval.

Understanding how the data view resolves into content is important for both the user designing the data view and the user working with that view for data science. Data views provide extensive visibility into the data included in the view. The concept of "resolving" a data view is when the data view's queries and logic are executed to determine the data view's exact schema and content.

The collection(s) of OCS resources that a data view is based on is the result of one or more queries. Streams, assets, and other OCS resources are collectively known as _data items_. Properties from data items can be included in the data view as _fields_, as well as information about the data items (such as Id and Metadata).

There are two primary means of controlling how the data items are organized: 

- One or more field may be designated to *group* the data view, effectively grouping or partitioning the data items on some value.

- Within a set of fields, one field may be designated to *identify* or align the items.

Data view data is available in several formats, including JSON and CSV, with a user-specified range and granularity. Data is obtained by querying the REST API.