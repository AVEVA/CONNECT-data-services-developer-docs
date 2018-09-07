---
uid: sdsReadingData
---

#### Qi_Reading_data_topic

Reading data
============

The REST APIs provide programmatic access to read and write data. This section identifies and describes 
the APIs used to read [Qi_Stream_topic](xref:sdsStreams#qistreamtopic) data. Results are influenced by [Qi_Types_topic](xref:sdsTypes#qitypetopic),  
[Sds_View_topic](xref:sdsViews), [Qi_Filter_expressions_topic](xref:sdsFilterExpressions), and [Qi_Table_format_topic](xref:sdsTableFormat).

If you are working in a .NET environment, convenient SDS Client libraries are available. 
The ``ISdsDataServiceinterface``, which is accessed using the ``SdsService.GetDataService()`` helper, 
defines the functions that are available.

The following methods for reading a single value are available:

* ``Get Value`` returns a value at a specified index, calculated if no stored value exists at that index. 
* ``Get First Value`` returns the first value in the stream.
* ``Get Last Value`` returns the last value in the stream.
* ``Get Distinct Value`` returns a value at the specified index, only if a stored value exists at that index.
* ``Find Distinct Value`` searches for a value based on a starting index and search criteria.

In addition, the following methods support reading multiple values:

* ``Get Values`` retrieves a collection of values at specified indexes, calculated if no stored 
  value exists at the index(es). ``Get values`` supports specifying the desired indexes as a list of indexes, 
  a filter expression and count, or a starting index, ending index, and count.
* ``Get Range Values`` retrieves a collection of stored values based on the specified start index and count.
* ``Get Window Values`` retrieves a collection of stored values based on specified start and end indexes.
* ``Get Intervals`` retrieves a collection of evenly spaced summary intervals based on a count 
  and specified start and end indexes.

All reads are HTTP GET actions. Reading data involves getting events from streams. The base reading URI is as follows:

``api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Data``


**where:**

``string tenantId``
  The tenant identifier
``string namespaceId``
  The namespace identifier
``string streamId``
  The stream identifier


Response Format
---------------

Supported response formats include json, verbose json, and Sds. 

The default response format for is json, which is used in all examples in this document.  Default json 
responses do not include any values that are equal to the default value for their type.

Verbose json responses include all values, including defaults, in the returned json payload. To specify 
verbose json return, add the header ``Accept-Verbosity`` with a value of ``verbose`` to the request.  

To specify SDS format, set the ``Accept`` header in the request to ``application/Sds``.

Indexes and reading data
------------------------

Most read operations take at least one index as a parameter. Indexes may be specified as strings, or, 
when using the Sds Client libraries, the index may be passed as-is to read methods that take the index 
type as a generic argument. Additional details about working with indexes can be found on the [Indexes_topic](xref:sdsIndexes) page.

Read Characteristics
--------------------

When data is requested at an index for which no stored event exists, the read characterisitics determine 
whether the result is an error, null event, interpolated event, or extrapolated event. The combination of 
the type of the index and the interpolation and extrapolation modes of the SdsType and the SdsStream 
determine the read characteristics. For more information on read characteristics, 
see [QiType_topic](xref:sdsTypes#qitypetopic) and [Qi_Stream_topic](xref:sdsStreams#qistreamtopic).

**Methods affected by Read Characteristics**

`GetValueAsync <https://qi-docs-rst.readthedocs.org/en/latest/Reading_Data_API.html#getvalueasync>`__
  Read characteristics are applied when the index is between, before, or after all data.

`GetValuesAsync <https://qi-docs-rst.readthedocs.org/en/latest/Reading_Data_API.html#getvaluesasync>`__
  Read characteristics applied when an index determined by the call is between, before, or after all data.

`GetWindowValuesAsync <https://qi-docs-rst.readthedocs.org/en/latest/Reading_Data_API.html#getwindowvaluesasync>`__
  Read characteristics applied to indexes between, before, or after data when the calls Boundary parameter is set to ExactOrCalculated.

`GetRangeValuesAsync <https://qi-docs-rst.readthedocs.org/en/latest/Reading_Data_API.html#getrangevaluesasync>`__
  Read characteristics applied to indexes between, before, or after data when the calls Boundary parameter is set to ExactOrCalculated.

SdsView and reading data
------------------------

All reads support specifying a SdsView identifier in the query string to shape the results of the read:

``viewId={viewId}``

Working with views is covered in detail in the [Sds_View_topic](xref:sdsViews) section.

When data is requested with a SdsView the read characteristics defined by the *target type* of the SdsView 
determine what is returned. The read characteristics are discussed in the *Get Value*, 
*GetValues* and *GetWindowValues* code samples.

Filter Expressions
------------------

Filter expressions can be applied to any read that returns multiple values, including Get Values, Get Range Values, 
Get Window Values, and Get Intervals. The filter expression is applied to the collection events conditionally 
filtering events that do not meet the filter conditions.

Filter expressions are covered in detail in the [Qi_Filter_expressions_topic](xref:sdsFilterExpressions) section.

Table Format
------------

Results of a query can be organized into tables by directing the form parameter to return a table. 
Two forms of table are available: table and header table.

When the form parameter is specified as table, ``?form=table``, events are returned in row column form. 
Results include a collection named ``Columns`` that lists column name and type and a collection named 
``Rows`` containing a collection of rows matching the order of the columns.

Specifying a form of type ``table-headers``, ``?form=tableh``, results in a collection where the Rows collection 
contains a column header list.

Table formats are covered in detail in the [Qi_Table_format_topic](xref:sdsTableFormat) section.


SdsBoundaryType
--------------

SdsBoundaryType defines how data on the boundary of queries is handled: around the start index for range value queries, 
and around the start and end index for window values. The following are valid values for SdsBoundaryType:

| Boundary          | Enumeration value                 | Operation                                                     |
|-------------------|-----------------------------------|---------------------------------------------------------------|
| Exact             | 0                                 | Results include the event at the specified index boundary     |
|                   |                                   | if a stored event exists at that index.                       |
| Inside            | 1                                 | Results include only events within the index boundaries       |
| Outside           | 2                                 | Results include up to one event that falls immediately        |
|                   |                                   | outside of the specified index boundary.                      |
| ExactOrCalculated | 3                                 | Results include the event at the specified index boundary. If |
|                   |                                   | no stored event exists at that index, one is calculated based |
|                   |                                   | on the index type and interpolation and extrapolation         |
|                   |                                   | settings.                                                     |

SdsSearchMode
-------------

The SdsSearchMode enum defines search behavior when seeking a stored event near a specified index. The following are 
available SdsSearchModes:

| Mode              | Enumeration value                 | Operation                                                     |
|-------------------|-----------------------------------|---------------------------------------------------------------|
| Exact             | 0                                 | If a stored event exists at the specified index, that event   |
|                   |                                   | is returned. Otherwise no event is returned.                  |
| ExactOrNext       | 1                                 | If a stored event exists at the specified index, that event   |
|                   |                                   | is returned. Otherwise the next event in the stream is        |
|                   |                                   | returned.                                                     |
| Next              | 2                                 | Returns the stored event after the specified index.           |
| ExactOrPrevious   | 3                                 | If a stored event exists at the specified index, that event   |
|                   |                                   | is returned. Otherwise the previous event in the stream is    |
|                   |                                   | returned.                                                     |
| Previous          | 4                                 | Returns the stored event before the specified index.          |

Reading data API and examples
-----------------------------

Many of the API methods described below contain sample JSON and sample code. 

When specifying a parameter of type enum, the API accepts both the name of the field and the numeric value of the field. 
Samples vary to highlight enum flexibility.

Samples use the following types:

Type with a simple index, named *Simple*:

**.NET**

      public enum State
      {
        Ok,
        Warning,
        Alarm
      }

      public class Simple
      {
        [SdsMember(IsKey = true, Order = 0) ]
        public DateTime Time { get; set; }
        public State State { get; set; }
        public Double Measurement { get; set; }
      }

**Python**

      class State(Enum):
        Ok = 0
        Warning = 1
        Alarm = 2

      class Simple(object):
        Time = property(getTime, setTime)
        def getTime(self):
          return self.__time
        def setTime(self, time):
          self.__time = time

        State = property(getState, setState)
        def getState(self):
          return self.__state
        def setState(self, state):
          self.__state = state

        Measurement = property(getValue, setValue)
        def getValue(self):
          return self.__measurement
        def setValue(self, measurement):
          self.__measurement = measurement

**JavaScript**

      var State =
      {
        Ok: 0,
        Warning: 1,
        Alarm: 2,
      }

      var Simple = function () {
        this.Time = null;
        this.State = null;
        this.Value = null;
      }

Has values as follows:

      11/23/2017 12:00:00 PM: Ok  0
      11/23/2017  1:00:00 PM: Ok 10
      11/23/2017  2:00:00 PM: Ok 20
      11/23/2017  3:00:00 PM: Ok 30
      11/23/2017  4:00:00 PM: Ok 40

Type with Compound Index, named ``DerivedCompoundIndex``


**.NET**

      public class Simple
      {
        [SdsMember(IsKey = true, Order = 0)]
        public DateTime Time { get; set; }
        public State State { get; set; }
        public Double Measurement { get; set; }
      }

      public class DerivedCompoundIndex : Simple
      {
        [SdsMember(IsKey = true, Order = 1)]
        public DateTime Recorded { get; set; }
      }

**Python**

      class Simple(object):
      # First-order Key property
      Time = property(getTime, setTime)
      def getTime(self):
        return self.__time
      def setTime(self, time):
        self.__time = time

      State = property(getState, setState)
      def getState(self):
        return self.__state
      def setState(self, state):
        self.__state = state

      Measurement = property(getValue, setValue)
      def getValue(self):
        return self.__measurement
      def setValue(self, measurement):
        self.__measurement = measurement

      class DerivedCompoundIndex(Simple):
      # Second-order Key property
      @property
      def Recorded(self):
        return self.__recorded
      @Recorded.setter
      def Recorded(self, recorded):
        self.__recorded = recorded

**JavaScript**

      var Simple = function () {
        this.Time = null;
        this.State = null;
        this.Value = null;
      }

      var DerivedCompoundIndex = function() {
        Simple.call(this);
        this.Recorded = null;
      }

Has values as follows:

      1/20/2017 1:00:00 AM : 1/20/2017 12:00:00 AM 	0
      1/20/2017 1:00:00 AM : 1/20/2017  1:00:00 AM 	2
      1/20/2017 1:00:00 AM : 1/20/2017  2:00:00 PM 	5
      1/20/2017 2:00:00 AM : 1/20/2017 12:00:00 AM 	1
      1/20/2017 2:00:00 AM : 1/20/2017  1:00:00 AM 	3
      1/20/2017 2:00:00 AM : 1/20/2017  2:00:00 AM 	4
      1/20/2017 2:00:00 AM : 1/20/2017  2:00:00 PM 	6

All times are represented at offset 0, GMT.
