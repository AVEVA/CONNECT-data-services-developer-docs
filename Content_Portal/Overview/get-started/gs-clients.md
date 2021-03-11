---
uid: gsClients
---
# Get started with clients

Clients provide a way for users or applications to authenticate against OSIsoft Cloud Services (OCS) from applications other than the OCS portal. OCS supports the following client types, each of which support different types of applications:
- [Client-credentials clients](#gsClient-credentials-clients)
- [Authorization code clients](#gsAuthorization-code-clients)
- [Hybrid clients](#gsHybrid-clients)

You must have the **Account Administrator** role to add and manage clients in a tenant.

## <a name="gsClient-credentials-clients"></a>Client-credentials clients

Client-credentials clients are used for server-to-server communication where no user interaction is required. See the following for more information about client-credentials clients:

- [Introduction to client credentials clients](xref:ccClients#client-credentials-client)
- [Client-credentials client PI Core counterpart](xref:ccClients#client-credentials-pi-core)
- [Client-credentials client best practices](xref:ccClients#client-credentials-bp)

### Creating a client-credentials client

1. Click the menu icon and click **Clients** (under Security).

1. From the **Client Type** dropdown list, select **Client-Credentials**. (This is the option that is displayed, by default.)

1. In the toolbar, click **Add Client**.

1. Enter a **Name** for the client.  
   Use this name to identify the device or application that will use this client.

1. Select the roles that are appropriate for the client.  
   By default, the client has the Account Member role which cannot be removed. Roles can be modified after the client is created.

1. (Optional) Set the **Token Lifetime**.  
   Token Lifetime represents the length of time (in seconds) the access token functions before it expires. The default, 3600 seconds (one hour), is the maximum length of time. The minimum value is 60 seconds.

1. Click **Continue**.

1. In the Add Secret window, enter a **Description** for the client secret.

1. Enter a date that the secret expires.  
   Ensure that the expiration date is valid for the secret. By default, the secret is set to expire one year after creation. You may specify that the secret does not expire by selecting the **Never Expires** checkbox. Secrets can be deleted later, including secrets that are set to never expire.

1. Click **Add**.  
   A window opens with the **Client Id** and **Client Secret**.  
   **IMPORTANT**:  
   Use the **Copy** buttons to the right of these fields to save the client secret and client ID. You will need to reference these in your applications. Once the window is closed, the **Client Secret** cannot be accessed or retrieved.

1. Click **Close**.  
   Note: In the list of secrets, the **Client Id** is still visible. If you did not save the **Client Secret**, select the client in the list and use the **Details** pane to remove the old secret and add a new secret.

## <a name="gsAuthorization-code-clients"></a>Authorization code clients

Authorization code clients are used with customer web applications that use OCS as their backend. They provide a secure means of authenticating users of the website to view OCS assets. See the following for more information about authorization code clients:

- [Introduction to authorization code clients](xref:ccClients#authorization-code-client)
- [Authorization code client PI Core counterpart](xref:ccClients#authorization-code-pi-core)
- [Authorization code best prractices](xref:ccClients#authorization-code-bp)

### Creating an authorization code client

1. Click the menu icon and click **Clients** (under Security).

1. From the **Client Type** dropdown list, select **Authorization Code**.

1. In the toolbar, click **Add Client**.

1. Enter a **Name** for the client.  
   Use this name to identify the device or application that will use this client.

1. Enter the URLs in the **Allowed Redirect URL(s)** text box.  
   The application will specify one of the URLs in this list when it authenticates against OCS, and the OCS identity server will return the results of the authentication to this URL.

1. (Optional) Enter URLs in the **Allowed Logout Redirect URL(s)** text box.  
   This is similar to the **Allowed Redirect URL(s)**. The application specifies an **Allowed Logout Redirect URL(s)** from this list when it logs out of OCS, and the OCS identity server sends the user to this URL after a successful log out.

1. (Optional) Enter URLs in the **Allowed CORS Origin(s)** text box.  
   This can be used to designate other URL(s) from which the application is allowed to make requests against OCS. For example, this may be necessary if the user authenticates from an application running at `https://authenticate.com`, but the result of the authentication is sent to an application running at a different URL, for example, `https://application.com`.

1. (Optional) Set the **Token Lifetime**.  
   Token Lifetime represents the length of time (in seconds) the access token is valid before it expires. The default, 3600 seconds (one hour), is the maximum length of time. The minimum value is 60 seconds.

1. Click **Add**.  
   The Client Successfully Created window displays the Client ID for the client. The application must specify this Client ID when it makes an authentication request. After you close this window, you can also retrieve the **Client Id** from the list of clients.

## <a name="gsHybrid-clients"></a>Hybrid clients

Hybrid clients are used by native and server-side web applications. Authentication can be performed using any browser. The server-side code retrieves an access token and a refresh token can also be provided. See the following for more information about hybrid clients:

- [Introduction to hybrid clients](xref;ccClients#hybrid-client)
- [Hybrid client PI Core counterpart](xref:ccClients#hybrid-client-pi-core)
- [Hybrid client best prractices](xref:ccClients#hybrid-client-bp)

### Creating a hybrid client

1. Click the menu icon and click **Clients** (under Security).

1. From the **Client Type** dropdown list, select **Hybrid**.

1. In the toolbar, click **Add Client**.

1. Enter a **Name** for the client.  
   Use this name to identify the application that will use this client.

1. (Optional) Select the **Allow Refresh Token** check box if the application uses refresh tokens to keep users logged in to OCS.

1. Enter the URLs in the **Allowed Redirect URL(s)** text box.  
   The application will specify one of the URLs in this list when it authenticates against OCS, and the OCS identity server will return the results of the authentication to this URL.

1. (Optional) Enter URLs in the **Allowed Logout Redirect URL(s)** text box.  
   This is similar to the **Allowed Redirect URL(s)**. The application specifies one of the **Allowed Logout Redirect URL(s)** from this list when it logs a user out of OCS, and the OCS identity server sends the user to that URL after a successful log out.

1. (Optional) Set the **Token Lifetime**.  
   Token Lifetime represents the length of time (in seconds) the access token is valid before it expires. The default, 3600 seconds (one hour), is the maximum length of time. The minimum value is 60 seconds.

1. Click **Add**.  
   The Client Successfully Created window displays the Client Id for the client. The application must specify this Client Id when it makes an authentication request. You can copy the Client ID by clicking on the Copy icon, or after you close this window, you can also retrieve the **Client Id** from the list of clients.
