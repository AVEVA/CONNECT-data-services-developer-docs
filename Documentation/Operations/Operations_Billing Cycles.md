---
uid: operationsBilling Cycles
---

# Billing Cycles

APIs related to querying Billing Cycles


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

## `Get Tenant Billing Cycles`

Gets the billing cycles for an account inferred from the account's subscription.

### Request

`GET api/v1/tenants/{tenantId}/subscriptionterm/billingcycles`

### Parameters

```csharp
[Required]
string tenantId
```

Id of the Tenant

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
    "StartDate": "2020-03-18T16:25:40.8421026-07:00",
    "EndDate": "2020-03-18T16:25:40.8421844-07:00"
  },
  {
    "StartDate": "2020-03-18T16:25:40.8422556-07:00",
    "EndDate": "2020-03-18T16:25:40.8422575-07:00"
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

