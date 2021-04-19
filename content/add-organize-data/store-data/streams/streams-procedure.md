---
uid: gpStreams
---

# Add a stream

Sequential Data Store (SDS) stream data are values or events of the same SDS type. SDS stream data are stored in the Sequential Data Store and indexed by one or more properties defined by the stream's SDS type. See the following for more information about streams:

- [Streams](xref:ccStreams)
- [Streams best practices](xref:bpStreams)

## Procedure

1. Click the ![Menu icon](C:/Users/lasato/source/repos/OCS-DOCS/sds-new/images/menu-icon.png) and click **Sequential Data Store** (under Data Management).
1. From the **Namespace** drop-down list, select the namespace in which you want to create the stream.
   ![Namespace list](../images/sds-namespace.png)
1. From the **Streams** drop-down list, select **Streams** if it is not already selected.
    ![Streams list](../images/streams-procedure-streams-list.png)
1. Click **Add Stream**.

1. In the `Add Stream` window, enter the following:

   - `Id` &ndash; Identifier for referencing the stream
   - `Description` &ndash; User-friendly description of the stream
   - `Type` &ndash; Sds type identifier of the type used in this stream          

    **Note:** Leave the `Name` field blank. By default, it takes the value of the stream Id.
   
1.  Click the **Tags** tab, if it is not already selected.

1. In the `New Tag` field, type the name of the metadata tag and click **+** to add the tag. 

    **Note:** You can click the tag to edit it, or click **X** to delete it from the stream.

1. Click the **Metadata** tab and click **Add Metadata**.

1. In the `Metadata Key` and `Metadata Value` fields, enter the key and value of your metadata.

    **Note:** You can click either of these fields to edit them later or click the **X** to delete it from the stream.


## Related links

- [Streams](xref:sdsStreams) API