---
uid: ccAssets
---
# Assets

An asset is a container that groups information about an asset. An asset is composed of the metadata or static information about the asset, such as location or company, and properties which are references to streams in the Sequential Data Store. Assets allow users to retrieve all of the stream values associated with an asset and to provide context to this dynamic data. 

## PI Server counterpart

Assets are comparable to elements in PI AF server. Similar to elements, OCS assets include both dynamic and static information associated with the asset. The static information provides context for the dynamic data. Assets in OCS are exposed as a flat list that can be searched using metadata values. This contrasts with the elements in PI AF server which are organized in a hierarchy.

## Assets best practices

The following best practices are recommended when you create your assets:

- Use OCS assets to bring together in one place the data from multiple streams and the static data associated with a logical asset. OCS assets make it easier to visualize and contextualize the data for a given logical asset.
- While it is possible to configure the UOM from the asset,  OSIsoft recommends that the UOM be defined on either the type or stream to maintain consistency across data retrieval endpoints for the underlying data,   
- <!-- Doug said --> Defining a different UOM in the asset does not perform any type of conversion from UOMs defined on the asset type or SDS type, so if the UOM is defined in multiple places, they should always match.
- <!-- Is this what you mean? --> Specify the UOM that is defined on the stream.  If you define a different UOM on the asset than is defined in the SDS type, there is no data conversion from one UOM to the other. <!-- Does this mean that the value remains the same. For example, if the UOM was "feet" and the value was 12, if you change the UOM to "yards," it will appear as 12 yards, not 4 yards. -->
