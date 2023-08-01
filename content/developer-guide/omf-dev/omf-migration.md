---
uid: OMFmigration
---

# Migrate OMF topics/subscriptions to connections

AVEVA has released the OMF connections API, which replaces the subscriptions and topics APIs for managing OMF connections. As a result, support for OMF topics and subscriptions will end on April 30, 2023. The changes are as follows:

- Topics and subscriptions are now consolidated into a single concept called OMF connections. See <xref:omf-ingress-omf-connections> for details.

- The process for [sending OMF data](xref:omf-ingress-omf) remains unchanged. Once an OMF connection is created and is in the active state, you can use the same API as before to send OMF data. There are no changes to how this data is processed or its throughput performance.

- With the previous APIs, you could create a topic in one namespace and its corresponding subscription could be created in a different namespace. This feature is not supported with the new API. With OMF connections, the OMF data resides in a single namespace.

You will need to manually migrate any existing topics and subscriptions to OMF connections before April 30, 2023. You can do this through **Data Collection** > **OMF Connections** on the portal, or by using the OMF APIs directly. The steps to migrate each topic are:

1. Create a list of ClientIds assigned to the topic.

1. Stop sending OMF data through these clients. Complete this step when you can tolerate a potential disruption in data flow.

   - For AVEVA Adapters (formerly PI Adapters), stop the adapter service. Data collection and data egress will stop. Refer to the adapter online documentation for details.

   - For Edge Data Store, complete this step when Periodic Egress is not running.

   - For custom OMF applications, consult the application provider for guidance.

1. Delete the topic. All subscriptions corresponding to the topic will be deleted automatically.

1. Create a new OMF connection and add the ClientIds to it that you noted in step 1.

1. Wait for the OMF connection to become active. This should only take a minute or two.

1. Resume sending OMF data through these clients.

   - For AVEVA adapters, start the adapter service. Data collection and data egress will resume. Refer to the adapter online documentation for details.

   - For custom OMF applications, consult the application provider for guidance.

Repeat the process for each topic. If you have any questions or need help with the migration, contact our [support team](https://my.osisoft.com).