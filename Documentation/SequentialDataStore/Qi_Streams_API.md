---
uid: sdsStreamsApi
---

QiStream API
============

The REST APIs provide programmatic access to read and write Qi data. The APIs in this 
section interact with QiStreams. When working in .NET convenient Qi Client libraries are 
available. The ``IQiMetadataService`` interface, accessed using the ``QiService.GetMetadataService( )`` helper, 
defines the available functions. See [QiStreams](xref:sdsStreams)) for general 
QiStream information. 


***********************

``Get Stream``
--------------

Returns the specified stream.


**Request**

        GET api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}


**Parameters**

``string tenantId``
  The tenant identifier
``string namespaceId``
  The namespace identifier
``string typeId``
  The type identifier


**Response**

  The response includes a status code and a response body.


**Response body**

  The requested QiStream.

  Sample response body:

      HTTP/1.1 200
      Content-Type: application/json

      {  
         "Id":"Simple"
         "Name":"Simple"
         "TypeId":"Simple",
      }


**.NET Library**

      Task<QiStream> GetStreamAsync(string streamId);


**Security**

  Allowed by administrator accounts


***********************

``Get Streams``
--------------

Returns a list of streams.

If the optional search parameter is specified, the list of streams returned are filtered to match 
the search criteria. If the optional search parameter is not specified, the list includes all streams 
in the Namespace. See [Searching for QiStreams](xref:sdsSearching) for information about specifying the search parameter.

**Request**

        GET	api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams?query={query}
            &skip={skip}&count={count}




**Parameters**

``string tenantId``
  The tenant identifier
``string namespaceId``
  The namespace identifier
``string query``
  An optional parameter representing a string search. 
  See [Searching for QiStreams](xref:sdsSearching) for information about specifying the search parameter.
``int skip``
  An optional parameter representing the zero-based offset of the first QiStream to retrieve. 
  If not specified, a default value of 0 is used.
``int count``
  An optional parameter representing the maximum number of QiStreams to retrieve. 
  If not specified, a default value of 100 is used.


**Response**

  The response includes a status code and a response body.


**Response body**

  A collection of zero or more QiStreams.

  Sample response body:

      HTTP/1.1 200
      Content-Type: application/json

       [  
         {  
            "Id":"Simple",
            "TypeId":"Simple"
         },
         {  
            "Id":"Simple with Secondary",
            "TypeId":"Simple",
            "Indexes":[  
               {  
                  "QiTypePropertyId":"Measurement"
               }
            ]
         },
         {  
            "Id":"Compound",
            "TypeId":"Compound"
         },
         ...
      ]


**.NET Library**

      Task<IEnumerable<QiStream>> GetStreamsAsync(string query = "", int skip = 0, 
          int count = 100);



**Security**

  Allowed for administrator and user accounts

***********************

``Get Stream Type``
-------------------

Returns the type definition that is associated with a given stream.


**Request**

        GET api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Type

**Parameters**

``string tenantId``
  The tenant identifier
``string namespaceId``
  The namespace identifier
``string streamId``
  The stream identifier


**Response**

  The response includes a status code and a response body.


**Response body**

  The requested QiType.


**.NET Library**

      Task<QiType> GetStreamTypeAsync(string streamId);


**Security**

  Allowed by administrator and user accounts


***********************

``Create Stream``
-----------------

Creates the specified stream. If a stream with a matching identifier already exists, Qi compares the 
existing stream with the stream that was sent. If the streams are identical, a ``Found`` (302) error 
is returned with the Location header set to the URI where the stream may be retrieved using a Get function. 
If the streams do not match, a ``Conflict`` (409) error is returned.

For a matching stream (Found), clients that are capable of performing a redirect that includes the 
authorization header can automatically redirect to retrieve the stream. However, most clients, 
including the .NET HttpClient, consider redirecting with the authorization token to be a security vulnerability.

When a client performs a redirect and strips the authorization header, Qi cannot authorize the request and 
returns ``Unauthorized`` (401). For this reason, it is recommended that when using clients that do not 
redirect with the authorization header, you should disable automatic redirect.


**Request**

        POST api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}


**Parameters**

``string tenantId``
  The tenant identifier
``string namespaceId``
  The namespace identifier
``string streamId``
  The stream identifier. The stream identifier must match the identifier in content. 
  The request content is the serialized QiStream.

**Response**

  The response includes a status code and a response body.


**Response body**

  The newly created QiStream.


**.NET Library**

      Task<QiStream> GetOrCreateStreamAsync(QiStream qiStream);


If a stream with a matching identifier already exists and it matches the stream in the request body, 
the client redirects a GET to the Location header. If the existing stream does not match the stream 
in the request body, a Conflict error response is returned and the client library method throws an exception. 


**Security**

  Allowed for administrator accounts


***********************

``Create or Update Stream``
-------------------------

Creates the specified stream. If a stream with the same Id already exists, the definition of the stream is updated. 
The following changes are permitted:

•	Name
•	BehaviorId
•	Description

Unpermitted changes result in an error.



**Request**

        PUT api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}

**Parameters**

``string tenantId``
  The tenant identifier of the tenant where you want to update the stream
``string namespaceId``
  The namespace identifier of the namespace where you want to update the stream
``string streamId``
  The stream identifier to be updated

The request content is the serialized QiStream.


**Response**

  The response includes a status code.


**.NET Library**

      Task CreateOrUpdateStreamAsync(QiStream qiStream);


**Security**

  Allowed for administrator accounts


***********************

``Update Stream Type``
--------------

Updates a stream’s type. The type is modified to match the specified view. 


**Request**

        PUT api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Type?viewId={viewId}


**Parameters**

``string tenantId``
  The tenant identifier
``string namespaceId``
  The namespace identifier
``string streamId``
  The stream identifier
``string viewId``
  The view identifier

The request contains no content.


**Response**

  The response includes a status code.


**Response body**

  On failure, the content contains a message describing the issue.


**.NET Library**

      Task UpdateStreamTypeAsync(string streamId, string viewId);


**Security**

  Allowed for administrator accounts


***********************

``Delete Stream``
--------------

Deletes a stream. 


**Request**

        DELETE api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}


**Parameters**

``string tenantId``
  The tenant identifier
``string namespaceId``
  The namespace identifier
``string streamId``
  The stream identifier


**Response**

  The response includes a status code.


**.NET Library**

      Task DeleteStreamAsync(string streamId);


**Security**

  Allowed for administrator accounts



QiStream Metadata and Tags
--------------------------

QiStream metadata is represented as a dictionary of string keys and associated string values. 
It can be used to associate additional information with a stream. QiStream tags are represented 
as a list of strings. Tags can be used to categorize or denote special attributes of streams. 

QiStream Metadata API 
---------------------

``Get stream metadata``
----------------------

Returns the metadata dictionary for the specified stream. 


**Request**

        GET api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Metadata 


**Parameters**

``string tenantId``
  The tenant identifier
``string namespaceId``
  The namespace identifier
``string streamId``
  The stream identifier


**Response**

  The response includes a status code and a response body.

**Response body**

  The metadata for the specified QiStream. 

**Sample response body**

      HTTP/1.1 200 
      Content-Type: application/json 
      { 
          "a metadata key":"a metadata value", 
          "another key":"another value" 
      } 


**.NET Library**

      Task<IDictionary<string, string>> GetStreamMetadataAsync(string streamId); 


**Security**

  Allowed for administrator and user accounts


***********************


``Get stream metadata value``
----------------------

Returns the value for the specified key in the metadata dictionary of the specified stream. 


**Request**

        GET api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Metadata/{key} 


**Parameters**

``string tenantId``
  The tenant identifier
``string namespaceId``
  The namespace identifier
``string streamId``
  The stream identifier
``string key``
  The key specifying the metadata value of interest 



**Response**

  The response includes a status code and a response body.

**Response body**

  The metadata for the specified QiStream. 

**Sample response body**

      HTTP/1.1 200 
      Content-Type: application/json 
      { 
          "a metadata value” 
      } 


**.NET Library**

      Task<string> GetStreamMetadataValueAsync(string streamId, string key); 


**Security**

  Allowed for administrator and user accounts


***********************

``Update stream metadata``
------------------------

Replaces the metadata for the specified stream with the metadata in the request body. 
Overwrites any existing metadata; does not merge. 


**Request**

        PUT api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Metadata 


**Parameters**

``string tenantId``
  The tenant identifier
``string namespaceId``
  The namespace identifier
``string streamId``
  The stream identifier


**Response**

  The response includes a status code.


**.NET Library**

       Task UpdateStreamMetadataAsync(string streamId, IDictionary<string, string> metadata); 


**Security**

  Allowed for administrator accounts


***********************



``Delete stream metadata``
------------------------

Deletes the metadata for the specified stream.  

**Request**

        DELETE api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Metadata 


**Parameters**

``string tenantId``
  The tenant identifier
``string namespaceId``
  The namespace identifier
``string streamId``
  The stream identifier


**Response**

  The response includes a status code.


**.NET Library**

        Task DeleteStreamMetadataAsync(string streamId); 


**Security**

  Allowed for administrator accounts


***********************


QiStream Tags API 
-----------------


``Get stream tags``
----------------------

Returns the tag list for the specified stream. 


**Request**

        GET api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Tags 


**Parameters**

``string tenantId``
  The tenant identifier
``string namespaceId``
  The namespace identifier
``string streamId``
  The stream identifier


**Response**

  The response includes a status code and a response body.

**Response body**

  The tags for the specified QiStream. 

**Sample response body**

      HTTP/1.1 200 
      Content-Type: application/json 
      [ 
          "a tag", 
          "another tag" 
      ] 


**.NET Library**

      Task<IList<string>> GetStreamTagsAsync(string streamId); 


**Security**

  Allowed for administrator and user accounts


***********************

``Update stream tags``
---------------------

Replaces the tag list for the specified stream with the tags listed in the request body.  
Overwrites any existing tags; does not merge. 


**Request**

        PUT api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Tags 


**Parameters**

``string tenantId``
  The tenant identifier
``string namespaceId``
  The namespace identifier
``string streamId``
  The stream identifier

  The request content is the serialized list of tags. 

**Response**

  The response includes a status code.


**.NET Library**

       Task UpdateStreamTagsAsync(string streamId, IList<string> tags); 


**Security**

  Allowed by administrator accounts.


***********************


``Delete stream metadata``
------------------------

Deletes the tag list for the specified stream. 


**Request**

       DELETE api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Tags 


**Parameters**

``string tenantId``
  The tenant identifier
``string namespaceId``
  The namespace identifier
``string streamId``
  The stream identifier


**Response**

  The response includes a status code.


**.NET Library**

       Task DeleteStreamTagsAsync(string streamId); 


**Security**

  Allowed for administrator accounts.


***********************
