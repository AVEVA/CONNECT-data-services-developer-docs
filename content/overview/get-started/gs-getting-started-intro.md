---
uid: gs-adh
---

# Get started 

This is an introduction to the main features of AVEVA Data Hub using the portal. Each section includes a tutorial with step-by-step procedures using the portal functionality with links to basic concepts and best practices. Before you start the exercises, see [Introduction to the AVEVA Data Hub portal](xref:introPortalInterface) to get an overview of the user interface. Alternatively, you can accomplish the same tasks through the AVEVA Data Hub REST-based API. 

## Before you begin

Before you begin the get started exercises, obtain the following:

* Request a tenant from your AVEVA&trade; account manager.
* Have a designated folder that is connected to a namespace created prior to beginning these exercises.
* You must have Tenant Administrator privileges in AVEVA&trade; Data Hub.

## Log into the AVEVA&trade; Data Hub

Once you have completed the prerequisites, log into AVEVA&trade; Connect.

1. In a web browser, enter the following URL to open AVEVA&trade; Connect: *http://datahub.connect.aveva.com*

   **Notes:**
   
   * These browsers are supported for the most recent three versions, unless otherwise stated: Microsoft Edge, Google Chrome, Mozilla Firefox, and Internet Explorer 11.

   * If single sign-on is enabled, you only need to provide your email address when signing in to AVEVA&trade; Connect. You may be prompted to sign into your corporate Sign-In page.

1. From the AVEVA&trade; Connect home page, click on the folder that represents your organization's services.

   The applications available from this namespace account are displayed below the folder.

1. Select the tile that represents AVEVA&trade; Data Hub.

   The AVEVA&trade; Data Hub portal opens.
   
   <!-- I'm guessing there are additional next steps that depend on the Identity Provider they are using? --> 

## Get started goals

In these get started exercises, you will do the following:

1. Create a namespace that will contain all of your Data Hub resources, including an instance of the Sequential Data Store and the data streams.

1. Create two connection types, one that brings in PI Data Archive data and another that brings in data using an OMF application.

1. Create a type that defines the data you want to store.

1. Create a stream container to store that data.

1. Create clients for different types of applications.

1. Invite a user to your tenant.

1. Create a role that defines permissions for users.

**Note:** Each exercise is built upon the previous one; therefore, complete the exercises in the order shown. At the end of each exercise, you will be directed to the next exercise.  

## Next step

Start with [Get started with namespaces](xref:gsNamespaces).
