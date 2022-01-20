---
uid: create-folders
---

# Create a folder and turn on AVEVA Data Hub

Before users can access AVEVA Data Hub, you must create a folder in Connect and then turn on the AVEVA Data Hub service for that folder.  

## What is a folder?

A folder is used to partition data into logical units that represent your organization's hierarchy. The folder is where data and resources are stored. For example, you can create folders to divide up assets or to represent geographical locations at your organization. 

**Important:** When you create a folder and then turn on the AVEVA Data Hub service in AVEVA Connect, a namespace is created that shares the same name of the Connect folder. See [Folders and namespaces](xref:ccNamespaces) for more information.

To create a folder in AVEVA Connect, follow these steps:

1. From the Connect home page, select the menu icon, then select **Folder Management** and select **Add Folder**.

   The `Add Folder` window opens.

1.	In the **Folder name** field, enter the name of the new folder.

1. (Optional) To select a different region, select **Change**.
 
   **Note:** The region cannot be changed after folder creation.

1. (Optional) Set a budget for Flex Credits for the folder. For more information, see [About Flex Credits](https://help.connect.aveva.com/#/home/767994/10/11). 

1. To select an image to represent the folder, perform one of the following actions:
 
   * To use your own image, click **Upload image** and then click **Select image to upload**. Navigate to and select the image and click **Open**.

   * To use an existing image, click **Select stock image** and select the image.

1. Select **Save**.
    
   The image appears in the carousel of folders displayed on the AVEVA Connect home page.

1. On the displayed folder details page, switch on the AVEVA Data Hub service, then select **Enable** to confirm the selection.

1. Select the ellipse button on the bottom right of the Service tile and then select **Manage Roles** to ensure that the services turned on has the relevant permissions to be accessed by users.
