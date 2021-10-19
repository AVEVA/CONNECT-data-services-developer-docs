---
uid: gpTypes
---

# Add a type

Sequential Data Store (SDS) types define the shape and structure of events and how to associate events with streams of data. Once created, you cannot modify a type. Follow this procedure to add a type.

1. In the left pane, select **Data Management** > **Sequential Data Store**.

1. In the upper left corner, select **Types**.

1. Click **Add Type**.

1. In the `Add Type` pane, enter the following information:

 - **Id** &ndash; Enter the Id for the type.
    
 - **Name** &ndash; (Optional) Enter a user-friendly name. If you do not provide a name, the Id will be assigned as the name.
   
 - **Description** &ndash; (Optional) Enter descriptive text that you can use to identify the type.
   
 - **Base Type** &ndash; (Optional) Select a previously created type on which the new type will be based. The new type inherits the properties of the base type. Inherited properties are read only and cannot be modified.

1. To add a property, select **Add Property** and complete the following fields:
 
 - **Key** &ndash;  Select the checkbox to indicate the property is an index. You can select up to three properties as indexes. Drag and drop the properties in the list to reorder the index keys. Only system SDS types can be designated as keys. <!-- AF 10/19/21 - I am not sure what the last sentence means. -->
   
 - **Id** &ndash; Enter the identifier for referencing the property.
   
 - **Name** &ndash; Enter the name of the property. By default, the **Id** and **Name** are the same. 
   
 - **Type** &ndash; Select the SDS type of the property.
   
     **Note:** You can filter the property types by entering text in the **Filter Types** box. You can also use the **System** or **Tenant** controls to include or exclude these types. *Tenant* includes any types that were previously created in the selected namespace for a particular tenant. *System* includes SDS types that are provided and defined such as *string*, *integer*, *double*, *datetime*, and *boolean*.
   
 - **UOM** &ndash; (Optional) Select a unit of measure for the property. 
   
1. When you have finished adding properties, click **Save**.

## Related links

- [Types](xref:sds-types) API
