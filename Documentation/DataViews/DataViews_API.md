---
uid: DataViewsApi
---

# DataViews

APIs for Working with Data Views

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

***

## `Get Data Views`

Get all created Data Views

### Request
`GET api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/`

### Parameters

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


The number of data views to skip
```csharp
Int32 skip [FromQuery] [Optional] [Default = 0]
```


The number of data views to display per page. Maximum count allowed is 1000
```csharp
Int32 count [FromQuery] [Optional] [Default = 100]
```


### Returns

#### 200

OK - retrieved the Data Views (could be an empty array)

```json
[
{
  "Id": "String",
  "Name": "String",
  "Description": "String",
  "Queries": [
    {
      "Id": "String",
      "Query": "String"
    }
  ],
  "GroupRules": [
    {
      "Id": "String",
      "GroupRuleType": "GroupRuleType enumeration",
      "TokenRules": {
        "Tokens": [
          {
            "Chars": "Char",
            "Length": "Int32"
          }
        ],
        "Patterns": [
          {
            "QueryId": "String",
            "Name": "String",
            "Value": "String"
          }
        ]
      }
    }
  ],
  "Mappings": {
    "TimeOfResolution": "DateTimeOffset",
    "SharedMappingRules": [
      {
        "Id": "String",
        "Token": "String",
        "MappingRulePattern": {
          "PropertyPaths": [
            {
              "Chars": "Char",
              "Length": "Int32"
            }
          ],
          "ItemIdentifier": {
            "FilterResource": "FilterResource enumeration",
            "FilterField": "FilterField enumeration",
            "Name": "String",
            "Value": "String",
            "FilterFunction": "FilterFunction enumeration"
          }
        }
      }
    ],
    "Columns": [
      {
        "Name": "String",
        "MappingRule": {},
        "IsKey": "Boolean",
        "DataType": "String"
      }
    ]
  },
  "IndexDataType": "IndexDataType enumeration",
  "IndexConfig": {
    "StartIndex": "String",
    "EndIndex": "String",
    "DataRetrievalMode": "DataRetrievalMode enumeration",
    "Interval": "String"
  }
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

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```


### Returns

#### 200

OK - retrieved the Data View

```json
{
  "Id": "String",
  "Name": "String",
  "Description": "String",
  "Queries": [
    {
      "Id": "String",
      "Query": "String"
    }
  ],
  "GroupRules": [
    {
      "Id": "String",
      "GroupRuleType": "GroupRuleType enumeration",
      "TokenRules": {
        "Tokens": [
          {
            "Chars": "Char",
            "Length": "Int32"
          }
        ],
        "Patterns": [
          {
            "QueryId": "String",
            "Name": "String",
            "Value": "String"
          }
        ]
      }
    }
  ],
  "Mappings": {
    "TimeOfResolution": "DateTimeOffset",
    "SharedMappingRules": [
      {
        "Id": "String",
        "Token": "String",
        "MappingRulePattern": {
          "PropertyPaths": [
            {
              "Chars": "Char",
              "Length": "Int32"
            }
          ],
          "ItemIdentifier": {
            "FilterResource": "FilterResource enumeration",
            "FilterField": "FilterField enumeration",
            "Name": "String",
            "Value": "String",
            "FilterFunction": "FilterFunction enumeration"
          }
        }
      }
    ],
    "Columns": [
      {
        "Name": "String",
        "MappingRule": {},
        "IsKey": "Boolean",
        "DataType": "String"
      }
    ]
  },
  "IndexDataType": "IndexDataType enumeration",
  "IndexConfig": {
    "StartIndex": "String",
    "EndIndex": "String",
    "DataRetrievalMode": "DataRetrievalMode enumeration",
    "Interval": "String"
  }
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

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```

### Parameters from request body: 

DataViewDefinition object
```csharp
DataViewDefinition dataViewDefinitionDto [FromBody] [Required] [No Default Value]
```

```json
{
  "Id": "String",
  "Name": "String",
  "Description": "String",
  "Queries": [
    {
      "Id": "String",
      "Query": "String"
    }
  ],
  "GroupRules": [
    {
      "Id": "String",
      "GroupRuleType": "GroupRuleType enumeration",
      "TokenRules": {
        "Tokens": [
          {
            "Chars": "Char",
            "Length": "Int32"
          }
        ],
        "Patterns": [
          {
            "QueryId": "String",
            "Name": "String",
            "Value": "String"
          }
        ]
      }
    }
  ],
  "Mappings": {
    "TimeOfResolution": "DateTimeOffset",
    "SharedMappingRules": [
      {
        "Id": "String",
        "Token": "String",
        "MappingRulePattern": {
          "PropertyPaths": [
            {
              "Chars": "Char",
              "Length": "Int32"
            }
          ],
          "ItemIdentifier": {
            "FilterResource": "FilterResource enumeration",
            "FilterField": "FilterField enumeration",
            "Name": "String",
            "Value": "String",
            "FilterFunction": "FilterFunction enumeration"
          }
        }
      }
    ],
    "Columns": [
      {
        "Name": "String",
        "MappingRule": {},
        "IsKey": "Boolean",
        "DataType": "String"
      }
    ]
  },
  "IndexDataType": "IndexDataType enumeration",
  "IndexConfig": {
    "StartIndex": "String",
    "EndIndex": "String",
    "DataRetrievalMode": "DataRetrievalMode enumeration",
    "Interval": "String"
  }
}
```

### Returns

#### 201

Successfully created a Data View Definition

```json
{
  "Id": "String",
  "Name": "String",
  "Description": "String",
  "Queries": [
    {
      "Id": "String",
      "Query": "String"
    }
  ],
  "GroupRules": [
    {
      "Id": "String",
      "GroupRuleType": "GroupRuleType enumeration",
      "TokenRules": {
        "Tokens": [
          {
            "Chars": "Char",
            "Length": "Int32"
          }
        ],
        "Patterns": [
          {
            "QueryId": "String",
            "Name": "String",
            "Value": "String"
          }
        ]
      }
    }
  ],
  "Mappings": {
    "TimeOfResolution": "DateTimeOffset",
    "SharedMappingRules": [
      {
        "Id": "String",
        "Token": "String",
        "MappingRulePattern": {
          "PropertyPaths": [
            {
              "Chars": "Char",
              "Length": "Int32"
            }
          ],
          "ItemIdentifier": {
            "FilterResource": "FilterResource enumeration",
            "FilterField": "FilterField enumeration",
            "Name": "String",
            "Value": "String",
            "FilterFunction": "FilterFunction enumeration"
          }
        }
      }
    ],
    "Columns": [
      {
        "Name": "String",
        "MappingRule": {},
        "IsKey": "Boolean",
        "DataType": "String"
      }
    ]
  },
  "IndexDataType": "IndexDataType enumeration",
  "IndexConfig": {
    "StartIndex": "String",
    "EndIndex": "String",
    "DataRetrievalMode": "DataRetrievalMode enumeration",
    "Interval": "String"
  }
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

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

DataViewDefinition object
```csharp
DataViewDefinition dataViewDefinitionDto [FromBody] [Required] [No Default Value]
```

```json
{
  "Id": "String",
  "Name": "String",
  "Description": "String",
  "Queries": [
    {
      "Id": "String",
      "Query": "String"
    }
  ],
  "GroupRules": [
    {
      "Id": "String",
      "GroupRuleType": "GroupRuleType enumeration",
      "TokenRules": {
        "Tokens": [
          {
            "Chars": "Char",
            "Length": "Int32"
          }
        ],
        "Patterns": [
          {
            "QueryId": "String",
            "Name": "String",
            "Value": "String"
          }
        ]
      }
    }
  ],
  "Mappings": {
    "TimeOfResolution": "DateTimeOffset",
    "SharedMappingRules": [
      {
        "Id": "String",
        "Token": "String",
        "MappingRulePattern": {
          "PropertyPaths": [
            {
              "Chars": "Char",
              "Length": "Int32"
            }
          ],
          "ItemIdentifier": {
            "FilterResource": "FilterResource enumeration",
            "FilterField": "FilterField enumeration",
            "Name": "String",
            "Value": "String",
            "FilterFunction": "FilterFunction enumeration"
          }
        }
      }
    ],
    "Columns": [
      {
        "Name": "String",
        "MappingRule": {},
        "IsKey": "Boolean",
        "DataType": "String"
      }
    ]
  },
  "IndexDataType": "IndexDataType enumeration",
  "IndexConfig": {
    "StartIndex": "String",
    "EndIndex": "String",
    "DataRetrievalMode": "DataRetrievalMode enumeration",
    "Interval": "String"
  }
}
```

### Returns

#### 201

Successfully created a Data View Definition

```json
{
  "Id": "String",
  "Name": "String",
  "Description": "String",
  "Queries": [
    {
      "Id": "String",
      "Query": "String"
    }
  ],
  "GroupRules": [
    {
      "Id": "String",
      "GroupRuleType": "GroupRuleType enumeration",
      "TokenRules": {
        "Tokens": [
          {
            "Chars": "Char",
            "Length": "Int32"
          }
        ],
        "Patterns": [
          {
            "QueryId": "String",
            "Name": "String",
            "Value": "String"
          }
        ]
      }
    }
  ],
  "Mappings": {
    "TimeOfResolution": "DateTimeOffset",
    "SharedMappingRules": [
      {
        "Id": "String",
        "Token": "String",
        "MappingRulePattern": {
          "PropertyPaths": [
            {
              "Chars": "Char",
              "Length": "Int32"
            }
          ],
          "ItemIdentifier": {
            "FilterResource": "FilterResource enumeration",
            "FilterField": "FilterField enumeration",
            "Name": "String",
            "Value": "String",
            "FilterFunction": "FilterFunction enumeration"
          }
        }
      }
    ],
    "Columns": [
      {
        "Name": "String",
        "MappingRule": {},
        "IsKey": "Boolean",
        "DataType": "String"
      }
    ]
  },
  "IndexDataType": "IndexDataType enumeration",
  "IndexConfig": {
    "StartIndex": "String",
    "EndIndex": "String",
    "DataRetrievalMode": "DataRetrievalMode enumeration",
    "Interval": "String"
  }
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

Update the Data View with specified Id

### Request
`PUT api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}`

### Parameters

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

Updated DataViewDefinition object in the request body
```csharp
DataViewDefinition dataViewDefinitionDto [FromBody] [Required] [No Default Value]
```

```json
{
  "Id": "String",
  "Name": "String",
  "Description": "String",
  "Queries": [
    {
      "Id": "String",
      "Query": "String"
    }
  ],
  "GroupRules": [
    {
      "Id": "String",
      "GroupRuleType": "GroupRuleType enumeration",
      "TokenRules": {
        "Tokens": [
          {
            "Chars": "Char",
            "Length": "Int32"
          }
        ],
        "Patterns": [
          {
            "QueryId": "String",
            "Name": "String",
            "Value": "String"
          }
        ]
      }
    }
  ],
  "Mappings": {
    "TimeOfResolution": "DateTimeOffset",
    "SharedMappingRules": [
      {
        "Id": "String",
        "Token": "String",
        "MappingRulePattern": {
          "PropertyPaths": [
            {
              "Chars": "Char",
              "Length": "Int32"
            }
          ],
          "ItemIdentifier": {
            "FilterResource": "FilterResource enumeration",
            "FilterField": "FilterField enumeration",
            "Name": "String",
            "Value": "String",
            "FilterFunction": "FilterFunction enumeration"
          }
        }
      }
    ],
    "Columns": [
      {
        "Name": "String",
        "MappingRule": {},
        "IsKey": "Boolean",
        "DataType": "String"
      }
    ]
  },
  "IndexDataType": "IndexDataType enumeration",
  "IndexConfig": {
    "StartIndex": "String",
    "EndIndex": "String",
    "DataRetrievalMode": "DataRetrievalMode enumeration",
    "Interval": "String"
  }
}
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

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
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

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```


### Returns

#### 200

OK - retrieved the Data View Access Control List.
                 See [Role-based access control](https://ocs-docs.osisoft.com/Documentation/Access_Control.html) for more information

```json
{
  "RoleTrusteeAccessControlEntries": [
    {
      "Trustee": {
        "TrusteeType": "TrusteeType enumeration",
        "ObjectId": "String",
        "TenantId": "String"
      },
      "AccessType": "AccessType enumeration",
      "AccessRights": "UInt64"
    }
  ]
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

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```


### Returns

#### 200

OK - retrieved the Data View owner

```json
{
  "TrusteeType": "TrusteeType enumeration",
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

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

Updated Access Control List
```csharp
AccessControlList acl [FromBody] [Required] [No Default Value]
```

```json
{
  "RoleTrusteeAccessControlEntries": [
    {
      "Trustee": {
        "TrusteeType": "TrusteeType enumeration",
        "ObjectId": "String",
        "TenantId": "String"
      },
      "AccessType": "AccessType enumeration",
      "AccessRights": "UInt64"
    }
  ]
}
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

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

Updated owner
```csharp
Trustee owner [FromBody] [Required] [No Default Value]
```

```json
{
  "TrusteeType": "TrusteeType enumeration",
  "ObjectId": "String",
  "TenantId": "String"
}
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

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```


### Returns

#### 200

OK - retrieved the Data View name

```json
{
  "Chars": "Char",
  "Length": "Int32"
}
```

#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Update Data View Name`

Update Data View name specified by Data View id

### Request
`PUT api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/name`

### Parameters

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

Updated name in the request body
```csharp
string name [FromBody] [Required] [No Default Value]
```

```json
{
  "Chars": "Char",
  "Length": "Int32"
}
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

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```


### Returns

#### 200

OK - retrieved the Data View description

```json
{
  "Chars": "Char",
  "Length": "Int32"
}
```

#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Update Data View Description`

Update Data View description specified by Data View id

### Request
`PUT api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/description`

### Parameters

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

Updated description in the request body
```csharp
string description [FromBody] [Required] [No Default Value]
```

```json
{
  "Chars": "Char",
  "Length": "Int32"
}
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

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
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

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```


### Returns

#### 200

OK - retrieved the Data View queries

```json
[
{
  "Id": "String",
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

Update Data View queries specified by Data View id

### Request
`PUT api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/queries`

### Parameters

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

Updated queries in the request body
```csharp
[QueryInfo] queriesDto [FromBody] [Required] [No Default Value]
```

```json
[
{
  "Id": "String",
  "Query": "String"
}
]
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

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```


### Returns

#### 200

OK - retrieved the Data View group rules

```json
[
{
  "Id": "String",
  "GroupRuleType": "GroupRuleType enumeration",
  "TokenRules": {
    "Tokens": [
      {
        "Chars": "Char",
        "Length": "Int32"
      }
    ],
    "Patterns": [
      {
        "QueryId": "String",
        "Name": "String",
        "Value": "String"
      }
    ]
  }
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

Update Data View group rules specified by Data View id

### Request
`PUT api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/grouprules`

### Parameters

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

Updated group rules in the request body
```csharp
[GroupRule] groupRulesDto [FromBody] [Required] [No Default Value]
```

```json
[
{
  "Id": "String",
  "GroupRuleType": "GroupRuleType enumeration",
  "TokenRules": {
    "Tokens": [
      {
        "Chars": "Char",
        "Length": "Int32"
      }
    ],
    "Patterns": [
      {
        "QueryId": "String",
        "Name": "String",
        "Value": "String"
      }
    ]
  }
}
]
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

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
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

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```


### Returns

#### 200

OK - retrieved the Data View mappings

```json
{
  "TimeOfResolution": "DateTimeOffset",
  "SharedMappingRules": [
    {
      "Id": "String",
      "Token": "String",
      "MappingRulePattern": {
        "PropertyPaths": [
          {
            "Chars": "Char",
            "Length": "Int32"
          }
        ],
        "ItemIdentifier": {
          "FilterResource": "FilterResource enumeration",
          "FilterField": "FilterField enumeration",
          "Name": "String",
          "Value": "String",
          "FilterFunction": "FilterFunction enumeration"
        }
      }
    }
  ],
  "Columns": [
    {
      "Name": "String",
      "MappingRule": {},
      "IsKey": "Boolean",
      "DataType": "String"
    }
  ]
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

Update Data View mappings specified by Data View id

### Request
`PUT api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/mappings`

### Parameters

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

Updated mappings in the request body
```csharp
Mappings mappingsDto [FromBody] [Required] [No Default Value]
```

```json
{
  "TimeOfResolution": "DateTimeOffset",
  "SharedMappingRules": [
    {
      "Id": "String",
      "Token": "String",
      "MappingRulePattern": {
        "PropertyPaths": [
          {
            "Chars": "Char",
            "Length": "Int32"
          }
        ],
        "ItemIdentifier": {
          "FilterResource": "FilterResource enumeration",
          "FilterField": "FilterField enumeration",
          "Name": "String",
          "Value": "String",
          "FilterFunction": "FilterFunction enumeration"
        }
      }
    }
  ],
  "Columns": [
    {
      "Name": "String",
      "MappingRule": {},
      "IsKey": "Boolean",
      "DataType": "String"
    }
  ]
}
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

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
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

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```


### Returns

#### 200

OK - retrieved the Data View index data type

```json
{
  "Chars": "Char",
  "Length": "Int32"
}
```

#### 403

Unauthorized


#### 404

Specified Data View not found


#### 500

Internal server error

***

## `Update Data View Index Data Type`

Update Data View index data type specified by Data View id

### Request
`PUT api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/indexdatatype`

### Parameters

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

Updated index data type in the request body
```csharp
IndexDataType indexDataTypeDto [FromBody] [Required] [No Default Value]
```

```json
{}
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

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```


### Returns

#### 200

OK - retrieved the Data View index config

```json
{
  "StartIndex": "String",
  "EndIndex": "String",
  "DataRetrievalMode": "DataRetrievalMode enumeration",
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

Update Data View index config specified by Data View id

### Request
`PUT api/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}/indexconfig`

### Parameters

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```

### Parameters from request body: 

Updated index config in the request body
```csharp
IndexConfig indexDto [FromBody] [Required] [No Default Value]
```

```json
{
  "StartIndex": "String",
  "EndIndex": "String",
  "DataRetrievalMode": "DataRetrievalMode enumeration",
  "Interval": "String"
}
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

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
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

Id of tenant
```csharp
string tenantId  [Required] [No Default Value]
```


Id of namespace
```csharp
string namespaceId  [Required] [No Default Value]
```


Id of Data View
```csharp
string id  [Required] [No Default Value]
```


Start index for the data
```csharp
string startIndex [FromQuery] [Required] [No Default Value]
```


End index for the data
```csharp
string endIndex [FromQuery] [Required] [No Default Value]
```


Data interval
```csharp
string interval [FromQuery] [Required] [No Default Value]
```


Data form
```csharp
string form [FromQuery] [Required] [No Default Value]
```


Optional, default is **preserve**. Using **refresh** causes Data View backing resources to be refreshed. See [Retrieving Data](#DataRetrieval)
```csharp
string cache [FromQuery] [Optional] [Default = "refresh"]
```


Max count of data points to retrieve
```csharp
Int32 maxCount [FromQuery] [Optional] [Default = 1000]
```


### Returns

#### 200

Successfully retrieved data

```json

Time,Temperature,Flowrate,Volume
2018-01-01T00:00:00Z,24,44,245
2018-01-01T00:00:01Z,24,44,245
2018-01-01T00:00:02Z,24,44,245
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

