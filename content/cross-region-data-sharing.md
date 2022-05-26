---
uid: cross-region-data-sharing
---

# Cross-region data sharing

By default, OSIsoft Cloud Services (OCS) processes data in other regions for:

- Performance reasons. 
- Enabling users to search and access data that may reside across regions. 

For data security and [General Data Protection Regulation (GDPR)](https://gdpr.eu/) compliance, you can [opt out](#to-opt-out-of-cross-region-data-sharing) of this cross-region data sharing. 

When opt-out is enabled, data is not processed outside of the region where it resides. Queries are routed to the appropriate region for complete results to be returned. The Community Preferred Region setting should be used when opting out so that clients are aware of the appropriate region to use.

If you want to opt out of cross-region data sharing, complete the following tasks in order:

1. [To opt out of cross-region data sharing](#to-opt-out-of-cross-region-data-sharing)

1. [To configure the community preferred region](#to-configure-the-community-preferred-region)

## How is data shared

By default, OCS processes your data in regions other than your own for performance reasons and search enablement. For example, if your default OCS region is `US-West`, OCS may process your data in the `EU-West` region, as depicted below.

**Tip:** For a list of available regional endpoints, see <xref:regional-endpoints-ocs>.

![Cross-region data sharing enabled](./_images/cross-region-data-sharing.drawio.svg)

If you disable cross-regional data sharing, data is only processed using your configured regional endpoint. Disabling this setting may reduce and searchability. However, it ensures that your namespace is GDPR compliant.

![Cross-region data sharing disabled](./_images/cross-region-data-sharing-disabled.drawio.svg)

## Namespaces

Irure proident officia mollit id voluptate.

### To opt out of cross-region data sharing

1. From the **Namespace** drop-down, select a namespace or community for which you want to opt out of data sharing. 

1. From the **Namespace** drop-down, select the **Cog** ![Cog](./_icons/default/cog.svg).

1. Select the **Data Sharing** tab.

1. Select **Edit**.

1. Enable **Opt-out for Namespace** and select **Save**.

## Communities

Nisi ex quis cupidatat sit fugiat aliquip aute.

### To configure the community preferred region

The Community Preferred Region setting should be used after you have opting out of cross-region data sharing so that clients are aware of the appropriate region to use.

1. Elit pariatur aute aliqua quis Lorem in excepteur commodo mollit ea.

1. Ullamco nulla quis est excepteur.

1. Aliqua cupidatat ea laborum enim Lorem culpa eiusmod sit deserunt ipsum tempor quis ex.