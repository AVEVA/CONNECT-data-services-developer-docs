---
uid: TokenManagement
---

# Token management

A successful authentication process creates a token that grants access to protected resources. A valid access token is as critical as passwords and secrets and should be protected the same way.

A token is sent as part of the Authorization header with all requests to resources and services. Clients can be configured to generate access tokens with varying expiration between 60 seconds and one hour. The default access token lifespan is one hour. There is no limit on the number of access tokens a client can be issued at any given time.

## Token management with client-credentials clients

For applications using client-credentials client authorization, the application must be running in a secured device/virtual machine that you either own or have provisioned. Only authorized persons should have access to the application and its associated secrets.

## Token management with authorization code clients

For applications using authorization code clients and running in a browser, the Open Worldwide Application Security Project (OWASP) foundation suggests storing the access token in the browser session Storage container.
