---
uid: DataViewsApi
---

# DataViews

APIs for working with Data Views

### Properties

Property | Type | Required | Descriptions
 --- | --- | --- | ---
Id | string | False | Id of the Data View
Name | string | False | Name of the Data View
Description | string | False | Description of the Data View
Queries | [QueryInfo] | True | A list of queries to select the data items to be displayed in the Data View
GroupRules | [GroupRule] | False | A list of group rules to organize data items into data groups
Mappings | Mappings | False | Defines the names of the columns and the stream properties that get mapped to them
IndexDataType | IndexDataType | True | Defines the index data type that index config uses
IndexConfig | IndexConfig | False | Defines the index information from which to retrieve data. Currently, only interpolation mode is supported



 ## `IndexDataType` 
 The IndexDataType can have the following values: 

Value | Type | Description
 --- | --- | ---
DateTime | string | Use DateTime as index type


***

## `Full Body Example` 
 ```json
{
  "Id": "DataViewDefinition_Id",
  "Name": "DataViewDefinition_Name",
  "Description": "DataViewDefinition_Description",
  "Queries": [
    {
      "Id": "pump",
      "Query": "id:*TestPump*"
    }
  ],
  "GroupRules": [
    {
      "Id": "DefaultGroupRule",
      "Type": "StreamName"
    }
  ],
  "Mappings": {
    "SharedMappingRules": [
      {
        "Id": "shared mapping rule",
        "Token": "{measurement}",
        "MappingRulePattern": {
          "PropertyPaths": [
            "Value"
          ],
          "ItemIdentifier": {
            "Resource": "Streams",
            "Field": "Id",
            "Value": "{measurement}",
            "Function": "Equals"
          }
        }
      }
    ],
    "Columns": [
      {
        "Name": "keyColumn",
        "MappingRule": {
          "PropertyPaths": [
            "path"
          ]
        },
        "IsKey": true,
        "DataType": "DateTime"
      },
      {
        "Name": "group rule",
        "MappingRule": {
          "GroupRuleId": "id",
          "GroupRuleToken": "token"
        },
        "IsKey": false,
        "DataType": "string"
      },
      {
        "Name": "column1",
        "MappingRule": {
          "PropertyPaths": [
            "path"
          ]
        },
        "IsKey": false
      },
      {
        "Name": "column2",
        "MappingRule": {
          "PropertyPaths": [
            "path"
          ],
          "ItemIdentifier": {
            "Resource": "Streams",
            "Field": "Id",
            "Value": "test",
            "Function": "Equals"
          }
        },
        "IsKey": false
      },
      {
        "Name": "column3",
        "MappingRule": {
          "SharedMappingRuleId": "shared mapping rule",
          "Token": "{measurement}"
        },
        "IsKey": false
      }
    ]
  },
  "IndexDataType": 0,
  "IndexConfig": {
    "StartIndex": "2018-01-01T00:00:00Z",
    "EndIndex": "2018-01-02T00:00:00Z",
    "Mode": "Interpolated",
    "Interval": "00:05:00"
  }
}
``` 

## `Get Data Views`

Get all created Data Views

### Request
`GET api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Skip:
```csharp
Int32 skip [FromQuery] [Required] [No Default Value]
```


Count:
```csharp
Int32 count [FromQuery] [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 200

OK - retrieved the Data Views (could be an empty array). Return type: [DataViewDefinition]

```json
[
{
  "Id": "String",
  "Name": "String",
  "Description": "String",
  "Queries": "[ QueryInfo object collection ]",
  "GroupRules": "[ GroupRule object collection ]",
  "Mappings": "Mappings object",
  "IndexDataType": "IndexDataType object",
  "IndexConfig": "IndexConfig object"
}
]
```

#### 400

Bad request


#### 500

Internal server error

***

## `Get Data View`

Get a Data View by id

### Request
`GET api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 200

OK - retrieved the Data View. Return type: DataViewDefinition

```json
{
  "Id": "String",
  "Name": "String",
  "Description": "String",
  "Queries": "[ QueryInfo object collection ]",
  "GroupRules": "[ GroupRule object collection ]",
  "Mappings": "Mappings object",
  "IndexDataType": "IndexDataType object",
  "IndexConfig": "IndexConfig object"
}
```

#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Create Data View`

Create a new Data View

### Request
`POST api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```

### Parameters from request body: 

DataViewDefinition object:
```csharp
DataViewDefinition dataViewDefinitionDto [FromBody] [Required] [No Default Value]
```

```json
{
  "Id": "String",
  "Name": "String",
  "Description": "String",
  "Queries": "[ QueryInfo object collection ]",
  "GroupRules": "[ GroupRule object collection ]",
  "Mappings": "Mappings object",
  "IndexDataType": "IndexDataType object",
  "IndexConfig": "IndexConfig object"
}
```

Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 201

Successfully created a Data View Definition. Return type: DataViewDefinition

```json
{
  "Id": "String",
  "Name": "String",
  "Description": "String",
  "Queries": "[ QueryInfo object collection ]",
  "GroupRules": "[ GroupRule object collection ]",
  "Mappings": "Mappings object",
  "IndexDataType": "IndexDataType object",
  "IndexConfig": "IndexConfig object"
}
```

#### 400

Bad request


#### 403

Unauthorized


#### 500

Internal server error

***

## `Create Data View With Id`

Create a new Data View

### Request
`POST api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

DataViewDefinition object:
```csharp
DataViewDefinition dataViewDefinitionDto [FromBody] [Required] [No Default Value]
```

```json
{
  "Id": "String",
  "Name": "String",
  "Description": "String",
  "Queries": "[ QueryInfo object collection ]",
  "GroupRules": "[ GroupRule object collection ]",
  "Mappings": "Mappings object",
  "IndexDataType": "IndexDataType object",
  "IndexConfig": "IndexConfig object"
}
```

Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 201

Successfully created a Data View Definition. Return type: DataViewDefinition

```json
{
  "Id": "String",
  "Name": "String",
  "Description": "String",
  "Queries": "[ QueryInfo object collection ]",
  "GroupRules": "[ GroupRule object collection ]",
  "Mappings": "Mappings object",
  "IndexDataType": "IndexDataType object",
  "IndexConfig": "IndexConfig object"
}
```

#### 400

Bad request


#### 403

Unauthorized


#### 409

Data View Definition with the specified Id already exists


#### 500

Internal server error

***

## `Create or Update Data View`

Edit the Data View with specified Id

### Request
`PUT api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

Updated DataViewDefinition object in the request body:
```csharp
DataViewDefinition dataViewDefinitionDto [FromBody] [Required] [No Default Value]
```

```json
{
  "Id": "String",
  "Name": "String",
  "Description": "String",
  "Queries": "[ QueryInfo object collection ]",
  "GroupRules": "[ GroupRule object collection ]",
  "Mappings": "Mappings object",
  "IndexDataType": "IndexDataType object",
  "IndexConfig": "IndexConfig object"
}
```

Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 204

Data View successfully created or updated


#### 400

Bad request


#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Delete Data View`

Delete the Data View with specified Id

### Request
`DELETE api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 204

Successfully deleted the Data View


#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Get Data View Access Control List`

Get the Data View Access Control List for Data View with specified Id

### Request
`GET api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/accesscontrol`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 200

OK - retrieved the Data View Access Control List.
                 See [Role-based access control](https://ocs-docs.osisoft.com/Documentation/Access_Control.html) for more information. Return type: AccessControlList

```json
{
  "RoleTrusteeAccessControlEntries": "[ AccessControlEntry object collection ]"
}
```

#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Get Data View Owner`

Get the Data View owner for Data View with specified Id

### Request
`GET api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/owner`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 200

OK - retrieved the Data View owner. Return type: Trustee

```json
{
  "Type": "TrusteeType object",
  "ObjectId": "String",
  "TenantId": "String"
}
```

#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Update Data View Access Control List`

Update the Data View Access Control List for Data View with specified Id

### Request
`PUT api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/accesscontrol`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

Updated Access Control List:
```csharp
AccessControlList acl [FromBody] [Required] [No Default Value]
```

```json
{
  "RoleTrusteeAccessControlEntries": "[ AccessControlEntry object collection ]"
}
```

Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 204

Successfully updated the Data View Access Control List


#### 400

Bad request


#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Update Data View Owner`

Update the Data View owner for Data View with specified Id

### Request
`PUT api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/owner`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

Updated owner:
```csharp
Trustee owner [FromBody] [Required] [No Default Value]
```

```json
{
  "Type": "TrusteeType object",
  "ObjectId": "String",
  "TenantId": "String"
}
```

Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 204

Successfully updated the Data View owner


#### 400

Bad request


#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Get Data View Name`

Get Data View name by Data View id

### Request
`GET api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/name`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 200

OK - retrieved the Data View name. Return type: String

```json
{}
```

#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Update Data View Name`

Edit Data View name specified by Data View id

### Request
`PUT api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/name`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

Updated name in the request body:
```csharp
string name [FromBody] [Required] [No Default Value]
```

```json
{}
```

Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 204

Successfully updated the Data View name


#### 400

Bad request


#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Get Data View Description`

Get Data View description by Data View id

### Request
`GET api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/description`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 200

OK - retrieved the Data View description. Return type: String

```json
{}
```

#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Update Data View Description`

Edit Data View description specified by Data View id

### Request
`PUT api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/description`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

Updated description in the request body:
```csharp
string description [FromBody] [Required] [No Default Value]
```

```json
{}
```

Cancellation cancellationToken:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 204

Successfully updated the Data View description


#### 400

Bad request


#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Delete Data View Description`

Delete Data View description specified by Data View id

### Request
`DELETE api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/description`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 204

Successfully deleted the Data View description


#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Get Data View Queries`

Get Data View queries by Data View id

### Request
`GET api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/queries`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 200

OK - retrieved the Data View queries. Return type: [QueryInfo]

```json
[
{
  "Id": "String",
  "NamespaceId": "String",
  "Query": "String"
}
]
```

#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Update Data View Queries`

Edit Data View queries specified by Data View id

### Request
`PUT api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/queries`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

Updated queries in the request body:
```csharp
[QueryInfo] queriesDto [FromBody] [Required] [No Default Value]
```

```json
[
{
  "Id": "String",
  "NamespaceId": "String",
  "Query": "String"
}
]
```

Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 204

Successfully updated the Data View queries


#### 400

Bad request


#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Get Data View Group Rules`

Get Data View group rules by Data View id

### Request
`GET api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/grouprules`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 200

OK - retrieved the Data View group rules. Return type: [GroupRule]

```json
[
{
  "Id": "String",
  "Type": "GroupRuleType object",
  "TokenRules": "TokenRules object"
}
]
```

#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Update Data View Group Rules`

Edit Data View group rules specified by Data View id

### Request
`PUT api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/grouprules`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

Updated group rules in the request body:
```csharp
[GroupRule] groupRulesDto [FromBody] [Required] [No Default Value]
```

```json
[
{
  "Id": "String",
  "Type": "GroupRuleType object",
  "TokenRules": "TokenRules object"
}
]
```

Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 204

Successfully updated the Data View group rules


#### 400

Bad request


#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Delete Data View Group Rules`

Delete Data View group rules specified by Data View id

### Request
`DELETE api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/grouprules`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 204

Successfully deleted the Data View group rules


#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Get Data View Mappings`

Get Data View mappings by Data View id

### Request
`GET api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/mappings`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 200

OK - retrieved the Data View mappings. Return type: Mappings

```json
{
  "SharedMappingRules": "[ SharedMappingRule object collection ]",
  "Columns": "[ Column object collection ]"
}
```

#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Update Data View Mappings`

Edit Data View mappings specified by Data View id

### Request
`PUT api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/mappings`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

Updated mappings in the request body:
```csharp
Mappings mappingsDto [FromBody] [Required] [No Default Value]
```

```json
{
  "SharedMappingRules": "[ SharedMappingRule object collection ]",
  "Columns": "[ Column object collection ]"
}
```

Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 204

Successfully updated the Data View mappings


#### 400

Bad request


#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Delete Data View Mappings`

Delete Data View mappings specified by Data View id

### Request
`DELETE api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/mappings`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 204

Successfully deleted the Data View mappings


#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Get Data View Index Data Type`

Get Data View index data type by Data View id

### Request
`GET api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/indexdatatype`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 200

OK - retrieved the Data View index data type. Return type: String

```json
{}
```

#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Update Data View Index Data Type`

Edit Data View index data type specified by Data View id

### Request
`PUT api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/indexdatatype`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

Updated index data type in the request body:
```csharp
IndexDataType indexDataTypeDto [FromBody] [Required] [No Default Value]
```

```json
{}
```

Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 204

Successfully updated the Data View index data type


#### 400

Bad request


#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Get Data View Index Config`

Get Data View index config by Data View id

### Request
`GET api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/indexconfig`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 200

OK - retrieved the Data View index config. Return type: IndexConfig

```json
{
  "StartIndex": "String",
  "EndIndex": "String",
  "Mode": "DataRetrievalMode object",
  "Interval": "String"
}
```

#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Update Data View Index Config`

Edit Data View index config specified by Data View id

### Request
`PUT api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/indexconfig`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

Updated index config in the request body:
```csharp
IndexConfig indexDto [FromBody] [Required] [No Default Value]
```

```json
{
  "StartIndex": "String",
  "EndIndex": "String",
  "Mode": "DataRetrievalMode object",
  "Interval": "String"
}
```

Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 204

Successfully updated the Data View index config


#### 400

Bad request


#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Delete Data View Index Config`

Delete Data View index config specified by Data View id

### Request
`DELETE api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/indexconfig`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 204

Successfully deleted the Data View index config


#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Preview Data View Data`

Get data preview based on created Data View definition

### Request
`GET api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/preview/interpolated`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Start index for the data:
```csharp
string startIndex [FromQuery] [Required] [No Default Value]
```


End index for the data:
```csharp
string endIndex [FromQuery] [Required] [No Default Value]
```


Data interval:
```csharp
string interval [FromQuery] [Required] [No Default Value]
```


Data form:
```csharp
string form [FromQuery] [Required] [No Default Value]
```


Max count of data points to retrieve:
```csharp
Int32 maxcount [FromQuery] [Optional] [Default = 1000]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 200

Successfully retrieved data. Return type: ContentResult

```json
Returns data formatted according to the user settings. Output formats: Default, Table, Tableh, Csv, Csvh
```

#### 400

Bad request


#### 403

Unauthorized


#### 404

Specified Data View Id not found


#### 500

Internal server error

***

## `Get Data View Data`

Get data from a specific session

### Request
`GET api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/data/interpolated`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Id of session:
```csharp
string sessionId [FromQuery] [Required] [No Default Value]
```


Form:
```csharp
string form [FromQuery] [Required] [No Default Value]
```


Skip:
```csharp
Int32 skip [FromQuery] [Required] [No Default Value]
```


Count:
```csharp
Int32 count [FromQuery] [Optional] [Default = 1000]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 200

Successfully retrieved data. Return type: ContentResult

```json
Returns data formatted according to the user settings. Output formats: Default, Table, Tableh, Csv, Csvh
```

#### 400

Bad request


#### 403

Unauthorized


#### 404

Specified Data View Id or session Id not found


#### 500

Internal server error

***

## `Get Data Groups`

Get data groups for a specified Data View

### Request
`GET api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/datagroups`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Skip:
```csharp
Int32 skip [FromQuery] [Required] [No Default Value]
```


Count:
```csharp
Int32 count [FromQuery] [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 200

Successfully retrieved data. Return type: DataGroupCollection

```json
{
  "Errors": "[ ErrorResponse object collection ]",
  "DataGroups": "[ DataGroup object collection ]"
}
```

#### 207

Multi-status. Look at response message. Return type: DataGroupCollection

```json
{
  "Errors": "[ ErrorResponse object collection ]",
  "DataGroups": "[ DataGroup object collection ]"
}
```

#### 403

Unauthorized


#### 404

Specified Data View Id not found


#### 500

Internal server error

***

## `Get Data Group`

Get a specific data group

### Request
`GET api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/dataGroups/{dataGroupId}`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Id of the data group:
```csharp
string dataGroupId  [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 200

Successfully retrieved data group. Return type: DataGroup

```json
{
  "Errors": "[ ErrorResponse object collection ]",
  "Tokens": "[ String object collection ]",
  "DataItems": "[ IDataItem object collection ]"
}
```

#### 403

Unauthorized


#### 404

Specified Data View Id not found


#### 500

Internal server error

***

## `Create Data View Session`

Create a session for a Data View

### Request
`POST api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/sessions`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

Session configuration object:
```csharp
SessionIndexAndTimeout sessionConfig [FromBody] [Required] [No Default Value]
```

```json
{
  "IndexConfig": "IndexConfig object",
  "SessionTimeout": "String"
}
```

Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 201

Successfully created a session. Return type: SessionInfo

```json
{
  "Id": "String",
  "Status": "SessionStatus object",
  "SessionTimeout": "String",
  "CreatedDate": "DateTime",
  "LastDataAccessTime": "DateTime",
  "DataViewDefinition": "DataViewDefinition object",
  "DataGroups": "DataGroupCollection object",
  "IdleTimeout": "TimeSpan"
}
```

#### 400

Bad request


#### 403

Unauthorized


#### 404

Specified Data View id not found


#### 500

Internal server error

***

## `Get Data View Session`

Get a specific session corresponding to a specific Data View

### Request
`GET api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/sessions/{sessionId}`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Session Id:
```csharp
string sessionId  [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 200

Successfully retrieved the session. Return type: SessionInfo

```json
{
  "Id": "String",
  "Status": "SessionStatus object",
  "SessionTimeout": "String",
  "CreatedDate": "DateTime",
  "LastDataAccessTime": "DateTime",
  "DataViewDefinition": "DataViewDefinition object",
  "DataGroups": "DataGroupCollection object",
  "IdleTimeout": "TimeSpan"
}
```

#### 403

Unauthorized


#### 404

Session or Data View not found


#### 500

Internal server error

***

## `Get Data View Sessions`

Get all sessions for a Data View

### Request
`GET api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/sessions`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 200

Successfully retrieved sessions. Return type: [SessionInfo]

```json
[
{
  "Id": "String",
  "Status": "SessionStatus object",
  "SessionTimeout": "String",
  "CreatedDate": "DateTime",
  "LastDataAccessTime": "DateTime",
  "DataViewDefinition": "DataViewDefinition object",
  "DataGroups": "DataGroupCollection object",
  "IdleTimeout": "TimeSpan"
}
]
```

#### 403

Unauthorized


#### 404

Specified Data View id not found


#### 500

Internal server error

***

## `Get Sessions`

Get all sessions for all Data Views

### Request
`GET api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/sessions`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 200

Successfully retrieved all sessions. Return type: [SessionInfo]

```json
[
{
  "Id": "String",
  "Status": "SessionStatus object",
  "SessionTimeout": "String",
  "CreatedDate": "DateTime",
  "LastDataAccessTime": "DateTime",
  "DataViewDefinition": "DataViewDefinition object",
  "DataGroups": "DataGroupCollection object",
  "IdleTimeout": "TimeSpan"
}
]
```

#### 500

Internal server error

***

## `Delete Data View Session`

Delete a specific session

### Request
`DELETE api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/sessions/{sessionId}`

### Parameters

Id of tenant:
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace:
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View:
```csharp
string id  [Required] [No Default Value]
```


Id of the session:
```csharp
string sessionId  [Required] [No Default Value]
```


Cancellation token:
```csharp
CancellationToken cancellationToken  [Optional] [Default = ""]
```


### Returns

#### 204

Successfully deleted session


#### 403

Unauthorized


#### 404

Session with specified Id not found


#### 500

Internal server error

***

