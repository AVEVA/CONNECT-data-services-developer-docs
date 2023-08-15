---
uid: Search
---

# Search in AVEVA Data Hub

Many pages in AVEVA Data Hub include a search capability, including:

- Sequential Data Store (streams, types, stream views)
- Asset Explorer (assets, asset types)
- Edge Data Store & Adapters (systems, configuration templates)
- Data Views (streams, assets)

This topic describes the available search query options.

## Search operators

You can use search operators to get more refined search results. Use the operators ``AND``, ``OR``, and ``NOT`` in all caps.

**Note**: If multiple search terms are used without an operator, ``OR`` will be the assumed operator.

| Operator | Description |
|---|---|
| ``AND`` | AND operator. The query ``cat AND dog`` searches for both "cat" and "dog". |
| ``OR`` | OR operator. The query ``cat OR dog`` searches for either "cat" or "dog", or both. |
| ``NOT`` | NOT operator. The query ``cat NOT dog`` searches for "cat" or those without "dog". |
| ``*`` | Wildcard operator. Matches 0 or more characters. See [Wildcard operator](#wildcard--operator). |
| ``:`` | Field-scoped query. Specifies a field to search. See [Field-scoping operator](#field-scoping--operator). |
| ``" "`` | Quote operator. Searches  on an exact sequence of characters rather than searching on words separated by spaces or punctuation. See [Quote operator](#quote---operator). |
| ``( )`` | Precedence operator. The query ``wind AND (speed OR deviation)`` searches for either "wind" and "speed", or "wind" and "deviation". |

## Wildcard (``*``) operator

Searching for a value finds only exact, whole-word matches. As an example, searching for "temperature" will not match a field value of "temperatures". You can use the wildcard operator (``*``) to match a partial search term. The wildcard can be used in the front (``*``perature), middle (tem``*``rature), or at the end (temp``*``) of each search term. It can only be used once for each search term, except to enclose a term (``*``perat``*``). AVEVA Data Hub does not support wildcard operators in the middle and at the front or end of a term (te``*``pera``*`` is invalid).

| **Query string** | **Matches field value** | **Does not match field value** |
| ---------------- | ----------------------- | ------------------------------ |
| ``log*``         | log<br>logger           | analog                         |
| ``*log``         | analog<br>alog          | logg                           |
| ``*log*``        | analog<br>alogger       | lop                            |
| ``l*g``          | log<br>logg             | lake swimming (``*`` does not span across tokens) |

## Field-scoping (``:``) operator

The field-scoping operator limits the search to a specific field, such as ``id:``, ``name:``, ``description:``, and ``metadatakey:``.

Stream metadata keys are only searchable in association with their values. Without the field-scoping operator, a search is limited to metadata values, along with other searchable fields in the stream. For example, searching streams for "sourcetag" only finds items if they include sourcetag as a value, but searching for "sourcetag:*" finds all streams that have a sourcetag metadata key.

## Quote (``" "``) operator

Search automatically searches on text delimited by white space and punctuation. To search for values that include these delimiters, enclose the value in double quotes.

When using double quotes, the matching text must include the whole value of the field on the object being searched. Partial text will not match unless you use wildcards. For example, if you are searching for a document that has a description of `Pump three on unit five`, a query of `unit five` will not match the description, but a query of `"unit five"` will.

Also, you can use wildcards (the `*` asterisk character) on the outside of the quote operators, but if an asterisk is inside of the quotes, it is treated as a string literal rather than a wildcard operator. For example, you can search for `"pump three"*` (asterisk outside the quotes) to find text that starts with `"pump three"`, but if you search for `"pump three*"` (asterisk within the quotes), it only matches on a value of `"pump three*"`.

| **Matches field value** | **Does not match field value** |
|---|---|---|
| **``"pump pressure"``** | pump pressure | pressure, pressure pump, pump pressure gauge |
| **``"pump pressure"*``** | pump pressure, pump pressure gauge | pressure, pressure pump, the pump pressure gauge |
| **``*"pump pressure"``** | pump pressure, the pump pressure | pressure, pressure pump, the pump pressure gauge |
| **``*"pump pressure"*``** | pump pressure, the pump pressure, the pump pressure gauge | pressure, pressure pump |
| **``"pump*pressure"``** | pump*pressure | pump pressure, the pump pressure gauge |

## Special characters in search queries

Add the backslash escape character ( \ ) before any special characters in search queries. The following special characters require an escape character: " | / * \ ( ) : 

The following are examples of using the escape character in query strings.

| Example Field Value                    | Query String                               |
| -------------------------------------- | ------------------------------------------ |
| Austin\Dallas\Fort Worth               | Austin\\\Dallas\\\Fort Worth               |
| 1:100                                  | 1\\:100                                    |
| http://www.aveva.com                   | http\\:\\/\\/www.aveva.com                 | 

## Examples of query strings

| Query String | Applies to | Description |
|---|---|---|
| Id:Id1 | assets, streams, stream types, stream views | Returns the item whose Id is **Id1**. |
| Id:Id* | assets, streams, stream types, stream views | Returns all items with Ids that begin with **Id**. |
| Name:Name1 | assets, streams, stream types, stream views | Returns all items with a name equal to **Name1**. |
| Id:Id AND Name:Name1 | assets, streams, stream types, stream views | Returns the item with an Id equal to **Id** and a name equal to **Name1**. |
| Description:floor1* | assets, streams, stream types, stream views | Returns all items with a description that starts with **floor1**. |
| Metadata/Serial Number:M0000* | assets, streams | Return all items that include metadata of the name "Serial Number" that start with **M0000** (such as M000099 and M000001). |
| Id:X* AND Metadata/Location:B* | assets, streams | Returns all items that contains: <ul><li>An Id starting with **X**.</li><li>A metadata with the name <code>Location</code> that has a value that starts with <code>B</code> (such as "Boston").</li></ul> |
| Tags:MarkedAsset | assets, streams | Returns all items that have **MarkedAsset** as a tag. |
| AssetTypeId:HeaterTypeId | assets | Returns all items with AssetTypeId matching **HeaterTypeId**. |
| AssetTypeName:HeaterTypeName | assets | Returns all items whose asset type Name field matches **HeaterTypeName**. |
| StreamPropertyId:Pressure | assets | Returns all items that have one or more stream references with the stream property ID **Pressure**. Note: This search only searches non-key Sds stream properties. |
| StreamReferenceName:Name1 | assets | Returns all items whose stream references contain a stream reference name that matches **Name1**. |

## Search result examples

When searching for the following streams:

**streamId** | **Name**  | **Description**
------------ | --------- | ----------------
stream1      | tempA     | Temperature from DeviceA
stream2      | pressureA | Pressure from DeviceA
stream3      | calcA     | Calculation from DeviceA values

Entering the following queries returns the following streams:

**Query string**     | **Returns**
------------------  | ----------------------------------------
``temperature``  | stream1
``calc*``        | stream3
``DeviceA*``     | stream1, stream2, stream3
``humidity*``    | nothing

## Tooltip

Some **Search** and **Query** bars include a tooltip that opens when you select the bar. This tooltip includes information on how use search features like wildcards, filters, and operators.

**Search tooltip**

![search field displaying tooltip](../home/images/tooltip.png)

## Autocomplete

Autocomplete suggests useful search tokens or phrases as you type in a search field. Autocomplete complements the search experience by:

- Enhancing the search experience for users who may not know the available keywords.

- Preventing typos and reducing the need for wildcards, which can result in more complex queries.

Autocomplete includes suggestions for tokens, facets, and status matches, as well as search history.

**Search autocomplete**

![search field displaying autocomplete options](../home/images/autocomplete.png)

### Token Autocomplete

Token autocomplete suggestions consist of a single token and an occurrence count. Tokens available for autocomplete include all tokens that appear in properties with a searchable attribute. Suggestions are ranked by each token's occurrence count, which is the number of times that the token occurs in completable properties across all objects. For example, if "Minnesota" appears 200 times across objects in the index and "Mitsubishi" appears 100 times, a query `mi` would result in "Minnesota" being weighted higher and appearing first.

### Faceted Autocomplete

Faceted autocomplete suggestions consist of a collection of matching phrases, each with a list of categories and a object count for each category. The categories are the name of the property for properties comprising of simple types (Int32, DateTime, etc.) and collections of simple types (static facets). For collections of key-value pairs, the keys represent categories and the values represent phrases. Suggestions are ranked by the phrase's object count. In other words, the phrase that appears in the most number of objects ranks first in the results.
