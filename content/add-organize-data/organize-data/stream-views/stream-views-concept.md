---
uid: ccStreamviews
---

# Stream views

A stream view is a logical overlay that enables you to customize your view of streaming data in a way that is most useful to you. While you cannot change the properties of types, stream views enable you to create a view of a selected stream that appears as if you had changed the type on which it is based. You create a stream view by choosing a source and target type, and then creating a set of mappings between the properties of the two types.

A stream view serves as a mapping between the true underlying type and the type in the stream view, enabling you to in effect remove, rename, or add properties on your original stream data. 
Using a stream view on data retrieval affects only the data retrieved, and does not alter the original source data. 

For example, a process engineer and a maintenance technician might want to see different data that exists in the same stream. With stream views you can change the appearance of the data stream to meet the needs of both users without changing the original data. In addition, stream views can perform other functions, such as converting units of measure and changing names so the terminology that is displayed is more appropriate for a particular audience.

OCS provides a graphical interface for setting up stream views, or you can use REST APIs to define stream views programmatically. If you are using the .NET framework, OSIsoft also offers client libraries to help you create and use stream views.
For information about setting up a stream view, see [Get started with stream views](xref:gsStreamviews).
For more information about types, see [Types](xref:sdsTypes).

**NOTE:** In rare cases, you might want to use a stream view to permanently change a stream's type. For more information, see [Streams](https://ocs-docs.osisoft.com/Content_Portal/Documentation/SequentialDataStore/SDS_Streams.html#update-stream-type).

### <a name="streamviews-pi-server"></a>PI Server counterpart

While there is no direct counterpart for stream views in PI Server, the closest analog is the PI Point Data Reference in PI AF. Like stream views, PI Point Data References allow you to give a friendly name and unit of measure on top of an existing PI Point, effectively viewing it in a different way. PI Point Data References do not alter the underlying PI Point in any way, just as stream views do not change the source stream or type in the Sequential Data Store.

### <a name="streamviews-bestpractices"></a>Stream views best practices

OSIsoft recommends the following best practices when working with stream views.

1. Stream views can be useful when you are using PI to OCS. PI to OCS creates streams with many additional flags, for example `IsQuestionable`, `IsSubstituted`, and `IsAnnotated`. 
You can use stream views to limit these properties or to give them a more meaningful name.

1. When you use a stream view to map to another type, use caution when not all properties in the target type are able to be mapped. Properties that are not mapped will be returned with their default value in the target type. For example, if the target type contains a double property that is not mapped, data transformation will give that property the value of `0`.

1. Stream views are the only way to change a stream's underlying type, as described in [Streams](https://ocs-docs.osisoft.com/Content_Portal/Documentation/SequentialDataStore/SDS_Streams.html#update-stream-type). CAUTION: Unmapped source properties will be lost after the update. Unmapped target properties will be set to their default value for all existing events.
