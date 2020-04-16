---
uid: identitySecret
---

# Secret

Secrets are used to authenticate both Client Credential clients and Hybrid clients.
            A Secret has an expiration date or can be created to never expire. We advise to avoid
            creating secrets that do not expire. After a Secret expires it can no longer be used
            to authenticate the Client. Any access token issued while a Secret is still valid will
            be active until the token itself expires. The same applies to refresh tokens, which are
            issued to Hybrid clients. Safe storage of secrets is your responsibility. OSIsoft Cloud Services
            does not store secret values, so once lost there is no way to retrieve the value of a Secret.

## Properties

For HTTP requests and responses, the Secret object has the following properties and JSON-serialized body: 

Property | Type | Description
 --- | --- | ---
Id | int32 | Gets or sets the Id for the secret. Note: This is currently an auto-incremented integer.
Description | string | Gets or sets the description.
Value | string | Gets or sets the value.
Expiration | DateTime | Gets or sets the expiration.
Type | string | Gets or sets the type of the client secret.

### Serialized Model

```json
{
  "Id": 0,
  "Description": "description",
  "Value": "Value",
  "Expiration": "2020-03-30T15:34:23.1822657-07:00",
  "Type": "Type"
}
```

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

## `Get Hybrid Client Secrets`

Get all secrets for a Hybrid Client.
            Total number of secrets in the Client
            set in the Total-Count header.

### Request

`GET api/v1/Tenants/{tenantId}/HybridClients/{clientId}/Secrets`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
string clientId
```

Id of Client.

```csharp
[FromQuery]
[Optional]
[Default = ""]
string query
```

Query to execute. Currently not supported.

```csharp
[FromQuery]
[Optional]
[Default = 0]
int32 skip
```

Number of clients to skip.

```csharp
[FromQuery]
[Optional]
[Default = 100]
int32 count
```

Maximum number of clients to return.

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success.

##### Type:

 `List`

```json
[
  {
    "Id": 0,
    "Expiration": "2020-03-30T15:34:23.188507-07:00",
    "Expires": false,
    "Description": "description"
  },
  {
    "Id": 0,
    "Expiration": "2020-03-30T15:34:23.1888317-07:00",
    "Expires": false,
    "Description": "description"
  }
]
```

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Client or Tenant not found.

#### 500

Internal server error.
***

## `Get Hybrid Client Secret`

Get a Hybrid Client Secret.

### Request

`GET api/v1/Tenants/{tenantId}/HybridClients/{clientId}/Secrets/{secretId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
string clientId
```

Id of Client.

```csharp
[Required]
int32 secretId
```

Id of Secret.

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success.

##### Type:

 `ClientSecret`

```json
{
  "Id": 0,
  "Expiration": "2020-03-30T15:34:23.1933632-07:00",
  "Expires": false,
  "Description": "description"
}
```

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Secret, Client, or Tenant not found.

#### 500

Internal server error.
***

## `Add Hybrid Client Secret`

Add a new secret to a Client Credential Client.
            A client can have a maximum of 10 secrets.
            We advise against creating secrets that do not expire.

### Request

`POST api/v1/Tenants/{tenantId}/HybridClients/{clientId}/Secrets`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
string clientId
```

Id of Client.

```csharp
[FromBody]
[Required]
ClientSecretCreateOrUpdate clientSecretCreateOrUpdate
```

ClientSecretCreateOrUpdate object.

Property | Type | Required | Description 
 --- | --- | --- | ---
Expiration | DateTime | No | Gets or sets expiration date for the client secret. Will be null if the secret does not expire.
Expires | bool | No | Gets or sets determines if the secret expires. Defaults to true.            If Expires is set to true (or null) and Expiration is not null, expiration of this secret will be enforced.            If Expires is set to true (or null) and Expiration is null, a 400 error will be returned.            If Expires is set to false and Expiration is not null, a 400 error will be returned.            If Expires is set to false and Expiration is null, there will be no expiration of this secret.
Description | string | No | Gets or sets description for the client secret. We suggest being as descriptive as possible. This field will make identifying            secrets easier.



```json
{
  "Expiration": "2020-03-30T15:34:23.1969711-07:00",
  "Expires": false,
  "Description": "description"
}
```

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 201

Created.

##### Type:

 `ClientSecretResponse`

```json
{
  "Secret": "Secret",
  "Id": 0,
  "Expiration": "2020-03-30T15:34:23.2004265-07:00",
  "Expires": false,
  "Description": "description"
}
```

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Client or Tenant not found.

#### 405

Method not allowed at this base URL. Try the request again at the Global base URL.

#### 408

Operation timed out.

#### 500

Internal server error.
***

## `Update Hybrid Client Secret`

Update a Hybrid Client Secret. It can take up to one hour for
            the update to manifest in the authentication process.

### Request

`PUT api/v1/Tenants/{tenantId}/HybridClients/{clientId}/Secrets/{secretId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
string clientId
```

Id of Client.

```csharp
[Required]
int32 secretId
```

Id of Secret.

```csharp
[FromBody]
[Required]
ClientSecretCreateOrUpdate clientSecretCreateOrUpdate
```

ClientSecretCreateOrUpdate object. Properties that are not set or are null will not be changed.

Property | Type | Required | Description 
 --- | --- | --- | ---
Expiration | DateTime | No | Gets or sets expiration date for the client secret. Will be null if the secret does not expire.
Expires | bool | No | Gets or sets determines if the secret expires. Defaults to true.            If Expires is set to true (or null) and Expiration is not null, expiration of this secret will be enforced.            If Expires is set to true (or null) and Expiration is null, a 400 error will be returned.            If Expires is set to false and Expiration is not null, a 400 error will be returned.            If Expires is set to false and Expiration is null, there will be no expiration of this secret.
Description | string | No | Gets or sets description for the client secret. We suggest being as descriptive as possible. This field will make identifying            secrets easier.



```json
{
  "Expiration": "2020-03-30T15:34:23.2055482-07:00",
  "Expires": false,
  "Description": "description"
}
```

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success.

##### Type:

 `ClientSecret`

```json
{
  "Id": 0,
  "Expiration": "2020-03-30T15:34:23.2057205-07:00",
  "Expires": false,
  "Description": "description"
}
```

#### 400

Missing or invalid inputs.

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Secret, Client, or Tenant not found.

#### 405

Method not allowed at this base URL. Try the request again at the Global base URL.

#### 408

Operation timed out.

#### 500

Internal server error.
***

## `Delete Hybrid Client Secret`

Delete a Secret from a Hybrid Client. It can take up to one hour for
            deletion to manifest in the authentication process.
            Access tokens issued using this Secret will be valid until their expiration.

### Request

`DELETE api/v1/Tenants/{tenantId}/HybridClients/{clientId}/Secrets/{secretId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
string clientId
```

Id of Client.

```csharp
[Required]
int32 secretId
```

Id of Secret.

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 204

Success.

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Secret, Client, or Tenant not found.

#### 405

Method not allowed at this base URL. Try the request again at the Global base URL.

#### 408

Operation timed out.

#### 500

Internal server error.
***

## `Get Header for Hybrid Client Secret`

Validate that a Secret with given Id exists in the Client.
            This endpoint is identical to the GET one but it does not
            return any objects in the body.

### Request

`HEAD api/v1/Tenants/{tenantId}/HybridClients/{clientId}/Secrets/{secretId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
string clientId
```

Id of Client.

```csharp
[Required]
int32 secretId
```

Id of Secret.

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success.

##### Type:

 `Void`

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Secret, Client, or Tenant not found.

#### 500

Internal server error.
***

## `Get Total Count of Hybrid Client Secrets`

Return total number of Secrets in a Hybrid Client. The value
            will be set in the Total-Count header. This endpoint
            is identical to the GET one but it does not return
            any objects in the body.

### Request

`HEAD api/v1/Tenants/{tenantId}/HybridClients/{clientId}/Secrets`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
string clientId
```

Id of Client.

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success.

##### Type:

 `Void`

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Client or Tenant not found.

#### 500

Internal server error.
***

## `Get Client Credential Client Secrets`

Get all secrets for a Client Credential Client.
            Total number of secrets in the Client set in the
            Total-Count header.

### Request

`GET api/v1/Tenants/{tenantId}/ClientCredentialClients/{clientId}/Secrets`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
string clientId
```

Id of Client.

```csharp
[FromQuery]
[Optional]
[Default = ""]
string query
```

Query to execute. Currently not supported.

```csharp
[FromQuery]
[Optional]
[Default = 0]
int32 skip
```

Number of clients to skip. From query.

```csharp
[FromQuery]
[Optional]
[Default = 100]
int32 count
```

Maximum number of clients to return.

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success.

##### Type:

 `List`

```json
[
  {
    "Id": 0,
    "Expiration": "2020-03-30T15:34:23.421257-07:00",
    "Expires": false,
    "Description": "description"
  },
  {
    "Id": 0,
    "Expiration": "2020-03-30T15:34:23.421273-07:00",
    "Expires": false,
    "Description": "description"
  }
]
```

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Client or Tenant not found.

#### 500

Internal server error.
***

## `Get Client Credential Client Secret`

Get a Client Credential Client Secret.

### Request

`GET api/v1/Tenants/{tenantId}/ClientCredentialClients/{clientId}/Secrets/{secretId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
string clientId
```

Id of Client.

```csharp
[Required]
int32 secretId
```

Id of Secret.

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success.

##### Type:

 `ClientSecret`

```json
{
  "Id": 0,
  "Expiration": "2020-03-30T15:34:23.423542-07:00",
  "Expires": false,
  "Description": "description"
}
```

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Secret, Client, or Tenant not found.

#### 500

Internal server error.
***

## `Add Client Credential Client Secret`

Add a new Secret to a Client Credential Client.
            A Client can have a maximum of 10 secrets.
            We advise against creating secrets that do not expire.

### Request

`POST api/v1/Tenants/{tenantId}/ClientCredentialClients/{clientId}/Secrets`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
string clientId
```

Id of Client.

```csharp
[FromBody]
[Required]
ClientSecretCreateOrUpdate clientSecretCreateOrUpdate
```

ClientSecretCreateOrUpdate object.

Property | Type | Required | Description 
 --- | --- | --- | ---
Expiration | DateTime | No | Gets or sets expiration date for the client secret. Will be null if the secret does not expire.
Expires | bool | No | Gets or sets determines if the secret expires. Defaults to true.            If Expires is set to true (or null) and Expiration is not null, expiration of this secret will be enforced.            If Expires is set to true (or null) and Expiration is null, a 400 error will be returned.            If Expires is set to false and Expiration is not null, a 400 error will be returned.            If Expires is set to false and Expiration is null, there will be no expiration of this secret.
Description | string | No | Gets or sets description for the client secret. We suggest being as descriptive as possible. This field will make identifying            secrets easier.



```json
{
  "Expiration": "2020-03-30T15:34:23.4255715-07:00",
  "Expires": false,
  "Description": "description"
}
```

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 201

Created.

##### Type:

 `ClientSecretResponse`

```json
{
  "Secret": "Secret",
  "Id": 0,
  "Expiration": "2020-03-30T15:34:23.4256863-07:00",
  "Expires": false,
  "Description": "description"
}
```

#### 400

Missing or invalid inputs.

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Client or Tenant not found.

#### 405

Method not allowed at this base URL. Try the request again at the Global base URL.

#### 408

Operation timed out.

#### 500

Internal server error.
***

## `Update Client Credential Client Secret`

Update a Client Credential Client Secret.
            It can take up to one hour for the update
            to manifest in the authentication process.

### Request

`PUT api/v1/Tenants/{tenantId}/ClientCredentialClients/{clientId}/Secrets/{secretId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
string clientId
```

Id of Client.

```csharp
[Required]
int32 secretId
```

Id of Secret.

```csharp
[FromBody]
[Required]
ClientSecretCreateOrUpdate clientSecretCreateOrUpdate
```

ClientSecretCreateOrUpdate object. Properties that are not set or are null will not be changed.

Property | Type | Required | Description 
 --- | --- | --- | ---
Expiration | DateTime | No | Gets or sets expiration date for the client secret. Will be null if the secret does not expire.
Expires | bool | No | Gets or sets determines if the secret expires. Defaults to true.            If Expires is set to true (or null) and Expiration is not null, expiration of this secret will be enforced.            If Expires is set to true (or null) and Expiration is null, a 400 error will be returned.            If Expires is set to false and Expiration is not null, a 400 error will be returned.            If Expires is set to false and Expiration is null, there will be no expiration of this secret.
Description | string | No | Gets or sets description for the client secret. We suggest being as descriptive as possible. This field will make identifying            secrets easier.



```json
{
  "Expiration": "2020-03-30T15:34:23.4279471-07:00",
  "Expires": false,
  "Description": "description"
}
```

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success.

##### Type:

 `ClientSecret`

```json
{
  "Id": 0,
  "Expiration": "2020-03-30T15:34:23.4280505-07:00",
  "Expires": false,
  "Description": "description"
}
```

#### 400

Missing or invalid inputs.

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Secret, Client, or Tenant not found.

#### 405

Method not allowed at this base URL. Try the request again at the Global base URL.

#### 408

Operation timed out.

#### 500

Internal server error.
***

## `Delete Client Credential Client Secret`

Delete a Secret from a Client Credential Client.
            It can take up to one hour for deletion to manifest
            in the authentication process. Access tokens issued
            using this Secret will be valid until their expiration.

### Request

`DELETE api/v1/Tenants/{tenantId}/ClientCredentialClients/{clientId}/Secrets/{secretId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
string clientId
```

Id of Client.

```csharp
[Required]
int32 secretId
```

Id of Secret.

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 204

Success.

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Secret, Client, or Tenant not found.

#### 405

Method not allowed at this base URL. Try the request again at the Global base URL.

#### 408

Operation timed out.

#### 500

Internal server error.
***

## `Get Header for Client Credential Client Secret`

Validate that a Secret with given Id exists in the Client.
            This endpoint is identical to the GET one but it does not
            return any objects in the body.

### Request

`HEAD api/v1/Tenants/{tenantId}/ClientCredentialClients/{clientId}/Secrets/{secretId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
string clientId
```

Id of Client.

```csharp
[Required]
int32 secretId
```

Id of Secret.

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success.

##### Type:

 `Void`

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Secret, Client, or Tenant not found.

#### 500

Internal server error.
***

## `Get Total Count of Client Credential Client Secrets`

Return total number of Secrets in a Client. The value
            will be set in the Total-Count header. This endpoint
            is identical to the GET one but it does not return
            any objects in the body.

### Request

`HEAD api/v1/Tenants/{tenantId}/ClientCredentialClients/{clientId}/Secrets`

### Parameters

```csharp
[Required]
string tenantId
```

Id of Tenant.

```csharp
[Required]
string clientId
```

Id of Client.

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success.

##### Type:

 `Void`

#### 401

Unauthorized.

#### 403

Forbidden.

#### 404

Client or Tenant not found.

#### 500

Internal server error.
***

