
---
uid: sdsFilterExpressionsObjects
---

#### Sds_Filter_expressions_objects_topic

Filter Expressions: Objects
==================

This section focuses on filter expressions that can be applied to certain read operations that return Sequential Data Store objects. For filtering on read operations of Sequential Data Store values refer to [Filter Expressions: Values](xref:sdsFilterExpressions#Sds_Filter_expressions_topic).

Filter expressions can be applied to any read that returns multiple values, including 
``Get Types`` and ``Get Streams``. 


Fields
------------
For Streams and Types the filter expressions are valid for the same properties that are valid for the Search parameter. Valid fields 
for both Streams and Types would be ``Name``, ``Id``, and ``Description``. 

Types additionally have a an IList of SdsTypeProperty objects named ``Properties``.
For object filter expressions we add all SdsTypeProperty Names and Ids to a collection of strings and that collection is mapped to the field name ``Properties``. 
Note that this string collection version of ``Properties`` includes all related SdsTypeProperty Names and Ids, including Base SdsType objects
that the object in question derives from.

String functions
------------

**Supported**

String operations are case insensitive. The following string functions are supported for use within a
filter expression:

| function      | Comment                                                         |
|---------------|-----------------------------------------------------------------|
| ``endswith``  | Compare the character at the end of the input string            |
| ``startwith`` | Compare the character at the start of the input string          |
|``substringof``| Search for characters anywhere in another string                |

**String function examples**


|Example                                      |Result                                                           |
|---------------------------------------------|-----------------------------------------------------------------|
|``endswith(Name, 'xyz')``                  |True if ``Name`` ends with the string ‘xyz’                |
|``startswith(Id, 'abc')``                 |True if ``Id`` starts with the string ‘abc’              |
|``substringof('bc', Name)``                 |True if string ‘bc’ is found anywhere in ``Name``         |


Logical operators
------------

**Supported**

The following logical operators are supported for use within an object filter
expression:

| Operator   | Comment                                             |
|------------|-----------------------------------------------------|
| ``eq``     | Equal to                                            |
| ``( )``    | Parenthesis can be used to affect the order of the operation|
| ``or``     | Or logical operator                                 |
| ``and``    | And logical operator                                |
| ``not``    | Not logical operator                                |

Not all operators supported for [values](xref:sdsFilterExpressions#Sds_Filter_expressions_topic) are 
supported for filtering on object metadata string fields.

**Logical Operator Examples**

The following examples show logical operators and string functions.

- ``Name eq 'abcxyz'``
- ``startswith(Id, 'abc') and endswith(Id, 'xyz')``
- ``startswith(Id, 'abc') or startswith(Name, 'abc')``
- ``not (Name eq 'abcxyz')``
- ``(startswith(Id, 'abc') and endswith(Id, 'xyz')) or (startswith(Name, 'abc') and endswith(Name, 'abc'))``


