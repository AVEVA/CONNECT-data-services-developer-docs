---
uid: operationsUsage Data
---

# Usage Data

APIs related to querying Usage data.


***

## Authentication

All endpoints referenced in this documentation require authenticated access. Authorization header must be set to the access token you retrieve after a successful authentication request.

`Authorization: Bearer <token>`

Requests made without an access token or an invalid/expired token will fail with a 401 Unauthorized response.
Requests made with an access token which does not have the correct permissions (see security subsection on every endpoint) will fail with a 403 Forbidden.
Read [here](https://github.com/osisoft/OSI-Samples-OCS/tree/master/basic_samples/Authentication) on how to authenticate against OCS with the various clients and receive an access token in response.

## Error Handling

All responses will have an error message in the body. The exceptions are 200 responses and the 401 Unauthorized response. The error message will look as follows:

```json
{
    "OperationId": "1b2af18e-8b27-4f86-93e0-6caa3e59b90c", 
    "Error": "Error message.", 
    "Reason": "Reason that caused error.", 
    "Resolution": "Possible solution for the error." 
}
```

If and when contacting OSIsoft support about this error, please provide the OperationId.

## `Get Tenant Usage`

Gets **Tenant** usage data calculated based on active / 
            completed billing cycles, when the **start** and 
            **end** parameters are omitted. When **start** is 
            provided and **end** is omitted, a single day of usage data
            is returned. When both **start** and 
            **end** are provided, daily usage data is returned
            from the provided range.

### Request

`GET api/v1/tenants/{tenantId}/usage`

### Parameters

```csharp
[Required]
string tenantId
```

Id of the Tenant

```csharp
[FromQuery]
[Optional]
[Default = ""]
DateTime start
```

Start date of the usage for daily usage data.

```csharp
[FromQuery]
[Optional]
[Default = ""]
DateTime end
```

End date of the daily usage data, if there is no end date only one summary is returned

```csharp
[FromQuery]
[Optional]
[Default = False]
bool groupByNamespace
```

When **true** the usage data is grouped by namespaces.

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `List`

```json
[
  {
    "Date": "2020-03-18T16:25:40.2131413-07:00",
    "TenantId": "00000000-0000-0000-0000-000000000000",
    "NamespaceId": "Name",
    "ClusterRegion": 0,
    "IngressEvents": 0,
    "IngressStreamsAccessed": 0,
    "EgressEvents": 0,
    "EgressStreamsAccessed": 0
  },
  {
    "Date": "2020-03-18T16:25:40.2181075-07:00",
    "TenantId": "00000000-0000-0000-0000-000000000000",
    "NamespaceId": "Name",
    "ClusterRegion": 0,
    "IngressEvents": 0,
    "IngressStreamsAccessed": 0,
    "EgressEvents": 0,
    "EgressStreamsAccessed": 0
  }
]
```

#### 400

Missing or invalid inputs

#### 401

Unauthorized

#### 403

Forbidden

#### 500

Internal server error
***

## `Get Namespace Usage`

Gets **Namespace** usage data calculated based on active / 
            completed billing cycles, when the **start** and 
            **end** parameters are omitted. When **start** is 
            provided and **end** is omitted, a single day of usage data
            is returned. When both **start** and 
            **end** are provided, daily usage data is returned
            from the provided range.

### Request

`GET api/v1/tenants/{tenantId}/namespaces/{namespaceId}/usage`

### Parameters

```csharp
[Required]
string tenantId
```

Id of the Tenant

```csharp
[Required]
string namespaceId
```

Id of the Namespace

```csharp
[FromQuery]
[Optional]
[Default = ""]
DateTime start
```

Start date of the usage for daily usage data.

```csharp
[FromQuery]
[Optional]
[Default = ""]
DateTime end
```

End date of the daily usage data, if there is no end date only one summary is returned

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `List`

```json
[
  {
    "Date": "2020-03-18T16:25:40.8374653-07:00",
    "TenantId": "00000000-0000-0000-0000-000000000000",
    "NamespaceId": "Name",
    "ClusterRegion": 0,
    "IngressEvents": 0,
    "IngressStreamsAccessed": 0,
    "EgressEvents": 0,
    "EgressStreamsAccessed": 0
  },
  {
    "Date": "2020-03-18T16:25:40.8374769-07:00",
    "TenantId": "00000000-0000-0000-0000-000000000000",
    "NamespaceId": "Name",
    "ClusterRegion": 0,
    "IngressEvents": 0,
    "IngressStreamsAccessed": 0,
    "EgressEvents": 0,
    "EgressStreamsAccessed": 0
  }
]
```

#### 400

Missing or invalid inputs

#### 401

Unauthorized

#### 403

Forbidden

#### 500

Internal server error
***

