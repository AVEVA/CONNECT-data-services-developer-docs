---
uid: gsHybridClients
---

# Get started with hybrid clients

Hybrid clients are used by native and server-side web applications. Authentication can be performed using any supported browser. The server-side code retrieves an access token and a refresh token can also be provided. See the following topics for more information about hybrid clients:

- [Introduction to hybrid clients](xref:ccClients#hybrid-client)

- [Hybrid client PI Server counterpart](xref:ccClients#hybrid-client-pi-server)

- [Hybrid client best practices](xref:ccClients#hybrid-client-bp)

## Create a hybrid client

1. In the left pane, select **Security** > **Clients**.

1. From the **Client Type** dropdown list, select **Hybrid**.

1. In the toolbar, click **Add Client**.

1. Enter a name for the client.  

   Use this name to identify the application that will use this client.

1. (Optional) Select the **Allow Refresh Token** check box if the application uses refresh tokens to keep users logged in to AVEVA™ Data Hub.
   
   **Note:** Avoid selecting this option if there is no need to refresh tokens. There is a long lifespan for requesting new access tokens. 

1. Enter the URLs in the **Allowed Redirect URL(s)** text box, then click **+** to add it to the list.  
   
   The application specifies one of the URLs in this list during authentication, and AVEVA Data Hub returns the results of the authentication to this URL.

1. (Optional) Enter URLs in the **Allowed Logout Redirect URL(s)** text box, and click **+** to add it to the list.  
   
   This is similar to the **Allowed Redirect URL(s)**. The application specifies one of the URLs from this list when it logs a user out of Data Hub, and the Data Hub identity server sends the user to that URL after a successful log out.

1. (Optional) Set the **Token Lifetime**.  
   
   Token Lifetime represents the length of time in seconds the access token is valid before it expires. The default, 3600 seconds (one hour), is the maximum length of time. The minimum value is 60 seconds.

1. Click **Add**.  

1. In the `Add Secret` dialog box, enter a description and expiration date for the secret, then click **Add**.
 
   **Note:** Enter a unique description if you plan to create multiple secrets. 
                
   The `Client Successfully Created` window displays the client Id for the client. The application must specify this client Id when it makes an authentication request. To copy the `client Id`, click the **Copy** icon. Alternatively, after you close the window, you can retrieve the `client Id` from the list of clients.

## Next step

Continue with either of the following topics: 

- [Get started with client-credentials clients](xref:gsClientCredentialsClients) 

- [Get started with authorization code clients](xref:gsAuthorizationCodeClients)
