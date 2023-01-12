If the data view is modified, any cached information is reset. There is no guarantee of the durability or lifespan of cached information. If that cached information is invalidated, the data view is re-resolved the next time that information is requested.

Cached information may be reset under any of the following circumstances:

- The data view is modified

- A community referenced by the data view is modified (for example, sharing is paused)

- The cached information expires

- System maintenance