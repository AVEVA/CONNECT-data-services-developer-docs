---
uid: accountServiceBlog
---

ServiceBlog
=======================================================

API's for CRUD operations on ServiceBlog

***

### `GetByPage()`

Returns blog entries ordered by time posted.

**Http**

`GET api/ServiceBlog/Entries`

**Parameters**

```csharp
string skip
```
Number of blogs to skip for paging purposes
```csharp
string count
```
Blogs to count after skip for paging purposes


**Security**

Any identity, including anonymous

**Returns**

Returns an object including an IEnumerable of blogEntries and an int with the total number of entries.

***
