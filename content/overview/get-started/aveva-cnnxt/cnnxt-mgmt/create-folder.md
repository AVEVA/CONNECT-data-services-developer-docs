---
uid: create-folders
---

# Create a folder and turn on AVEVA Data Hub

Before users can access AVEVA™ Data Hub, you must create a folder in Connect and turn on the AVEVA™ Data Hub service for that folder. A folder is used to partition data into logical units and represents a set of assets at your organization. For example, you can create folders to divide up assets or represent geographical locations in your organization. 

**Important:** When you turn on the AVEVA™ Data Hub service and set up a folder in AVEVA™ Connect, a namespace is also created and shares the same name of the Connect folder. See [Folders and namespaces](xref:ccNamespaces) for more information.

Perform the following steps to create a folder in AVEVA™ Connect:

1. In the navigation menu, select **Folder Management**, then click the **Add Folder** button.

   **Result:** The Add Folder window opens.

1.	Enter the name of the new folder in the **Folder name** field.

1. Optional: Click **Change** to select a different region.

1. Perform one of the following actions to select an image to represent the folder:
 
   * To use your own image, click **Upload image** and then click Select image to upload. Navigate and select the desired image and click **Open**.

   * To use an existing image, click **Select stock image** and select the desired image.

1. Click **Save**.
    
   **Result** The image appears in the carousel of folders displayed on the AVEVA™ Connect home page.

1. On the displayed folder details page, switch on the Data Hub service, then click **Enable** to confirm the selection.

2. Click the ellipse button on the bottom right of the Service tile and then click **Manage Roles** to ensure that the services turned on has the relevant permissions to be accessed by users.

    **Note:** If you do not set up folders, access to services can only be assigned at the account level. Some services can only be assigned at the folder level.
