---
uid: gsClientCredentialsClients
---

# Get started with client-credentials clients

Client-credentials clients are used for server-to-server communication where no user interaction is required. For more information about client-credentials clients, see [Client-credentials clients](xref:ccClients#client-credentials-client).

To create a client-credentials client, follow these steps:

1. In the left pane, select **Security** > **Clients**.

1. From the **Client Type** field, select **Client-Credentials**. This is the option that is displayed by default.

1. In the toolbar, click **Add Client**.

  The `Add Client` window opens.

1. In the **Name** field, enter a name for the client that identifies the device or application that will use this client.

1. Select the **MyData.Role** role for the client.
   
   By default, the client is assigned the Tenant Member role which cannot be removed. Roles can be modified after the client is created.

   **Note:** The **MyData.Role** role is a custom role in this exercise. 

1. (Optional) Set the **Token Lifetime**.  
   
   Token Lifetime represents the length of time in seconds that the access token for this Client is valid from the time issued until it expires.
   
   The default, 3600 seconds (one hour), is the maximum length of time. The minimum value is 60 seconds.

1. Select **Continue**.

1. In the `Add Secret` window, enter a description for the client secret. If you plan to create multiple secrets, include a unique description.

1. Enter an expiration date.

   Choose an expiration date that is appropriate for your use case. By default, the secret is set to expire one year after creation. You may specify that the secret does not expire by selecting the **Never Expires** checkbox. Secrets can be deleted later, including secrets that are set to never expire.

1. In the **Expiration Date** field, enter a date and time that the secret expires.
  
   Ensure that the expiration date is valid for the secret. By default, the secret is set to expire one year after creation. Select the **Never Expires** checkbox to specify that the secret does not expire. Secrets can be deleted later, including secrets that are set to never expire.

1. Select **Add**.

  The `Client Successfully Created` window opens and displays the **Client Id** and **Client Secret**.
    
   **Important:** Select the **Copy** button to the right of each field to save the client secret and client Id. You need this information to connect your applications. Once the window is closed, the client secret cannot be accessed or retrieved.
    
1. Select **Close**.  

   **Note:** In the list of secrets, the **Client Id** is still visible. If you did not save the client secret, select the client in the list and use the `Details` pane to remove the old secret and add a new secret. Client modifications may take up to an hour before being visibly updated.

## Next step

Continue with either of the following:

- [Get started with authorization code clients](xref:gsAuthorizationCodeClients)

- [Get started with hybrid clients](xref:gsHybridClients)

When all three are complete, continue with [Get started with assets](xref:gsAssets).
