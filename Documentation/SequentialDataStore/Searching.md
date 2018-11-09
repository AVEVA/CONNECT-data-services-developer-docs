---
uid: sdsSearching
---

#### Sds_Searching_topic

Searching
=====================
SdsSearch provides a way to search text, phrases, fields etc over the Sequential Data Store. This document covers the 
searching for SdsStreams and SdsTypes.

Searching for streams
=====================

The search functionality for streams is exposed through REST API and the client libraries method ``GetStreamsAsync``.

``GetStreamsAsync`` is an overloaded method that is also used to search for and return streams (also see [Streams](xref:sdsStreams) for information about using ``GetStreamAsync`` to return streams). When you call an overloaded method, the software determines the most appropriate method to use by comparing the argument types specified in the call to the method definition.

The syntax of the client libraries method is as follows:

      _metadataService.GetStreamsAsync(string searchText, int skip, int count);


Searching for streams is also possible using the REST API and specifying the optional ``query`` parameter, as shown here:

      GET api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams?query={query}&skip={skip}&count={count}


Searching for types
=====================

Similarly, the search functionality for types is also exposed through REST API and the client libraries method ``GetTypesAsync``.

``GetTypesAsync`` is an overloaded method that is also used to search for and return types. 

The syntax of the client libraries method is as follows:

      _metadataService.GetTypesAsync(string searchText, int skip, int count);


As previously mentioned, searching for types is also possible using the REST API and specifying the optional ``query`` parameter, as shown here:

      GET api/Tenants/{tenantId}/Namespaces/{namespaceId}/Types?query={query}&skip={skip}&count={count}

The ``GetStreamsAsync`` or ``GetTypesAsync`` overload returns streams/types that match specific search criteria within a given namespace. 
You use the ``searchText`` parameter to specify a search string. Both methods then return any stream/type
that matches the search string in the ``name``, ``description`` list. 

The ``skip`` and ``count`` parameters determine which streams/types are returned when a large number of streams/types match 
the ``searchText`` criteria.   

``count`` indicates the maximum number of streams/types returned by the ``GetStreamsAsync()`` or ``GetTypesAsync()`` call. The maximum value of 
the ``count`` parameter is 1000. 

``skip`` indicates the number of matched streams/types to skip over before returning matching streams/types. You use the 
skip parameter when more streams/types match the search criteria than can be returned in a single call. 

For example, assume there are 175 streams that match the search criteria: “temperature”.

The following call returns the first 100 matches:

       _metadataService.GetStreamsAsync(“temperature”, 0, 100)

After the previous call, you can use the following call to return the remaining 75 matches, skipping over the first 
100 matches because of the skip parameter set at 100):

       _metadataService.GetStreamsAsync(“temperature”, 100, 100)


OrderBy Parameter
=====================
The ``orderby`` parameter is supported for searching both the streams and types. The basic functionality of it is to search the streams or types and then return the result in sorted order.
The default value for ``orderby`` parameter is ascending order. It can be changed to descending order by specifying ``desc`` alongside the orderby field value. It can be used in conjunction with 
``query``, ``skip``, and ``count`` parameters.

**REST API examples**

	GET api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams?query=name:pump name:pressure&orderby=name

	GET api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams?query=name:pump name:pressure&orderby=id asc

	GET api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams?query=name:pump name:pressure&orderby=name desc

	GET api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams?query=name:pump name:pressure&orderby=name desc&skip=10&count=20


Search operators
=====================

You can specify search operators in the ``searchText`` string to return more specific search results. 

Operators | Description
----------|-------------------------------------------------------------------
``AND`` | AND operator. For example, ``"cat AND dog"`` searches for streams containing both "cat" and "dog".  AND must be in all caps.
``OR``  | OR operator. For example, ``"cat OR dog"`` searches for streams containing either "cat" or "dog" or both.  OR must be in all caps.
``NOT`` | NOT operator. For example, ``"cat NOT dog"`` searches for streams that have the "cat" term or do not have "dog".  NOT must be in all caps.
``*``   | Wildcard operator. For example, ``"cat*"`` searches for streams that have a term that starts with "cat", ignoring case.
``:``   | Field-scoped query.  For example, ``id:stream*`` will search for streams where the ``id`` field starts with "stream", but will not search on other fields like ``name`` or ``description``.  *Note that field names are camel case and are case sensitive.*
``" "`` | Phrase search operator. For example, while ``Roach Motel`` (without quotes) would search for streams containing Roach Motel anywhere in any order, ``"Roach Motel"`` (with quotes) will only match documents that contain the whole phrase together and in that order.
``( )`` | Precedence operator. For example, ``motel AND (wifi OR luxury)`` searches for streams containing the motel term and either wifi or luxury (or both).

 The wildcard ``*`` can't be combined when searching for a phrase using the ``" "`` operators which combine multiple ordered search terms. 
It only works when specifying a single search term. For example, you can search for ``Tank*``, ``*Tank``, ``Ta*nk`` but not ``"Tank Meter*"``.

For example, assume that a namespace contains the following Streams:

**streamId** | **Name**  | **Description**  | **Tags**
------------ | --------- | ---------------- | -------------------------
stream1      | tempA     | The temperature from DeviceA | “temperature”, “DeviceA”
stream2      | pressureA | The pressure from DeviceA    | “pressure”, “DeviceA”
stream3      | calcA     | calculation from DeviceA values | “temperature”, “pressure”, “DeviceA”


Using the stream data above, the following table shows the results of a ``GetStreamsAsync`` call with different ``SearchText`` values:

**QueryString**     | **Streams returned**
------------------ | ----------------------------------------
``“temperature”``  | stream1 and stream3 returned.
``“calc*”``        | Only stream3 returned.
``“DeviceA*”``     | All three streams returned.
``“humidity*”``    | No streams returned.

**: Operator**
---------------

You can also qualify which fields are searched by using the following syntax: 

	fieldname:fieldvalue

**REST API example**

	GET api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams?query=name:pump name:pressure

**C# example**

	GetStreamsAsync(query:”name:pump name:pressure”);

**\* Operator**
-----------------

You can use the ‘\*’ character as a wildcard to specify an incomplete
string.

**Query string**   | **Matches field value**    | **Does not match field value**
------------------ | -------------------------- | --------------------------------
``"log*"``		   |	log	                    | analog
			       |    logger                  |

**REST API example**

	GET api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams?query=log*

**C# example**

	GetStreamsAsync(query:”log*”);


\"" Operator
-------------------

The search engine automatically searches on strings delimited by
whitespace and dashes (with the exception of identifier fields like Id
or TypeId fields). To search for values that include delimiters, enclose the value in double quotes.

**Query string**   | **Matches field value**    | **Does not match field value**
------------------ | -------------------------- | ----------------------------
``"pump pressure"`` | pump pressure 			| the pump
					| the pump pressure gauge	| pressure
					|							| pressure pump

**REST API example**

	GET api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams?query=”pump pressure”

**C# example**

	GetStreamsAsync(query:”\\”pump pressure\\””);

Other useful examples.

Query string | Matches field value | Does not match field value
----------|-------------------------------------------------------------------
``"mud AND log"``		| log mud		| mud
``"mud AND log"``		| mud log		| log
``"mud OR log"``		| mud			|
``"mud OR log"``   		| log			|
``"mud OR log"``		| mud log		|
``"mud AND (NOT log)"`` | mud			| mud log
``"mud AND (log OR pump\*)"`` | mud log | mud bath
``"name:stream\* AND (tags:pressure OR tags:pump)"`` | The name starts with “stream” and has tag values of either “pressure” or “pump” | 


Searching on Metadata
---------------------

Streams can have metadata collections associated with them. Metadata allows you to specify arbitrary key-value 
pairs to help organize and add context your streams. To search for streams by metadata, use the following syntax:
``"key:value"``. Because the colon is a special character used in field-scoped queries, the search term for metadata 
*must* be enclosed in double quotes. For example, to search for all streams with a key of "Manufacturer" and a value 
of "OSI", you would use ``"Manufacturer:OSI"``.  If you want to search for a stream with a key of "Manufacturer" and 
any value, you could drop the quotes and the colon and search for ``Manufacturer*``.  While searching for a key with 
a wildcard value is supported, searching on a value with a wildcard key is not supported.
