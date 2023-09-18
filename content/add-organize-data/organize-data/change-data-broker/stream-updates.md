---
uid: StreamUpdates
---

# Manage data event updates

You can sign up for data event updates for streams of interest with AVEVA Data Hub's API Console. This works with the Sequential Data Store (SDS) event provider service. For more on SDS and streams, read [Sequential Data Store](xref:lpstoredata).

Follow the steps below to create a Signup, activate Signups, and receive change data updates. Note that all steps must be done in order.

## Create a Signup

To sign up for data event updates from streams of interest, perform the following steps:

1. In the left pane, select **Developer Tools** > **API Console**.

1. In the **URI** field, type **/**, then select your desired Namespace. Then, type **Signups** to go to the Signups endpoint.

1. Select **POST** in the URI dropdown.

    The **POST** button appears.

1. Select **v1-preview** in the Full Path dropdown.

1. Paste the body text in the **Body** field. You should include the name of your Signup in the **Name** field, the resource type in the **ResourceType** field, and the stream Id(s) in the **ResourceIds** field. See below for an example:

```
{
  "Name": "string",
  "ResourceType": "Stream",
  "ResourceIds": [
    "string"
  ]
}
```

  For more information on the Signups API, read [Signups](xref:streaming-updates-signups).

1. Select the **POST** button.

  You should receive output containing an Id and a SignupState of "Activating."

## Activate Signups

To activate stream updates, perform the following steps:

1. Copy the Id provided in the previous output.

1. In the **URI** field, type **/**, then paste in your Id.

1. Select **GET** in the **URI** dropdown.

    The **GET** button appears.

1. Select the **GET** button.

  A SignupState of "Active" appears in the output.

## View accessible resources

Tenant admins can view all Signups created by users in the tenant. However, only the Signup owner is able to query a Signup.

To view the streams that are accessible for data event updates, perform the following steps:

1. In the **URI** field, type **/Resources** after your Id.

1. Select **Get**.

  The AccessibleResources and InaccessibleResources appear in the output.

## Receive change data updates

To receive stream updates, perform the following steps:

1. Copy the bookmark from the GET Signup endpoint header.

1. In the **URI** field, delete **/Resources** and paste the bookmark after your Id.

1. Select the **GET** button.

  The stream updates appear in the output.

You will now receive data event updates via the Change Data Broker.