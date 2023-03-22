---
uid: create-folders
---

# Step 1C: Create a folder and turn on AVEVA Data Hub

Before users can access AVEVA Data Hub, you must create a folder in AVEVA Connect and then turn on the AVEVA Data Hub service for that folder. A folder is used to partition data into logical units that represent your organization's hierarchy. The folder is where data and resources are stored. For example, you can create folders to divide up assets or to represent geographical locations at your organization.

When you create a folder in AVEVA Connect, the folder name is also saved as a namespace within AVEVA Data Hub. For more information, see [Folders and namespaces](xref:ccNamespaces).

Perform the following steps to create a folder in AVEVA Connect:

1. From the AVEVA Connect home page, select ![menu](../../../../_icons/default/menu.svg) > **Folder Management**.

1. Select **Add Folder**.

1. In the **Folder name** field, enter the name of the new folder.

1. Choose a **Region** that supports AVEVA Data Hub. Select **Change** to choose a region.

    AVEVA Data Hub is only supported in a limited number of geographical regions. Choose one of the supported Connect regions listed in the following table. Note that the table also indicates differences between naming of regions in AVEVA Connect and AVEVA Data Hub:

    | AVEVA Connect region label | AVEVA Data Hub region label |
    | ------------- | ------------- |
    | US-West | (westus) |
    | EU-West | (northeurope) |
    | Australia | (australiaeast) |

1. (Optional) Set a **Credits budget** for Flex Credits for the folder. For more information, see [Flex Credits](https://docs.aveva.com/bundle/aveva-connect/page/885356.html).

1. Select an **Image** to represent the folder. Either upload your own image or select a stock image.

1. Select **Save**.

1. Select ![menu](../../../../_icons/default/menu.svg) > **Folder Management**. Open the folder that you just created.

1. Set **AVEVA Data Hub** to **On**. Then select **Enable** to confirm the selection.

   **Note:** The default maximum number of namespaces for a tenant is five. To increase this maximum, customers must communicate this request to AVEVA.
