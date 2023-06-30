---
uid: StatusDefinitions
---

# System status definitions

The following table lists the system status definitions for systems in AVEVA Data Hub.

| Status | Meaning |
|---|---|
| ``Good`` | The system is connected to the data source and it is collecting data. |
| ``Starting`` | The system is currently in the process of starting up and is not yet connected to the data source. |
| ``Attempting Failover`` | The system is switching to the standby server due to failure or scheduled downtime. |
| ``Connected / No Data`` | The system is connected to the data source but it is not receiving data from it. |
| ``Not Configured`` | The system is created but not yet configured. |
| ``Server Error`` | The system encountered an error either while connecting to the data source or attempting to collect data. |
| ``Unknown`` | The system is experiencing an unknown connection error. |
| ``Device in error`` | The system encountered an error either while connecting to the data source or attempting to collect data. |
| ``Removed`` | The system has been removed and will no longer collect data. |
| ``Shutdown`` | The system is either in the process of shutting down or has finished. |