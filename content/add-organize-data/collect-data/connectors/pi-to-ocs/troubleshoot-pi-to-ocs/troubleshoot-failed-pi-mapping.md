---
uid: troubleshoot-failed-mapping
---

# Troubleshoot a failed PI mapping

If you encounter an error message and the PI to Data Hub Configuration Utility crashes after an attempt to create or edit a PI mapping, follow these steps to troubleshoot and correct the issue:

1. Take one of the following steps:
 
    a) Reinstall the PI to Data Hub Agent with a service account that has access to the configured Data Archive.

    b) Add a different Data Archive that the service account has permission to access.

1. Relaunch the PI to Data Hub Configuration Utility: Click the Windows start button, then **AVEVA** > **PI to Data Hub Configuration Utility**.
1. Successfully connect and authenticate to AVEVA Data Hub.
1. In the PI to Data Hub Configuration utility, click the pencil icon to the right of the **PI Mapping** field.
2. Follow the steps in [Create a PI mapping](xref:pi-to-ocs-utility#create-a-pi-mapping) to add a PI mapping.
3. After adding the PI mapping, save your changes. 
