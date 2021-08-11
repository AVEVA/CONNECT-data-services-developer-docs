---
uid: manage-streams
---
# Manage streams

The Sequential Data Store gives you capabilities to manage stored streams. The capabilities function the same if you are working in the context of a namespace or a community.

???what permissions are necessary to performs these actions???

## Manage permissions

For a role to perform any actions on a stream, you must grant that role permissions for the stream. You can assign the following permissions to a role: 
- Read
- Write
- Delete
- Manage Permissions

### Procedure

1. Click the menu icon ![Menu icon](../images/menu-icon.png) and click **Sequential Data Store** (under Data Management).
1. At upper left, click **Change Namespace or Community** to open the `Select a Namespace or Community` window. Then select a namespace or community that owns the streams you want to modify.
1. Select one or more streams.
1. Click the **More options** icon ![More options icon](../../images/more-options-wite-background.png) and then select **Manage Permissions**.
1. In the `Manage Permissions` window, from **Select Role**, choose the role whose permissions you want to modify.
1. Check the permissions to grant to the selected role.
1. Click **Save**. 


## Add tags or metadata

Tags and metadata allow you to associate additional information with a stream. For example, tags can denote special attributes for a stream. Metadata consist of keys and values associated with those keys. 

### Procedure

1. Click the menu itcon ![Menu icon](../images/menu-icon.png) and click **Sequential Data Store** (under Data Management).
1. At upper left, click **Change Namespace or Community** to open the `Select a Namespace or Community` window. Select the namespace or community where you want to modify streams.
1. Select a stream.
1. Click the **More options** icon ![More options icon](../../images/more-options-wite-background.png) and then select **Edit Stream**.<br>A tab opens allowing you to modify information about the stream.
1. To enter metadata, take the following steps:   
   1. Click the **Metadata** tab.
   1. Click **Add Metadata**.
   1. In the **Metadata Key** box, enter the name of the key. In the **Metadata Value**, enter a value for that key. 
   1. To add another metadata entry, click **Add Metadata**. To remove an entry, click the **X** beside the row to be deleted. 
1. To add tags, take the following steps:   
   1. Click the **Tags** tab, if it isn't already selected.
   1. In the **New Tag** box, enter the name of the tag and click the plus sign (**+**). 
   1. To add another tag, click **New Tag**. To remove a tag, click the **X** beside the tag name.???is this correct

## Remove streams
What are you doing when you remove a stream are you deleting the stream from the namespace? The community? 

### Procedure

1. Click the menu icon ![Menu icon](../images/menu-icon.png) and click **Sequential Data Store** (under Data Management).
1. At upper left, click **Change Namespace or Community** to open the `Select a Namespace or Community` window. Select the namespace or community where you want to remove a stream.
1. Select one or more streams.
1. Click the **More options** icon ![More options icon](../../images/more-options-wite-background.png) and then select **Remove Stream**. A confirmation message appears. Click **Remove** to confirm the deletion.

