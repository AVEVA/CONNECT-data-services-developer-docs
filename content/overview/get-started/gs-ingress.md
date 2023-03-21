---
uid: gs-ingress
---

# Step 4: Ingress data

Ingress data into your AVEVA Data Hub tenant using one of two options, or both:

## Option A: Collect data from PI Server

**Prerequisite:** You must have a PI Server installed and configured.

1. [Install the PI to Data Hub Agent](https://docs.aveva.com/bundle/data-hub/page/add-organize-data/collect-data/connectors/pi-to-ocs/set-up-pi-to-ocs/install-agent.html)
2. [Run the PI to Data Hub Agent Configuration Utility](https://docs.aveva.com/bundle/data-hub/page/add-organize-data/collect-data/connectors/pi-to-ocs/set-up-pi-to-ocs/config-utility.html)
3. [Create a data transfer to ingress the PI Server data to AVEVA Data Hub.](https://docs.aveva.com/bundle/data-hub/page/add-organize-data/collect-data/connectors/pi-to-ocs/pi-to-ocs-data-transfers/transfer-data-to-ocs.html)

## Option B: Collect data directly from edge devices

Review the following documentation and complete the following tasks:

**Prerequisite:** You must have EDS or an adapter installed and configured on an edge device.

1. [Review OMF best practices](https://docs.aveva.com/bundle/data-hub/page/add-organize-data/collect-data/connectors/omf/omf-connection-best-practices.html)
2. [Create a client credential client](https://docs.aveva.com/bundle/data-hub/page/set-up/clients/client-credentials-client-procedure.html)
 The edge device uses this client to authenticate with AVEVA Data Hub.
3. [Create an OMF connection](https://docs.aveva.com/bundle/data-hub/page/add-organize-data/collect-data/connectors/omf/omf-connection-procedure.html)
 Connect your edge devices to AVEVA Data Hub.
