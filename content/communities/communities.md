---
uid: communities
---

# Communities

The _communities_ feature lets an OCS tenant create a private group where business partners can share and view each other's operational data. Using communities, industrial companies can share their data streams with external business partners, service providers, and analytics providers. 

Sharing operational data allows you and your partners find value in each other's data: 

* Collectively operate more efficiently and reduce waste.
* Detect hidden problems in your equipment and processes, helping to troubleshoot issues.
* Predict future failures before they occur.
* Share data across engineering and operational partners.  

**Want to set up a community now?** See <xref:gsCommunities>.

## Community diagram

The following diagram visually displays an established community. 

![Community diagram](images/community-diagram.drawio.svg)

Within this diagram, a [tenant administrator](xref:communityroles#tenant-administrator) (figure **1**) from  **Tenant A** has invited **Tenant B** to form a community. 

Both **Tenant A** and **Tenant B** have established two streams, as depicted by figure **2**. The data from these streams are being collected from various sources: PI Databases, edge devices, and other industrial site devices (figure **3**). 

Both tenants are only sharing one of their data streams within the community: **Tenant A** is sharing their silver stream, and **Tenant B** is sharing their light blue stream (figure **4**). Either a [community administrator](xref:communityroles#community-administrator) or [community moderator](xref:communityroles#community-moderator) must explicity share a data stream.

All data steams shared within the community can be viewed by any [community member](xref:communityroles#community-member). Community administrators or moderators within a tenant can invite and manage which users within a tenants can view shared data.

## Community features and benefits
### Connect with business partners

Establish a community by creating it and then inviting other tenants owned by business partners. Each invitation is a three-way handshake. A tenant administrator from the establishing tenant, also known as the _community owner_, sends an email invitation to one or more OCS tenant administrator. The business partner then accepts the invitation before the tenant administrator confirms it. After confirmation, users from the newly confirmed tenant can view data from other community tenants or share data streams from their own tenant with the community.

* For more information on creating a community, see <xref:add-community>.
* For more information on inviting other tenants to a community, see <xref:managecommunity>.

### Scalable

Communities are scalable and can include multiple partners without increasing overhead on your IT department. Community administrators can invite or remove tenant members while keeping user and permissions separate.

The data streams that you share within your community are scalable as well. You can share no data streams or as many as you like. You can unshare data streams at any time, after which partners can no longer view those streams.

### Multi-tenant users and permissions

Communities support multi-tenant management of users and permissions. Each tenant within the community has individual control over which of its users can access the community or share data within it. Tenant administrators cannot control users or permission in other tenants. Because each tenant self-manages, the IT departments for each tenant only manage access and permissions for their own users, not their business partners, reducing overhead.

Additionally, OCS provides [community roles](xref:communityroles) that allow each tenant to manage users and roles specifically for communities. Users can be assigned granular permission to view community data, share data streams within the community, or manage community access for other tenants.

### Secure data sharing

- Opt in to community.
- Explicitly choose what streams you want to share.
- Data is viewed at source and never copied.
- Stop sharing at any time.

- IT departments for each partner no longer have to manage access for external users
- No need for workarounds like VPNs or custom apps.
- No need to allow customers onsite, improving safety and IT security.
- Share data with external partners without bringing their users inside the corporate firewall or taking extra security precautions.

### Easy setup

Because Communities are in the cloud, using them does not require installation of additional hardware or software.

Communities can accommodate business partners who are not sharing data or do not have a PI system of their own. They can own an OCS tenant without sharing data, allowing them to participate in a partnership without purchasing the full PI System or other required software.
