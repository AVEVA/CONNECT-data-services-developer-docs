---
uid: VerifyPItoADHService
---

# Verify the PI to Data Hub Agent is running and registered

As a first step in troubleshooting, check that the PI to Data Hub Agent Windows service is running on the machine where the agent is installed. You also should confirm the agent is registered in AVEVA Data Hub. For a new installation, the PI to Data Hub Agent service will not be running and registered until the PI to Data Hub Configuration Utility is completed.

1. On the computer where the agent is installed, open the Microsoft Management Console (MMC) snap-in for Services. 

   **Tip:** Enter *services.msc* in Windows search to locate the application.

1. In the `Services` window, find the PI to Data Hub Agent service and verify that the status is `Running`, then close the window.

   ![](../../images/services-window.png)

1. In the AVEVA Data Hub portal, in the left pane, select **Data Collection** > **PI to Data Hub Agents**.

1. On the `PI to Data Hub Agents` page, select the connection you created.

1. On the `Details` pane, verify that Registered appears next to **Agent Status**.

   ![Agent status](../../images/details-pane.png)

   **Note:** The agent status is also displayed in the PI to Data Hub Configuration Utility. For a list of states and descriptions that explain why an agent may not be running, see [List of agent status states](xref:pi-to-ocs-utility#list-of-agent-states).
