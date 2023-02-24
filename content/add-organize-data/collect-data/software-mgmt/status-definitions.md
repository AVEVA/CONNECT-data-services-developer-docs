---
uid: StatusDefinitions
---

# Edge system status definitions

The following table lists the system status definitions for edge systems in AVEVA Data Hub.

| Status | Meaning |
|---|---|
| ``Good`` | The edge system is connected to the data source and it is collecting data. |
| ``Starting`` | The edge system is currently in the process of starting up and is not yet connected to the data source.. |
| ``Attempting Failover`` | The edge system is switching to the standby server due to failure or scheduled downtime. |
| ``Connected / No Data`` | The edge system is connected to the data source but it is not receiving data from it. |
| ``Not Configured`` | The edge system is created but not yet configured. |
| ``Server Error`` | The edge system encountered an error either while connecting to the data source or attempting to collect data. |
| ``Unknown`` | The edge system is experiencing an unknown connection error. |
| ``Device in error`` | The edge system encountered an error either while connecting to the data source or attempting to collect data. |
| ``Removed`` | The edge system has been removed and will no longer collect data. |
| ``Shutdown`` | The edge system is either in the process of shutting down or has finished. |