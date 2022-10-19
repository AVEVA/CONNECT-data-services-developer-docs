---
uid: data-view-query-errors
---

# Data view errors

While working with data views, you may encounter warnings or errors. This topics details possible warning or errors and how to address them.

## `Unknown community`

Query sources of `Unknown Community` indicate that you have insufficient permissions to access the community or that has been deleted. You must be a member of the community to access its data. Additionally, you cannot edit the query for the community until you are member of the community. Request that a community administrator add you to the community. For more information, see <xref:community-manage-users>. 

**Unknown community chip**

![unknown](_images/unknown-community.png)

## `No included fields`

If the field set for a query includes no fields, an alert of `No Included Fields` displays. You can correct this error by adding one or more fields to the query. For more information, see <xref:data-views-manage-data-fields#to-add-data-fields-to-field-set>.

**No Included Fields**

![no included fields](_images/no-included-fields.png)

## `There are included fields that don't map to anything`

If only of your queries includes fields that do not map to anything, an error of `There are included fields that don't map to anything` displays at the bottom of the field sets.

**Field set error**

![field set error](_images/field-set-error.png)

You can correct this error by finding the individual fields that do not map to anything and removing them. Fields that do not map to anything are denoted by the alert ![alert](../../_icons/default/alert.svg) icon. For more information on removing a field from a field set, see <xref:data-views-manage-data-fields#to-add-data-fields-to-field-set>.  
