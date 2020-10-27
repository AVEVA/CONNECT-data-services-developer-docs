---
uid: TokenManagement
---

# Token Management
Access tokens are used to grant a client access to OSIsoft resources on behalf of a user. 

## ClientCredential Clients

The application must be running in a device/virtual machine that you either own or have provisioned and must be a secure environment (for example, only authorized persons can access the application and its associated secrets).

A valid Access Token grants its possessor access to protected resources. As such, they are as critical as passwords and secrets and should be treated the same way.

## Authorization Code Clients

The application will be running in a browser.
The OWASP foundation suggests storing the Access Token in the browser session Storage container.
