
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

Streams additionally have a ``TypeId`` field that is filterable.

Types additionally have a field ``Properties`` that is a collection of SdsTypeProperty Id and Name values. This is composed based on the IList of SdsTypeProperty objects that is a member of the Sds Type (also named ``Properties``). The filter (as well as [search](xref:sdsSearching#qisearchingtopic)) functionality of Sds Types and Streams is intended for string values and therefore we only filter on the Names and Ids of SdsTypeProperty objects associated with a given Sds Type. Note that this string collection version of ``Properties`` includes all related SdsTypeProperty Names and Ids, including Base SdsType objects that the Sds Type object in question derives from. Lastly, to filter on a collection the Any() or All() functions must be used, see [Lambda Operators](#Sds_Filter_expressions_objects_lambda_operators_topic).

## <a name="Sds_Filter_expressions_objects_string_functions_topic"></a>String functions

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


## <a name="Sds_Filter_expressions_objects_logical_operators_topic"></a>Logical operators

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
- ``startswith(Id, 'abc') and not endswith(Id, 'xyz')``
- ``(startswith(Id, 'abc') and endswith(Id, 'xyz')) or (startswith(Name, 'abc') and endswith(Name, 'abc'))``

## <a name="Sds_Filter_expressions_objects_lambda_operators_topic"></a>Lambda operators

**Supported**

The following lambda operators are supported for use within an object filter
expression:

| Operator   | Comment                                             |
|------------|-----------------------------------------------------|
| ``any``    | Match if any elements of the collection match the criteria|
| ``all``    | Match if all elements of the collection match the criteria|

The lambda operators require defining a lambda parameter and a boolean expression. Note that currently the only supported boolean expressions for the nested clause of the lambda operators are the three string functions and the equals logical operator. Other [logical operators](#Sds_Filter_expressions_objects_logical_operators_topic) are not allowed.

**Lambda Operator Examples**

The following examples show logical operators which have a body defining the required lambda parameter and a single boolean expression. The lambda parameter is defined initially, and in the provided examples the user has chosen a query time lambda parameter named "parameter". After the ':' proceed to define your expression as defined in the aforementioned examples for [string functions](#Sds_Filter_expressions_objects_string_functions_topic) (or the 'eq' [logical operator](#Sds_Filter_expressions_objects_logical_operators_topic)) but replace all references to your SdsType/SdsStream field name with the lambda parameter name.

- ``Properties/any(parameter: parameter eq "value")``
- ``Properties/all(parameter: startswith(parameter, 'abc'))``
