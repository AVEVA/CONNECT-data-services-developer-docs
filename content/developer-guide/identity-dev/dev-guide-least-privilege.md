---
uid: LeastPrivilege
---

# Least privilege

When creating new users or client-credentials clients, configure them using the principle of least privilege, which is that a process, user, or program should be able to access only the information and resources that are necessary for its legitimate purpose. Assign users and clients the lowest privileged role necessary to access resources.

Ensure that clients which are not in use are either deleted or disabled by setting the **Enabled** property to false. This can be done through the portal (see <xref:ClientMaintenance>) or through the appropriate API (see <xref:identityClientCredentialClient>, <xref:identityHybridClient>, or <xref:identity-authorization-code-clients>).

To limit the potential consequences of client credential theft, do not assign client credentials clients to the Administrator role. Any actions that require Administrator privileges should be done through the portal, when possible. 

## One client per application

It is recommended to create a client for each instance of a running application. This makes identification easier and decreases the attack surface from a leaked secret. In such an event, only one application needs to be updated.
