---
uid: gsAuthorizationCodeClients
---

# Get started with authorization code clients

Authorization code clients are used with customer web applications that use AVEVA Data Hub as their backend. They provide a secure means of authenticating users of the website to view AVEVA Data Hub assets. For more information about authorization code clients, see [Authorization code clients](xref:ccClients#authorization-code-client).

To create an authorization code client, follow these steps:

1. In the left pane, select **Security > Clients**.

1. In the **Client Type** field, select **Authorization Code**.

1. In the toolbar, select **Add Client**.

   The `Add Client` window appears.

1. In the **Name** field, enter a name to identify the device or application that will use this client. 

   Use this name to identify the device or application that will use this client.

1. Enter the URLs in the **Allowed Redirect URL(s)** text box, and click  **+**  to add it to the list. 

   The application specifies one of the URLs in this list when it authenticates, and AVEVA Data Hub returns the results of the authentication to this URL.

1. (Optional) Enter URLs in the **Allowed Logout Redirect URL(s)** text box, then click **+**  to add it to the list. 
   
      This can be used to designate other URLs from which the application is allowed to make requests against AVEVA Data Hub. For example, this may be necessary if the user authenticates from an application running at `https://authenticate.com`, but the result of the authentication is sent to an application running at a different URL, for example, `https://application.com`.
   
1. (Optional) Enter URLs in the **Allowed CORS Origin(s)** text box, then click **+** to add it to the list. <!--VTT, 12/13/21: New step added since it was missing. Requested by N. Parakh & A. Woodall.-->
   
   Entering a URL in the Allowed CORS Origin(s) text box enables cross-origin requests to the client from selected sites. This can be used to designate other URLs from which the application is allowed to make requests against AVEVA Data Hub. For example, this may be necessary if the user authenticates from an application running at one URL but the result of the authentication is sent to an application running at a different URL.

1. (Optional) Set the **Token Lifetime**. 

   The default, 3600 seconds (one hour), is the maximum length of time. The minimum value is 60 seconds.

1. Select **Add**.  

   The `Client Successfully Created` window displays the client Id for the client. The application must specify this client Id when it makes an authentication request. To copy the client Id, select the **Copy** icon. After you close this window, you can also retrieve the client Id from the list of clients.

1. Click **Close**.

## Next step

Continue with either of the following:

- [Get started with client-credentials clients](xref:gsClientCredentialsClients) 

- [Get started with hybrid clients](xref:gsHybridClients)

When all three are complete, continue with [Get started with assets](xref:gsAssets).