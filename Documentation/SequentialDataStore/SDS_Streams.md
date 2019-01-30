---
uid: sdsStreams
---

Streams
=======

SDS stores collections of events and provides convenient ways to find and associating events. Events 
of consistent structure are stored in streams, called SdsStreams.  An SdsType defines the structure 
of events in an SdsStream.

SdsStreams are referenced by their identifier or Id field. SdsStream identifiers must be unique 
within a Namespace.

An SdsStream must include a TypeId that references the identifier of an existing SdsType. 
When an SdsStream contains data, you must use a stream view to update the stream type.

SdsStream management using the .NET SDS Client Libraries is performed through ISdsMetadataService. 
Create the ISdsMetadataService, using one of the ``SdsService.GetMetadataService()`` factory methods.

The following table shows the required and optional SdsStream fields. Fields not listed are reserved
for internal SDS use. 


| Property          | Type                             | Optionality | Details |
|-------------------|----------------------------------|-------------|---------|
| Id                | String                           | Required    | An identifier for referencing the stream |
| TypeId            | String                           | Required    | The SdsType identifier of the type to be used for this stream |
| Name              | String                           | Optional    | Friendly name |
| Description       | String                           | Optional    | Description text |
| Indexes           | IList<SdsStreamIndex>            | Optional    | Used to define secondary indexes for stream |
| InterpolationMode | SdsInterpolationMode             | Optional    | Interpolation setting of the stream. Default is null. |
| ExtrapolationMode | SdsExtrapolationMode             | Optional    | Extrapolation setting of the stream. Default is null. |
| PropertyOverrides | IList<SdsStreamPropertyOverride> | Optional    | Used to define unit of measure and interpolation mode overrides for a stream |


**Rules for Identifier (SdsStream.Id)**

1. Is not case sensitive.
2. Can contain spaces.
3. Cannot start with two underscores ("\_\_").
4. Can contain a maximum of 100 characters.
5. Cannot use the following characters: ( / : ? # [ ] @ ! $ & ' ( ) \\\* +
   , ; = %)
6. Cannot start or end with a period.
7. Cannot contain consecutive periods.
8. Cannot consist of only periods. 



Indexes
-------

The Key or Primary Index is defined at the SdsType. Secondary
Indexes are defined at the SdsStream.

Secondary Indexes are applied to a single property; there are no
compound secondary indexes. Only SdsTypeCodes
that can be ordered are supported for use in a secondary index.


Indexes are discussed in greater detail here: [Indexes](xref:sdsIndexes)


Interpolation and Extrapolation
-------------------------------

The InterpolationMode, ExtrapolationMode, and [PropertyOverrides](#propertyoverrides) can be used to determine how a specific stream reads data. These read characteristics are inherited from the type if they are not defined at the stream level. For more information about type read characteristics and how these characteristics dictate how events are read see [Types](xref:sdsTypes).


PropertyOverrides
-----------------

PropertyOverrides provide a way to override interpolation behavior and unit of measure for individual 
SdsType Properties for a specific stream.

The ``SdsStreamPropertyOverride`` object has the following structure:


| Property          | Type                           | Optionality | Details |
|-------------------|--------------------------------|-------------|---------|
| SdsTypePropertyId | String                         | Required    | SdsTypeProperty identifier |
| InterpolationMode | SdsInterpolationMode           | Optional    | Interpolation setting. Default is null |
| Uom               | String                         | Optional    | Unit of measure |


The unit of measure can be overridden for any type property defined by the stream type, including primary keys 
and secondary indexes. For more information about type property units of measure see [Types](xref:sdsTypes). 

Read characteristics of the stream are determined by the type and the PropertyOverrides of the stream. The 
interpolation mode for non-index properties can be defined and overridden at the stream level. For more 
information about type read characteristics see [Types](xref:sdsTypes).

When specifying property interpolation overrides, if the SdsType InterpolationMode is ``Discrete``, it cannot be overridden 
at any level. When InterpolationMode is set to ``Discrete`` and an event it not defined for that index, a null 
value is returned for the entire event.


SdsStream API
------------


The REST APIs provide programmatic access to read and write SDS data. The APIs in this 
section interact with SdsStreams. When working in .NET convenient SDS Client libraries are 
available. The ``ISdsMetadataService`` interface, accessed using the ``SdsService.GetMetadataService( )`` helper, 
defines the available functions. See [Streams](#streams) for general 
SdsStream information. 


***********************

``Get Stream``
--------------

Returns the specified stream.


**Request**

        GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}


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

  The requested SdsStream.

  Sample response body:

      HTTP/1.1 200
      Content-Type: application/json

      {  
         "Id":"Simple"
         "Name":"Simple"
         "TypeId":"Simple",
      }


**.NET Library**

      Task<SdsStream> GetStreamAsync(string streamId);


**Security**

  Allowed by administrator accounts


***********************

``Get Streams``
--------------

Returns a list of streams.

If specifying the optional search parameter or optional filter parameter, the list of streams returned are filtered to match 
the search/filter criteria. If neither parameter is specified, the list includes all streams 
in the Namespace. See [Searching](xref:sdsSearching) 
and [Filter Expressions: Metadata Objects](xref:sdsFilterExpressionsMetadata)  
for information about specifying those respective parameters.


**Request**

        GET	api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams?query={query}&filter={filter}&skip={skip}&count={count}&orderby={orderby}

**Parameters**

``string tenantId``  
  The tenant identifier

``string namespaceId``  
  The namespace identifier

``string query``  
  An optional parameter representing a string search. 
  See [Searching](xref:sdsSearching)
  for information about specifying the search parameter.

``string filter``   
  An optional filter string to match which SdsStreams will be returned.  See the 
  [Filter Expressions: Metadata Objects](xref:sdsFilterExpressionsMetadata) 
  topic for information about specifying the filter parameter.

``int skip``  
  An optional parameter representing the zero-based offset of the first SdsStream to retrieve. 
  If not specified, a default value of 0 is used.

``int count``  
  An optional parameter representing the maximum number of SdsStreams to retrieve. 
  If not specified, a default value of 100 is used.

``string orderby``  
  An optional parameter representing sorted order which SdsStreams will be returned. A field name is required. The sorting is based on the stored values for the given field (of type string). For example, ``orderby=name`` would sort the returned results by the ``name`` values (ascending by default). Additionally, a value can be provided along with the field name to identify whether to sort ascending or descending, by using values ``asc`` or ``desc``, respectively. For example, ``orderby=name desc`` would sort the returned results by the ``name`` values, descending. If no value is specified, there is no sorting of results.

**Response**

  The response includes a status code and a response body.


**Response body**

  A collection of zero or more SdsStreams.

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
                  "SdsTypePropertyId":"Measurement"
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

      Task<IEnumerable<SdsStream>> GetStreamsAsync(string query = "", int skip = 0, 
          int count = 100);



**Security**

  Allowed for administrator and user accounts

***********************

``Get Stream Type``
-------------------

Returns the type definition that is associated with a given stream.


**Request**

        GET api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Type

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

  The requested SdsType.


**.NET Library**

      Task<SdsType> GetStreamTypeAsync(string streamId);


**Security**

  Allowed by administrator and user accounts


***********************

``Create Stream``
-----------------

Creates the specified stream. If a stream with a matching identifier already exists, SDS compares the 
existing stream with the stream that was sent. If the streams are identical, a ``Found`` (302) error 
is returned with the Location header set to the URI where the stream may be retrieved using a Get function. 
If the streams do not match, a ``Conflict`` (409) error is returned.

For a matching stream (Found), clients that are capable of performing a redirect that includes the 
authorization header can automatically redirect to retrieve the stream. However, most clients, 
including the .NET HttpClient, consider redirecting with the authorization token to be a security vulnerability.

When a client performs a redirect and strips the authorization header, SDS cannot authorize the request and 
returns ``Unauthorized`` (401). For this reason, it is recommended that when using clients that do not 
redirect with the authorization header, you should disable automatic redirect.


**Request**

        POST api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}


**Parameters**

``string tenantId``  
  The tenant identifier  
  
``string namespaceId``  
  The namespace identifier  
  
``string streamId``  
  The stream identifier. The stream identifier must match the identifier in content. 
  The request content is the serialized SdsStream.

**Response**

  The response includes a status code and a response body.


**Response body**

  The newly created SdsStream.


**.NET Library**

      Task<SdsStream> GetOrCreateStreamAsync(SdsStream SdsStream);


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
•	Description
•  PropertyOverrides

Unpermitted changes result in an error.


**Request**

        PUT api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}

**Parameters**

``string tenantId``  
  The tenant identifier  
  
``string namespaceId``  
  The namespace identifier  
  
``string streamId``  
  The stream identifier  

The request content is the serialized SdsStream.


**Response**

  The response includes a status code.


**.NET Library**

      Task CreateOrUpdateStreamAsync(SdsStream SdsStream);


**Security**

  Allowed for administrator accounts


***********************

``Update Stream Type``
--------------

Updates a stream’s type. The type is modified to match the specified stream view. 
Defined Indexes and PropertyOverrides are removed when updating a stream type.


**Request**

        PUT api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Type?streamViewId={streamViewId}

**Parameters**

``string tenantId``  
  The tenant identifier  
  
``string namespaceId``  
  The namespace identifier  
  
``string streamId``  
  The stream identifier  
  
``string streamViewId``  
  The stream view identifier  

The request contains no content.


**Response**

  The response includes a status code.


**Response body**

  On failure, the content contains a message describing the issue.


**.NET Library**

      Task UpdateStreamTypeAsync(string streamId, string streamViewId);


**Security**

  Allowed for administrator accounts


***********************

``Delete Stream``
--------------

Deletes a stream. 


**Request**

        DELETE api/v1-preview/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}


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
