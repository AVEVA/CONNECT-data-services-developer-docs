---
uid: gsTypes
---

# Get started with types

After creating the namespace, the next step is to add one or more types. A type defines the shape and structure of events and how to associate events within a stream of data. For more information about types, see the following topics:

- [Types](xref:ccTypes)

- [Types best practices](xref:bpTypes)

To add a type, follow these steps:

1. In the left pane, select **Data Management** > **Sequential Data Store**.

1. From the **Streams** dropdown list, select **Types**.

1. Select **Add Type**.

1. In the `Add Type` window, enter the values for these fields:

   - **Id** – *MyData.PumpState*

   - **Name** – *MyData.PumpState*

   - **Description** – *SDS Type used by MyData*

   **Note:** You can use an existing SDS type as the starting point for the new type by selecting an existing SDS type in the **Base Type** field. When you add a base type, its properties populate the `Properties` list. You can then add other properties to the type.

1. To add a property, select **Add Property** and complete the fields as follows:

   - **Key** – Select the checkbox.

      **Note:** The `Key` field identifies this property as the index. 

   - **Id** – Enter *Timestamp*.

   - **Type** – Select *DateTime*. <!-- Do we need to mention that you can filter by System or Tenant types? --> 

   - **UOM** – Leave this blank.

1. To add a second property, select **Add Property** again and complete the fields as follows:

   - **Id** – Enter *Temperature*.

   - **Type** – Select *Double*.

   - **UOM** – Select *degree Celsius*.

1. To add a third property, select **Add Property** again and complete the fields as follows:

   - **Id** – Enter *Pressure*.

   - **Type** – Select *Double*.
   
   - **UOM** – Select *kilogram per cubic meter*.

1. To add a fourth property, select **Add Property** again and complete the fields as follows:

   - **Id** – Enter *Status*.

   - **Type** – Select *String*.

   - **UOM** – Leave this blank.

   **Note:** You can select up to three properties as indexes. Drag and drop the properties in the list to order the index keys. For this exercise, use only the `Timestamp` property as an index.

1. Select **Apply**.

To explore information about the type you just created, follow these steps:

1. Select the `MyData.PumpState` type, select the ![More Options button](../../_icons/default/dots-vertical.svg) icon, and then select **Manage Permissions**.

    The `Manage Permissions for MyData.PumpState` window opens where you can override the default permissions and set permissions for the specific type. You must be assigned the Tenant Administrator role to configure the type permissions.

    Review the permissions for the `MyData.PumpState` type, and when you have finished exploring this window, select **Cancel** to continue. 

1. Select the `MyData.PumpState` type, select the ![More Options button](../../_icons/default/dots-vertical.svg) icon, and then select **Get Type Streams**.

   The **Streams** list opens and, by default, the `typeId:MyData.PumpState` query is used to filter any streams with the `MyData.PumpState` type. The list is currently empty, because you have not created streams for this type yet.

## Next step

Continue with [Get started with streams](xref:gsStreams).
