---
uid: install-agent
---

# Install the PI to Data Hub Agent

When you install the PI to Data Hub Agent, make sure to follow these guidelines:

- Install the agent on a host computer separate from your PI Server deployment.

- Use a domain account that has been granted Administrator privileges on a computer registered to the same domain.

- Enable read access to Data Archive security tables and the PI points and data to be transferred.

- Enable read access to the AF server elements and attributes to be transferred.

- Use an account that is assigned to the `Tenant Administrator` role for the PI to Data Hub Agent installation.

You can download the PI to Data Hub Agent from the PI to Data Hub Agents page on the portal and then transfer it to the computer that will host the agent.

**Note:** The PI to Data Hub Agent installation cannot be completed if the system time is not correct. Additionally, you will not be able to complete the PI to Data Hub Agent installation if Internet Explorer Enhanced Security Configuration is enabled. For more information, see [Disable Internet Explorer Enhanced Security Configuration](xref:disable-ie-security). 

## Configure access to PI Data Archive Security tables, PI point data, and optional AF server

**Important:** The PI to Data Hub Agent requires the Windows service account to `Run as user`. Enable read access to the following PI Server data:

- Archive data (PIARCDATA Security table)

- The PI points configuration table (PIPOINT Security table)

- The PI points and data to be transferred

- The AF server elements and attributes to be transferred 

## Install the PI to Data Hub Agent

To install the PI to Data Hub Agent:

1. In the left pane, select **Data Collection** > **PI to Data Hub Agents**.

1. Select **Download Agent**.

1. On the `Agent Installer Download` window, select **Download**. When the download completes, close the window.

1. Open the downloaded PI to Data Hub agent installation file, then select **Yes** to confirm running the installation file.
   
   The `Welcome` page of the PI to Data Hub Agent window opens.

1. On the `Welcome` page, select **Next**.

   You are logged on to your tenant account. A message opens in your web browser regarding the status of the user authentication process. 

1. Close the browser window, and then select **Next** on the `Browser Login` page.

1. On the `Namespace` page, complete the following fields, then select **Next**:

   - **Namespace** - Select the namespace and location where the transferred data will be stored. The location is a region that appears in parenthesis after the namespace indicates where the namespace resides. Streaming data sent by the PI to Data Hub Agent only goes to the selected namespace's region.

   - **Agent Description** - Enter an optional name for the agent.

   The `Service Account` page opens.

1. On the `Service Account` page, select the service account type for the connection:

   - **NT Service** - Enter an NT account to connect to PI Data Archive.

   - **This account** - Specify a user name and password (domain\account) to connect to PI Data Archive.

   **Note:** The service account used to run the PI to Data Hub Service requires Administrator privileges. Read access to the PIARCDATA Security and PIPOINT Security tables, the PI points and data to be transferred, and the AF server, elements, and attribute data is required.

1. Select **Install**.

1. After the agent is installed, select **Close**.

   The PI to Data Hub Configuration Utility opens. See [Run the PI to Data Hub Agent Configuration Utility](xref:pi-to-ocs-utility) for instructions.

   **Note:** An agent cannot be registered until a PI Data Archive server has been added and configured in the PI to Data Hub Configuration Utility.

## Verify the PI to Data Hub Agent is running and registered

After installation, check that the PI to Data Hub Agent Windows service is running on the machine where the agent is installed. You also should confirm the agent is registered in AVEVA Data Hub. 

To verify the installation:

1. On the computer where the agent is installed, open the Microsoft Management Console (MMC) snap-in for Services. <!--Angela Flores 11/12/21 there is no mention of selecting a host machine for this installation before this point.-->

   **Tip:** Enter *services.msc* in Windows search to locate the application.

1. In the `Services` window, find the PI to Data Hub Agent service and verify that the status is `Running`, then close the window.

   ![](../../images/services-window.png)

1. In the AVEVA Data Hub portal, in the left pane, select **Data Collection** > **PI to Data Hub Agents**.

1. On the `PI to Data Hub Agents` page, select the connection you created.

1. On the `Details` pane, verify that Registered appears next to **Agent Status**.

   ![Agent status](../../images/details-pane.png)

   **Note:** The agent status is also displayed in the PI to Data Hub Configuration Utility. For a list of states and descriptions that explain why an agent may not be running, see [List of agent status states](xref:pi-to-ocs-utility#list-of-agent-states).
