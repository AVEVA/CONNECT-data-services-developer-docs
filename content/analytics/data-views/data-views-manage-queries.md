---
uid: data-views-manage-queries
---

# Manage queries

Following initial configuration of a data view, you can go back to add new queries or remove existing ones.

## To manage queries for a data view

Following initial addition of a data view, you can add queries or remove them from the data view.

1. In the left pane, select **Analytics** > **Data Views**.

1. Select the data view that you want to edit.

1. Select **Edit Data View**.

	The data view opens.

1. Select **Manage Queries**.

## To add queries to a data view

1. Select **Add**.

1. From **Query Id**, overwrite the default value of `Query1` with a unique identifier.

1. From **Query Source**, select a namespace ![namespace](../../_icons/default/database.svg) or community ![community](../../_icons/default/share-variant.svg) to query operational data from. The source can either be a namespace from your own tenant or a community shared by another tenant.

   **Tip:** You can filter the namespaces and communities that are listed using the slide toggles and the filter field.

1. From **Query Type**, select the type of object that you want to search for in the query source: **Streams** or **Assets**. 

   **Note**: To query for assets, you must be licensed for them. If you are interested in using Assets, contact your account team for more details.

1. From **Query Value**, enter a query to find the objects that you want to include in the data view. Then select **Search**.

   When you select the **Query Value** search field, a cheat sheet displays, providing examples of how to use wildcards, filters, and operators in your query.
   
   - For more information on entering queries for **streams**, see [Search for streams](xref:sdsSearching#search-for-streams).

   - For more information on entering queries for **assets**, see <xref:asset-search-dev-guide>.

   If you have created a metadata rule in the same namespace, you can enter a selected metadata key instead of an object name in the **Search** field to display a more specific set of streams or assets.

   When the query populates with objects, you can view more about each object by selecting it from the table. The object details display in the pane on the right.

   [!include[query-notes](_includes/query-notes.md)]

1. (Optional) To add additional queries to the data view, select **Add Query** and repeat the steps listed above.

1. Once you are satisfied with your queries and query results, select **Save**.


## To remove queries from a data view

1. Select the query that you want to remove.

1. Select **Remove**.