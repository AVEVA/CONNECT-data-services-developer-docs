---
uid: streaming-updates-updates

---

# Updates
The Updates API allows users to retrieve updates for resources (for example, streams) in a specified Signup. This API is to be used after the user has successfully created a Signup using the Signups API. The user may begin a polling flow with this API by using the starter request URI provided in the 'Get-Updates' response header through the Signups API.

## `Get Updates`

<a id="opIdUpdates_Get Updates"></a>

Returns a sequence of updates for all resources within the Signup, starting from the sequential marker represented by a provided `Bookmark`.

<h3>Request</h3>

```text 
GET /api/v1-preview/tenants/{tenantId}/namespaces/{namespaceId}/signups/{signupId}/updates
?bookmark={bookmark}
```

<h4>Parameters</h4>

`string tenantId`
<br/>The tenant identifier.<br/><br/>`string namespaceId`
<br/>The namespace identifier.<br/><br/>`string signupId`
<br/>The signup identifier.<br/><br/>`string bookmark`
<br/>An encoded token representing a sequential starting point from which updates are to be retrieved for the current request. A request URI including a starter Bookmark token is provided in the 'Get-Updates' header of a successful Signup activation response.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|string|Returns a sequence of updates. Absence of data for a successful response indicates that no new updates have arrived following the marker of the provided `Bookmark`, or that there is no data for the associated Signup.|
|400|None|Bad Request. The server could not understand the request due to malformed syntax. See response details for more information.|
|401|None|Unauthorized. The client is not authenticated.|
|403|None|Forbidden. The client is not authorized.|
|500|None|Internal Server Error. The server has encountered an error while processing the request.|

<h4>Response Headers</h4>

|Status|Header|Type|Description|
|---|---|---|---|
|200|Next-Request|string|A request URI including an encoded token to be used in the subsequent request to retrieve the next sequence of updates.|

