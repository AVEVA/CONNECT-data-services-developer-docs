_Data views_ allow you to access subsets of data from OSIsoft Cloud Services (OCS) sources (such as streams and assets) in data-driven applications, where the data can be used for data science enablement. With data views, you can bridge your raw OCS data to third-party applications like Microsoft Power BI, where it can be used for analytics, machine learning, and so on. With data views, users can programmatically access data view content using an API for the purposes of advanced analytics. Data views deliver shaped data that is ready for consumption because it is normalized, aligned, and interpolated.

A data view is a declarative query and shape for OCS data. It includes the following components:

- **Index field** 

	Specifies the primary index type and label of the index. The index must be a timestamp and displays in the first column of the data view.

- **Query**

	Determines what data items are available for a data view. Queries can include streams or assets. A data view can have multiple queries.

- **Data field set** 

	Collections of fields originating from the same query.

- **Data view shape** 

	Determines if the data should be returned in the standard grouped row format or a narrow view, which is a pivot of the standard table.

Data views also include other components such as grouping instructions and default data range and interval.