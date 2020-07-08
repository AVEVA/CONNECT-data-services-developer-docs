# Create a hybrid client

1. On the OCS Portal home page, click the [add icon image] icon to display the menu.
2. Under Security, click **Clients**.
3. On the Manage Clients page, select **Hybrid** from the Client Type list.
4. Click **Add Client** to display the Add Client window.
5. Assign a name to the hybrid client.
6. Select **Allow Refresh Token** to enable refresh tokens.
7. In the Redirect URL field, enter the URL to which the OCS identity provider sends the access token it generates for an authenticated user.
8. In the Logout Redirect URL field, provide the URL of the page to which users will be redirected after they log out from the OCS identity provider.
9. Click + to commit your entry.
10. In the Token Lifetime field, accept the default, 3600 seconds, or enter another time.
11. Click **Continue**. 
12. In the Expiration Date field, select an expiration date and time for the secret. 
13. Click **Add**.
14. Click the Client ID and Client Secret copy icons.
15. Save both and reference them in the application code. 

