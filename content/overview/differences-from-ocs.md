---
uid: DifferencesFromOCS
---

# Differences between OSIsoft Cloud Services and AVEVA Data Hub

OSIsoft Cloud Services (OCS) is moving to the AVEVA™ Connect cloud platform and being rebranded as AVEVA Data Hub. Most of the functionality from OCS remains the same in AVEVA Data Hub, but there are a few differences to be aware of.

- [AVEVA Connect](https://www.aveva.com/aveva-connect/) is our common cloud platform, providing a central location to securely access the broadest and deepest industrial software-as-a-service (SaaS) portfolio enhanced by the power of industrial Artificial Intelligence (AI).

  AVEVA Connect hosts AVEVA Data Hub and subscription to AVEVA Data Hub is handled through the AVEVA Connect Services Catalog.

- Namespaces are not managed within AVEVA Data Hub, as they were in OCS. Creating a folder in AVEVA Connect automatically activates a corresponding namespace within AVEVA Data Hub. See [Folders and namespaces](xref:ccNamespaces).

- The only identity provider (IdP) AVEVA Data Hub supports is AVEVA Connect. IdPs that can federate with AVEVA Connect should work with AVEVA Data Hub, subject to AVEVA evaluation for IdP compatibility. See the [AVEVA Connect Service Description](https://www.aveva.com/content/dam/aveva/documents/legal/service-documents/AVEVA-Connect-Services-v1-21.pdf).

- Adding users and creating groups is handled initially within AVEVA Connect. See [Manage permissions in AVEVA Connect](xref:manage-permissions-connect). Once those users and groups exist in AVEVA Connect, they can be added and assigned roles within AVEVA Data Hub. See [AVEVA Data Hub users](xref:ccUsers) and [AVEVA Data Hub Groups](xref:Groups).
