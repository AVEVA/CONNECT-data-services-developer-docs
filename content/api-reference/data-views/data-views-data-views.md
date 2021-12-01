---
uid: data-views-data-views

---

# Data Views
#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-summaries.yaml#class-dataviewscontroller

## `List Data Views`

<a id="opIdDataViews_List Data Views"></a>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-summaries.yaml#dataviews-get

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/dataviews
?skip={skip}&count={count}
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#tenantId<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#namespaceId<br/><br/>
`[optional] integer skip`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-parameters.yaml#skip-dataviews<br/><br/>`[optional] integer count`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-parameters.yaml#count-dataviews<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[DataView](#schemadataview)[]|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#200-dataviews-get|
|500|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#500-standard-message|

<h4>Response Headers</h4>

|Status|Header|Type|Description|
|---|---|---|---|
|200|Total-Count|integer|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-headers.yaml#total-count-dataviews|
|200|Link|string|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-headers.yaml#link-standard-message|
|200|Next-Page|string|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-headers.yaml#next-page-standard-message|
|200|First-Page|string|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-headers.yaml#first-page-standard-message|

<h4>Example response body</h4>

> 200 Response

```json
null
```

> 500 Response ([ErrorResponse](#schemaerrorresponse))

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  },
  "ChildErrors": {
    "property1": null,
    "property2": null
  }
}
```

---

## `Create Data View`

<a id="opIdDataViews_Create Data View"></a>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-summaries.yaml#dataview-create

<h3>Request</h3>

```text 
POST /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/dataviews
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#tenantId<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#namespaceId<br/><br/>

<h4>Request Body</h4>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-parameters.yaml#dataview-no-id<br/>

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "IndexField": {
    "Source": 0,
    "Keys": [
      "string"
    ],
    "StreamReferenceNames": [
      "string"
    ],
    "Label": "string",
    "SummaryType": 0,
    "SummaryDirection": 1,
    "IncludeUom": true
  },
  "Queries": [
    {
      "Id": "string",
      "Kind": 1,
      "Value": "string"
    }
  ],
  "DataFieldSets": [
    {
      "QueryId": "string",
      "DataFields": [
        {
          "Source": 0,
          "Keys": [
            "string"
          ],
          "StreamReferenceNames": [
            "string"
          ],
          "Label": "string",
          "SummaryType": 0,
          "SummaryDirection": 1,
          "IncludeUom": true
        }
      ],
      "IdentifyingField": {
        "Source": 0,
        "Keys": [
          "string"
        ],
        "StreamReferenceNames": [
          "string"
        ],
        "Label": "string",
        "SummaryType": 0,
        "SummaryDirection": 1,
        "IncludeUom": true
      }
    }
  ],
  "GroupingFields": [
    {
      "Source": 0,
      "Keys": [
        "string"
      ],
      "StreamReferenceNames": [
        "string"
      ],
      "Label": "string",
      "SummaryType": 0,
      "SummaryDirection": 1,
      "IncludeUom": true
    }
  ],
  "DefaultStartIndex": "string",
  "DefaultEndIndex": "string",
  "DefaultInterval": "string",
  "IndexTypeCode": 0,
  "Shape": 0
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|201|[DataView](#schemadataview)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#201-dataview-standard-message|
|400|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#400-standard-message|
|403|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#403-dataview-create|
|500|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#500-standard-message|

<h4>Example response body</h4>

> 201 Response

```json
null
```

> 400 Response ([ErrorResponse](#schemaerrorresponse))

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  },
  "ChildErrors": {
    "property1": null,
    "property2": null
  }
}
```

---

## `Get Data View`

<a id="opIdDataViews_Get Data View"></a>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-summaries.yaml#dataview-get

<h3>Request</h3>

```text 
GET /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#tenantId<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#namespaceId<br/><br/>`string id`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#dataViewId<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[DataView](#schemadataview)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#200-dataview-get|
|403|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#403-dataview-get|
|404|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#404-dataviewid-standard-message|
|500|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#500-standard-message|

<h4>Example response body</h4>

> 200 Response

```json
null
```

> 403 Response ([ErrorResponse](#schemaerrorresponse))

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  },
  "ChildErrors": {
    "property1": null,
    "property2": null
  }
}
```

---

## `Get or Create Data View`

<a id="opIdDataViews_Get or Create Data View"></a>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-summaries.yaml#dataview-getorcreate

<h3>Request</h3>

```text 
POST /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#tenantId<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#namespaceId<br/><br/>`string id`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#dataViewId<br/><br/>

<h4>Request Body</h4>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-parameters.yaml#dataview-no-id<br/>

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "IndexField": {
    "Source": 0,
    "Keys": [
      "string"
    ],
    "StreamReferenceNames": [
      "string"
    ],
    "Label": "string",
    "SummaryType": 0,
    "SummaryDirection": 1,
    "IncludeUom": true
  },
  "Queries": [
    {
      "Id": "string",
      "Kind": 1,
      "Value": "string"
    }
  ],
  "DataFieldSets": [
    {
      "QueryId": "string",
      "DataFields": [
        {
          "Source": 0,
          "Keys": [
            "string"
          ],
          "StreamReferenceNames": [
            "string"
          ],
          "Label": "string",
          "SummaryType": 0,
          "SummaryDirection": 1,
          "IncludeUom": true
        }
      ],
      "IdentifyingField": {
        "Source": 0,
        "Keys": [
          "string"
        ],
        "StreamReferenceNames": [
          "string"
        ],
        "Label": "string",
        "SummaryType": 0,
        "SummaryDirection": 1,
        "IncludeUom": true
      }
    }
  ],
  "GroupingFields": [
    {
      "Source": 0,
      "Keys": [
        "string"
      ],
      "StreamReferenceNames": [
        "string"
      ],
      "Label": "string",
      "SummaryType": 0,
      "SummaryDirection": 1,
      "IncludeUom": true
    }
  ],
  "DefaultStartIndex": "string",
  "DefaultEndIndex": "string",
  "DefaultInterval": "string",
  "IndexTypeCode": 0,
  "Shape": 0
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|201|[DataView](#schemadataview)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#201-dataview-standard-message|
|302|None|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#302-data-get|
|400|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#400-standard-message|
|403|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#403-standard-message|
|409|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#409-data-get|
|500|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#500-standard-message|

<h4>Example response body</h4>

> 201 Response

```json
null
```

> 400 Response ([ErrorResponse](#schemaerrorresponse))

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  },
  "ChildErrors": {
    "property1": null,
    "property2": null
  }
}
```

---

## `Create or Update Data View`

<a id="opIdDataViews_Create or Update Data View"></a>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-summaries.yaml#dataview-createorupdate

<h3>Request</h3>

```text 
PUT /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#tenantId<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#namespaceId<br/><br/>`string id`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#dataViewId<br/><br/>

<h4>Request Body</h4>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-parameters.yaml#dataview<br/>

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "IndexField": {
    "Source": 0,
    "Keys": [
      "string"
    ],
    "StreamReferenceNames": [
      "string"
    ],
    "Label": "string",
    "SummaryType": 0,
    "SummaryDirection": 1,
    "IncludeUom": true
  },
  "Queries": [
    {
      "Id": "string",
      "Kind": 1,
      "Value": "string"
    }
  ],
  "DataFieldSets": [
    {
      "QueryId": "string",
      "DataFields": [
        {
          "Source": 0,
          "Keys": [
            "string"
          ],
          "StreamReferenceNames": [
            "string"
          ],
          "Label": "string",
          "SummaryType": 0,
          "SummaryDirection": 1,
          "IncludeUom": true
        }
      ],
      "IdentifyingField": {
        "Source": 0,
        "Keys": [
          "string"
        ],
        "StreamReferenceNames": [
          "string"
        ],
        "Label": "string",
        "SummaryType": 0,
        "SummaryDirection": 1,
        "IncludeUom": true
      }
    }
  ],
  "GroupingFields": [
    {
      "Source": 0,
      "Keys": [
        "string"
      ],
      "StreamReferenceNames": [
        "string"
      ],
      "Label": "string",
      "SummaryType": 0,
      "SummaryDirection": 1,
      "IncludeUom": true
    }
  ],
  "DefaultStartIndex": "string",
  "DefaultEndIndex": "string",
  "DefaultInterval": "string",
  "IndexTypeCode": 0,
  "Shape": 0
}
```

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|201|[DataView](#schemadataview)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#201-dataview-standard-message|
|204|None|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#204-dataview-update-standard-message|
|400|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#400-standard-message|
|403|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#403-standard-message|
|500|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#500-standard-message|

<h4>Example response body</h4>

> 201 Response ([DataView](#schemadataview))

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "IndexField": {
    "Source": 0,
    "Keys": [
      "string"
    ],
    "StreamReferenceNames": [
      "string"
    ],
    "Label": "string",
    "SummaryType": 0,
    "SummaryDirection": 1,
    "IncludeUom": true
  },
  "Queries": [
    {
      "Id": "string",
      "Kind": 1,
      "Value": "string"
    }
  ],
  "DataFieldSets": [
    {
      "QueryId": "string",
      "DataFields": [
        {
          "Source": 0,
          "Keys": [
            "string"
          ],
          "StreamReferenceNames": [
            "string"
          ],
          "Label": "string",
          "SummaryType": 0,
          "SummaryDirection": 1,
          "IncludeUom": true
        }
      ],
      "IdentifyingField": {
        "Source": 0,
        "Keys": [
          "string"
        ],
        "StreamReferenceNames": [
          "string"
        ],
        "Label": "string",
        "SummaryType": 0,
        "SummaryDirection": 1,
        "IncludeUom": true
      }
    }
  ],
  "GroupingFields": [
    {
      "Source": 0,
      "Keys": [
        "string"
      ],
      "StreamReferenceNames": [
        "string"
      ],
      "Label": "string",
      "SummaryType": 0,
      "SummaryDirection": 1,
      "IncludeUom": true
    }
  ],
  "DefaultStartIndex": "string",
  "DefaultEndIndex": "string",
  "DefaultInterval": "string",
  "IndexTypeCode": 0,
  "Shape": 0
}
```

---

## `Delete Data View`

<a id="opIdDataViews_Delete Data View"></a>

#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-summaries.yaml#dataview-delete

<h3>Request</h3>

```text 
DELETE /api/v1/tenants/{tenantId}/namespaces/{namespaceId}/dataviews/{id}
```

<h4>Parameters</h4>

`string tenantId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#tenantId<br/><br/>`string namespaceId`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#namespaceId<br/><br/>`string id`
<br/>#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/parameters.yaml#dataViewId<br/><br/>

<h3>Response</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#204-dataview-update-standard-message|
|403|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#403-standard-message|
|404|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#404-dataviewid-standard-message|
|500|[ErrorResponse](#schemaerrorresponse)|#https://raw.githubusercontent.com/osisoft/OCS-Docs/main/content/external-references/dataviews-response-codes.yaml#500-standard-message|

---
## Definitions

### DataView

<a id="schemadataview"></a>
<a id="schema_DataView"></a>
<a id="tocSdataview"></a>
<a id="tocsdataview"></a>

A declarative way to select, label and shape data

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|The data view's unique identifier|
|Name|string|false|true|The data view's friendly name|
|Description|string|false|true|The data view's description|
|IndexField|[Field](#schemafield)|false|true|The data view's index field|
|Queries|[[Query](#schemaquery)]|false|true|The collection of queries used by the data view|
|DataFieldSets|[[FieldSet](#schemafieldset)]|false|true|The collection of data field sets defined on the data view|
|GroupingFields|[[Field](#schemafield)]|false|true|The collection of fields to be used as grouping fields|
|DefaultStartIndex|string|false|true|The default start index used when data view data is queried, if no explicit value is specified|
|DefaultEndIndex|string|false|true|The default end index used when data view data is queried, if no explicit value is specified|
|DefaultInterval|string|false|true|The default interval used when data view data is retrieved, if no explicit value is specified|
|IndexTypeCode|[SdsTypeCode](#schemasdstypecode)|false|false|The data type of the index field|
|Shape|[DataViewShape](#schemadataviewshape)|false|false|The output shape of the data view|

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "IndexField": {
    "Source": 0,
    "Keys": [
      "string"
    ],
    "StreamReferenceNames": [
      "string"
    ],
    "Label": "string",
    "SummaryType": 0,
    "SummaryDirection": 1,
    "IncludeUom": true
  },
  "Queries": [
    {
      "Id": "string",
      "Kind": 1,
      "Value": "string"
    }
  ],
  "DataFieldSets": [
    {
      "QueryId": "string",
      "DataFields": [
        {
          "Source": 0,
          "Keys": [
            "string"
          ],
          "StreamReferenceNames": [
            "string"
          ],
          "Label": "string",
          "SummaryType": 0,
          "SummaryDirection": 1,
          "IncludeUom": true
        }
      ],
      "IdentifyingField": {
        "Source": 0,
        "Keys": [
          "string"
        ],
        "StreamReferenceNames": [
          "string"
        ],
        "Label": "string",
        "SummaryType": 0,
        "SummaryDirection": 1,
        "IncludeUom": true
      }
    }
  ],
  "GroupingFields": [
    {
      "Source": 0,
      "Keys": [
        "string"
      ],
      "StreamReferenceNames": [
        "string"
      ],
      "Label": "string",
      "SummaryType": 0,
      "SummaryDirection": 1,
      "IncludeUom": true
    }
  ],
  "DefaultStartIndex": "string",
  "DefaultEndIndex": "string",
  "DefaultInterval": "string",
  "IndexTypeCode": 0,
  "Shape": 0
}

```

---

### Field

<a id="schemafield"></a>
<a id="schema_Field"></a>
<a id="tocSfield"></a>
<a id="tocsfield"></a>

A data field that targets information resolved within its FieldSet

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Source|[FieldSource](#schemafieldsource)|false|false|The target part of a data item, if this Field targets a data item. NotApplicable otherwise.|
|Keys|string[]|false|true|The collection of keys this field can match on its target data source Can be used to account for differences across target data types, e.g. matching either "Temperature" or "temperature_val"|
|StreamReferenceNames|string[]|false|true|The collection of possible stream reference names|
|Label|string|false|true|A friendly label|
|SummaryType|[SdsSummaryType](#schemasdssummarytype)|false|false|Specifies summary operation|
|SummaryDirection|[SummaryDirection](#schemasummarydirection)|false|true|Specifies summary direction|
|IncludeUom|boolean|false|false|Specifies whether to include this field's unit of measure as an additional field mapping in the resolved data view|

```json
{
  "Source": 0,
  "Keys": [
    "string"
  ],
  "StreamReferenceNames": [
    "string"
  ],
  "Label": "string",
  "SummaryType": 0,
  "SummaryDirection": 1,
  "IncludeUom": true
}

```

---

### FieldSource

<a id="schemafieldsource"></a>
<a id="schema_FieldSource"></a>
<a id="tocSfieldsource"></a>
<a id="tocsfieldsource"></a>

The targeted part of a DataItem

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|NotApplicable|0|
|Id|1|
|Name|2|
|PropertyId|3|
|PropertyName|4|
|Metadata|5|
|Tags|6|

---

### SdsSummaryType

<a id="schemasdssummarytype"></a>
<a id="schema_SdsSummaryType"></a>
<a id="tocSsdssummarytype"></a>
<a id="tocssdssummarytype"></a>

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|None|0|
|Count|1|
|Minimum|2|
|Maximum|4|
|Range|8|
|Mean|16|
|StandardDeviation|32|
|PopulationStandardDeviation|64|
|Total|128|
|Skewness|256|
|Kurtosis|512|
|WeightedMean|1024|
|WeightedStandardDeviation|2048|
|WeightedPopulationStandardDeviation|4096|

---

### SummaryDirection

<a id="schemasummarydirection"></a>
<a id="schema_SummaryDirection"></a>
<a id="tocSsummarydirection"></a>
<a id="tocssummarydirection"></a>

Specifies summary direction for a Field

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|Forward|1|
|Backward|2|

---

### Query

<a id="schemaquery"></a>
<a id="schema_Query"></a>
<a id="tocSquery"></a>
<a id="tocsquery"></a>

A query for data items of a specified resource type.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|The unique identifier of this query|
|Kind|[DataItemResourceType](#schemadataitemresourcetype)|false|false|The type of resource being queried|
|Value|string|false|true|The text of this query|

```json
{
  "Id": "string",
  "Kind": 1,
  "Value": "string"
}

```

---

### DataItemResourceType

<a id="schemadataitemresourcetype"></a>
<a id="schema_DataItemResourceType"></a>
<a id="tocSdataitemresourcetype"></a>
<a id="tocsdataitemresourcetype"></a>

The type of resource that a data item represents

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|Stream|1|
|Asset|2|

---

### FieldSet

<a id="schemafieldset"></a>
<a id="schema_FieldSet"></a>
<a id="tocSfieldset"></a>
<a id="tocsfieldset"></a>

A set of fields defined for a particular source of data.

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|QueryId|string|false|true|The identifier of the Query this field set uses.|
|DataFields|[[Field](#schemafield)]|false|true|The collection of Data Fields defined in this field set.|
|IdentifyingField|[Field](#schemafield)|false|true|The field used to identify each data item resolved by this field set.|

```json
{
  "QueryId": "string",
  "DataFields": [
    {
      "Source": 0,
      "Keys": [
        "string"
      ],
      "StreamReferenceNames": [
        "string"
      ],
      "Label": "string",
      "SummaryType": 0,
      "SummaryDirection": 1,
      "IncludeUom": true
    }
  ],
  "IdentifyingField": {
    "Source": 0,
    "Keys": [
      "string"
    ],
    "StreamReferenceNames": [
      "string"
    ],
    "Label": "string",
    "SummaryType": 0,
    "SummaryDirection": 1,
    "IncludeUom": true
  }
}

```

---

### SdsTypeCode

<a id="schemasdstypecode"></a>
<a id="schema_SdsTypeCode"></a>
<a id="tocSsdstypecode"></a>
<a id="tocssdstypecode"></a>

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|Empty|0|
|Object|1|
|Boolean|3|
|Char|4|
|SByte|5|
|Byte|6|
|Int16|7|
|UInt16|8|
|Int32|9|
|UInt32|10|
|Int64|11|
|UInt64|12|
|Single|13|
|Double|14|
|Decimal|15|
|DateTime|16|
|String|18|
|Guid|19|
|DateTimeOffset|20|
|TimeSpan|21|
|Version|22|
|NullableBoolean|103|
|NullableChar|104|
|NullableSByte|105|
|NullableByte|106|
|NullableInt16|107|
|NullableUInt16|108|
|NullableInt32|109|
|NullableUInt32|110|
|NullableInt64|111|
|NullableUInt64|112|
|NullableSingle|113|
|NullableDouble|114|
|NullableDecimal|115|
|NullableDateTime|116|
|NullableGuid|119|
|NullableDateTimeOffset|120|
|NullableTimeSpan|121|
|BooleanArray|203|
|CharArray|204|
|SByteArray|205|
|ByteArray|206|
|Int16Array|207|
|UInt16Array|208|
|Int32Array|209|
|UInt32Array|210|
|Int64Array|211|
|UInt64Array|212|
|SingleArray|213|
|DoubleArray|214|
|DecimalArray|215|
|DateTimeArray|216|
|StringArray|218|
|GuidArray|219|
|DateTimeOffsetArray|220|
|TimeSpanArray|221|
|VersionArray|222|
|Array|400|
|IList|401|
|IDictionary|402|
|IEnumerable|403|
|SdsType|501|
|SdsTypeProperty|502|
|SdsStreamView|503|
|SdsStreamViewProperty|504|
|SdsStreamViewMap|505|
|SdsStreamViewMapProperty|506|
|SdsStream|507|
|SdsStreamIndex|508|
|SdsTable|509|
|SdsColumn|510|
|SdsValues|511|
|SdsObject|512|
|SByteEnum|605|
|ByteEnum|606|
|Int16Enum|607|
|UInt16Enum|608|
|Int32Enum|609|
|UInt32Enum|610|
|Int64Enum|611|
|UInt64Enum|612|
|NullableSByteEnum|705|
|NullableByteEnum|706|
|NullableInt16Enum|707|
|NullableUInt16Enum|708|
|NullableInt32Enum|709|
|NullableUInt32Enum|710|
|NullableInt64Enum|711|
|NullableUInt64Enum|712|

---

### DataViewShape

<a id="schemadataviewshape"></a>
<a id="schema_DataViewShape"></a>
<a id="tocSdataviewshape"></a>
<a id="tocsdataviewshape"></a>

The shape of the data view. By default, each Field will resolve to one or more FieldMappings. In narrow shape, all Fields that map to a DataItem are "pivoted" vertically, into two fields: Label and Value.

<h4>Enumerated Values</h4>

|Property|Value|
|---|---|
|Standard|0|
|Narrow|1|

---

### ErrorResponse

<a id="schemaerrorresponse"></a>
<a id="schema_ErrorResponse"></a>
<a id="tocSerrorresponse"></a>
<a id="tocserrorresponse"></a>

<h4>Properties</h4>

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|false|true|None|
|Error|string|false|true|None|
|Reason|string|false|true|None|
|Resolution|string|false|true|None|
|Parameters|object|false|true|None|
|ChildErrors|object|false|true|None|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "Parameters": {
    "property1": "string",
    "property2": "string"
  },
  "ChildErrors": {
    "property1": null,
    "property2": null
  }
}

```

---

