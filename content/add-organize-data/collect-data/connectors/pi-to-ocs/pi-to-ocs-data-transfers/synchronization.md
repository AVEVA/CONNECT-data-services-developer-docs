---
uid: PItoDHSync
---

# PI to OCS change synchronization

The PI to OCS Agent supports synchronizing changes in the PI Data Archive and PI Asset Framework. Updates are automatically sent to OCS without any user interaction. This topic outlines how synchronization works and its limitations.

## Data Archive synchronization 

The PI To OCS Agent signs up for the following updates to stay in sync with the Data Archive:

- PI point updates

  - Adding a PI point: If PointId was listed in the transfer specification, a stream is created and data streams to SDS.

  - Updating a PI point name: The SDS stream name is updated.

  - Updating metadata: The corresponding SDS stream metadata is updated.

  - Deleting a PI point: The SDS stream is deleted, if the AutoDeleteCloudObject flag is enabled in the transfer settings.

- Digital state updates

  - Update set name/values: The SDS stream values are changed to the updated digital state set/name; see limitations below.

- Data updates

  - Point compression updates.

Sign-up for PI point updates and digital state updates occurs when the agent starts, while data updates do not begin until the start of a transfer.

### Data Archive synchronization limitations 

| Issue | Restrictions |
| ----- | ------------ |
| Toggling Compression | Toggling On to Off: It is possible that the PI point’s corresponding SDS stream may be missing an event near the time when the PI point’s compression setting was changed from On to Off. <br />Toggling Off to On: There is a small chance for an extra event (an event which was compressed out from the server) to be in SDS near the time when the PI point’s compression setting was changed from Off to On. |
| Analysis backfilling and rapid succession of data addition and deletion | There is a possibility for a data gap after an analysis backfill operation due to the nature of rapid data deletion and insertions being performed by the analysis service on the PI point. |
| Updating Digital State | The SDS stream will store the updated state name and values at time of change. Previously stored state values are preserved.<br />Updated digital state values will not be backfilled or recalculated for existing data saved to the corresponding SDS stream. |

## Asset Framework synchronization 

For AF synchronization to be successful the agent needs to perform an indexing of the AF server. AF indexing occurs once agent registration is successful. During the initial indexing, the agent crawls through the AF server and caches all known elements and templates in addition to their attributes. Once the initial indexing is complete, the agent persists a cookie and the cache of the elements and templates on the server. The agent progresses the persisted cookie periodically to check for changes or updates since the last successful indexing.

In the event of an agent restart, the agent performs a check for the persisted cookie in the cache directory. If no cookie is found, the agent performs an initial index and persists a new cookie for periodic indexing.

Upon the start of a transfer, the agent utilizes the AFIndex to build out the implicit PI points referenced by the element Ids specified in the transfer specification to track, in addition to sending those references to the cloud.

Once the transfer is initialized in the agent, change processing of the cookie also propagates down to the transfer and is filtered down to only take actions on elements and element templates of interest.

Below are the supported AF change synchronization events and the result of each change:

- Database

  - Database addition

  - Database rename: The Path metadata of assets referencing the database is updated.

  - Database deletion: Will propagate and synchronize all elements and templates that were also deleted because of the database being removed.<sup>1</sup>

- Element

  - Updates to Name, Description, Template: The corresponding asset property is updated.

  - Addition or updates to attributes: An SDS stream is created if newly referenced in transfer. The stream reference of the asset is added or updated.

  - Deletion of attributes: The stream reference is removed from the asset. The SDS stream is removed if a point is no longer referenced in the transfer.<sup>1</sup>

  - Deletion of the element: The asset is deleted.<sup>1</sup>

- Point attributes

  - Metadata updates (Name, Description, etc.): The asset property is updated to reflect the change.

  - PI point reference updates: Changes the stream reference of the asset on the cloud to the updated stream. If the previously referenced point is no longer referenced implicitly or explicitly in the transfer, the SDS Stream will be removed.<sup>1</sup>

- Static attributes

  - Metadata updates (Name, Description, etc.): The asset metadata associated with the attribute is updated.

  - Value updates: The value of the attribute is updated.

- Template

  - Updates to Name, Description, Template: The corresponding property is updated on the asset type.

  - Addition or updates to attribute templates: The stream reference and metadata associated with the asset type is updated.

  - Deletion of attribute templates: The stream reference and metadata is removed from the asset type.

  - Deletion of the template: The asset type is removed.<sup>1</sup>

- Point attribute templates

  - Metadata updates (Name, Description, etc.): The asset type property is updated to reflect the change.

  - PI point reference updates: The stream reference is updated on the asset type.

- Static attribute templates

  - Metadata updates (Name, Description, etc.): The asset type metadata associated with the attribute is updated.

  - Asset type value updates: The asset type metadata is updated.

<sup>1</sup> If the AutoDeleteCloudObject flag is enabled in the transfer settings.

### Asset Framework synchronization limitations 

| Issue | Restrictions |
| ----- | ------------ |
| Programmatic template updates | Programmatic changes using AFSDK are not properly propagated to the cookie when adding an attribute template after creating the element template within the same transaction. |
| Resetting to template | If an element has an override on its values that was previously inherited from its template, resetting the element to the template defaults will not be picked up by the change sync. | 

## PI point type change

A PI point type change occurs when a PI point's type is changed on the source PI Data Archive after the corresponding stream has been created in the SDS database. When the PI to OCS Agent detects this change, it takes the following actions:

- Displays the `PI Point Type Change Detected` message next to **Current Activity** in the `Details` pane as shown in the screenshot below.

- Prevents data being sent from the source PI point to the SDS stream until the type is changed to match the corresponding SDS Stream type and the transfer is restarted.

- Logs details about the corresponding SDS stream in both the Windows Event Viewer and OCS logs.

![](../../images/pi-point-type-change.png)

A point change can occur for the following reasons:

* The source PI point had an incorrect configuration of data and type. The data and point must be deleted and recreated.

* The source PI point was misconfigured initially. For example, the point needed to be updated from `Float32` to `Float64`. The data is still relevant and should be kept.

* Other reasons.
<!--Angela Flores 6/28/21 This list is oddly specific. Also, what is PI to OCS Services? And PI to OCS service? This topic still needs work. --> 
<!--VT, 11/29/21: PI to OCS Services/service is the PI to OCS Agent. I had a discussion w/one of the Bonsai developers, Zane Odeh & he confirmed this info. They have been removed from this topic. This topic was updated recently. What other work is needed?-->

After you create an SDS stream, its underlying SdsType cannot change. As a result, new data from the PI point in question cannot be stored in the same stream. You can resume streaming data from the PI point to the existing SDS stream by taking the following corrective actions:

- View the [Windows Event Viewer logs](xref:view-logs) or [OCS logs](xref:download-tenant-log) to determine which PI point incurred a PI point type change.

    **Note:** The Windows Event Viewer logs are the preferred source of information for PI point type changes.

- Change the PI point type to match the SDS stream type and then restart the transfer.

To see what types of point coercions are supported in PI Data Archive, refer to the [Allowable point type coercions](https://docs.osisoft.com/bundle/pi-server/page/allowable-point-type-coercions.html) topic.<!--Angela Flores 6/28/21 should that be "coercions" or "conversions"? --> <!--VTT, 11/29/21: Coercion is the preferred term per the referenced topic.-->
