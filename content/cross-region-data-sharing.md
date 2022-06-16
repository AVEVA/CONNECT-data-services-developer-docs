---
uid: cross-region-data-sharing
---

# Cross-region data sharing

By default, OSIsoft Cloud Services (OCS) processes operational data from your tenant's namespaces and communities in geographical regions other than your selected default region. OCS shares this data for the following purposes:

- Performance optimization 
- Enabling users to search and access data that may be stored across regions

For example, if you have a namespace in OCS that stores operational data in the `US-West` region, OCS may process that data in the `EU-West` region, as depicted below.

![Cross-region data sharing enabled](./_images/cross-region-data-sharing.drawio.svg)

## Cross region data sharing scenarios

Cross-region data sharing is enabled by default. When cross-region data sharing is enabled, OCS may share operational data for a namespace across regions under the following circumstances.

### Additional processing

Each namespace in OCS is bound to a geographical region. Operational data stored in each namespace is usually processed within that region, which is chosen while [adding the namespace](xref:gpNamespaces) and depicted below.

**Geographical region chosen during namespace creation**

![Namespace region](_images/add-namespace-region.png)

However, OCS may process a namespace's operational data in a different region (in other words, _cross-region_). For example, if you create a namespace in the `US-West` region, OCS may process its operational data cross-region in `EU-West`.

Processing operational data usually involves reshaping it. In these instances where operational data is processed cross-region, data from your region may reside in the cross-region processing service memory up to several hours. 

### Data augmentation

In use cases where your operational data is stored within both the chosen region and cross-region, OCS may process operational data from namespace region in a different region. OCS then adds and processes additional operational data from the other region before it displays in your browser session. In these instances, your data from both regions resides in the cross-region processing service memory up to several hours.

### Temporary storage

In some instances where OCS sends operational data stored in your namespace's region for processing or data augmentation cross-region, OCS may temporarily persist data from your region across regions before it is processed. This temporary storage is used for performance optimization. In these instances, data from your region persists in the cross-region processing service storage and memory up to several hours.

## Opt out of cross-region data sharing

Optionally, you can opt out of sharing operational data from namespaces and communities across regions. If you opt out of cross-region data sharing, your operational data is not processed or stored outside of the namespace's assigned region.

![Cross-region data sharing disabled](./_images/cross-region-data-sharing-disabled.drawio.svg)

<!-- ### To opt out of cross-region data sharing

If you want to opt out of cross-region data sharing, complete the following tasks in order:

- [Step 1: Opt out of cross-region data sharing for namespace](#step-1-opt-out-of-cross-region-data-sharing-for-namespace)
- [Step 2: Configure the community preferred region for community](#step-2-configure-the-community-preferred-region-for-community) -->

### To opt out of cross-region data sharing for namespace

When you disable cross-region data sharing, any queries for namespace data are routed to the appropriate region for complete results to be returned. Repeat these steps for each namespace that you want to disable cross-region data sharing.

1. From the **Namespace** drop-down, select a namespace for which you want to opt out of cross-region data sharing. 

1. From the **Namespace** drop-down, select the **Cog** ![Cog](./_icons/default/cog.svg).

1. Select the **Data Sharing** tab.

1. Select **Edit**.

1. Enable **Opt-out for Namespace** and select **Save**.

<!-- ### Step 2: Configure the community preferred region for community

If you are sharing data to one or more community, use the **Community Preferred Region** to control the region that clients view your shared data. Repeat these steps for each applicable community.

**Note:** You can skip this step if you are not using <xref:communities>.

**Prerequisite:** You must have write access in each community affected by cross-region data sharing.

1. Elit pariatur aute aliqua quis Lorem in excepteur commodo mollit ea.

1. Ullamco nulla quis est excepteur.

1. Aliqua cupidatat ea laborum enim Lorem culpa eiusmod sit deserunt ipsum tempor quis ex. -->