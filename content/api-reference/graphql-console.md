---
uid: graphQLConsole
---

# GraphQL console (Preview)

The GraphQL console provides a graphical interface for creating queries for the GraphQL API. The GraphQL API returns Manufacturing Execution System (MES) streaming events and associated metadata stored in AVEVA Data Hub.

You can run a query within the console, or use it to create a query that can be used by an external application.

To use the GraphQL console:

1. In the left pane, select **Developer Tools** > **GraphQL Console**.

   The `GraphQL Explorer` pane populates with the queries for search and aggregation from your organization's schema.

1. Select the **Query** tab in the `GraphQL Explorer` pane to compose a data retrieval request, or the **Mutation** tab to modify data.

1. Select ![expand](../_icons/branded/plus-circle-outline.svg) next to an object in the GraphQL Explorer to show the available fields.

1. Use the GraphQL Explorer tree to create a query.

   - Use the selections under the `where:` argument to filter by fields that equal, contain, start with, or end with a specified value, or are included in an array of values.

   - Use the selections under the `options:` argument to retrieve a specified count of objects or to sort the data returned. Select **+ Add** to add a secondary sort field.

   - For fields that can be arrays, select **+ Add** below them to add spaces for additional values to the query.

   - Select the fields to include in the response.

   - Select **Reset** to clear all selections.

   - Select ![GraphQL Explorer Panel](../_icons/branded/sitemap.svg) to hide or show the explorer panel.

   **Note:** The `GraphQL Explorer` and `Query` panes work in both directions. The query is updated as you make selections in the GraphQL Explorer tree, and editing the text directly in the query or pasting a complete query will update the GraphQL Explorer tree.

1. Select ![left arrow](../_icons/branded/arrow-left.svg) to return to the top level and repeat the process with other objects, as needed.

1. When you have completed the query, select **Send Request** to run the query.

   The results of your query appear in the `Response` pane.

1. When a certain amount of fields has been requested, such as `count: 1`, and there are more fields available to display, a continuation token appears in the response. Select `Resend with Continuation` to view the next item.

## Variables

Rather than entering specific values for your query, you can use variables.

1. Select the green **$** that appears next to an argument when you hover over it.

1. Enter a variable name in the box that appears.

   A variable declaration is added to the `Query` pane and the new variable is added to the `Variables` pane in JSON format. The variable is assigned a value of `null` by default.

1. Edit the value in the `Variables` pane to assign a value to the variable.

   You can also make an array a variable and include multiple values, such as `[98, 99, ...]`.

## Fragments

GraphQL supports reusable units called fragments. With fragments you construct sets of fields once, and then reuse them in multiple locations in a query.

1. In the `Query` pane, add the fragment text above or below the query. The location does not matter.

   For example:

   ```
   fragment AlarmFields on Alarm {
    id
    eventStartTime
    eventState
    severity
   }
   ```

1. Within the query, place instances of the fragment in the format `...[fragment name]`.

Fragments are only in the `Query` pane and are not reflected in the GraphQL Explorer. They persist when you make changes in the GraphQL Explorer.
