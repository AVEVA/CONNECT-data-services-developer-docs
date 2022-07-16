---
uid: data-views-configure-data-field-sets
---

# Step 4: Configure data field sets

[!include[configure-data-field-sets](_includes/configure-data-field-sets.md)]

## Configure grouping fields

You can organize the data items within a data view by grouping them, which is one method of producing a meaningful, consumable shape of data. Configure grouping fields using the **Grouping Fields** accordion panel. Grouping is optional when defining the data view.

Without grouping, all of the data items returned by a query appear side-by-side. If the view includes many data items, its data records will be vast. The fields are also likely to be ambiguous.

[Configuring identifying fields](#configure-identifying-fields) to identifying the items within each field set is one way to disambiguate the fields, but only one field may be an identifying field. What if multiple metadata fields are required to fully describe each data item? Grouping can organize the data items into shapes that are consumable, represent a physical asset, or both.

Only certain fields are eligible to be used as grouping fields. Fields are only eligible if they include one or more of the following source types:

Fields are only eligible if they include one of the following source types listed in the table below. All source types require a field label. Some source types also require having a key defined. The following table lists eligible data sources along with additional requirements for field labels and keys.

| Eligible source type | Field label required? | Key required? |
|----------------------|-----------------------|---------------|
| Id                   | ✔                    | &#10006;      |
| Name                 | ✔                    | &#10006;      |
| Metadata             | ✔                    | ✔             |
| Tags                 | ✔                    | ✔             |

To add a grouping field, select **Add a Grouping Field** and choose an eligible field. You can add as many eligible fields as you prefer.

**Add a grouping field**

![add-a-grouping-field](_images/add-a-grouping-field.png)

- If you define **Grouping Fields**, the data view shows multiple groups, each with the list of data items for the group and its field values displaying. If a data item does not match any group, it is added to all groups.

	Within the data view preview, groups are ordered alphabetically by the first grouping value for each group. Within each group, data items are ordered alphabetically by data item id.

	If you are using multiple grouping fields, you can arrange their order by drag and drop. For more information, see [Configure field order](#configure-field-order).

- If **Grouping Fields** is not defined on the data view, the resolved data view shows a single group with all eligible data items.
  
## Configure identifying fields

If the field set resolves to multiple data items in any group (or if grouping is not used), then you should designate an **Identifying field** for the field set. The identifying field of a data field set specifies the primary field to identify multiple items in a group. This identification methods allows the identifying field value to be used automatically in field labels of the group. If a lone criterion is not a sufficient or useful way of disambiguating the fields, then grouping by additional criteria may be necessary. 

Fields are only eligible if they include one or more of the following source types listed in the table below. Some source types include the an requirement of having a key defined. following table lists eligible data sources along with additional requirements for keys.

| Eligible source type | Key required? |
|----------------------|---------------|
| Id                   | &#10006;      |
| Name                 | &#10006;      |
| Metadata             | ✔            |
| Tags                 | ✔            |

To add an identifying field to a field set, select **Identifying Field** and choose an eligible field. You can only choose a single field.

**Add an identifying field**

![add-an-identifying-field](_images/add-an-identifying-field.png)

## Configure field order

You can change the order that fields display within your data view by dragging and dropping fields in the preferred order.

![reorder fields](_images/reorder-fields.gif)

## Link fields

For fields that contain the same type of information under a different name, you can link them by dragging and dropping one field onto the other.

![consolidate fields](_images/consolidate-fields.gif)

## Next steps

Continue to <xref:data-view-choose-data-shape>.