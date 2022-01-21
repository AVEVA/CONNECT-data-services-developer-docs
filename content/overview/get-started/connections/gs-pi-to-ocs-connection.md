---
uid: gsPItoOCS
---

# Get started with PI to Data Hub connections

Before you set up your PI to Data Hub connection, see [PI System best practices](xref:bpPISystemConnection) for recommendations on the PI Data Hub Agent.

To use PI to Data Hub to transfer data from your PI System to AVEVA Data Hub, you must complete the following tasks:

- Install the PI to Data Hub Agent.

- Set up your PI to Data Hub connection in the PI to Data Hub Configuration Utility.

- Create a data transfer.

**Prerequisite:** The exercise below assumes that your organization has a PI System with default PI points (for example, `sinusoid`) stored on Data Archive.

To set up a PI to Data Hub transfer, follow these steps:

1. In the left pane, select **Data Collection** > **PI to Data Hub Agents**.

1. Select **Download Agent**, then follow the instructions in [Install the PI to Data Hub Agent](xref:install-agent).

1. After agent installation, follow the instructions in [Run the PI to Data Hub Agent Configuration Utility](xref:pi-to-ocs-utility) to set up your PI to Data Hub connection and register your agent on AVEVA Data Hub.

1. After successful data source configuration, return to the `PI to Data Hub Agents` window in the AVEVA Data Hub portal.

1. Select your PI to Data Hub Agent connection in the `PI to Data Hub Agents` window, then select **Create Transfer** in the right pane.

1. Follow the procedures in [Transfer data to AVEVA Data Hub](xref:transfer-data) to define transfer settings and transfer data into AVEVA Data Hub.

## Next step

If you have not already completed [Get started with OMF connections](xref:gsOMF), do this next. Otherwise, continue with [Get started with types](xref:gsTypes).
