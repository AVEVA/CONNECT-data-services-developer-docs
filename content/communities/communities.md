---
uid: communities
---

# Communities

The _communities_ feature lets a tenant create a private group where business partners can share and view operational data amongst themselves. Using communities, industrial companies can share their data streams with external business partners, service providers, and analytics providers. 

Sharing data streams allows you and your partners to find value in each other's operational data: 

* Collectively operate more efficiently and reduce waste.
* Detect hidden problems in your equipment and processes, helping to troubleshoot issues.
* Predict future failures before they occur.
* Share data across engineering and operational partners.  

**Want to set up a community now?** See <xref:gsCommunities>. 

## Community diagram

The following diagram visually displays an established community. 

![Community diagram](images/community-diagram.svg)

Within this diagram, a [tenant administrator](xref:communityroles#tenant-administrator) (callout **1**) from  **Tenant A** has invited **Tenant B** to form a community. 

Both **Tenant A** and **Tenant B** have established two streams, as depicted by callout **2**. The data from these streams are being collected from various sources: PI databases, edge devices, and other industrial site devices (callout **3**). 

Both tenants are only sharing one of their data streams within the community: **Tenant A** is sharing their silver stream, and **Tenant B** is sharing their light blue stream (callout **4**). Either a [community administrator](xref:communityroles#community-administrator) or [community moderator](xref:communityroles#community-moderator) must explicitly share a data stream.

All data streams shared within the community can be viewed by any [community member](xref:communityroles#community-member)(callout **5**). Within a community, administrators or moderators can invite and manage which users within their tenant can view shared data.

## Community features and benefits

Communities allow you to easily and securely share operational data with business partners. 

### Connect with business partners

Establish a community by [creating it](add-community) and then [inviting other tenants](xref:managecommunity) owned by business partners. Each invitation is a three-way handshake. A [tenant administrator](xref:communityroles#tenant-administrator) from the establishing tenant, also known as the [community owner](xref:communityroles#community-owner), sends an email invitation to one or more OCS tenant administrators. The business partner then accepts the invitation before the inviting tenant administrator confirms it. After confirmation, users from the newly confirmed tenant can view data from other community tenants or share data streams from their own tenant with the community.

### Scalable

Communities are scalable and can include multiple business partners without increasing overhead on your IT department. The community itself supports membership for an unlimited number of tenants. Communities scale with the number of tenants in the partnership.

Data streams that you share within your community are scalable as well. You can share no data streams or as many as you like. You can stop sharing data streams at any time, after which partners can no longer view those streams.

### Multi-tenant users and permissions

Communities support multi-tenant management of users and permissions. 

Within each tenant, [community administrators](xref:communityroles#tenant-administrator#community-administrator) can independently [invite or remove users](xref#managecommunityusers), keeping user and permissions separate from other tenants in the community. Each tenant within the community has individual control over which of its users can access the community or share data within it. Community administrators cannot control users or permission in other tenants.

Additionally, OCS provides [community roles](xref:communityroles) that allow each tenant to manage users and roles specifically for communities. Users can be assigned granular permissions to view community data, share data streams within the community, or manage community access for other tenants.

### Secure data sharing

Communities allow tenants to [securely share operational data](xref:ShareStreams#share-streams) with their business partners. 

Any tenant invited to a community must accept the community invitation before they can share data with other tenants. After joining a community, each tenant must explicitly share any data stream that they want to share with the community. Each tenant shares individual data streams with the community&mdash;not their entire operational data set. 

Each tenant in the community can [stop sharing their data streams](xref:ShareStreams#unshare-streams-from-community-details) at any time. When you stop sharing a data stream, the other tenants within the community can no longer view it, nor its history, as when you share data streams, each community member views them from the source&mdash;stream data is not copied among tenants. 

Because tenants can share their data natively within OCS, IT departments no longer have to:

* Manage access for external users within a corporate firewall.
* Create workarounds like VPNs or custom apps.
* Allow customers onsite.
  
### Easy setup

Because communities are in the cloud, using them does not require installation of additional hardware or software.

Communities can accommodate business partners who are not sharing data or do not have a PI system of their own. They can provision their own OCS tenant without sharing data, allowing them to participate in a partnership without purchasing the full PI System or other software.
