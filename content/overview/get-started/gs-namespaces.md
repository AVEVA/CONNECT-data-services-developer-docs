---
uid: gsNamespaces
---

# Get started with namespaces

The first task is to create a namespace, a logical unit of organization for data within a tenant. For more information on namespaces, see the following topics:

- [Namespaces](xref:ccNamespaces)

- [PI Server counterpart](xref:ccNamespaces#pi-server-counterpart) 

- [Namespace IDs](xref:ccNamespaces#namespace-ids)

- [Querying data across namespaces](xref:ccNamespaces#querying-data-across-namespaces)

- [Namespaces best practices](xref:bpNamespaces)

## Procedure

Creating a namespace is a resource-intensive operation. Therefore, you may prefer to use an existing namespace. In this procedure, the ID assigned to the namespace is MyOCS. Throughout the get started exercises, we refer to the namespace with this name. Substitute MyOCS with the name of an existing namespace or any other name you prefer.

1. In the left pane, select **Data Management** > **Namespaces**.

1. In the **Namespace Id** field, enter *MyOCS* for your namespace Id, enter a description, and select a region. 

   **Note:** Once the namespace is created, the **Namespace Id** and **Region** fields cannot be changed.

   When you are done, click **Add**.

1. Click **Display Details**.  

   - The window shows the tenant Id, namespace Id, description, and region of the namespace. It also displays zero (0) in the **Type Count** and **Stream Count** fields.

   - The details window shows the **State** field, which indicates the status of the namespace. Once the process of creating a namespace and bringing it online is complete, the value of the **State** field changes to *Active*. If the status does not display as *Active*, close the window and refresh the page. 

    **Note:** It will take some time for the namespace to be created. 

   <!-- LA: What is the status while the namespace is being set up? Can we give them an estimate of how long it might take for the namespace status to change to Active? Follow up with Derek. -->

1. Select the namespace in the list, and click **Edit Namespace**.  

   **Note:** The only field you can edit is the **Description** field.

1. Make any changes to the description and click **Save**.

### How to manage permissions on the namespace

<!-- DB: I think it makes sense to have that discussion as part of the Roles discussion, since that's the explicit purpose of Roles. But agreed it shouldn't be repeated in every page. --> 
<!-- LA: I will make a pass through all the topics once we've created the Roles topic. -->

Access control is managed by assigning permissions to roles. Each role is granted (Allow) or denied (Deny) permission to perform an access operation (read, write, delete, or manage permissions). Users are assigned to a role that determines their access to resources. 

**Note:** The remaining steps are optional. 

1. Click **Manage Permissions**.

1. Click the **Selected role** arrow, and select **Tenant Member** from the list.

1. To give the tenant member write permissions, select the **Allow** checkbox for the Write access type.

1. Click **Save**.

## Next step

Continue with [Get started with connections](xref:gsConnections).
