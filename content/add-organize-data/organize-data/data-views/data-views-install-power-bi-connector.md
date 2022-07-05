---
uid: data-views-install-power-bi-connector
---

# Install Power BI Connector

The OSIsoft Cloud Services Power BI Connector retrieves Data Views from OCS and makes them available in Microsoft Power BI for advanced data visualization and analysis. Install OSIsoft Cloud Services Power BI Connector to retrieve Data Views for use with Microsoft Power BI as described in this section.

## System requirements

The following are required before you install and use OSIsoft Cloud Services Power BI Connector.

- Operation Systems: Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2016, Windows Server 2019

- For desktop installation: Microsoft Power BI Desktop 2.91.884.0 or later

- For on-premises Data Gateway installation: Microsoft Power BI On-premises Data Gateway 3000.89.6 or later

- Microsoft Edge WebView 2 Runtime

- A user account with Administrator privileges to install OSIsoft Cloud Services Power BI Connector on a local machine.

## Release notes

See <xref:PowerBIReleaseNotes>.

## Install OSIsoft Cloud Services Power BI Connector

To install the OSIsoft Cloud Services Power BI Connector:

1. Download the `OCSPowerBIConnector.exe` file from the [OSIsoft Customer portal](https://customers.osisoft.com/s/products).

1. Install OSIsoft Cloud Services Power BI Connector by either the setup wizard or silent installation.

    - Setup wizard

        - Double-click the `OCSPowerBIConnector.exe` file and select **Next**.

        - (Optional) To install the connector to an on-premises data gateway, select `On-premises data gateway installation` and enter the directory where you want to install the connector.

    - Silent installation

        - Open a command prompt window and type following command:

        `.\OCSDataConnectorInstaller.exe -Y INSTALLDIR="<install path>" /quiet`

             **Note:** OSIsoft Cloud Services Power BI Connector supports silent installation for on-premises data gateway installations.