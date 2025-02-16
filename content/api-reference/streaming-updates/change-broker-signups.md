---
uid: change-broker-signups

---

# Signups
The Signups API allows users to create, update, view, and delete signups. Signups allow for the user who creates the Signup, the owner, to subscribe resources (for example, streams) to a signup and receive all 'change data' updates from the resources.

## `Get All Signups`

<a id="opIdSignupManager_Get All Signups"></a>

Gets all signups in a tenant's namespace.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/signups
?skip={skip}&count={count}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>
`[optional] integer skip`
<br/>Parameter representing the zero-based offset of the first signup to retrieve. If unspecified, a default value of 0 is used.<br/><br/>`[optional] integer count`
<br/>Parameter representing the maximum number of signups to retrieve. If unspecified, a default value of 100 is used.<br/><br/>

<h4>Request Headers</h4>

|Header|Type|Required|Description|
|---|---|---|---|
|Community-Id|string|false|Community unique identifier. Must be provided to retrieve signups containing resources shared in a community.|

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[SignupCollection](#schemasignupcollection)|Returns the signups for the tenant. This is a collection containing a list of `Signup` objects.|
|400|None|Bad request.|
|403|None|Forbidden. The client does not have the required permissions to make the request.|
|500|None|Internal Server Error. The server has encountered a situation it doesn't know how to handle.|

<h4>Response Headers</h4>

|Status|Header|Type|Description|
|---|---|---|---|
|200|Total-Count|integer|Total number of signups.|

<h4>Example response body</h4>

> 200 Response

```json
{
  "Signups": [
    {
      "Id": "string",
      "Name": "string",
      "Owner": {
        "Type": 1,
        "ObjectId": "string",
        "TenantId": "string"
      },
      "CommunityId": "string",
      "Type": "Stream",
      "CreatedDate": "2019-08-24T14:15:22Z",
      "ModifiedDate": "2019-08-24T14:15:22Z",
      "SignupState": "Activating"
    },
    {
      "Id": "string",
      "Name": "string",
      "Owner": {
        "Type": 1,
        "ObjectId": "string",
        "TenantId": "string"
      },
      "CommunityId": "string",
      "Type": "Stream",
      "CreatedDate": "2019-08-24T14:15:22Z",
      "ModifiedDate": "2019-08-24T14:15:22Z",
      "SignupState": "Active"
    },
    {
      "Id": "string",
      "Name": "string",
      "Owner": {
        "Type": 1,
        "ObjectId": "string",
        "TenantId": "string"
      },
      "CommunityId": "string",
      "Type": "Stream",
      "CreatedDate": "2019-08-24T14:15:22Z",
      "ModifiedDate": "2019-08-24T14:15:22Z",
      "ExpiredDate": "2019-09-24T14:15:22Z",
      "SignupState": "Expired"
    }
  ]
}
```

---

## `Create Signup`

<a id="opIdSignupManager_Create Signup"></a>

Creates a signup for the list of resource identifiers provided. Upon creating your signup, it will be placed in the Activating `SignupState`. It is essential to invoke GetSignupById while your signup is in this Activating `SignupState`. Note that invoking GetSignupById will change the signup's `SignupState` from Activating to Active only when the background setup process is finished.

<h3>Request</h3>

```text 
POST /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/signups
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>

<h4>Request Headers</h4>

|Header|Type|Required|Description|
|---|---|---|---|
|Community-Id|string|false|Community unique identifier. Represents a signup for resources shared to the specified Community Id. Must be provided if the signup contains shared resources.|

<h4>Request Body</h4>

CreateSignupInput. Input of the signup to be created.<br/>

```json
{
  "Name": "string",
  "ResourceType": "Stream",
  "ResourceIds": [
    "string"
  ]
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|202|[Signup](#schemasignup)|Accepted. Background services are validating access permission to resources.|
|400|None|Bad request.|
|403|None|Forbidden. The client does not have the required permissions to make the request.|
|500|None|The server has encountered a situation it doesn't know how to handle.|

<h4>Example response body</h4>

> 202 Response

```json
{
  "Id": "string",
  "Name": "string",
  "Owner": {
    "Type": "Client",
    "ObjectId": "string",
    "TenantId": "string"
  },
  "CommunityId": "string",
  "Type": "Stream",
  "CreatedDate": "2019-08-24T14:15:22Z",
  "ModifiedDate": "2019-08-24T14:15:22Z",
  "SignupState": "Activating"
}
```

---

## `Get Signup By Id`

<a id="opIdSignupManager_Get Signup By Id"></a>

Retrieves a signup by signup identifier.

**Notes**: Each signup includes a `SignupState` that describes its current status. To set your signup to a `SignupState` of `Active`, you must invoke this route while the `SignupState` is `Activating`. This route can only activate your signup after the background setup process completes, so retries may be required if the signup response is still in a `SignupState` of `Activating`.

All `SignupState`s are accompanied by a separate property of `ModifiedDate`, which indicates the date and time of the most recent modification to the signup, such as changing its properties by invoking the [Update Signup](#update-signup) route, updating a signup's resource subscriptions, or when the signup's `SignupState` changes.

Based on the returned `SignupState` value, the response may include additional properties, which are described below:

* `Activating`: Includes an empty `Bookmark`.
* `Active`: Includes an encoded `Bookmark` that can be used to retrieve change data updates from subscribed resources.
* `Expired`: Includes an empty `Bookmark` and an additional `ExpiredDate` timestamp. Expired signups cannot be reactivated.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/signups/{signupId}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string signupId`
<br/>Signup unique identifier.<br/><br/>

<h4>Request Headers</h4>

|Header|Type|Required|Description|
|---|---|---|---|
|Community-Id|string|false|Community unique identifier. Must be provided to retrieve a signup containing resources shared through a community.|

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[SignupWithBookmark](#schemasignupwithbookmark)|Success. Returns the signup.|
|400|None|Bad request.|
|403|None|Forbidden. The client does not have the required permissions to make the request.|
|404|None|Not Found.|
|500|None|The server has encountered a situation it doesn't know how to handle.|

<h4>Example response body</h4>

> 200 Response

```json
{
  "Bookmark": "string",
  "Id": "string",
  "Name": "string",
  "Owner": {
    "Type": "Client",
    "ObjectId": "string",
    "TenantId": "string"
  },
  "CommunityId": "string",
  "Type": "Stream",
  "CreatedDate": "2019-08-24T14:15:22Z",
  "ModifiedDate": "2019-08-24T14:15:22Z",
  "SignupState": "Active"
}
```

---

## `Update Signup`

<a id="opIdSignupManager_Update Signup"></a>

Updates the properties (for example, name) of a signup.

<h3>Request</h3>

```text 
PUT /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/signups/{signupId}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string signupId`
<br/>Signup unique identifier.<br/><br/>

<h4>Request Headers</h4>

|Header|Type|Required|Description|
|---|---|---|---|
|Community-Id|string|false|Community unique identifier. Must be provided if the signup contains resources shared in a community.|

<h4>Request Body</h4>

UpdateSignupInput. Signup input object to replace the existing signup's properties.<br/>

```json
{
  "Name": "string"
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Signup](#schemasignup)|Success. Signup updated.|
|400|None|Bad request.|
|403|None|Forbidden. The client does not have the required permissions to make the request.|
|404|None|Not Found.|
|500|None|The server has encountered a situation it doesn't know how to handle.|

<h4>Example response body</h4>

> 200 Response

```json
{
  "Id": "string",
  "Name": "string",
  "Owner": {
    "Type": "Client",
    "ObjectId": "string",
    "TenantId": "string"
  },
  "CommunityId": "string",
  "Type": "Stream",
  "CreatedDate": "2019-08-24T14:15:22Z",
  "ModifiedDate": "2019-08-24T14:15:22Z",
  "SignupState": "Active"
}
```

---

## `Delete Signup`

<a id="opIdSignupManager_Delete Signup"></a>

Deletes a signup.

<h3>Request</h3>

```text 
DELETE /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/signups/{signupId}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string signupId`
<br/>Signup unique identifier.<br/><br/>

<h4>Request Headers</h4>

|Header|Type|Required|Description|
|---|---|---|---|
|Community-Id|string|false|Community unique identifier. Must be provided to delete a signup containing shared resources..|

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|No content. Signup was successfully deleted.|
|400|None|Bad request.|
|403|None|Forbidden. The client does not have the required permissions to make the request.|
|404|None|Not Found.|
|500|None|The server has encountered a situation it doesn't know how to handle.|

---

## `Get Signup Owner By Id`

<a id="opIdSignupManager_Get Signup Owner By Id"></a>

Retrieves the trustee (owner) of a signup.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/signups/{signupId}/owner
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string signupId`
<br/>Signup unique identifier.<br/><br/>

<h4>Request Headers</h4>

|Header|Type|Required|Description|
|---|---|---|---|
|Community-Id|string|false|Community unique identifier. Must be provided if the signup contains shared resources.|

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Trustee](#schematrustee)|Success. Returns the signup owner identifier.|
|400|None|Bad request.|
|403|None|Forbidden. The client does not have the required permissions to make the request.|
|404|None|Not Found.|
|500|None|The server has encountered a situation it doesn't know how to handle.|

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

## `Get Signup Resources`

<a id="opIdSignupManager_Get Signup Resources"></a>

Retrieves a list of the signup's resources.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/signups/{signupId}/resources
?skip={skip}&count={count}&resourceFilter={resourceFilter}
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string signupId`
<br/>Signup unique identifier.<br/><br/>
`[optional] integer skip`
<br/>Parameter representing the zero-based offset of the first resource to retrieve. If unspecified, a default value of 0 is used.<br/><br/>`[optional] integer count`
<br/>Maximum number of signup resources to be returned. If unspecified, a default value of 100 is used.<br/><br/>`[optional] any resourceFilter`
<br/>`SignupResourceFilter`. Specifies the accessibility of resources to be returned. If unspecified, all resources will be returned.<br/><br/>

<h4>Request Headers</h4>

|Header|Type|Required|Description|
|---|---|---|---|
|Community-Id|string|false|Community unique identifier. Must be provided if the signup contains shared resources.|

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[SignupResources](#schemasignupresources)|Ok. Returns the signup's resources.|
|400|None|Bad request.|
|403|None|Forbidden. The client does not have the required permissions to make the request.|
|404|None|Not Found.|
|500|None|The server has encountered a situation it doesn't know how to handle.|

<h4>Response Headers</h4>

|Status|Header|Type|Description|
|---|---|---|---|
|200|Total-Count|integer|Total number of signup resources.|

<h4>Example response body</h4>

> 200 Response ([SignupResources](#schemasignupresources))

```json
{
  "Resources": [
    {
      "ResourceId": "string",
      "IsAccessible": true
    }
  ]
}
```

---

## `Update Signup Resources`

<a id="opIdSignupManager_Update Signup Resources"></a>

Subscribes and/or unsubscribes resources to an Active Signup.

<h3>Request</h3>

```text 
POST /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/signups/{signupId}/resources
```

<h4>Parameters</h4>

`string tenantId`
<br/><br/>`string namespaceId`
<br/><br/>`string signupId`
<br/>Signup unique identifier.<br/><br/>

<h4>Request Headers</h4>

|Header|Type|Required|Description|
|---|---|---|---|
|Community-Id|string|false|Unique Community Identifier. Must be provided in order to add or remove shared resources.|

<h4>Request Body</h4>

SignupResourcesInput. Signup resources input object to replace signup's resources.<br/>

```json
{
  "ResourcesToAdd": [
    "string"
  ],
  "ResourcesToRemove": [
    "string"
  ]
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|202|None|Accepted. Background services are validating access permission to added resources.|
|207|[SignupInvalidResources](#schemasignupinvalidresources)|Multistatus response if some resources to be updated were invalid or failed.|
|400|None|Bad request.|
|403|None|Forbidden. The client does not have the required permissions to make the request.|
|404|None|Not Found.|
|500|None|The server has encountered a situation it doesn't know how to handle.|

<h4>Example response body</h4>

> 207 Response ([SignupInvalidResources](#schemasignupinvalidresources))

```json
{
  "InvalidResourcesToRemove": [
    "string"
  ],
  "FailedResourceIds": [
    "string"
  ]
}
```

---
## Definitions

### Signup

<a id="schemasignup"></a>
<a id="schema_Signup"></a>
<a id="tocSsignup"></a>
<a id="tocssignup"></a>

Represents a signup base model.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|true|false|Signup Identifier.|
|Name|string|true|false|Signup Name.|
|Owner|[Trustee](#schematrustee)|true|false|Signup Owner.|
|CommunityId|string|false|true|Community Identifier Associated with Signup.|
|Type|[ResourceType](#schemaresourcetype)|true|false|Signup Resource Type.|
|CreatedDate|date-time|true|false|Date Signup was Created.|
|ModifiedDate|date-time|true|false|Date Signup was Last Modified.|
|ExpiredDate|date-time|false|true|Date Signup was expired. Signups expire after 24 hours of inactivity.|
|SignupState|[SignupState](#schemasignupstate)|true|false|Signup Status.|

```json
{
  "Id": "string",
  "Name": "string",
  "Owner": {
    "Type": "Client",
    "ObjectId": "string",
    "TenantId": "string"
  },
  "CommunityId": "string",
  "Type": "Stream",
  "CreatedDate": "2019-08-24T14:15:22Z",
  "ModifiedDate": "2019-08-24T14:15:22Z",
  "SignupState": "Active"
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

### ResourceType

<a id="schemaresourcetype"></a>
<a id="schema_ResourceType"></a>
<a id="tocSresourcetype"></a>
<a id="tocsresourcetype"></a>

The resource type.

<h4>Enumerated Values</h4>

|Property|Value|Description|
|---|---|---|
|Stream|Stream|Stream resource.|

---

### SignupState

<a id="schemasignupstate"></a>
<a id="schema_SignupState"></a>
<a id="tocSsignupstate"></a>
<a id="tocssignupstate"></a>

Signup Status.

<h4>Enumerated Values</h4>

|Property|Value|Description|
|---|---|---|
|Activating|Activating|Signup is being activated.|
|Active|Active|Signup is active.|
|Expired|Expired|Signup is expired.|
|Failed|Failed|Signup is failed.|

---

### CreateSignupInput

<a id="schemacreatesignupinput"></a>
<a id="schema_CreateSignupInput"></a>
<a id="tocScreatesignupinput"></a>
<a id="tocscreatesignupinput"></a>

The CreateSignupInput object.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|false|true|Signup Name.|
|ResourceType|[ResourceType](#schemaresourcetype)|true|false|Resource type of the resource identifiers.|
|ResourceIds|string[]|true|false|Collection of resource identifiers.|

```json
{
  "Name": "string",
  "ResourceType": "Stream",
  "ResourceIds": [
    "string"
  ]
}

```

---

### SignupCollection

<a id="schemasignupcollection"></a>
<a id="schema_SignupCollection"></a>
<a id="tocSsignupcollection"></a>
<a id="tocssignupcollection"></a>

A collection of signups.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Signups|[[Signup](#schemasignup)]|true|false|Collection of signups.|

```json
{
  "Signups": [
    {
      "Id": "string",
      "Name": "string",
      "Owner": {
        "Type": 1,
        "ObjectId": "string",
        "TenantId": "string"
      },
      "CommunityId": "string",
      "Type": "Stream",
      "CreatedDate": "2019-08-24T14:15:22Z",
      "ModifiedDate": "2019-08-24T14:15:22Z",
      "SignupState": "Active"
    }
  ]
}

```

---

### SignupWithBookmark

<a id="schemasignupwithbookmark"></a>
<a id="schema_SignupWithBookmark"></a>
<a id="tocSsignupwithbookmark"></a>
<a id="tocssignupwithbookmark"></a>

Represents a signup model with encoded bookmark.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|true|false|Signup Identifier.|
|Name|string|true|false|Signup Name.|
|Owner|[Trustee](#schematrustee)|true|false|Signup Owner.|
|CommunityId|string|false|true|Community Identifier Associated with Signup.|
|Type|[ResourceType](#schemaresourcetype)|true|false|Signup Resource Type.|
|CreatedDate|date-time|true|false|Date Signup was Created.|
|ModifiedDate|date-time|true|false|Date Signup was Last Modified.|
|ExpiredDate|date-time|false|true|Date Signup was expired. Signups expire after 24 hours of inactivity.|
|SignupState|[SignupState](#schemasignupstate)|true|false|Signup Status.|
|Bookmark|string|true|false|An encoded string representing a starting point for updates retrieval. Bookmarks expire after 1 hour.|

```json
{
  "Bookmark": "string",
  "Id": "string",
  "Name": "string",
  "Owner": {
    "Type": "Client",
    "ObjectId": "string",
    "TenantId": "string"
  },
  "CommunityId": "string",
  "Type": "Stream",
  "CreatedDate": "2019-08-24T14:15:22Z",
  "ModifiedDate": "2019-08-24T14:15:22Z",
  "SignupState": "Active"
}

```

---

### UpdateSignupInput

<a id="schemaupdatesignupinput"></a>
<a id="schema_UpdateSignupInput"></a>
<a id="tocSupdatesignupinput"></a>
<a id="tocsupdatesignupinput"></a>

The UpdateSignupInput object.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Name|string|true|false|Signup name to be updated.|

```json
{
  "Name": "string"
}

```

---

### SignupResources

<a id="schemasignupresources"></a>
<a id="schema_SignupResources"></a>
<a id="tocSsignupresources"></a>
<a id="tocssignupresources"></a>

A model that holds lists of recources retrieved from signup.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Resources|[[SignupResource](#schemasignupresource)]|true|false|Collection of resources from a signup.|

```json
{
  "Resources": [
    {
      "ResourceId": "string",
      "IsAccessible": true
    }
  ]
}

```

---

### SignupResource

<a id="schemasignupresource"></a>
<a id="schema_SignupResource"></a>
<a id="tocSsignupresource"></a>
<a id="tocssignupresource"></a>

A model that holds a signup resource.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|ResourceId|string|true|false|Resource Identifier.|
|IsAccessible|boolean|true|false|Boolean indicating if resource is accessible or inaccessible.|

```json
{
  "ResourceId": "string",
  "IsAccessible": true
}

```

---

### SignupResourceFilter

<a id="schemasignupresourcefilter"></a>
<a id="schema_SignupResourceFilter"></a>
<a id="tocSsignupresourcefilter"></a>
<a id="tocssignupresourcefilter"></a>

Filter to be applied to Signup Resources.

<h4>Enumerated Values</h4>

|Property|Value|Description|
|---|---|---|
|Inaccessible|Inaccessible|Returns inaccessible signup resources.|
|Accessible|Accessible|Returns accessible signup resources.|
|All|All|Returns accessible and inaccessible signup resources.|

---

### SignupInvalidResources

<a id="schemasignupinvalidresources"></a>
<a id="schema_SignupInvalidResources"></a>
<a id="tocSsignupinvalidresources"></a>
<a id="tocssignupinvalidresources"></a>

The SignupInvalidResources object.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|InvalidResourcesToRemove|string[]|false|false|Invalid resources to remove that were not subscribed to the signup.|
|FailedResourceIds|string[]|false|true|Failed resources that could not be added or removed.|

```json
{
  "InvalidResourcesToRemove": [
    "string"
  ],
  "FailedResourceIds": [
    "string"
  ]
}

```

---

### SignupResourcesInput

<a id="schemasignupresourcesinput"></a>
<a id="schema_SignupResourcesInput"></a>
<a id="tocSsignupresourcesinput"></a>
<a id="tocssignupresourcesinput"></a>

The SignupResourcesInput object.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|ResourcesToAdd|string[]|true|false|Signup resources to be added.|
|ResourcesToRemove|string[]|true|false|Signup resources to be removed.|

```json
{
  "ResourcesToAdd": [
    "string"
  ],
  "ResourcesToRemove": [
    "string"
  ]
}

```

---

