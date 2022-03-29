---
uid: ccStreams
---
# Streams

Sequential Data Store (SDS) stream data are values or events of the same SDS type. SDS stores stream data and indexes it by one or more properties defined in the stream's SDS type.

The SDS stream is the container that holds the data. When you create a stream, you add it to a specific namespace. Then you define an SDS type for that stream that determines the values and events in the stream, their data type, and the properties used to index the data. Once you create a stream, you cannot change its SDS type.

The SDS stream container uses metadata and tags to define information about the stream container itself. Metadata are key-value pairs that add context to the data, for example, the metadata key, `Manufacturer`, and a metadata value, `Caterpiller`. Tags are string values that represent stream attributes, for example, region. Organizing data using metadata and tags makes it much easier to retrieve data streams.

## Streams best practices

The following best practices are recommended when creating streams:

- Ensure that the default stream permissions are configured before you begin creating streams. While you can later do a bulk update of stream permissions, it is easier to configure the default permissions before the streams are created. Permissions that vary from the default are configured on the individual streams.

- Use a meaningful pattern when naming streams. For example, a naming pattern might be "*Company_name*.{*Region*}.{*Site*}.{*Equipment*}". This makes it possible for tools, such as metadata rules, to use this naming schema to find relevant data. Metadata like this can also be stored as key-value pairs on the stream, but a well-defined naming pattern allows metadata to be generated automatically. 

- Use the stream description field, metadata, and tags to capture any other relevant information about the stream. This information is useful to search for specific streams in the system, especially as systems become large. If possible, use consistent patterns in description, metadata, and tags.

   - Use metadata for information that follows a specific or consistent pattern, such as the location, manufacturer, and site. 
   
   - Use tags for simple information about the stream that does not adhere to any particular pattern.
   
   - Use the description field for longer descriptions of the stream and what it represents.
## PI Server counterpart

An SDS stream is comparable to a PI point in the PI Data Archive. For example, a `float32` PI point might be sent to OSIsoft Cloud Services as an SDS stream with a type that contains a `timestamp` index and `float32` value. If you use PI to OCS to import data into SDS, each PI point in the PI Data Archive is created in SDS as an individual stream and the data itself is added as values in the stream.

