---
uid: graphQLConsole
---

# GraphQL console (Preview)

The GraphQL console provides a graphical interface for creating queries for the GraphQL API. The GraphQL API returns event data and associated reference data stored in AVEVA Data Hub.

You can run a query within the console, or use it to create a query that can be used by an external application.

To use the GraphQL console:

1. In the left pane, select **Developer Tools** > **GraphQL Console**.

   The `GraphQL Explorer` pane populates with your organization's schema.

1. Select the **Query** tab in the `GraphQL Explorer` pane to compose a data retrieval request, or the **Mutation** tab to upsert or delete data.

1. Select ![drill-down](../_icons/branded/arrow-right-circle-outline.svg) next to an object in the GraphQL Explorer to drill down and show the available filtering options and fields.

1. Use the GraphQL Explorer tree to create a request.

   - Use the selections under the `where:` argument to filter by fields that equal, contain, start with, or end with a specified value, or are included in an array of values.

   - Use the selections under the `options:` argument to retrieve a specified count of objects or to sort the data returned. If you select multiple sort fields, the order in which you select them determines the sort order.

   - For fields that can be arrays, when an item is selected or entered, a new blank item appears below it to allow for additional values.

   - For upsert or delete operations, use the selections under `input:` to identify the object to update or delete.

   - Select the fields to include in the response.

   - Select **Reset** to clear all selections.

   - Select ![copy](../_icons/branded/content-copy.svg) in the `Request` or `Variables` pane to copy the contents of that pane to the clipboard.

   - Select ![GraphQL Explorer Pane](../_icons/branded/sitemap.svg) to hide or show the `GraphQL Explorer` pane.

   - Select ![Response pane](../_icons/branded/response.svg) to hide or show the `Response` pane.

   **Note:** The `GraphQL Explorer` and `Request` panes work in both directions. The request updates as you make selections in the GraphQL Explorer tree, and editing the text directly in the request or pasting a complete request updates the GraphQL Explorer tree. When editing the request directly, select ![Format](../_icons/default/auto-fix.svg) to automatically format the request.

1. Select ![return](../_icons/branded/arrow-left-circle-outline.svg) to return to the top level and repeat the process with other objects, as needed.

1. When your query is complete, select **Send Request** to run the query.

   The results of your query appear in the `Response` pane.

1. When you request a certain amount of fields, such as `count: 1`, and there are more fields available to display, a continuation token appears in the response. Select `Resend with Continuation` to view the next item.

## Variables

Rather than entering specific values for your query, you can use variables.

1. Select the ![set variable](../_icons/custom/currency-usd-off.svg) icon that appears next to an argument when you hover over it.

1. Enter a variable name in the box that appears.

   A variable declaration is added to the `Request` pane and the new variable is added to the `Variables` pane in JSON format. The variable is assigned a value of `null` by default.

1. Edit the value in the `Variables` pane to assign a value to the variable.

   You can also make an array a variable and include multiple values, such as `[98, 99, ...]`.

If you manually edit the variable name within the `Request` pane, select ![Format](../_icons/default/auto-fix.svg) to automatically update the variable name in the header and `Variables` pane.

## Fragments

GraphQL supports reusable units called fragments. With fragments you construct sets of fields once, and then reuse them in multiple locations in a query.

1. In the `Request` pane, add the fragment text above or below the query. The location does not matter.

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

Fragments appear only in the `Request` pane and are not reflected in the GraphQL Explorer. They persist when you make changes in the GraphQL Explorer.
