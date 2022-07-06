---
uid: data-views-add-query
---

# Step 3: Add a query

[!include[add-query](_includes/add-query.md)]

1. From **Query Id**, overwrite the default value of `Query1` with a unique identifier.

1. From **Query Source**, select a namespace ![namespace](../../../_icons/default/database.svg) or community ![community](../../../_icons/default/share-variant.svg) to query operational data from. The source can either be a namespace from your own tenant or a community shared by another tenant.

   **Tip:** You can filter the namespaces and communities that are listed using the slide toggles and the filter field.

1. From **Query Type**, select the type of object that you want to search for in the query source: **Streams** or **Assets**. 

   **Note**: To query for assets, you must be licensed for them. If you are interested in using Assets, contact your account team for more details.

1. From **Query Value**, enter a query to find the objects that you want to include in the data view. Then select **Search**.

   When you select the **Query Value** search field, a cheat sheet displays, providing examples of how to use wildcards, filters, and operators in your query.
   
   - For more information on entering queries for **streams**, see [Search for streams](xref:sdsSearching#search-for-streams).

   - For more information on entering queries for **assets**, see <xref:asset-search-dev-guide>.

   If you have created a metadata rule in the same namespace, you can enter a selected metadata key instead of an object name in the **Search** field to display a more specific set of streams or assets.

   When the query populates with objects, you can view more about each object by selecting it from the table. The object details display in the pane on the right. 

1. (Optional) To add additional queries to the data view, select **Add Query** and repeat the steps listed above.

1. Once you are satisfied with your queries and query results, select **Save**.

[!include[ineligible-date-items](_includes/ineligible-date-items.md)]

## Next steps

Continue to <xref:data-views-add-data-fields>.