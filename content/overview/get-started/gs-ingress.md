---
uid: gs-ingress
---

# Step 4: Ingress data

Ingress data into your AVEVA Data Hub tenant using any of the following options.

## Option A: Collect data from PI Server

Transfer on-premises PI data and Asset Framework (AF) data into AVEVA Data Hub via a PI to Data Hub Agent.

1. <xref:install-agent>.

1. <xref:pi-to-ocs-utility>.

1. <xref:create-transfer>.

## Option B: Collect data directly from edge devices

Collect data from edge devices using an AVEVA Data Hub client and OMF connection.

**Prerequisite:** You must have EDS or an adapter installed and configured on an edge device.

1. Review <xref:bpOMFConnection>.

1. <xref:gpClientCredentialsClient>. The edge device uses this client to authenticate with AVEVA Data Hub.

1. <xref:gpOMFConnection>. Connect your edge devices to AVEVA Data Hub.

## Option C: Ingress data programmatically

APIs provide programmatic access to bring sequential data into AVEVA Data Hub. This can be done through custom OMF applications or utilizing SDS data writes.

See <xref:omfVsSds>.
