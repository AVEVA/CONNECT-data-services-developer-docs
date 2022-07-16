---
uid: data-views-add-data-fields
---

# Step 3: Add data fields

[!include[add-data-fields](../../_includes/data-views-add-data-fields.md)]

## 1. Select data fields

In the `Add Data Fields` window, select the data fields that you want to include in the data field set for each query. You can filter the data fields listed for each query by [summary type](#filter-by-summary-type) or by [text](#filter-by-text).

**Tip:** To display which fields are already included in the data view, select **Show Included Fields**.

After you choose data fields, perform one of the following actions:

- Select **Apply** to finish adding data fields to your data view. You can always edit the data fields later.

- Select **Next** to edit the selected data fields. For more information, see [2. Edit data fields (optional)](#2-edit-data-fields-optional).

### Filter by summary type

You can filter the data fields listed for each query by summary type, which returns different calculations for a given data field. The `Value` summary type is selected by default.

### Filter by text

You can further filter the data fields listed for each query by text.  

## 2. Edit data fields (optional)

For each data view query, you can include data fields that represent a particular source of information, such as the `.Id` for a data item or the values from one of its properties.

### Data field labels

[!include[data-view-label](../../_includes/data-view-label.md)]

To edit data field label, enter `{` to display tokens to use as a data field label. [!include[field-label-tokens](../../_includes/data-view-field-label-tokens.md)]

### Include UOM as a column

This option includes the unit of measure as a column in your data view.

### Summary direction

Summary Direction controls whether the start or end index of the summary is used by the data view to calculate the summary values. For more information, see <xref:DataViewsSummaries>.

### Data field preview

This preview lists each data field and property included within the affected data view queries.

## Next steps

Continue to <xref:data-views-configure-data-field-sets>.