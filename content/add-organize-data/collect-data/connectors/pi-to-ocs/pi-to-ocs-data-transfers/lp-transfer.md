---
uid: lp-transfer
---

# Transfer PI System data to AVEVA Data Hub

To transfer AF elements and PI System data to AVEVA Data Hub, you must set filter criteria and select the data for the transfer. Then, you can stream the selected AF elements and PI points from your on-premises PI System to AVEVA Data Hub.

The following tasks must be performed before you can complete a data transfer:

1. Download and install the PI to Data Hub Agent.

2. Configure your PI System data source connections by adding the desired Data Archive and optional AF server.

3. Create a data transfer by adding the desired AF elements and/or PI points.

## Historical transfer

During the creation of a transfer, you have the option of including historical data. You specify the start time for a historical data transfer. When the start time is in the past, before `*` in PI terminology, the PI to Data Hub Agent asks Data Archive for past data. The PI to Data Hub Agent retrieves the data between the start time and the time when the transfer started. The data it collects is referred to as the historical transfer.

## Backfilling

When a PI to Data Hub Agent shuts down in the middle of a transfer, it needs to fill this gap after it starts back up. During normal operation, the agent signs up for updates from Data Archive. This signup is lost when the agent shuts down. When the agent starts back up, it signs up for updates again, but it must fill the gap for the shutdown period by retrieving historical data from Data Archive. The gap-filling process is called backfilling and this part of the transfer is referred to as a "backfill transfer job".

For example, if the service shuts down for two hours, it will have to sign up for updates when it starts back up again. However, the PI to Data Hub Agent cannot use updates to retrieve the data for the two hours it was down. Instead, it queries Data Archive for historical data. In this example, the "backfill transfer job" fills the gap for these two hours.

## Historical transfer versus backfilling

Historical transfer fills the gap between a configured, past start time and the time the transfer started. Backfilling fills the data from the time the transfer stopped to the time the transfer resumed.
