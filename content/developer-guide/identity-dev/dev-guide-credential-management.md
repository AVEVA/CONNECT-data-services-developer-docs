---
uid: CredentialManagement
---

# Credential management

All connections to CONNECT data services are made using secure credentials, which are either user credentials or client secrets.

## User credentials and authentication

External identity providers manage user credentials and authentication.

## Client secrets and authentication

Client applications can authenticate a connection to CONNECT data services using a client Id and client secret pair. The client Id is the public identifier of the application. Client Ids are valid GUIDs that CONNECT data services randomly generates or the API caller provides when creating the client. The client Id does not need to be protected the same way as a client secret.

A client secret is a unique key that CONNECT data services generates for each client-credentials client to authenticate a connection to CONNECT data services for a limited period of time. Each client can have a maximum of 10 secrets at a time. Client secrets have a description, which contains information about their purpose and usage, and an expiration date.

**Caution:** As a security best practice, always create client secrets that expire.

CONNECT data services generates the secret value using a cryptographically secure algorithm. The secret value is available only upon creation. CONNECT data services does not maintain the actual value of the secret. If a secret value is lost, delete the secret and create a new one. 

### Client secret security

Keep client secrets secure. Do not store client secrets in text or transfer them through insecure channels. We recommend developing a strategy for managing and securing client secrets. Consider the following options while developing your security strategy:

- Use a cloud key management service, such as Azure Key Vault, Windows Credential Manager, Amazon Key Management Service, and Google Cloud Key Management, to persist and access the client secret for the environment where the client application is running.

- Refer to the Microsoft instructions on how to handle secrets and passwords in applications in the article [Handling Passwords](https://learn.microsoft.com/en-us/windows/win32/secbp/handling-passwords).

- Refer to the documentation from the programing language or framework you use to develop applications to determine what secret management security features they provide. 

- Use the hardware security module on the device where your application runs.

### Client secret rotation

We recommend using a secret rotation pattern to change secrets before they expire. Generate a new secret before the current secret expires and provide it to the client. The client should have logic to start using the new secret. Once the client is using the new secret, delete the old secret. 

**Caution:** Do not extend and reuse client secrets that are close to their expiration date. 
