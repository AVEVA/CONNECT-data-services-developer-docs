# Create an authorization code client

1. On the OCS Portal home page, click the [add icon image] icon to display the menu.
2. Under Security, click **Clients**.
3. On the Manage Clients page, select **Authorization Code** from the Client Type list.
4. Click **Add Client** to display the Add Client window.
   In the Add Client window, you define key information required for the Authorization Code process flow.
5. Assign a name to the authorization code client.
6. In the Redirect URL field, enter the URL of the logon page of the website where users will be authenticating. The OCS identity provider will send the access token it generates for an authenticated user to this URL.
7. In the Logout Redirect URL field, provide the URL of the page which will log authenticated users out from the website. 
8. In the CORS Origin field, provide the domain name on which the website is running.
9. Click the + to commit your entry.
10. After completing all entries, click **Add** to create the authorization code client.
11. Click the **Copy Client ID** icon to capture the client ID. 
12. Save the client ID and reference it in the code for your website.