---
uid: create-folders
---

# Create a folder and turn on AVEVA Data Hub

Before users can access AVEVA Data Hub, you must create a folder in AVEVA Connect and then turn on the AVEVA Data Hub service for that folder.  

## What is a folder?

A folder is used to partition data into logical units that represent your organization's hierarchy. The folder is where data and resources are stored. For example, you can create folders to divide up assets or to represent geographical locations at your organization. 

**Important:** When you create a folder and then turn on the AVEVA Data Hub service in AVEVA Connect, the folder name is also saved as the namespace description. This namespace description appears in the AVEVA Data Hub portal. For more information, see [Folders and namespaces](xref:ccNamespaces).

Perform the following steps to create a folder in AVEVA Connect:

1. From the AVEVA Connect home page, click the menu icon, then select **Folder Management** and click the **Add Folder** button.

   **Result:** The **Add Folder** window opens.

1.	Enter the name of the new folder in the **Folder name** field.

1. (Optional) Click **Change** to select a different region.
 
   **Note:** The region cannot be changed after folder creation. Before the folder is saved, click **Change** to select a different region. Region labels in AVEVA Connect and AVEVA Data Hub differ: 

    | AVEVA Connect region label  | Corresponding AVEVA Data Hub region label |
    | ------------- | ----------------- |
    | US-West | westus |
    | EU-West | northeurope | 

1. (Optional) Set a budget for Flex Credits for the folder. See [About Flex Credits](https://help.connect.aveva.com/#/home/767994/10/11) for more information. 

1. Perform one of the following actions to select an image to represent the folder:
 
   * To use your own image, click **Upload image** and then click Select image to upload. Navigate and select the desired image and click **Open**.

   * To use an existing image, click **Select stock image** and select the desired image.

1. Click **Save**.
    
   **Result** The image appears in the carousel of folders displayed on the AVEVA Connect home page.

1. On the displayed folder details page, switch on the AVEVA Data Hub service, then click **Enable** to confirm the selection.

2. Click the ellipse button on the bottom right of the Service tile and then click **Manage Roles** to ensure that the services turned on has the relevant permissions to be accessed by users.
