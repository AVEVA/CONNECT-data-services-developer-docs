---
uid: cross-region-data-sharing
---

# Cross-region data sharing

By default, OSIsoft Cloud Services (OCS) processes data in other regions for:

- Performance reasons. 
- Enabling users to search and access data that may reside across regions. 

For example, if your default OCS region is `US-West`, OCS may process your data in the `EU-West` region, as depicted below. For a list of available regional endpoints, see <xref:regional-endpoints-ocs>.

![Cross-region data sharing enabled](./_images/cross-region-data-sharing.drawio.svg)

## Opt out of cross-region data sharing

For data security and [General Data Protection Regulation (GDPR)](https://gdpr.eu/) compliance, you can opt out of cross-region data sharing. If you opt out of cross-region data sharing, your data is not processed outside of the region where it resides. Disabling this setting may reduce performance and searchability. However, it ensures that your namespace is GDPR compliant.

![Cross-region data sharing disabled](./_images/cross-region-data-sharing-disabled.drawio.svg)

If you want to opt out of cross-region data sharing, complete the following tasks in order:

- [Step 1: Opt out of cross-region data sharing for namespace](#step-1-opt-out-of-cross-region-data-sharing-for-namespace)

- [Step 2: Configure the community preferred region for community](#step-2-configure-the-community-preferred-region-for-community)

### Step 1: Opt out of cross-region data sharing for namespace

Queries are routed to the appropriate region for complete results to be returned.

1. From the **Namespace** drop-down, select a namespace or community for which you want to opt out of data sharing. 

1. From the **Namespace** drop-down, select the **Cog** ![Cog](./_icons/default/cog.svg).

1. Select the **Data Sharing** tab.

1. Select **Edit**.

1. Enable **Opt-out for Namespace** and select **Save**.

### Step 2: Configure the community preferred region for community

The Community Preferred Region setting should be used when opting out so that clients are aware of the appropriate region to use.

1. Elit pariatur aute aliqua quis Lorem in excepteur commodo mollit ea.

1. Ullamco nulla quis est excepteur.

1. Aliqua cupidatat ea laborum enim Lorem culpa eiusmod sit deserunt ipsum tempor quis ex.