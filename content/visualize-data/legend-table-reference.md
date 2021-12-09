---
uid: LegendTableReference
---

# Legend table reference

While visualizing data from the **Trend** page, you can toggle between a **Trend** (// TODO) view and a **Cursor** (![cursor](../_images/icons/location_on_black_18dp.svg)) view to display different metadata about the stream within a selected time frame.

![Trend page legend table](images/trend-page.png)

## Trend view

The **Trend** view lists each data stream depicted within the `Trend` pane. Each data stream includes traces, which are stream properties plotted within the `Trend` pane. For example, in the following image, a data stream related to weather is plotted within the `Trend` pane. The pane depicts the weather stream data for the **temperature** and **wind speed** properties.

![Trend view](images/trend-view.png)

Each data stream name includes metadata icons (image below) that display more information about the data stream origin:

![Metadata icons](images/metadata-icons.png)

The following table describes each icon.

Metadata Icon | Description
--|--
Database // TODO | Indicates the origin namespace of the stream data.
![share](_images/icons/../../../_images/icons/share_black_18dp.svg) | Indicates that the stream originates from a [community](xref:communities). Mouse over the icon to view the community identifier.
Tenant // TODO | Indicates the tenant that is sharing the stream within the community. This icon displays only when the stream is shared within a community.

Each stream property listed in the **Trend** view also lists metadata for the property:

Column | Description
--|--
Name | The name of the stream property depicted within the `Trend` pane. The color swatch for each property corresponds to the visualization.
Timestamp | The date and time of the trace.
Value | The value of the property.
UOM | The unit of measure.
Min | The lowest value recorded for the property for easy cursors that you have set in the Trend view.
Max | The highest value recorded for the property for easy cursors that you have set in the Trend view. 

**Tip:** Select or clear a property checkbox to display or hide the property within the `Trend`  pane.

## Cursor view

The **Cursor** (![cursor](../_images/icons/location_on_black_18dp.svg)) view lists property values for each cursor added to the `Trend` pane. Cursors are listed chronologically according to their timestamps.

![Cursor view](images/cursor-view.png)

**Tip:** For more information on placing cursors, see <xref:GettingStartedWithTrendData>.
