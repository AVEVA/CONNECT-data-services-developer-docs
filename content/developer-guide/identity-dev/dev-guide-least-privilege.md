---
uid: LeastPrivilege
---

# Least privilege

When creating new users or client credential clients, configure them using the principle of least privilege. For more information, see the Microsoft article [Enhance security with the principle of least privilege](https://learn.microsoft.com/en-us/azure/active-directory/develop/secure-least-privileged-access). Assign users and clients the lowest privileged role necessary to access resources.

Ensure that clients that are not in use are either deleted or disabled by setting the **Enabled** property to false. This can be done through the portal (see <xref:ClientMaintenance>) or through the appropriate API (see <xref:identityClientCredentialClient>, <xref:identityHybridClient>, or <xref:identity-authorization-code-clients>).

To limit the potential consequences of client credential theft, do not assign client-credentials clients to the administrator role. Any actions that require administrator privileges should be done through the portal, when possible. 

## One client per application

It is recommended to create a client for each instance of a running application. This makes identification easier and decreases the attack surface from a leaked secret. In such an event, only one application needs to be updated.
