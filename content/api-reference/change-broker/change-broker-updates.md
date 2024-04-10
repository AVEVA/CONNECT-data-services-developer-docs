---
uid: change-broker-updates

---

# Updates
The Updates API allows users to retrieve updates for resources (for example, streams) in a specified Signup. This API is to be used after the signup Owner has successfully created a Signup using the Signups API. The signup Owner may begin a polling flow with this API by using the starter bookmark of an active Signup, provided through the Signups API (via GET /Signups/{signupId}).

## `Get Updates`

<a id="opIdUpdates_Get Updates"></a>

Returns a sequence of updates for all resources within the Signup, starting from the sequential marker represented by a provided `Bookmark`.

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/signups/{signupId}/updates
?bookmark={bookmark}
```

<h4>Parameters</h4>

`string tenantId`
<br/>The tenant identifier.<br/><br/>`string namespaceId`
<br/>The namespace identifier.<br/><br/>`string signupId`
<br/>The signup identifier.<br/><br/>`string bookmark`
<br/>An encoded token representing a sequential starting point from which users can retrieve updates for the current request. A starter Bookmark token appears in the response body of a successfully activated Signup.<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|string|Returns a sequence of updates. Absence of data for a successful response indicates that no new updates have arrived following the marker of the provided `Bookmark`, or that there is no data for the associated Signup.|
|400|None|Bad Request. The server could not understand the request due to malformed syntax. See response details for more information.|
|401|None|Unauthorized. The client is not authenticated.|
|403|None|Forbidden. The client is not authorized.|
|500|None|Internal Server Error. The server has encountered an error while processing the request.|

<h4>Example response body</h4>

> 200 Response

```json
{
  "data": [
    {
      "resourceId": "stream2",
      "operation": "Insert",
      "events": [
        {
          "Timestamp": "3/7/2024 12:00:00 AM",
          "Value": 12
        },
        {
          "Timestamp": "3/8/2024 12:00:00 AM",
          "Value": 53
        }
      ]
    },
    {
      "resourceId": "stream1",
      "operation": "Insert",
      "events": [
        {
          "Timestamp": "3/7/2024 12:00:00 AM",
          "Value": 234
        },
        {
          "Timestamp": "3/8/2024 12:00:00 AM",
          "Value": 7
        }
      ]
    },
    {
      "resourceId": "stream1",
      "operation": "Remove",
      "events": [
        {
          "Timestamp": "2024-03-07T00:00:00Z"
        }
      ]
    },
    {
      "resourceId": "stream2",
      "operation": "Update",
      "events": [
        {
          "Timestamp": "3/7/2024 12:00:00 AM",
          "Value": 121
        }
      ]
    }
  ],
  "bookmark": "H4sIAAAAAAAAChXEiQ2AMAwEwYKQ0dlxXtqggTxOFS6eoF1NyU_VZNusUw4LpCUqVVuDlHVP7dNkDheIEv5fkcalcb1DTJKLXEADnOGHEzz8foLRcKNaAAAA"
}
```