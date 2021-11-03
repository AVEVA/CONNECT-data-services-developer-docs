---
uid: manage-streams
---
# Manage streams

The Sequential Data Store gives you capabilities to manage stored streams. The capabilities function the same if you are working in the context of a namespace or a community.

## Manage permissions

For a role to perform any actions on a stream, you must grant that role permissions for the stream. For any stream, you can assign the following permissions to a role:

- Read
- Write
- Delete
- Manage Permissions

1. From the left pane, select **Data Management** > **Sequential Data Store**.

1. Select one or more streams.

1. Select **More options** ![More options icon](../../images/more-options-wite-background.png), and then select **Manage Permissions**.

1. In the `Manage Permissions` window, from **Select Role**, choose the role whose permissions you want to modify.

1. Select the permissions to grant to the selected role, and then click **Save**.

## Add tags or metadata

Tags and metadata allow you to associate additional information with a stream. For example, tags can denote special attributes for a stream. Metadata consists of keys and their associated values.

1. From the left pane, select **Data Management** > **Sequential Data Store**.

1. Select a stream.

1. Click the **More options** ![More options icon](../../images/more-options-wite-background.png), and then select **Edit Stream**.

   A tab opens to allow you to modify the metadata and tags for the stream.

1. Add metadata.

   - Click the **Metadata** tab, and then click **Add Metadata**. In the `Metadata Key` box, enter the name of the key and in the `Metadata Value` box, enter a value for that key.

   - To remove a metadata, click the **X** beside the row to be deleted.

1. Add tags.

   - Click the **Tags** tab, if it is not already selected. In the `New Tag` box, enter the name of the tag, and then click the plus sign (**+**).
   
   - To remove a tag, click the **X** beside the tag name.

## Remove streams

When you remove a stream, you are deleting it.

1. From the left pane, select **Data Management** > **Sequential Data Store**.

1. Select one or more streams.

1. Click **More options** ![More options icon](../../images/more-options-wite-background.png), and then select **Remove Stream**.

1. In the confirmation window, click **Remove** to confirm the deletion.