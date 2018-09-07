---
uid: sdsSearching
---

#### Qi_Searching_topic

Searching for streams
=====================

``GetStreamsAsync`` is an overloaded method that is also used to search for and return streams (also see [Streams](xref:sdsStreams) for information about using ``GetStreamAsync`` to return streams). When you call an overloaded method, the software determines the most appropriate method to use by comparing the argument types specified in the call to the method definition.

The syntax of the client libraries method is as follows:

      _metadataService.GetStreamsAsync(string searchText, int skip, int count);


Searching for streams is also possible using the REST API and specifying the optional ``query`` parameter, as shown here:

      GET api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams?query={query}&skip={skip}&count={count}


The ``GetStreamsAsync`` overload returns streams that match specific search criteria within a given namespace. 
You use the ``searchText`` parameter to specify a search string. The ``GetStreamsAsync`` method then returns any 
stream that matches the search string in the ``name``, ``description``, or ``tag`` list. 

For example, assume that a namespace contains the following Streams:

**streamId** | **Name**  | **Description**  | **Tags**
------------ | --------- | ---------------- | -------------------------
stream1      | tempA     | The temperature  | “temperature”, “DeviceA”
             |           | from DeviceA     |          
stream2      | pressureA | The pressure     | “pressure”, “DeviceA”
             |           | from DeviceA     |
stream3      | calcA     | calculation from | “temperature”, 
             |           | DeviceA values   | “pressure”, “DeviceA”


Using the stream data above, the following table shows the results of a ``GetStreamsAsync`` call with different ``SearchText`` values:

**SearchText**     | **Streams returned**
------------------ | ----------------------------------------
``“temperature”``  | stream1 and stream3 returned.
``“calc*”``        | Only stream3 returned.
``“DeviceA*”``     | All three streams returned.
``“humidity*”``    | No streams returned.

When searching for a stream, be aware that a string of contiguous, non-whitespace characters is indexed as a solid block 
of text. For example, suppose that a stream has the name "Tank:ABC". Searching for “Tan*” would find the stream, but 
searching for “AB*” would not find it. By inserting spaces you break up the contiguous block and allow for in-string 
searching. For example, if the stream Name is "Tank ABC" instead of "Tank:ABC" then searches for “Tan*” or for “AB*” 
would both be successful.

The ``skip`` and ``count`` parameters determine which streams are returned when a large number of streams match 
the ``searchText`` criteria. 

The asterisk (*) character is a suffix-only wildcard which matches zero or more characters (see Search operators_).  

``count`` indicates the maximum number of streams returned by the ``GetStreamsAsync()`` call. The maximum value of 
the ``count`` parameter is 1000. 

``skip`` indicates the number of matched stream names to skip over before returning matching streams. You use the 
skip parameter when more streams match the search criteria than can be returned in a single call. 

For example, assume there are 175 streams that match the search criteria: “temperature*”. 
The following call returns the first 100 matches:

       _metadataService.GetStreamsAsync(“temperature*”, 0, 100)

After the previous call, you can use the following call to return the remaining 75 matches, skipping over the first 
100 matches because of the skip parameter set at 100):

       _metadataService.GetStreamsAsync(“temperature*”, 100, 100) 


Search operators
----------------

You can specify search operators in the ``searchText`` string to return more specific search results. 

#### operators 

Operators | Description
----------|-------------------------------------------------------------------
``AND`` | AND operator. For example, ``"cat AND dog"`` searches for streams containing both "cat" and "dog".  AND must be in all caps.
``OR``  | OR operator. For example, ``"cat OR dog"`` searches for streams containing either "cat" or "dog" or both.  OR must be in all caps.
``NOT`` | NOT operator. For example, ``"cat NOT dog"`` searches for streams that have the "cat" term or do not have "dog".  NOT must be in all caps.
``*``   | Suffix operator. For example, ``"cat*"`` searches for streams that have a term that starts with "cat", ignoring case.
``:``   | Field-scoped query.  For example, ``id:stream*`` will search for streams where the ``id`` field starts with "stream", but will not search on other fields like ``name`` or ``description``.  *Note that field names are camel case and are case sensitive.*
``" "`` | Phrase search operator. For example, while ``Roach Motel`` (without quotes) would search for streams containing Roach Motel anywhere in any order, ``"Roach Motel"`` (with quotes) will only match documents that contain the whole phrase together and in that order.
``( )`` | Precedence operator. For example, ``motel AND (wifi OR luxury)`` searches for streams containing the motel term and either wifi or luxury (or both).

Note that the suffix operator ``*`` is not the same as a generic wildcard operator that you might be more familiar with. 
It can only be used at the end of a search term, not the beginning. Also, it can't be combined when searching for a 
phrase using the ``" "`` operators which combine multiple ordered search terms. It only works when specifying a single 
search term. For example, you can search for ``Tank*``, but not ``*Tank`` or ``"Tank1 Meter*"``.


Searching on Metadata
---------------------

Streams can have metadata collections associated with them. Metadata allows you to specify arbitrary key-value 
pairs to help organize and add context your streams. To search for streams by metadata, use the following syntax:
``"key:value"``. Because the colon is a special character used in field-scoped queries, the search term for metadata 
*must* be enclosed in double quotes. For example, to search for all streams with a key of "Manufacturer" and a value 
of "OSI", you would use ``"Manufacturer:OSI"``.  If you want to search for a stream with a key of "Manufacturer" and 
any value, you could drop the quotes and the colon and search for ``Manufacturer*``.  While searching for a key with 
a wildcard value is supported, searching on a value with a wildcard key is not supported.
