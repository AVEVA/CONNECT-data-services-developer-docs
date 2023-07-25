---
uid: LeastPrivilege
---

# Least privileges

When creating new users or client credential clients, configure them using the principle of Least Privilege. For more information, see Microsoft's article "Enhance security with the principle of least privilege" [Least Privilege](https://learn.microsoft.com/en-us/azure/active-directory/develop/secure-least-privileged-access). Assign users and clients the lowest privileged role necessary to access resources.

Ensure that clients which are not in use are either deleted or disabled by setting the **Enabled** property to false.
To limit the potential consequences of client credential theft, do not assign client credentials clients to the Administrator role. Any actions that require Administrator privileges should be done through the portal, when possible. 
<!-- Angela Flores 6/18/21 This should have a link to a procedure topic with instructions for setting the Enabled property. Also the link to Least Priviledge points to a page the is marked archived and contains a warning that the information may be out of date. Can we find an up-to-date link? -->

## One client per application

It is recommended to create a client for each instance of a running application. This makes identification easier and decreases the attack surface from a leaked secret. In such an event, only one application needs to be updated.
