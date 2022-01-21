---
uid: gs-adh
---

# Get started 

The topics in this section contain exercises that introduce you to the AVEVA Data Hub portal. These exercises should be completed in order. Before you begin, see [Introduction to the AVEVA Data Hub portal](xref:introPortalInterface) to get acquainted with the portal's main features.

As an alternative, you can accomplish the same tasks in this section using the AVEVA Data Hub REST-based API.  

## Prerequisites

Before you begin the "Get started" exercises, perform these tasks:

* Request a tenant from your AVEVA account manager.

* Have a designated folder and associated namespace in place.

* Obtain Tenant Administrator privileges in AVEVA Data Hub.

## Log into the AVEVA Data Hub through AVEVA Connect

Once you have completed the prerequisites, log into AVEVA Connect to gain access to AVEVA Data Hub.

**Notes:**
   
   * The latest versions of Microsoft Edge, Google Chrome, and Mozilla Firefox are supported.

   * If single sign-on is enabled, you only need to provide your email address when signing in to AVEVA Connect. You may be prompted to sign into your corporate Sign-In page.

1. Point your web browser to *http://datahub.connect.aveva.com*.

1. From the AVEVA Connect home page, click on the folder that represents your organization's services.

   The applications available for this namespace account are displayed below the folder.

1. Select the AVEVA Data Hub tile.

   The AVEVA Data Hub portal opens.
   
## Get started goals

In these get started exercises, you will do the following:

1. Create a namespace that will contain all of your AVEVA Data Hub resources, including an instance of the Sequential Data Store and the data streams.

1. Create two connection types, one that brings in PI Data Archive data and another that brings in data using an OMF application.

1. Create a type that defines the data you want to store.

1. Create a stream container to store that data.

1. Create clients for different types of applications.

1. Invite a user to your tenant.

1. Create a role that defines permissions for users.

**Note:** Each exercise is built upon the previous one. It is important to complete the exercises in the order shown. At the end of each exercise, you will be directed to the next exercise.  

## Next step

Start with [Get started with namespaces](xref:gsNamespaces).
