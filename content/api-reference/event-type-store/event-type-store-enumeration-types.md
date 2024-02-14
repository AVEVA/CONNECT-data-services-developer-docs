---
uid: event-type-store-enumeration-types

---

# Enumeration Types

## `List Enumerations`

<a id="opIdEnumerations_List Enumerations"></a>

Returns an array of Enumerations in a given namespace and the version ETag in the HTTP response header. The If-Match and If-None-Match headers are supported.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations
?skip={skip}&count={count}&filter={filter}&includeDeleted={includeDeleted}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>
`[optional] integer skip`
<br/>Parameter representing the zero-based offset of the first object to retrieve.  If unspecified, a default value of 0 is used.<br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of objects to retrieve. If unspecified, a default value of 100 is used.<br/><br/>`[optional] string filter`
<br/>Parameter representing the condition for results to be filtered by. If unspecified, results are not filtered.<br/><br/>`[optional] boolean includeDeleted`
<br/>Parameter indicating whether to include soft-deleted Enumerations. If unspecified, a default value of false is used.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Enumeration](#schemaenumeration)[]|Success.|
|304|None|Not modified.|
|400|[AdhErrorResponse](#schemaadherrorresponse)|Missing or invalid inputs.|
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|
|412|[AdhErrorResponse](#schemaadherrorresponse)|Precondition failed.|

<h4>Example response body</h4>

> 200 Response

```json
[
  {
    "Id": "SimpleEnumeration",
    "Name": "SimpleEnumeration",
    "GraphQLName": "SimpleEnumeration",
    "Members": [
      {
        "Name": "ACTIVE",
        "GraphQLName": "ACTIVE",
        "Code": 0,
        "State": "Active",
        "Description": "This is an active state"
      },
      {
        "Name": "CLOSED",
        "GraphQLName": "CLOSED",
        "Code": 1,
        "State": "Active",
        "Description": "This is a closed state"
      }
    ],
    "Version": 1,
    "State": "Active",
    "CreatedDate": "0001-01-01T00:00:00Z",
    "ModifiedDate": "0001-01-01T00:00:00Z"
  },
  {
    "Id": "SimpleEnumeration",
    "Name": "SimpleEnumeration",
    "GraphQLName": "SimpleEnumeration",
    "Members": [
      {
        "Name": "ACTIVE",
        "GraphQLName": "ACTIVE",
        "Code": 0,
        "State": "Active",
        "Description": "This is an active state"
      },
      {
        "Name": "CLOSED",
        "GraphQLName": "CLOSED",
        "Code": 1,
        "State": "Active",
        "Description": "This is a closed state"
      }
    ],
    "Version": 1,
    "State": "Active",
    "CreatedDate": "0001-01-01T00:00:00Z",
    "ModifiedDate": "0001-01-01T00:00:00Z"
  }
]
```

> 400 Response ([AdhErrorResponse](#schemaadherrorresponse))

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "property1": null,
  "property2": null
}
```

---

## `Create Enumeration With Server Generated Id`

<a id="opIdEnumerations_Create Enumeration With Server Generated Id"></a>

Creates a new Enumeration. Response includes ETag header.

<h3>Request</h3>

```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

<h4>Request Body</h4>

An Enumeration.<br/>

```json
{
  "Name": "SimpleEnumeration",
  "Members": [
    {
      "Name": "ACTIVE",
      "Code": 0
    },
    {
      "Name": "CLOSED",
      "Code": 1
    }
  ]
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|201|[Enumeration](#schemaenumeration)|Created.|
|400|[AdhErrorResponse](#schemaadherrorresponse)|Missing or invalid inputs.|
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|
|409|[AdhErrorResponse](#schemaadherrorresponse)|Conflict|

<h4>Example response body</h4>

> 201 Response

```json
{
  "Id": "SimpleEnumeration",
  "Name": "SimpleEnumeration",
  "GraphQLName": "SimpleEnumeration",
  "Members": [
    {
      "Name": "ACTIVE",
      "GraphQLName": "ACTIVE",
      "Code": 0,
      "State": "Active",
      "Description": "This is an active state"
    },
    {
      "Name": "CLOSED",
      "GraphQLName": "CLOSED",
      "Code": 1,
      "State": "Active",
      "Description": "This is a closed state"
    }
  ],
  "Version": 1,
  "State": "Active",
  "CreatedDate": "0001-01-01T00:00:00Z",
  "ModifiedDate": "0001-01-01T00:00:00Z"
}
```

> 400 Response ([AdhErrorResponse](#schemaadherrorresponse))

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "property1": null,
  "property2": null
}
```

---

## `Get Enumeration By Id`

<a id="opIdEnumerations_Get Enumeration By Id"></a>

Returns the specified Enumeration and the version ETag in the HTTP response header. The If-Match and If-None-Match headers are supported.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations/{id}
?includeDeleted={includeDeleted}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>The id of the Enumeration.<br/><br/>
`[optional] boolean includeDeleted`
<br/>Parameter indicating whether to include soft-deleted Enumerations. If unspecified, a default value of false is used.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Enumeration](#schemaenumeration)|Success.|
|304|None|Not modified.|
|400|[AdhErrorResponse](#schemaadherrorresponse)|Missing or invalid inputs.|
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|
|404|[AdhErrorResponse](#schemaadherrorresponse)|Enumeration not found.|
|412|[AdhErrorResponse](#schemaadherrorresponse)|Precondition failed.|

<h4>Example response body</h4>

> 200 Response

```json
{
  "Id": "SimpleEnumeration",
  "Name": "SimpleEnumeration",
  "GraphQLName": "SimpleEnumeration",
  "Members": [
    {
      "Name": "ACTIVE",
      "GraphQLName": "ACTIVE",
      "Code": 0,
      "State": "Active",
      "Description": "This is an active state"
    },
    {
      "Name": "CLOSED",
      "GraphQLName": "CLOSED",
      "Code": 1,
      "State": "Active",
      "Description": "This is a closed state"
    }
  ],
  "Version": 1,
  "State": "Active",
  "CreatedDate": "0001-01-01T00:00:00Z",
  "ModifiedDate": "0001-01-01T00:00:00Z"
}
```

> 400 Response ([AdhErrorResponse](#schemaadherrorresponse))

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "property1": null,
  "property2": null
}
```

---

## `Get Or Create Enumeration`

<a id="opIdEnumerations_Get Or Create Enumeration"></a>

Creates a new Enumeration or returns the current one if the body is equivalent to what is stored. Response includes ETag header.

<h3>Request</h3>

```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations/{id}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>The id of the Enumeration.<br/><br/>

<h4>Request Body</h4>

An Enumeration.<br/>

```json
{
  "Id": "SimpleEnumeration",
  "Name": "SimpleEnumeration",
  "Members": [
    {
      "Name": "ACTIVE",
      "Code": 0
    },
    {
      "Name": "CLOSED",
      "Code": 1
    }
  ]
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Enumeration](#schemaenumeration)|Success.|
|201|[Enumeration](#schemaenumeration)|Created.|
|302|None|Found.|
|400|[AdhErrorResponse](#schemaadherrorresponse)|Missing or invalid inputs.|
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|
|409|[AdhErrorResponse](#schemaadherrorresponse)|Conflict.|

<h4>Example response body</h4>

> 200 Response

```json
{
  "Id": "SimpleEnumeration",
  "Name": "SimpleEnumeration",
  "GraphQLName": "SimpleEnumeration",
  "Members": [
    {
      "Name": "ACTIVE",
      "GraphQLName": "ACTIVE",
      "Code": 0,
      "State": "Active",
      "Description": "This is an active state"
    },
    {
      "Name": "CLOSED",
      "GraphQLName": "CLOSED",
      "Code": 1,
      "State": "Active",
      "Description": "This is a closed state"
    }
  ],
  "Version": 1,
  "State": "Active",
  "CreatedDate": "0001-01-01T00:00:00Z",
  "ModifiedDate": "0001-01-01T00:00:00Z"
}
```

> 201 Response

```json
{
  "Id": "SimpleEnumeration",
  "Name": "SimpleEnumeration",
  "GraphQLName": "SimpleEnumeration",
  "Members": [
    {
      "Name": "ACTIVE",
      "GraphQLName": "ACTIVE",
      "Code": 0,
      "State": "Active",
      "Description": "This is an active state"
    },
    {
      "Name": "CLOSED",
      "GraphQLName": "CLOSED",
      "Code": 1,
      "State": "Active",
      "Description": "This is a closed state"
    }
  ],
  "Version": 1,
  "State": "Active",
  "CreatedDate": "0001-01-01T00:00:00Z",
  "ModifiedDate": "0001-01-01T00:00:00Z"
}
```

> 400 Response ([AdhErrorResponse](#schemaadherrorresponse))

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "property1": null,
  "property2": null
}
```

---

## `Create Or Update Enumeration`

<a id="opIdEnumerations_Create Or Update Enumeration"></a>

Creates a new Enumeration or updates an existing and adds its Etag in the HTTP response header. The If-Match header is supported.

<h3>Request</h3>

```text 
PUT /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations/{id}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>The id of the Enumeration.<br/><br/>

<h4>Request Body</h4>

An Enumeration.<br/>

```json
{
  "Id": "SimpleEnumeration",
  "Name": "SimpleEnumeration",
  "Members": [
    {
      "Name": "ACTIVE",
      "Code": 0
    },
    {
      "Name": "CLOSED",
      "Code": 1
    }
  ]
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Enumeration](#schemaenumeration)|Success.|
|201|[Enumeration](#schemaenumeration)|Created.|
|400|[AdhErrorResponse](#schemaadherrorresponse)|Missing or invalid inputs.|
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|
|409|[AdhErrorResponse](#schemaadherrorresponse)|Conflict.|
|412|[AdhErrorResponse](#schemaadherrorresponse)|Precondition failed.|

<h4>Example response body</h4>

> 200 Response

```json
{
  "Id": "SimpleEnumeration",
  "Name": "SimpleEnumeration",
  "GraphQLName": "SimpleEnumeration",
  "Members": [
    {
      "Name": "ACTIVE",
      "GraphQLName": "ACTIVE",
      "Code": 0,
      "State": "Active",
      "Description": "This is an active state"
    },
    {
      "Name": "CLOSED",
      "GraphQLName": "CLOSED",
      "Code": 1,
      "State": "Active",
      "Description": "This is a closed state"
    }
  ],
  "Version": 1,
  "State": "Active",
  "CreatedDate": "0001-01-01T00:00:00Z",
  "ModifiedDate": "0001-01-01T00:00:00Z"
}
```

> 201 Response

```json
{
  "Id": "SimpleEnumeration",
  "Name": "SimpleEnumeration",
  "GraphQLName": "SimpleEnumeration",
  "Members": [
    {
      "Name": "ACTIVE",
      "GraphQLName": "ACTIVE",
      "Code": 0,
      "State": "Active",
      "Description": "This is an active state"
    },
    {
      "Name": "CLOSED",
      "GraphQLName": "CLOSED",
      "Code": 1,
      "State": "Active",
      "Description": "This is a closed state"
    }
  ],
  "Version": 1,
  "State": "Active",
  "CreatedDate": "0001-01-01T00:00:00Z",
  "ModifiedDate": "0001-01-01T00:00:00Z"
}
```

> 400 Response ([AdhErrorResponse](#schemaadherrorresponse))

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "property1": null,
  "property2": null
}
```

---

## `Delete Enumeration By Id`

<a id="opIdEnumerations_Delete Enumeration By Id"></a>

Deletes the Enumeration.

<h3>Request</h3>

```text 
DELETE /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations/{id}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>The id of the Enumeration.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|Deleted.|
|400|[AdhErrorResponse](#schemaadherrorresponse)|Missing or invalid inputs.|
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|
|404|[AdhErrorResponse](#schemaadherrorresponse)|Enumeration not found.|
|409|[AdhErrorResponse](#schemaadherrorresponse)|Conflict.|

---

## `Bulk Create Enumeration`

<a id="opIdEnumerations_Bulk Create Enumeration"></a>

Creates multiple new Enumeration and returns a list of any errors along with the created objects. Response includes ETag header.

<h3>Request</h3>

```text 
POST /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Bulk/Enumerations
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

<h4>Request Body</h4>

A list of Enumeration objects.<br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Enumeration](#schemaenumeration)|Success.|
|207|[MultiStatusResultOfEnumerationAndAdhErrorResponse](#schemamultistatusresultofenumerationandadherrorresponse)|Partial.|
|400|[AdhErrorResponse](#schemaadherrorresponse)|Missing or invalid inputs.|
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|
|409|[AdhErrorResponse](#schemaadherrorresponse)|Conflict.|

<h4>Example response body</h4>

> 200 Response

```json
{
  "Id": "SimpleEnumeration",
  "Name": "SimpleEnumeration",
  "GraphQLName": "SimpleEnumeration",
  "Members": [
    {
      "Name": "ACTIVE",
      "GraphQLName": "ACTIVE",
      "Code": 0,
      "State": "Active",
      "Description": "This is an active state"
    },
    {
      "Name": "CLOSED",
      "GraphQLName": "CLOSED",
      "Code": 1,
      "State": "Active",
      "Description": "This is a closed state"
    }
  ],
  "Version": 1,
  "State": "Active",
  "CreatedDate": "0001-01-01T00:00:00Z",
  "ModifiedDate": "0001-01-01T00:00:00Z"
}
```

> 207 Response ([MultiStatusResultOfEnumerationAndAdhErrorResponse](#schemamultistatusresultofenumerationandadherrorresponse))

```json
{
  "Reason": "string",
  "Error": "string",
  "OperationId": "string",
  "Data": [
    {
      "Id": "SimpleEnumeration",
      "Name": "SimpleEnumeration",
      "GraphQLName": "SimpleEnumeration",
      "Members": [
        {
          "Name": "ACTIVE",
          "GraphQLName": "ACTIVE",
          "Code": 0,
          "State": "Active",
          "Description": "This is an active state"
        },
        {
          "Name": "CLOSED",
          "GraphQLName": "CLOSED",
          "Code": 1,
          "State": "Active",
          "Description": "This is a closed state"
        }
      ],
      "Version": 1,
      "State": "Active",
      "CreatedDate": "0001-01-01T00:00:00Z",
      "ModifiedDate": "0001-01-01T00:00:00Z"
    }
  ],
  "ChildErrors": [
    {
      "OperationId": "string",
      "Error": "string",
      "Reason": "string",
      "Resolution": "string",
      "property1": null,
      "property2": null
    }
  ]
}
```

---

## `Bulk Delete Enumeration`

<a id="opIdEnumerations_Bulk Delete Enumeration"></a>

Deletes multiple Enumerations and returns an Ok if successful. In the case where a deletion is invalid, it will be added to a child errors list while the ones that were succesful will be returned in the data.

<h3>Request</h3>

```text 
DELETE /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Bulk/Enumerations
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

<h4>Request Body</h4>

A list of Enumeration object ids.<br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Enumeration](#schemaenumeration)[]|Success.|
|207|[MultiStatusResultOfEnumerationAndAdhErrorResponse](#schemamultistatusresultofenumerationandadherrorresponse)|Partial.|
|400|[AdhErrorResponse](#schemaadherrorresponse)|Missing or invalid inputs.|
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|
|409|[AdhErrorResponse](#schemaadherrorresponse)|Conflict.|

<h4>Example response body</h4>

> 200 Response

```json
[
  {
    "Id": "SimpleEnumeration",
    "Name": "SimpleEnumeration",
    "GraphQLName": "SimpleEnumeration",
    "Members": [
      {
        "Name": "ACTIVE",
        "GraphQLName": "ACTIVE",
        "Code": 0,
        "State": "Active",
        "Description": "This is an active state"
      },
      {
        "Name": "CLOSED",
        "GraphQLName": "CLOSED",
        "Code": 1,
        "State": "Active",
        "Description": "This is a closed state"
      }
    ],
    "Version": 1,
    "State": "Active",
    "CreatedDate": "0001-01-01T00:00:00Z",
    "ModifiedDate": "0001-01-01T00:00:00Z"
  },
  {
    "Id": "SimpleEnumeration",
    "Name": "SimpleEnumeration",
    "GraphQLName": "SimpleEnumeration",
    "Members": [
      {
        "Name": "ACTIVE",
        "GraphQLName": "ACTIVE",
        "Code": 0,
        "State": "Active",
        "Description": "This is an active state"
      },
      {
        "Name": "CLOSED",
        "GraphQLName": "CLOSED",
        "Code": 1,
        "State": "Active",
        "Description": "This is a closed state"
      }
    ],
    "Version": 1,
    "State": "Active",
    "CreatedDate": "0001-01-01T00:00:00Z",
    "ModifiedDate": "0001-01-01T00:00:00Z"
  }
]
```

> 207 Response ([MultiStatusResultOfEnumerationAndAdhErrorResponse](#schemamultistatusresultofenumerationandadherrorresponse))

```json
{
  "Reason": "string",
  "Error": "string",
  "OperationId": "string",
  "Data": [
    {
      "Id": "SimpleEnumeration",
      "Name": "SimpleEnumeration",
      "GraphQLName": "SimpleEnumeration",
      "Members": [
        {
          "Name": "ACTIVE",
          "GraphQLName": "ACTIVE",
          "Code": 0,
          "State": "Active",
          "Description": "This is an active state"
        },
        {
          "Name": "CLOSED",
          "GraphQLName": "CLOSED",
          "Code": 1,
          "State": "Active",
          "Description": "This is a closed state"
        }
      ],
      "Version": 1,
      "State": "Active",
      "CreatedDate": "0001-01-01T00:00:00Z",
      "ModifiedDate": "0001-01-01T00:00:00Z"
    }
  ],
  "ChildErrors": [
    {
      "OperationId": "string",
      "Error": "string",
      "Reason": "string",
      "Resolution": "string",
      "property1": null,
      "property2": null
    }
  ]
}
```

---

## `Get Enumeration Acl By Id`

<a id="opIdEnumerations_Get Enumeration Acl By Id"></a>

Returns the `AccessControlList` for the specified Enumeration.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations/{id}/AccessControl
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>The id of the Enumeration.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AccessControlList](#schemaaccesscontrollist)|Success.|
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|
|404|[AdhErrorResponse](#schemaadherrorresponse)|Enumeration not found.|

<h4>Example response body</h4>

> 200 Response ([AccessControlList](#schemaaccesscontrollist))

```json
{
  "RoleTrusteeAccessControlEntries": [
    {
      "Trustee": {
        "Type": 1,
        "ObjectId": "string",
        "TenantId": "string"
      },
      "AccessType": 0,
      "AccessRights": 0
    }
  ]
}
```

---

## `Update Enumeration Acl By Id`

<a id="opIdEnumerations_Update Enumeration Acl By Id"></a>

Updates and returns the `AccessControlList` for the specified Enumeration.

<h3>Request</h3>

```text 
PUT /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations/{id}/AccessControl
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>The id of the Enumeration.<br/><br/>

<h4>Request Body</h4>

An AccessControlList.<br/>

```json
{
  "RoleTrusteeAccessControlEntries": [
    {
      "Trustee": {
        "Type": 3,
        "ObjectId": "11111111-1111-1111-1111-111111111111"
      },
      "AccessRights": 3
    },
    {
      "Trustee": {
        "Type": 3,
        "ObjectId": "22222222-2222-2222-1111-111111111111"
      },
      "AccessRights": 15
    }
  ]
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[AccessControlList](#schemaaccesscontrollist)|Success.|
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|
|404|[AdhErrorResponse](#schemaadherrorresponse)|Enumeration not found.|

<h4>Example response body</h4>

> 200 Response ([AccessControlList](#schemaaccesscontrollist))

```json
{
  "RoleTrusteeAccessControlEntries": [
    {
      "Trustee": {
        "Type": 1,
        "ObjectId": "string",
        "TenantId": "string"
      },
      "AccessType": 0,
      "AccessRights": 0
    }
  ]
}
```

---

## `Get Enumeration Owner By Id`

<a id="opIdEnumerations_Get Enumeration Owner By Id"></a>

Returns the `Trustee` for the specified Enumeration.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations/{id}/Owner
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>The id of the Enumeration.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Trustee](#schematrustee)|Success.|
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|
|404|[AdhErrorResponse](#schemaadherrorresponse)|Enumeration not found.|

<h4>Example response body</h4>

> 200 Response ([Trustee](#schematrustee))

```json
{
  "Type": 1,
  "ObjectId": "string",
  "TenantId": "string"
}
```

---

## `Update Enumeration Owner By Id`

<a id="opIdEnumerations_Update Enumeration Owner By Id"></a>

Updates and returns the `Trustee` for the specified Enumeration.

<h3>Request</h3>

```text 
PUT /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations/{id}/Owner
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>The id of the Enumeration.<br/><br/>

<h4>Request Body</h4>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/common.yaml#owner<br/>

```json
{
  "Type": 1,
  "TenantId": "55555555-5555-5555-5555-555555555555",
  "ObjectId": "44444444-4444-4444-4444-444444444444"
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Trustee](#schematrustee)|Success.|
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|
|404|[AdhErrorResponse](#schemaadherrorresponse)|Enumeration not found.|

<h4>Example response body</h4>

> 200 Response ([Trustee](#schematrustee))

```json
{
  "Type": 1,
  "ObjectId": "string",
  "TenantId": "string"
}
```

---

## `List Enumeration Access Rights By Id`

<a id="opIdEnumerations_List Enumeration Access Rights By Id"></a>

Returns a list of `CommonAccessRights` for the specified Enumeration.

<h3>Request</h3>

```text 
GET /api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Enumerations/{id}/AccessRights
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string id`
<br/>The id of the Enumeration.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|Inline|Success.|
|403|[AdhErrorResponse](#schemaadherrorresponse)|Forbidden.|
|404|[AdhErrorResponse](#schemaadherrorresponse)|Enumeration not found.|

---
## Definitions

### Enumeration

<a id="schemaenumeration"></a>
<a id="schema_Enumeration"></a>
<a id="tocSenumeration"></a>
<a id="tocsenumeration"></a>

Represents an Enumeration object.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|The name of this object|
|GraphQLName|string|false|true|The name of this object as it appears in GraphQL|
|Version|int32|false|false|The current version number of this object|
|Id|string|false|true|The id which is used in lookup|
|State|[LifeCycleState](#schemalifecyclestate)|false|false|The lifecycle state of this object|
|CreatedDate|date-time|false|true|Date this object was created|
|ModifiedDate|date-time|false|true|The last time this object was modified|
|Description|string|false|true|Description of what this object is|
|Members|[[EnumerationState](#schemaenumerationstate)]|false|true|List of all the states the Enumeration can be in.|

```json
{
  "Id": "SimpleEnumeration",
  "Name": "SimpleEnumeration",
  "GraphQLName": "SimpleEnumeration",
  "Members": [
    {
      "Name": "ACTIVE",
      "GraphQLName": "ACTIVE",
      "Code": 0,
      "State": "Active",
      "Description": "This is an active state"
    },
    {
      "Name": "CLOSED",
      "GraphQLName": "CLOSED",
      "Code": 1,
      "State": "Active",
      "Description": "This is a closed state"
    }
  ],
  "Version": 1,
  "State": "Active",
  "CreatedDate": "0001-01-01T00:00:00Z",
  "ModifiedDate": "0001-01-01T00:00:00Z"
}

```

---

### LifeCycleState

<a id="schemalifecyclestate"></a>
<a id="schema_LifeCycleState"></a>
<a id="tocSlifecyclestate"></a>
<a id="tocslifecyclestate"></a>

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|Active|0|
|Deprecated|1|
|Deleted|2|

---

### EnumerationState

<a id="schemaenumerationstate"></a>
<a id="schema_EnumerationState"></a>
<a id="tocSenumerationstate"></a>
<a id="tocsenumerationstate"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|The name of this EnumerationState|
|GraphQLName|string|false|true|The name of this EnumerationState as it appears in GraphQL|
|Code|int32|false|false|The code the enumeration state is associated with. Must be non-negative and unique|
|State|[LifeCycleState](#schemalifecyclestate)|false|false|The lifecycle state of this EnumerationState|
|Description|string|false|true|Description of what this EnumerationState is for|

```json
{
  "Name": "string",
  "GraphQLName": "string",
  "Code": 0,
  "State": 0,
  "Description": "string"
}

```

---

### ErrorResponse

<a id="schemaadherrorresponse"></a>
<a id="schema_AdhErrorResponse"></a>
<a id="tocSadherrorresponse"></a>
<a id="tocsadherrorresponse"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|false|true|An optional unique string used to identify an operation|
|Error|string|false|true|Description of the error|
|Reason|string|false|true|Short blurb on why the error occured|
|Resolution|string|false|true|Short blurb on how to fix the error|

```json
{}

```

---

### MultiStatusResultOfEnumerationAndAdhErrorResponse

<a id="schemamultistatusresultofenumerationandadherrorresponse"></a>
<a id="schema_MultiStatusResultOfEnumerationAndAdhErrorResponse"></a>
<a id="tocSmultistatusresultofenumerationandadherrorresponse"></a>
<a id="tocsmultistatusresultofenumerationandadherrorresponse"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Reason|string|false|false|Short blurb on why the error occured|
|Error|string|false|false|Description of the error|
|OperationId|string|false|false|An optional unique string used to identify an operation|
|Data|[[Enumeration](#schemaenumeration)]|false|false|List of data returned from the multi-calls|
|ChildErrors|[[AdhErrorResponse](#schemaadherrorresponse)]|false|false|List of errors from all the multi-calls|

```json
{
  "Reason": "string",
  "Error": "string",
  "OperationId": "string",
  "Data": [
    {
      "Id": "SimpleEnumeration",
      "Name": "SimpleEnumeration",
      "GraphQLName": "SimpleEnumeration",
      "Members": [
        {
          "Name": "ACTIVE",
          "GraphQLName": "ACTIVE",
          "Code": 0,
          "State": "Active",
          "Description": "This is an active state"
        },
        {
          "Name": "CLOSED",
          "GraphQLName": "CLOSED",
          "Code": 1,
          "State": "Active",
          "Description": "This is a closed state"
        }
      ],
      "Version": 1,
      "State": "Active",
      "CreatedDate": "0001-01-01T00:00:00Z",
      "ModifiedDate": "0001-01-01T00:00:00Z"
    }
  ],
  "ChildErrors": [
    {
      "OperationId": "string",
      "Error": "string",
      "Reason": "string",
      "Resolution": "string",
      "property1": null,
      "property2": null
    }
  ]
}

```

---

### AccessControlList

<a id="schemaaccesscontrollist"></a>
<a id="schema_AccessControlList"></a>
<a id="tocSaccesscontrollist"></a>
<a id="tocsaccesscontrollist"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|RoleTrusteeAccessControlEntries|[[AccessControlEntry](#schemaaccesscontrolentry)]|false|true|None|

```json
{
  "RoleTrusteeAccessControlEntries": [
    {
      "Trustee": {
        "Type": 1,
        "ObjectId": "string",
        "TenantId": "string"
      },
      "AccessType": 0,
      "AccessRights": 0
    }
  ]
}

```

---

### AccessControlEntry

<a id="schemaaccesscontrolentry"></a>
<a id="schema_AccessControlEntry"></a>
<a id="tocSaccesscontrolentry"></a>
<a id="tocsaccesscontrolentry"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Trustee|[Trustee](#schematrustee)|false|true|None|
|AccessType|[AccessType](#schemaaccesstype)|false|false|None|
|AccessRights|int64|false|false|None|

```json
{
  "Trustee": {
    "Type": 1,
    "ObjectId": "string",
    "TenantId": "string"
  },
  "AccessType": 0,
  "AccessRights": 0
}

```

---

### Trustee

<a id="schematrustee"></a>
<a id="schema_Trustee"></a>
<a id="tocStrustee"></a>
<a id="tocstrustee"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Type|[TrusteeType](#schematrusteetype)|false|false|None|
|ObjectId|string|false|true|None|
|TenantId|string|false|true|None|

```json
{
  "Type": 1,
  "ObjectId": "string",
  "TenantId": "string"
}

```

---

### TrusteeType

<a id="schematrusteetype"></a>
<a id="schema_TrusteeType"></a>
<a id="tocStrusteetype"></a>
<a id="tocstrusteetype"></a>

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|User|1|
|Client|2|
|Role|3|

---

### AccessType

<a id="schemaaccesstype"></a>
<a id="schema_AccessType"></a>
<a id="tocSaccesstype"></a>
<a id="tocsaccesstype"></a>

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|Allowed|0|
|Denied|1|

---

