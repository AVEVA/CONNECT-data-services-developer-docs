---
uid: create-folders
---

# Create a folder and turn on AVEVA Data Hub

Before users can access AVEVA™ Data Hub, you must create a folder in Connect and turn on the AVEVA™ Data Hub service for that folder. A folder is used to partition data into logical units and represents a set of assets at your organization. For example, you can create folders to divide up assets or represent geographical locations in your organization. 

**Important:** When you turn on the AVEVA™ Data Hub service and set up a folder in AVEVA™ Connect, a namespace is also created and shares the same name of the Connect folder. See [Folders and namespaces](xref:ccNamespaces) for more information.

Perform the following steps to create a folder in AVEVA™ Connect:

1. In the navigation menu, select **Folder Management**, then click the **Add Folder** button.

   **Result:** The Add Folder area is displayed.

1.	Enter the name of the new folder in the **Folder name** field

   **Note:** The new folder will be created in the selected region only and the region cannot be changed after the folder is created. You can click **Change** and select a different region.

1. Select **Upload image** to use your own image or **Select stock image** to use an existing image for the new folder.
    
   **Note:** The image is used in the carousel of folders displayed on the AVEVA™ Connect home page users see.

1. In AVEVA Connect, navigate to the newly created folder and switch on the Data Hub service.

2. Click the ellipse button on the bottom right of the Service tile and then click **Manage Roles** to ensure that the services turned on has the relevant permissions to be accessed by users.

    **Note:** If you do not set up folders, access to services can only be assigned at the account level. Some services can only be assigned at the folder level.