---
uid: known-issues
---

# PI to OCS known issues

The following are known issues in PI to OCS:

1. If there is no default PI server associated and listed for your AF server, you will not be able to transfer data to OCS.

1. PI servers that have a non-GUID server ID are not supported in PI to OCS. See [Generate a new server ID for PI Data Archive](https://docs.osisoft.com/bundle/pi-server/page/generate-a-new-server-id-for-a-pi-server-for-3.4.375-and-later.html) for how to address this issue.

1. PI to OCS Configuration Utility: Detected Data Archives fail to load if the user doesn't have permissions to one or more of the referenced Data Archives. The workaround is to add the Data Archive by clicking the green plus icon in the utility and then manually type the name of the Data Archive.

1. Query search results that contain a very large number of PI points (> 1 million) will generate an exception error and not be processed.

1. PI points with the type Float16 are supported, but the data is sent as Float32 to the cloud. The initial streaming value is rounded in the historical archive, so historical retrieval of the value may not match the initial value exactly.