---
uid: identityAzureActiveDirectoryTenantInformation
---

# AzureActiveDirectoryTenantInformation

APIs for creating, getting, updating, and deleting Azure Active Directory Tenant Information

## Properties

For HTTP requests and responses, the AzureActiveDirectoryTenantInformation object has the following properties and JSON-serialized body: 

Property | Type | Descriptions
 --- | --- | ---
Id | string | Id of entry
AzureActiveDirectoryTenantId | string | Azure Active Directory Tenant Id
TenantId | string | ID of Tenant the AzureActiveDirectoryTenantInformation belongs to.

### Serialized Model

```json
{
  "Id": "Id",
  "AzureActiveDirectoryTenantId": "AzureActiveDirectoryTenantId",
  "TenantId": "TenantId"
}
```

***

## `Add Azure Active Directory Tenant Information`

Add Azure Active Directory Tenant Information to a Tenant

### Request

`POST api/Tenants/{tenantId}/AzureActiveDirectoryTenantInformation/`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[FromBody]
[Required]
AzureActiveDirectoryTenantInformationDto azureActiveDirectoryTenantInformationDto
```

Azure Active Directory Tenant information to add

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 201

Created

##### Type:

 `AzureActiveDirectoryTenantInformationDto`

```json
{
  "TenantId": "TenantId"
}
```

#### 400

Missing or invalid inputs

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Tenant not found

#### 409

Azure Active Directory Tenant Id is already in use on the specified Tenant

#### 500

Internal server error
***

## `Get All Azure Active Directory Tenant Information`

Get all Azure Active Directory Tenant Information for a Tenant

### Request

`GET api/Tenants/{tenantId}/AzureActiveDirectoryTenantInformation/`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[FromQuery]
[Optional]
[Default = ""]
string query
```

Query to execute. Currently not supported

```csharp
[FromQuery]
[Optional]
[Default = 0]
int32 skip
```

Number of providers to skip.

```csharp
[FromQuery]
[Optional]
[Default = 100]
int32 count
```

Max number of providers to return

### Security

Allowed for these roles:

- `Account Administrator`
- `Cluster Operator`
- `Cluster Support`

### Returns

#### 200

Success

##### Type:

 `List[AzureActiveDirectoryTenantInformationDto]`

```json
[
  {
    "TenantId": "TenantId"
  },
  {
    "TenantId": "TenantId"
  }
]
```

#### 401

Unauthorized

#### 403

Forbidden

#### 403

Forbidden

#### 500

Internal server error
***

## `Get Azure Active Directory Tenant Information`

Remove Azure Active Directory Tenant Information from a tenant

### Request

`GET api/Tenants/{tenantId}/AzureActiveDirectoryTenantInformation/{azureActiveDirectoryTenantId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[FromQuery]
[Required]
string azureActiveDirectoryTenantId
```

Azure Active Directory Tenant Id to remove

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 200

Success

##### Type:

 `AzureActiveDirectoryTenantInformationDto`

```json
{
  "TenantId": "TenantId"
}
```

#### 400

Missing or invalid inputs

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Tenant not found

#### 500

Internal server error
***

## `Remove Azure Active Directory Tenant Information`

Remove Azure Active Directory Tenant Information from a tenant

### Request

`DELETE api/Tenants/{tenantId}/AzureActiveDirectoryTenantInformation/{azureActiveDirectoryTenantId}`

### Parameters

```csharp
[Required]
string tenantId
```

Id of tenant

```csharp
[FromQuery]
[Required]
string azureActiveDirectoryTenantId
```

Azure Active Directory Tenant Id to remove

### Security

Allowed for these roles:

- `Account Administrator`

### Returns

#### 204

Removed

#### 400

Missing or invalid inputs

#### 401

Unauthorized

#### 403

Forbidden

#### 404

Tenant not found

#### 500

Internal server error
***

