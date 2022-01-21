---
uid: gsHybridClients
---

# Get started with hybrid clients

Hybrid clients are used by native and server-side web applications. Authentication can be performed using any supported browser. The server-side code retrieves an access token and a refresh token can also be provided. For more information about hybrid clients, see [Hybrid clients](xref:ccClients#hybrid-client).

**Note:** Client modifications may take up to an hour before being visibly updated.

To create a hybrid client, follow these steps:

1. In the left pane, select **Security** > **Clients**.

1. From the **Client Type** field, select **Hybrid**.

1. In the toolbar, select **Add Client**.

   The `Add Client` window appears.

1. In the **Name** field, enter a name to identify the device or application that will use this client.

1. (Optional) Select the **Allow Refresh Token** checkbox if the application uses refresh tokens to keep users logged in to AVEVA&trade; Data Hub.
   
   **Note:** Do not select this option if there is no need to refresh tokens. There is a long lifespan for requesting new access tokens. 

1. In the **Allowed Redirect URL(s)** box, enter a URL and select **+** to add it to the list.  
   
   The application specifies one of the URLs in this list during authentication, and AVEVA Data Hub returns the results of the authentication to this URL.

1. (Optional) In the **Allowed Logout Redirect URL(s)** box, enter a URL and select **+** to add it to the list.  
   
   The application specifies one of the URLs from this list when it logs a user out of AVEVA Data Hub, and AVEVA Data Hub sends the user to that URL after a successful log out.

1. (Optional) In the **Token Lifetime** field, enter the length of time in seconds that the access token functions before it expires. 

   The default, 3600 seconds (one hour), is the maximum length of time. The minimum value is 60 seconds.

1. Select **Add**.  

  The `Add Secret` window opens.

1. (Optional) In the **Description** field, enter a description to identify the client secret.

1. In the **Expiration Date** field, enter a date and time that the secret expires.

  Ensure that the expiration date is valid for the secret. By default, the secret is set to expire one year after creation. Select the **Never Expires** checkbox to specify that the secret does not expire. Secrets can be deleted later, including secrets that are set to never expire.

1. Select **Add**.  
                
   The `Client Successfully Created` window displays the client Id and client secret.
   
   **Important:** Select the **Copy** button to the right of each field to save the client secret and client Id. You need this information to connect your applications. Once the window is closed, the client secret cannot be accessed or retrieved.

## Next step

Continue with either of the following: 

- [Get started with client-credentials clients](xref:gsClientCredentialsClients) 

- [Get started with authorization code clients](xref:gsAuthorizationCodeClients)

When all three are complete, continue with [Get started with assets](xref:gsAssets).
