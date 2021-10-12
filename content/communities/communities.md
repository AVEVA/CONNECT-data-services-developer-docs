---
uid: communities
---

# Communities

The _communities_ feature lets a tenant create a private group where business partners can share their own operational data and view operational data that their partner has shared. Using communities, industrial companies can share their data streams with external business partners, service providers, and analytics providers. 

Sharing operational data allows you and your partners find value in each other's data: 

* Collectively operate more efficiently and reduce waste.
* Detect hidden problems in your equipment and processes, helping to troubleshoot issues.
* Predict future failures before they occur.
* Share data across engineering and operational partners.  

**Want to set up a community now?** See <xref:gsCommunities>.

## Community diagram

The following diagram visually displays an established community. 

![Community diagram](images/community-diagram.svg)

Within this diagram, a [tenant administrator](xref:communityroles#tenant-administrator) (callout **1**) from  **Tenant A** has invited **Tenant B** to form a community. 

Both **Tenant A** and **Tenant B** have established two streams, as depicted by callout **2**. The data from these streams are being collected from various sources: PI Databases, edge devices, and other industrial site devices (callout **3**). 

Both tenants are only sharing one of their data streams within the community: **Tenant A** is sharing their silver stream, and **Tenant B** is sharing their light blue stream (callout **4**). Either a [community administrator](xref:communityroles#community-administrator) or [community moderator](xref:communityroles#community-moderator) must explicitly share a data stream.

All data steams shared within the community can be viewed by any [community member](xref:communityroles#community-member). Community administrators or moderators within a tenant can invite and manage which users within a tenants can view shared data.

## Community features and benefits

Communities allow you to easily and securely share operational data with business partners. 

### Connect with business partners

Establish a community by creating it and then inviting other tenants owned by business partners. Each invitation is a three-way handshake. A tenant administrator from the establishing tenant, also known as the _community owner_, sends an email invitation to one or more OCS tenant administrator. The business partner then accepts the invitation before the tenant administrator confirms it. After confirmation, users from the newly confirmed tenant can view data from other community tenants or share data streams from their own tenant with the community.

* For more information on creating a community, see <xref:add-community>.
* For more information on inviting other tenants to a community, see <xref:managecommunity>.

### Scalable

Communities are scalable and can include multiple partners without increasing overhead on your IT department. Community administrators can invite or remove tenant members while keeping user and permissions separate.

The data streams that you share within your community are scalable as well. You can share no data streams or as many as you like. You can stop sharing data streams at any time, after which partners can no longer view those streams.

### Multi-tenant users and permissions

Communities support multi-tenant management of users and permissions. Each tenant within the community has individual control over which of its users can access the community or share data within it. Tenant administrators cannot control users or permission in other tenants. Because each tenant self-manages, the IT departments for each tenant only manage access and permissions for their own users, not their business partners, reducing overhead.

Additionally, OCS provides [community roles](xref:communityroles) that allow each tenant to manage users and roles specifically for communities. Users can be assigned granular permission to view community data, share data streams within the community, or manage community access for other tenants.

### Secure data sharing

Communities allow tenants to share data operational data with their business partners securely. Any tenant invited to a community must accept the community invitation before they can share data with other tenants. After joining a community, each tenant must explicitly share any data stream that they want to share with the community. Each tenant can share individual data streams with the community&mdash;not their entire operational data set. Each tenant in the community can stop sharing their data streams at any time. When you stop sharing a data stream, the other tenants within the community can no longer view it, nor its history, as when you share data streams, each community member that views it viewing it from its source&mdash;stream data is never copied. 

Because tenants can share their data natively within OCS, IT departments no longer have to:

* Manage access for external users within a corporate firewall.
* Create workarounds like VPNs or custom apps.
* Allow customers onsite.
  
### Easy setup

Because communities are in the cloud, using them does not require installation of additional hardware or software.

Communities can accommodate business partners who are not sharing data or do not have a PI system of their own. They can own an OCS tenant without sharing data, allowing them to participate in a partnership without purchasing the full PI System or other required software.
