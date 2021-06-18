---
uid: CredentialManagement
---

# Credential management

All connections to OCS are made using secure credentials, which are either user credentials or client secrets.

## User credentials and authentication

The management of user credentials and authentication is delegated to external identity providers.

## Client secrets and authentication

Applications can authenticate a connection to OCS using a client Id and a client secret. The client Id is the public identifier of the application. 

A client secret is a unique key that OCS generates for each client credential client to authenticate a connection to OCS for a limited period of time. Each client can have a maximum of 10 secrets at a time. Client secrets have a description, which contains information about their purpose and usage, and an expiration date. 

**Caution:** As a security best practice, always create client secrets that expire. 

OCS generates the secret value using a cryptographically secure, random number generator. The secret value is available only upon creation. OCS does not maintain the actual value of the secret. If a secret value were ever lost, delete the secret and create a new one. 

OSIsoft suggests persisting and accessing the Client Secret to/from secure storage for the environment the client application is running in. Some examples are: Azure Key Vault, Windows Credential Manager, Amazon Key Management Service, Google Cloud Key Management, etc. Microsoft provides instructions on how to handle secrets and passwords in applications in the Microsoft article [Handling Passwords](https://docs.microsoft.com/en-us/windows/win32/secbp/handling-passwords). We suggest referencing security documentation from the programing language or framework you develop your applications on to determine what secret management security features they provide. Another option is to use the hardware security module on the device your application runs on, or one of the cloud key management services that are available.

**Caution:** Keep client secrets secure. Do not store client secrets in text or transfer them through insecure channels.

Client Ids are valid GUIDs that are randomly generated, or provided by the caller upon creation. A client Id and client secret pair is required to perform an authentication, for clients that have been issued a secret. The client Id does not need to be protected the same way as a client secret.

### Client secret rotation

We recommend using a secret rotation pattern to change secrets before they expire. Generate a new secret before the current secret expires and provide it to the client. The client should have logic to start using the new secret. Once the client is using the new secret, delete the old secret. 

**Caution:** Do not extend and reuse client secrets that are close to their expiration date. 
