---
uid: data-view-troubleshooting
---

# Data view troubleshooting

While working with data views, you may encounter warnings about your data view configuration settings. This topics details possible warnings and how to address them.

## Data Views page

While browsing the list of data views, you may encounter the following warnings .

### `Unknown community`

Query sources of `Unknown Community` indicate that you have insufficient permissions to access the community or that has been deleted. You must be a member of the community to access its data. Additionally, you cannot edit the query for the community until you are member of the community. Request that a community administrator add you to the community. For more information, see <xref:community-manage-users>.

**Unknown community chip**

![unknown](_images/unknown-community.png)

**Note:** Community Administrators or Community Members with read access only do not see `Unknown Community`. Instead they see the community name. Community Administrators can then use the visible community name to add users to the community. For more information on adding a user to the community, see <xref:community-manage-users>.

## Data View page

You may encounter the following warnings while editing a data view.

### `No included fields`

If the field set for a query includes no fields, an alert of `No Included Fields` displays. You can correct this error by adding one or more fields to the query. For more information, see <xref:data-views-manage-data-fields#to-add-data-fields-to-field-set>.

**No Included Fields**

![no included fields](_images/no-included-fields.png)

### `There are included fields that don't map to anything`

If only of your queries includes fields that do not map to anything, an error of `There are included fields that don't map to anything` displays at the bottom of the field sets.

**Field set error**

![field set error](_images/field-set-error.png)

You can correct this error by finding the individual fields that do not map to anything and removing them. Fields that do not map to anything are denoted by the alert ![alert](../../_icons/default/alert.svg) icon. For more information on removing a field from a field set, see <xref:data-views-manage-data-fields#to-add-data-fields-to-field-set>.

## Manage Queries

While managing data view queries, you may encounter the following warnings.

### Cross region processing disabled

If you encounter a message of `This namespace does not allow data to be processed outside of the region where it resides`, this message indicates that your tenant has opted out of sharing the namespace data across regions for performance purposes. Therefore, the data view cannot be processed in your geographical region. For additional information, see <xref:cross-region-data-sharing>.

You can encounter this message in different contexts:

- **While adding a query**

    If you attempt to add a namespace that has opted out of cross region data sharing, the source is unavailable and cannot be added. A tooltip displays if you mouse over the source.

    ![opt-out tooltip](_images/opt-out-tooltip.png)

- **While managing an existing query**

    If a data view is created that includes a namespace that later opts out of cross region data sharing, an alert displays in the **Query** panel that the data view includes a source that cannot be shared across region:

    ![another opt-out tooltip](_images/opt-out-warning-tooltip.png)

    When the query that includes a disabled source is selected, the following message displays notifying you:

    ![warning message](_images/cross-region-data-sharing-disabled.png)