---
uid: create-folders
---

# Step 1C: Create a folder and turn on AVEVA Data Hub

Before users can access AVEVA Data Hub, you must create a folder in AVEVA Connect and then turn on the AVEVA Data Hub service for that folder.  

## What is a folder?

A folder is used to partition data into logical units that represent your organization's hierarchy. The folder is where data and resources are stored. For example, you can create folders to divide up assets or to represent geographical locations at your organization. 

**Important:** When you create a folder and then turn on the AVEVA Data Hub service in AVEVA Connect, the folder name is also saved as the namespace name. This namespace appears in the AVEVA Data Hub portal. For more information, see [Folders and namespaces](xref:ccNamespaces).

Perform the following steps to create a folder in AVEVA Connect:

1. From the AVEVA Connect home page, select the menu icon, then select **Folder Management** and select **Add Folder**.

   The `Add Folder` window opens.

1.	In the **Folder name** field, enter the name of the new folder.

1. (Optional) To select a different region, select **Change**.
 
   **Note:** The region cannot be changed after folder creation. Before the folder is saved, select **Change** to select a different region. Region labels in AVEVA Connect and AVEVA Data Hub differ: 

    | AVEVA Connect region label | AVEVA Data Hub region label | 
    | ------------- | ------------- |
    | US-West | (westus) |
    | EU-West | (northeurope) | 
    | Australia | (australiaeast) |

   **Note:** Other regions (such as Japan, India, etc.) are available for selection when creating a folder in AVEVA Connect, but AVEVA Data Hub only supports the three regions listed above. Therefore, when you activate the AVEVA Data Hub service for the folder, if you have chosen a region not in the list above you are prompted to select an alternative region from the list for the service.

1. (Optional) Set a budget for Flex Credits for the folder. For more information, see [About Flex Credits](https://help.connect.aveva.com/#/home/767994/10/11). 

1. To select an image to represent the folder, perform one of the following actions:
 
   * To use your own image, select **Upload image** and then select **Select image to upload**. Navigate to and select the image and select **Open**.

   * To use an existing image, select **Select stock image** and select the image.

1. Select **Save**.
    
   The image appears in the carousel of folders displayed on the AVEVA Connect home page.

1. On the displayed folder details page, switch on the AVEVA Data Hub service, then select **Enable** to confirm the selection.

   **Note:** The default maximum number of namespaces for a tenant is five. To increase this maximum, customers must communicate this request to AVEVA.

1. Select the ellipse button on the bottom right of the Service tile and then select **Manage Roles** to ensure that the services turned on has the relevant permissions to be accessed by users.
