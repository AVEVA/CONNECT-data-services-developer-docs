---
uid: Search
---

# Search in OCS

Many pages in OCS include a search function. This topic describes the available search options.

## Search operators

You can use search operators to get more refined search results. Use the operators ``AND``,``OR``, and ``NOT`` in all caps.

**Note**: If multiple search terms are used without an operator, ``OR`` will be the assumed operator.

| Operator | Description |
|----------|-------------|
| ``AND`` | AND operator. The query ``cat AND dog`` searches for both "cat" and "dog". |
| ``OR``  | OR operator. The query ``cat OR dog`` searches for either "cat" or "dog", or both. |
| ``NOT`` | NOT operator. The query ``cat NOT dog`` searches for "cat" or those without "dog". |
| ``*``   | Wildcard operator. Matches 0 or more characters. See [Wildcard operator](#wildcard). |
| ``:``   | Field-scoped query. Specifies a field to search. See [Field-scoping operator](#fieldScoped). |
| ``( )`` | Precedence operator. The query ``wind AND (speed OR deviation)`` searches for either "wind" and "speed", or "wind" and "deviation". |

## <a name="wildcard"></a>Wildcard (``*``) operator

Searching for a value finds only exact, whole-word matches. As an example, searching for "process" will not match a field value of "processing". You can use the wildcard operator (``*``) to match a partial search term. The wildcard can be used in the front (``*``perature), middle (tem``*``rature), or at the end (temp``*``) of each search term. It can only be used once for each search term, except to enclose a term (``*``perat``*``). OCS does not support wildcard operators in the middle and at the front or end of a term (te``*``pera``*`` is invalid).

| **Query string** | **Matches field value** | **Does not match field value** |
| ---------------- | ----------------------- | ------------------------------ |
| ``log*`` | log<br>logger | analog |
| ``*log`` | analog<br>alog | logg |
| ``*log*`` | analog<br>alogger | lop |
| ``l*g`` | log<br>logg | lake swimming (``*`` does not span across tokens) |

### <a name="fieldScoped"></a>Field-scoping (``:``) operator

The field-scoping operator limits the search to a specific field, such as ``id:``, ``name:``, ``description:``, and ``metadatakey:``.

Stream metadata keys are only searchable in association with their values. Without the field-scoping operator, a search is limited to metadata values, along with other searchable fields in the stream.

## Special characters in search queries

Add the backslash escape character ( \ ) before any special characters in search queries. The following special characters require an escape character: " | / * \ ( ) : 

The following are examples of using the escape character in query strings.

| Example Field Value                    | Query String                               |
| -------------------------------------- | ------------------------------------------ |
| Austin\Dallas\Fort Worth               | Austin\\\Dallas\\\Fort Worth               |
| 1:100                                  | 1\\:100                                    |
| http://www.aveva.com                   | http\\:\\/\\/www.aveva.com                 | 

## Examples of asset query strings

| Query String                 | Description                                                  |
| ---------------------------- | ------------------------------------------------------------ |
| Id:Id1                       | Returns the asset with `Id` equal to **Id1**.                |
| Id:Id*                       | Returns all assets with `Id` matching **id*** wildcard.      |
| Name:Name1                   | Returns all asset with a friendly name equal to **Name1**.   |
| Id:Id AND Name:Name1         | Returns all assets with `Id` matching the **id** and with a friendly name equal to **Name1**. |
| Description:floor1*          | Returns all assets with a description that starts with **floor1**. |
| Metadata/Name:Building*      | Returns all assets with at least one metadata name whose description contains the string **Building**. |
| Metadata/Description:heater* | Returns all assets with at least one metadata whose description starts with **heater**. |
| Metadata/Value:123           | Returns all assets with at least one metadata whose Value property equals **123**. |
| Id:X* AND Metadata/Name:B*   | Returns all assets with `Id` starting with **X** and containing at least one metadata value with a name that starts with a **B**. |
| AssetTypeId:HeaterTypeId     | Returns all assets with `AssetTypeId` matching `HeaterTypeId` |
| AssetTypeName:HeaterTypeName | Returns all assets whose `Name` field of the asset type matches **HeaterTypeName** |
| StreamPropertyId:Pressure    | Returns all assets that have one or more stream references with the stream property ID **Pressure**. Note: This search only searches non-key Sds stream properties. |
| StreamReferenceName:Name1    | Returns all assets whose stream references contain a stream reference name that matches **Name1**. |
| Tags:MarkedAsset             | Returns all assets which have "MarkedAsset" as a tag.         |
