---
uid: overview-data-transfers
---

# Overview of data transfers
<!--AF 11/15/21 This topic should be the first one in the data transfers section. --> 
<!--VT, 11/29/21: According to the toc.yml for this section, it is the first topic. I think the edits I made in PR #764 address your concern. :) -->
To transfer AF elements and PI System data to AVEVA Data Hub, you must set filter criteria and select the data for the transfer. Then, you can stream the selected AF elements and PI points from your on-premises PI System to AVEVA Data Hub.

The following tasks must be performed before you can complete a data transfer:

1. Download and install the PI to Data Hub Agent.

2. Configure your PI System data source connections by adding the desired Data Archive and optional AF server.

3. Create a data transfer by adding the desired AF elements and/or PI points.

## Historical transfer

During the creation of a transfer, you have the option of including historical data. You specify the start and end times for a historical data transfer. When the start time is in the past, that is before `*` in PI terminology, the PI to Data Hub Agent asks PI Data Archive for past data. The PI to Data Hub Agent retrieves the data between the start time and the time when the transfer started. The data it collects is referred to as the historical transfer.

## Backfilling

Backfilling is the process of transferring missing data. It happens when a PI to Data Hub Agent shuts down while it is transferring data. When a PI to Data Hub Agent is stopped or the PI to Data Hub Agent Windows service shuts down, it loses its update signup. For example, if the service shuts down for two hours, it will have to re-signup for updates when it becomes available; however, the PI to Data Hub Agent cannot use updates to retrieve the data for the two hours it was down. In this example, the backfill transfer job fills the gap for these two hours.

## Historical transfer versus backfilling

Historical transfer fills the gap between a configured, past start time and the time the transfer started. Backfilling fills the data for the time period that a configured transfer stopped up until the time the transfer resumed again.
