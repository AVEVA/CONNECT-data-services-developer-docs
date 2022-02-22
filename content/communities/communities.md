---
uid: communities
---

# Communities (Preview)

The _communities_ feature lets a tenant create a private group where trusted business partners can share and view operational data across tenants. Using communities, industrial companies can share their data streams with external trusted business partners, service providers, and analytics providers. 

Sharing data streams allows you and your partners to find value in each other's operational data: 

* Collectively operate more efficiently and reduce waste.

* Detect hidden problems in your equipment and processes, helping to troubleshoot issues.

* Predict future failures before they occur.

* Share data across engineering and operational partners.  

**Want to set up a community now?** See <xref:community-workflow-create>. 

## Community data flow

The following diagram shows an established community. 

![Community diagram](images/community-diagram.svg)

Within this diagram, a Tenant Administrator (callout **1**) from **Tenant A** has invited **Tenant B** to form a community. 

Both **Tenant A** and **Tenant B** have two streams stored in each of their tenants, as depicted by callout **2**. The data from these streams are being collected from various sources: PI Servers, edge devices, and other industrial data sources (callout **3**). 

Both tenants are sharing only one of their data streams within the community **4**). A data steward with sharing privileges on the stream must explicitly share it into a community that they have read access to.

All data streams shared within the community can be viewed by any community member (callout **5**). Within a community, users with community administration privileges can invite and manage which users within their tenant can participate in the community and view shared data.

## Community features and benefits

Communities allow you to easily and securely share operational data with trusted business partners. 

### Connect with trusted business partners

Establish a community by creating it and then inviting your trusted business partners to join from their tenant. Each invitation is a three-way handshake. The Tenant Administrator that established the community, known as the Community Owner, sends an email invitation to a Tenant Administrator for the business partner's tenant. The trusted business partner then accepts the invitation. The Community Owner confirms the invitation, allowing the trusted partner to join the community. After confirmation, users from the business partner's tenant can view data from other community tenants or share data streams from their own tenant with the community.

### Scalable

Communities allow you to share your data streams with multiple trusted business partners in a standardized way. Each community supports membership for an unlimited number of tenants, and each tenant can join an unlimited number of communities.

### Multi-tenant users and permissions

Communities support multi-tenant management of users and permissions. 

Within each tenant, community administrators can independently invite or remove users, separating users and permissions from other tenants in the community. Each tenant within the community has individual control over which of its users can access the community or share data within it. Community administrators cannot control users or permissions in other tenants.

<!-- TODO: Update paragraph below based on design document -->

Additionally, community roles allow each tenant to manage users and roles specifically for communities. Users can be assigned granular permissions to view community data, share data streams within the community, or invite other tenants to the community.

### Secure data sharing

Communities allow tenants to securely share operational data with their trusted business partners. 

Any tenant invited to a community must accept the community invitation and be confirmed by the inviting tenant before they can share data with other tenants or view shared data from other tenants. After joining a community, each tenant must explicitly share any data stream that they want the community to view. Each tenant shares individual data streams with the community—not their entire operational data set. 

Each tenant in the community can stop sharing their data streams at any time. When you stop sharing a data stream, the other tenants within the community can no longer view it, nor its history. When you share data streams, you provide the community with _access_ to your streams rather than copying data across tenants.

Because tenants can share their data natively within OCS, IT departments no longer have to:

* Manage access for external users within a corporate firewall.

* Create workarounds like VPNs or custom apps.

* Allow business partners onsite to access local operational systems.
  
### Easy setup

Because communities are in the cloud, using them does not require installation of additional hardware or software.

Communities can accommodate trusted business partners who are not sharing data or do not have a PI system of their own. With Communities, business partners can sign up for their own OCS tenant to read and gain access to data shared, without having to implement an on-premises PI System or other software.
