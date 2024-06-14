---
uid: assets-filter-expressions-dev-guide
---

# Asset filter expressions

Filter expressions can be used to filter asset and asset type objects on their `CreatedDate` and `LastModifiedDate` property values. Filter expressions can be applied to all collection-level GET and HEAD operations for assets and asset types, including asset search.

## Logical operators

The following logical operators are supported for use within a filter expression:

| Operator   | Description                                                 |
|------------|-------------------------------------------------------------|
| `eq`       | Equal to                                                    |
| `ne`       | Not equal                                                   |
| `ge`       | Greater than or equal to                                    |
| `le`       | Less than or equal to                                       |
| `lt`       | Less than                                                   |
| `gt`       | Greater than                                                |
| `( )`      | Parenthesis can be used to affect the order of the operation|
| `or`       | Or logical operator                                         |
| `and`      | And logical operator                                        |
| `not`      | Not logical operator                                        |
| `-`        | Negation                                                    |

### Examples of logical operators

- `ModifiedDate gt 2015-01-01T00:00:00Z`
- `CreatedDate le 2018-01-01T00:00:00Z`
- `(ModifiedDate gt 2021-01-01T00:00:00Z) and (ModifiedDate lt 2021-01-02T00:00:00Z)`
- `not ModifiedDate gt 2023-01-01T00:00:00Z`

## DateTime functions

The following DateTime functions are supported for use within a filter expression:

| Function   | Description                   |
|------------|-------------------------------|
| `year`     | Get year value                |
| `month`    | Get month value               |
| `day`      | Get day value                 |
| `hour`     | Get hour value                |
| `minute`   | Get minute value              |
| `second`   | Get second value              |

### Examples of DateTime functions

- `year(CreatedDate) eq 2020`
- `month(CreatedDate) eq 11`
- `day(CreatedDate) eq 3`
- `hour(ModifiedDate) eq 8`
- `minute(ModifiedDate) eq 45`
- `second(ModifiedDate) eq 10`
