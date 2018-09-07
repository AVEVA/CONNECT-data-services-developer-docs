---
uid: accountApplications
---

Applications
=======================================================

**********************

``CreateClientApiKeyForApplication()``
--------------------------------------------------------------------

Create a [ClientApiKeySet](#clientapikeysetobj) for the specified application.

**Http**

    	POST api/Tenants/{tenantId}/ClientApiKeySets/Keys

**Parameters**

``string tenantId``
	ID of the tenant the application belongs to.
``string applicationId``
	ID of the application for this request
``string description``
	Description of the [ClientApiKeySet](#clientapikeysetobj)

**Security**  
Allowed by Account Administrator [Role](xref:accountRole#roleobj)

**Returns**  
The created [ClientApiKeySet](#clientapikeysetobj)

**Notes**  
For HTTP requests and responses, the ClientApiKeySet object has the following properties and JSON-serialized body: 

#### ClientApiKeySetObj 

``string AppUri``
	App ID URI.
``bool CreateFirstKey``
	Create the first key in the Client API Key Set.
``string DisplayName``
	Display name.
``[string,[string]] RequiredResource``
	List of required resources.
``string TenantId``
	Tenant Id.

.. highlight:: C#

    	HTTP/1.1 200
    	Content-Type: application/json

     {
    	"AppUri": "appuri",
    	"CreateFirstKey": false,
    	"DisplayName": "displayname",
    	"RequiredResource":  { },
    	"TenantId": "tenantid"
     }

**********************

``GetClientApiKeyCollectionFromApplication()``
--------------------------------------------------------------------

Get the [ClientApiKeyCollection](#clientapikeycollectionobj) for the specified applicaiton.

**Http**

    	GET api/Tenants/{tenantId}/ClientApiKeySets/Keys

**Parameters**

``string tenantId``
	ID of the tenant the application belongs to.
``string applicationId``
	ID of the application for this request

**Security**  
Allowed by Account Administrator [Role](xref:accountRole#roleobj)

**Returns**  
[ClientApiKeyCollection](#clientapikeycollectionobj) for the specified applicaiton.

**Notes**  
For HTTP requests and responses, the ClientApiKeyCollection object has the following properties and JSON-serialized body: 

#### ClientApiKeyCollectionObj 

``string Id``
	Gets the identifier for this collection of API access keys, a GUID.
``[ClientApiKey] Keys``
	Gets a list of the application's access keys.

.. highlight:: C#

    	HTTP/1.1 200
    	Content-Type: application/json

     {
    	"Id": "id",
    	"Keys": []
     }

**********************

``DeleteClientApiKeyFromApplication()``
--------------------------------------------------------------------

Delete a specified [ClientApiKeySet](#clientapikeysetobj).

**Http**

    	DELETE api/Tenants/{tenantId}/ClientApiKeySets/Keys

**Parameters**

``string tenantId``
	ID of the tenant the application belongs to.
``string applicationId``
	ID of the application for this request
``string keyId``
	ID of the [ClientApiKeySet](#clientapikeysetobj) to be deleted.

**Security**  
Allowed by Account Administrator [Role](xref:accountRole#roleobj)

**Returns**  
HTTP status code - 200 OK if the [ClientApiKeySet](#clientapikeysetobj) was deleted.

**********************

``GetExternalApplicationsAsync()``
--------------------------------------------------------------------

Lists all applications from a customer's directory

**Http**

    	GET api/Tenants/{tenantId}/externalapplications

**Parameters**

``string tenantId``
	ID of the tenant the application belongs to
``string skip``
	Number of applications to skip for paging purposes.
``string count``
	>Maximum number of applications to return in this page.
``string query``
	Prefix match to filter applications by applicationId or display name

**Security**  
Allowed by Account Administrator [Role](xref:accountRole#roleobj)

**Returns**  
An array of [Application](#applicationobj) objects that could be added to this account.

**Notes**  
For HTTP requests and responses, the Application object has the following properties and JSON-serialized body: 

#### ApplicationObj 

``string Id``
	Application Identifier
``string TenantId``
	Tenant Id
``string Name``
	Application Display Name
``[Role] Roles``
	List of roles for the application

.. highlight:: C#

    	HTTP/1.1 200
    	Content-Type: application/json

     {
    	"Id": "id",
    	"TenantId": "tenantid",
    	"Name": "name",
    	"Roles": []
     }

**********************

``RegisterClientApplicationAsync()``
--------------------------------------------------------------------

Registers the application with cloud services

**Http**

    	POST api/Tenants/{tenantId}/Applications

**Parameters**

``string tenantId``
	ID of the tenant the application belongs to
``Application application``
	[Application](#applicationobj) object with required properties.

**Security**  
Account admin or Cluster operator

**Returns**  
The [Application](#applicationobj) for a tenant

**********************
