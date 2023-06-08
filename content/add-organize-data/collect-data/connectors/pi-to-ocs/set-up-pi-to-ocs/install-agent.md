---
uid: install-agent
---

# Install the PI to Data Hub Agent

The PI to Data Hub Agent can be installed as part of the PI Server installation kit, or as a standalone install. When you install the PI to Data Hub Agent, make sure to follow these guidelines:

- Use a domain account that has been granted Administrator privileges on a computer registered to the same domain.

- Enable read access to Data Archive security tables and the PI points and data to be transferred.

- Enable read access to the AF server elements and attributes to be transferred.

- Use an account that is assigned to the `Tenant Administrator` role for the PI to Data Hub Agent installation.

- For heavy workloads, install the agent on a host computer separate from your PI Server deployment.

You can download the PI to Data Hub Agent from the PI to Data Hub Agents page on the portal and then transfer it to the computer that will host the agent.

**Note:** The PI to Data Hub Agent installation cannot be completed if the system time is not correct. Additionally, you will not be able to complete the PI to Data Hub Agent installation if Internet Explorer Enhanced Security Configuration is enabled. For more information, see [Disable Internet Explorer Enhanced Security Configuration](xref:disable-ie-security). 

## Configure access to PI Data Archive Security tables, PI point data, and optional AF server

**Important:** The PI to Data Hub Agent requires the Windows service account to `Run as user`. Enable read access to the following PI Server data:

- Archive data (PIARCDATA Security table)

- The PI points configuration table (PIPOINT Security table)

- The PI points and data to be transferred

- The AF server elements and attributes to be transferred 

## Install the PI to Data Hub Agent

To install the standalone PI to Data Hub Agent:

1. In the left pane, select **Data Collection** > **PI to Data Hub Agents**.

1. Select **Download Agent**.

1. On the `Agent Installer Download` window, select **Download**. When the download completes, close the window.

1. Open the downloaded PI to Data Hub agent installation file, then select **Yes** to confirm running the installation file.
   
   The `Welcome` page of the PI to Data Hub Agent window opens.

1. On the `Welcome` page, select **Next**.

   The `Service Account` page opens.

1. On the `Service Account` page, select the service account type for the connection:

   - **NT Service** - Enter an NT account to connect to PI Data Archive.

   - **This account** - Specify a user name and password (domain\account) to connect to PI Data Archive.

   **Note:** The service account requires read access to the PIARCDATA Security and PIPOINT Security tables, the PI points and data to be transferred, and the AF server, elements, and attribute data.

1. Select **Install**.

1. After the agent is installed, select **Close**.

   The PI to Data Hub Configuration Utility opens. See [Run the PI to Data Hub Agent Configuration Utility](xref:pi-to-ocs-utility) for instructions.

   **Note:** An agent cannot be registered until a PI Data Archive server has been added and configured in the PI to Data Hub Configuration Utility.

## Silent Installation Instructions for PI to Data Hub Agent 

There are several use cases for doing a silent installation of the PI to Data Hub Agent. 

- Silent installations are useful for automating deployments. 

- Silent installations avoid browser logins to PI to Data Hub. In particular, a new, interactive installation requires that Internet Explorer enhanced security be disabled, and some customers cannot disable this security. 

- Installations of the PI to Data Hub Agent on Windows Server Core Operating System is supported only with a silent installation. 

1. Create a client-credentials client with an assigned role of Tenant Contributor and add a secret. See <xref:gpClientCredentialsClient>.

   **Note:** Be sure to record the Client Id and Client Secret where you can access it again, because this is the only time you will have access to this information. You will need this information to proceed with the silent install. 

1. Find the TENANTID and record it where you can access it.

   When you log into AVEVA Data Hub, the TENANTID is visible in the URL. It is the long GUID.
   `https://datahub.connect.aveva.com/tenant/[YOUR TENANT ID]/dashboard`

   Alternatively, select **Developer Tools** > **API Console** and the TENANTID is displayed in the Full Path.
   `uswe.datahub.connect.aveva.com/api/v1/Tenants/[YOUR TENANT ID]/Namespaces`. 

1. Find the NAMESPACE Id and record it where you can access it.

   Select **Developer Tools** > **API Console** and select **GET**. The NAMESPACE Id appears as the `Id` field in the response.

   ![NamespaceID in API response](../../images/namespace-id.png)

   **Note:** If you have multiple namespaces, you will have multiple entries in this list. Be sure to select the NAMESPACE Id of the namespace where you want PI to Data Hub to send data. 

1. Open a Windows command prompt as an administrator.

1. Change to the folder where you have downloaded the PI To Data Hub Agent installation kit. 

1. If you wish to configure an Alternate Display Name for your Data Archive or AF Servers, enter the following command: 

   **Note:** The TENTANTID, CLIENTID, CLIENTSECRET, and NAMESPACE keywords are required. All keywords are case sensitive. SERVICEACCOUNT and SERVICEPASSWORD provide the "RunAs" user/password for the PI to Data Hub Agent service to connect to the PI Server (with Read permission). The "RunAs" account typically needs to be specified when PI to Data Hub Agent is remote to PI Data Archive or AF Server. 

   `PItoDataHubAgent_SetupKit.exe TENTANTID=[tenantid] CLIENTID=[clientid] CLIENTSECRET=[clientsecret] NAMESPACE=[namespaceID] DATAARCHIVE=[DataArchiveName] AFSERVER=[AFServerName] SERVICEACCOUNT=[user] SERVICEPASSWORD=[password] AGENTDESCRIPTION= "Your Description" /quiet`

1. If you do not wish to configure an Alternate Display Name for your Data Archive or AF Servers, enter the following command:

   **Note:** The TENTANTID, CLIENTID, CLIENTSECRET, and NAMESPACE keywords are required. All keywords are case sensitive. 

   `PItoDataHubAgent_SetupKit.exe TENTANTID=[tenantid] CLIENTID=[clientid] CLIENTSECRET=[clientsecret] NAMESPACE=[namespaceID] AGENTDESCRIPTION= "Your Description" /quiet`

1. Check that the PIToDataHubAgent service is running.

   From an administrative command prompt, run the command `net start | find "PI"` and verify that "PI To Data Hub Agent" is in the list. 

1. Check the event logs for any errors.

   Right-click on Start and select **Event Viewer**.

   Select **Applications and Services Logs** and double-click **PI to Data Hub**.

   For Windows Server Core operating systems, you can connect to the Event Viewer remotely.

1. Check the setup logs.

   Open a command prompt and navigate to `%ProgramData%/OSIsoft/Setup/log`.

   Logs can be listed from oldest to newest with the command `dir /od`.

1. (Optional) Configure an Alternate Display Name for PI Data Archive and/or AF Server.

   **Note:** Do not configure a PI to Data Hub Transfer until you complete this step if you do not want to replicate your Data Archive or AF Server name to AVEVA Data Hub. 

   1. Open an administrative command prompt and navigate to `%ProgramData%/OSIsoft/PItoDataHub`.

   1. Run the command `notepad.exe appsettings.json`.

   1. To specify an alternate display name for the Data Archive, add the following AlternateDisplayName entry. If you did not specify AFSERVER and DATAARCHIVE on the command line above, you will need to add the server names in this step as well as specifying the alternate display name. 

      ```
      "PIDataArchiveServerNames": [ 
          { 
            "Name": "MyActualDataArchiveServerName", 
            "AlternateDisplayName": "AlternateDisplayName", 
            "ConnectionTimeout": 10, 
            "OperationTimeout": 60 
          } 
        ],
      ```

   1. To specify an alternate display name for AF, add the following AlternateDisplayName Entry: 

      ```
      "PIAssetFrameworkServerNames": [ 
          { 
            "Name": "MyActualAFServerName", 
            "AlternateDisplayName": "AlternateDisplayName", 
            "ConnectionTimeout": 10, 
            "OperationTimeout": 60 
          } 
        ], 
      ```

   1. Save the changes and restart the PI to Data Hub Agent service from an administrative command prompt with the command `net start pitodatahubagent`.
 
1. Verify your Agent is visible on the `PI to Data Hub Agents` page in the portal and ready to configure. 
