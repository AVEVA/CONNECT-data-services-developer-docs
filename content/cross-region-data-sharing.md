---
uid: cross-region-data-sharing
---

# Cross-region data sharing

By default, OSIsoft Cloud Services (OCS) processes data in other regions for:

- Performance reasons. 
- Enabling users to search and access data that may reside across regions. 

For data security and [General Data Protection Regulation (GDPR)](https://gdpr-info.eu/) compliance, you can [opt out](#to-opt-out-of-cross-region-data-sharing) of this cross-region data sharing. 

When opt-out is enabled, data is not processed outside of the region where it resides. Queries are routed to the appropriate region for complete results to be returned. The Community Preferred Region setting should be used when opting out so that clients are aware of the appropriate region to use.

## Namespaces

<!-- Help wanted -->

Sunt est voluptate deserunt dolor sit magna dolore nulla culpa aliqua consectetur est.

## Communities

<!-- Help wanted -->

Aliqua in ut mollit sint aute mollit velit cupidatat cillum culpa exercitation amet sit ullamco.

## How is data shared

By default, OCS processes your data in regions other than your own for performance reasons and search enablement. For example, if your default OCS region is `US-West`, OCS may process your data in the `EU-West` region, as depicted below.

**Tip:** For a list of available regional endpoints, see <xref:regional-endpoints-ocs>.

![Cross-region data sharing enabled](./_images/cross-region-data-sharing.drawio.svg)

If you disable cross-regional data sharing, data is only processed using your configured regional endpoint. Disabling this setting may reduce and searchability. However, it ensures that your namespace is GDPR compliant.

![Cross-region data sharing disabled](./_images/cross-region-data-sharing-disabled.drawio.svg)

## To opt out of cross-region data sharing

1. From the **Namespace** drop-down, select a namespace or community for which you want to opt out of data sharing. 

1. From the **Namespace** drop-down, select the **Cog** ![Cog](./_icons/default/cog.svg).

1. Select the **Data Sharing** tab.

1. Select **Edit**. 

1. Enable **Opt-out for Namespace** and select **Save**.