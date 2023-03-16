---
uid: OMFmigration
---

# OMF API v1 to v2 migration

AVEVA has released v2 APIs for managing OMF connections that replace the current v1 APIs for managing OMF topics and subscriptions. As a result, support for OMF topics and subscriptions will end on April 30, 2023. The changes are as follows:

- Topics and subscriptions are now consolidated into a single concept called OMF connections. You can read more about OMF Connections in <xref:omf-ingress-omf-connections>.

- The process for [sending OMF data](xref:omf-ingress-omf) remains unchanged. Once an OMF Connection is created and is in the Active state, you can use the same API as before to send OMF data. There are no changes to how this data is processed or its throughput performance.

- With the v1 APIs, you could create a topic in one namespace and its corresponding Subscription could be created in a different namespace. This feature is not supported with the new APIs. With an OMF Connection, the OMF data resides in a single namespace.

You will need to manually migrate any existing topics and subscriptions to OMF Connections before April 30, 2023. You can do this through **Data Collection** > **OMF Connections** on the portal, or by using the OMF APIs directly. The steps to migrate each topic are:

1. Create a list of ClientIds assigned to the topic.

1. Stop sending OMF data through these clients. Complete this step when you can tolerate a potential disruption in data flow.

   - For AVEVA Adapters (formerly PI Adapters), stop the adapter service. Data collection and data egress will stop. Refer to the adapter online documentation for details.

   - For Edge Data Store, complete this step when Periodic Egress is not running.

   - For custom OMF applications, consult the application provider for guidance.

1. Delete the topic. All Subscriptions corresponding to the topic will be deleted automatically.

1. Create a new OMF Connection and add the ClientIds to it that you noted in step 1.

1. Wait for the OMF Connection to become active. This should only take a minute or two.

1. Resume sending OMF data through these clients.

   - For AVEVA Adapters, start the adapter service. Data collection and data egress will resume. Refer to the adapter online documentation for details.

   - For custom OMF applications, consult the application provider for guidance.

Repeat the process for each topic. If you have any questions or need help with the migration, contact our [support team](https://my.osisoft.com).