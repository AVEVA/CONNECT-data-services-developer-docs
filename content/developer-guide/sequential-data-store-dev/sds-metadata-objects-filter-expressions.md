---
uid: sdsFilterExpressionsObjects
---

# Filter expressions for SDS objects

Filter expressions can be applied to read operations (such as [List Types](xref:sds-types#list-types) and [List Streams](xref:sds-streams#list-streams)) that return Sequential Data Store (SDS) objects (SdsTypes, SdsStreams, SdsStreamViews, SdsUomQuantities, and SdsUoms). All filter expressions for metadata objects are case-insensitive.

## Logical operators

The following logical operators are supported for use within a filter expression:

| Operator | Description                                                  |
| -------- | ------------------------------------------------------------ |
| `eq`     | Equal to                                                     |
| `ne`     | Not equal                                                    |
| `ge`     | Greater than or equal to                                     |
| `le`     | Less than or equal to                                        |
| `lt`     | Less than                                                    |
| `gt`     | Greater than                                                 |
| `( )`    | Parenthesis can be used to affect the order of the operation |
| `or`     | Or logical operator                                          |
| `and`    | And logical operator                                         |
| `not`    | Not logical operator                                         |
| `-`      | Negation                                                     |

> [!NOTE]
>
> You can use logical operators on ordered properties.  
> You can only use negation on numeric properties.

### Examples of logical operators

The examples below are using the `CreatedDate` and `ModifiedDate` properties of an SDS object, which are of type _DateTime_:

- `ModifiedDate gt 2022-12-06T00:00:00Z`
- `CreatedDate le 2022-01-01T00:00:00Z`
- `(ModifiedDate gt 2022-12-06T00:00:00Z) and (CreatedDate le 2022-01-01T00:00:00Z)`
- `(ModifiedDate gt 2022-12-06T00:00:00Z) and (ModifiedDate lt 2022-12-07T00:00:00Z)`
- `not ModifiedDate gt 2022-12-06T00:00:00Z`

## Math functions

The following math functions are supported for use within a filter expression:

| Function | Description |
| --- | --- |
| `add` | Addition |
| `sub` | Subtraction |
| `mul` | Multiplication |
| `div` | Division |
| `mod` | Modulo |
| `round` | Rounds to the nearest numeric component without a decimal, with the midpoint rounded away from 0. For example, 0.5 rounds to 1; -0.5 rounds to -1) |
| `floor` | Rounds down to the nearest numeric component without a decimal |
| `ceiling` | Rounds up to the nearest numeric component without a decimal |

### Examples of math functions

The examples below use the `ConversionFactor` and `ConversionOffset` properties of an SdsUom, which are of type _double_:

- `ConversionFactor eq (6.0 add 3.0)`
- `ConversionFactor eq (6.0 sub 3.0)`
- `ConversionFactor eq (6.0 mul 3.0)`
- `ConversionFactor eq (6.0 div 3.0)`
- `ConversionOffset eq (7.0 mod 3.0)`
- `round(ConversionOffset) eq 16`
- `floor(ConversionOffset) eq 15`
- `ceiling(ConversionOffset) eq 16`

## String functions

The character index in a string is zero-based. The following string functions are supported for use within a filter expression:

| Function | Description |
| --- | --- |
| `endswith` | Compare the character at the end of the input string |
| `startswith` | Compare the character at the start of the input string |
| `length` | Examines the string length |
| `indexof` | Examines the character starting at a given index |
| `substring` | Examine characters within another string at a specific location |
| `contains` | Search for characters anywhere in another string |
| `tolower` | Convert characters to lowercase |
| `toupper` | Convert characters to uppercase |
| `trim` | Remove whitespace from front and end of a string |
| `concat` | Concatenate strings together |
| `replace` | Replace one set of characters with another |

### Examples of string functions

The examples below are using the `Id`, `Name`, and `Description` properties of an SDS object, which are of type _string_:

| Example | Result |
| --- | --- |
| `endswith(Id, 'XYZ')` | True if `Id` ends with the characters ‘XYZ’ |
| `startswith(Id, 'Val'` | True if `Id` starts with the characters ‘Val’ |
| `length(Id) eq 11` | True if `Id` is 11 characters |
| `indexof(Id, 'ab') eq 4` | True if the 5th and 6th characters of `Id` are ‘ab’ |
| `contains(Description, 'ab')` | True if characters ‘ab’ are found anywhere in `Description` |
| `substring(Description, 10) eq 'a b'` | True if ‘a b’ is found in `Description` at index 10 |
| `tolower(Name) eq 'val5'` | Change `Name` to lowercase and compare to ‘val5’ |
| `toupper(Name) eq 'ABC'` | Change `Name` to uppercase and compare to ‘ABC’ |
| `trim(Name) eq 'vall22'` | Trim whitespace from front and end of `Name` and compare to ‘val22’ |
| `concat(Name,'xyz') eq 'dataValue_7xyz'` | Add characters to `Name` and compare to ‘dataValue_7xyz’ |
| `replace(Name,'L','D') eq 'Dog1'` | Replace any ‘L’ in `Name` with ‘D’ and compare to ‘Dog1’ |

## DateTime functions

The following DateTime functions are supported for use within a filter expression:

| Function | Description                    |
| -------- | ------------------------------ |
| `year`   | Get year value from DateTime   |
| `month`  | Get month value from DateTime  |
| `day`    | Get day value from DateTime    |
| `hour`   | Get hour value from DateTime   |
| `minute` | Get minute value from DateTime |
| `second` | Get second value from DateTime |

### Examples of DateTime functions

The examples below are using the `CreatedDate` and `ModifiedDate` properties of an SDS object, which are of type _DateTime_:

- `year(CreatedDate) eq 2015`
- `month(CreatedDate) eq 11`
- `day(CreatedDate) eq 3`
- `hour(ModifiedDate) eq 1`
- `minute(ModifiedDate) eq 5`
- `second(ModifiedDate) eq 3`
