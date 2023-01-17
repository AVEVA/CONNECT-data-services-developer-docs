---
uid: troubleshoot-rpc
---

# Troubleshoot insufficient RPC threads for concurrent queries

If there are insufficient RPC threads for a large PI to Data Hub transfer, the transfer will fail and the event log will contain the error `OSIsoft.PI.Net.PIException: [-10767] Client exceeded maximum concurrent queries in RPC thread pool`.

To resolve this issue, set the `PIarchss_MaxThreadsPerClientQuery` tuning parameter in the PI System Management tool to 12 or higher. See the "PI Data Archive tuning parameters" section in the AVEVA™ PI Server documentation.
