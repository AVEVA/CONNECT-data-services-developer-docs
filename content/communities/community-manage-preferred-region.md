---
uid: community-manage-preferred-region
---

# Manage preferred region

Each community includes settings to manage the preferred region, which controls the geographical regions where operational data shared within a community can be processed. 

## Prerequisites

[!include[prereq-community-admin](includes/prereq-community-admin.md)]

## Manage preferred region settings

Edit the **Community preferred region** or **My preferred region** from a community's details.

1. In the left pane, select **Data Management** > **Communities**.

1. Find the community you want to edit and select **Details**.

1. Select **More Options** ![More Options](../_icons/default/dots-vertical.svg) > **Manage Preferred Region**.

1. Edit the preferred region settings and select **Update**.

   - **Community Preferred Region**

   This setting is used to optimize access to community shared data. It ensures that queries are sent to the appropriate region if a tenant in the community opts-out of cross-region data sharing, which allows processing of data outside of the primary region where it resides. If no value is set, then **Community Preferred Region** setting defaults to the `West-US` region. Select the region where you expect most of the data in this community to reside. 

   - **My Preferred Region**

   This setting overrides the **Community Preferred Region** for your tenant and allows you to control which region your tenant's queries to this community are sent to.
