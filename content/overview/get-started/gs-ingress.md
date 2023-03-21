---
uid: gs-ingress
---

# Step 4: Ingress data

Ingress data into your AVEVA Data Hub tenant using one of two options, or both:

## Option A: Collect data from PI Server

**Prerequisite:** You must have a PI Server installed and configured.

1. <xref:install-agent>
2. <xref:pi-to-ocs-utility>
3. <xref:create-transfer>

## Option B: Collect data directly from edge devices

Review the following documentation and complete the following tasks:

**Prerequisite:** You must have EDS or an adapter installed and configured on an edge device.

1. [Review OMF best practices](xref:bpOMFConnection)
2. [Create a client credential client](https://docs.aveva.com/bundle/data-hub/page/set-up/clients/client-credentials-client-procedure.html)
 The edge device uses this client to authenticate with AVEVA Data Hub.
3. [Create an OMF connection](https://docs.aveva.com/bundle/data-hub/page/add-organize-data/collect-data/connectors/omf/omf-connection-procedure.html)
 Connect your edge devices to AVEVA Data Hub.
