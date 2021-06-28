---
uid: ccStreamviews
---

# Stream views

A stream view is a logical overlay that enables you to customize your view of streaming data in a way that is most useful to you. While you cannot change the properties of types, stream views enable you to create a view of a selected stream that appears as if you had changed the type on which it is based. You create a stream view by choosing a source and target type, and then creating a set of mappings between the properties of the two types.

A stream view maps the underlying source type to the target type in the stream view, enabling you to in effect remove, rename, or add properties without altering the original stream type. 
Using a stream view on data retrieval affects only the data retrieved, and does not alter the original source data. 

For example, a process engineer and a maintenance technician might want to see different data that exists in the same stream. With stream views you can change the appearance of the data stream to meet the needs of both users without changing the original data. In addition, stream views can perform other functions, such as converting units of measure and changing names so the terminology that is displayed is more appropriate for a particular audience.

OCS provides a graphical interface for setting up stream views, or you can use REST APIs to define stream views programmatically. If you are using the .NET framework, OSIsoft also offers client libraries to help you create and use stream views.
For information about setting up a stream view, see [Get started with stream views](xref:gsStreamviews).
For more information about types, see [Types](xref:sdsTypes).

**NOTE:** In rare cases, you might want to use a stream view to permanently change a stream's type. For more information, see [Streams](https://ocs-docs.osisoft.com/Content_Portal/Documentation/SequentialDataStore/SDS_Streams.html#update-stream-type).

### <a name="streamviews-pi-server"></a>PI Server counterpart

While there is no direct counterpart for stream views in PI Server, the closest analog is the PI point data reference in PI AF. Like stream views, PI point data references allow you to give a friendly name and unit of measure on top of an existing PI point, effectively viewing it in a different way. PI point data references do not alter the underlying PI point, just as stream views do not change the source stream or type in the Sequential Data Store.

### <a name="streamviews-bestpractices"></a>Stream views best practices

OSIsoft recommends the following best practices when working with stream views:

1. Stream views can be useful when you are using PI to OCS. PI to OCS creates streams with many additional flags, for example `IsQuestionable`, `IsSubstituted`, and `IsAnnotated`. 
You can use stream views to limit these properties or to give them a more meaningful name.

1. When you use a stream view to map to another type, use caution when not all properties in the target type can be mapped from the source. Properties that are not mapped return their default value in the target type. For example, if the target type contains a property of data type double that is not mapped, data transformation gives that property a value of `0`.
For example, assume you have a source type with two properties, Timestamp and Pressure, and you use a stream view to map to a type with the properties Timestamp, Pressure, and Temperature. If Temperature is of data type double, a value of 0 (zero) is always returned for it, because it cannot be mapped from the source type. 

1. Stream views are the only way to change a stream's underlying type, as described in [Streams](https://ocs-docs.osisoft.com/Content_Portal/Documentation/SequentialDataStore/SDS_Streams.html#update-stream-type). Use caution if you do permamnetly change a stream's underlying type, because any source properties that cannot be mapped are removed from the stream data. Unmapped target properties are set to their default value for all existing events. For example, if you have a mapping where the source type has the properties Timestamp, Pressure, and Temperature, and you use a stream view to map to a type with the properties Timestamp, Pressure, and Depth, you might only be able to map Timestamp and Pressure. In this case, the source data for the Temperature field would be lost, and the existing events would be given a value of 0 for the new Depth property, which did not exist on the stream before.
