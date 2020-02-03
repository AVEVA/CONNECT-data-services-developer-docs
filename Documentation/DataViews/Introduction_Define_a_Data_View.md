---
uid: DataViewsIntroductionDefine
---

# Introduction - Define a Data View

This is an introduction to the recommended workflow for defining data views. The [Quick Start - Define a Data View](xref:DataViewsQuickStartDefine) shows these concepts in action. For details, see [Data View](xref:DataView) and [Resolved Data View](xref:ResolvedDataView).


Designing and tweaking a data view is expected to be an iterative process. You are not expected to "get it right the first time," nor to be an expert at the streams available in the Sequential Data Store. Data views provide an interactive way to select, identify, and arrange the data you and your applications need.

There are three main steps required to define a data view: 
1. Including data items (streams)
2. Including specific data fields
3. Arranging them within the data view.

This is not a one-way street. You are likely to, for example, keep adjusting what data fields are included in the view even after you have begun working on how the fields are arranged in the data view.

## Prerequisite: Create a data view
Very little information is required to create a new data view. In fact, if you request that the system generate an identifier for the new data view, no information at all is necessary. However, it is recommended to specify a meaningful `.Id`, because the identifier cannot be changed late without recreating the data view. All other properties are modifiable.



## 1. Include data items

- Define (or modify) `.Queries` for SDS streams to be included as data items in the data view. View the collection data items found by each query.
- Use a distinct query for each general type of data item, such as streams about assets and streams about the weather where each asset is located.

You can return at any time to modify or add queries.

## 2. Include specific data fields

- View the information on which data fields resolve as available to include in the data view. Choose the fields you want, and add them to your data view's `.FieldSets`
- If your streams have slight variations in property naming (e.g. a property called either `temperature` or `ambient_temperature`), combine fields so that they can match alternate values.

You can return at any time to adjust which fields are included in the data view.

## 3. Section and distinguish the data items

### Sectioning items globally
You may wish to globally *section*, or group, the data items by some common factor (e.g. site or asset id).  

- Define one or more fields as `.Sectioners` of the data view. Data items will be grouped by these fields. The available field sets now include field(s) that link to the sectioner values.

- Include the newly-available sectioner value fields in the data view, so those values are included in the data view data.

### Distinguishing items locally within a field set
If a section contains multiple data items from the same query, you may wish to *distinguish* those data items so that they are not ambiguous and so they will be aligned across sections.

- On the field set in question, assign a field as the `.Distinguisher` to tell the data items apart.
- Ensure that each field's label includes the {DistinguisherValue} token so the field labels are unique. The default field labels already include it.

You can return at any time to change the sectioners and distinguishers.