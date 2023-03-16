---
uid: OMFv2
---

# OMF API update

AVEVA has released v2 APIs for managing OMF Connections that replace the current v1 APIs for managing OMF Topics and Subscriptions. As a result, we will end support for OMF Topics and Subscriptions on April 30, 2023. The changes are as follows:

- Topics and Subscriptions are now consolidated into a single concept called OMF Connections. You can read more about OMF Connections in our documentation here.

- The process for sending OMF data remains unchanged. Once an OMF Connection is created and is in the Active state, you can use the same API as before to send OMF data. There are no changes to how this data is processed or its throughput performance.

- With the v1 APIs, you could create a Topic in one namespace and its corresponding Subscription could be created in a different namespace. This feature is not supported with the new APIs; with an OMF Connection, the OMF data resides in a single namespace.

If you use OMF, you will need to manually migrate your Topics and Subscriptions to OMF Connections before April 30, 2023. You can do this through the OMF Connections portal, or by using the OMF APIs directly. The steps to carry out the migration for each Topic are as follows:

1. Note the list of ClientIds assigned to the Topic.

1. Stop sending OMF data through these Clients. Complete this step when you can tolerate a potential disruption in data flow.

   - For AVEVA Adapters (formerly PI Adapters), stop the adapter service. Data collection and data egress will stop. Refer to the adapter online documentation for details.

   - For Edge Data Store, complete this step when Periodic Egress is not running.

   - For custom OMF applications, consult the application provider for guidance.

1. Delete the Topic. All Subscriptions corresponding to the Topic will be deleted automatically.

1. Create a new OMF Connection and add the same ClientIds to it as the ones you noted in Step 1.

1. Wait for the OMF Connection to become active. This should only take a minute or two.

1. Resume sending OMF data through these Clients.

   - For AVEVA Adapters, start the adapter service. Data collection and data egress will resume. Refer to the adapter online documentation for details.

   - For custom OMF applications, consult the application provider for guidance.

1. Repeat the above process for each Topic.

If you have any questions or need help with the migration, don't hesitate to contact our support team at https://my.osisoft.com.