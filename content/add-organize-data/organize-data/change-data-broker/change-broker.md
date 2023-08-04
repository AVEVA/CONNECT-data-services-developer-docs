---
uid: ChangeBroker
---

# Change Broker (Preview)

Change Broker is an Enterprise-scale egress capability for AVEVA Data Hub. Update streaming is crucial to enterprise-scale analytics, data science, visualization, and integration. Operations data is always changing. The Change Broker helps you navigate live data, delayed uploads, late manual measurements, recalculations, and even rare occurrences of incorrect readings that require change data.

## Change Data

This feature solves both new and changing data issues, and can provide near real-time data. More specifically, Change Broker monitors changes to the streams’ property values. The change data supported by the Signup includes the following capabilities: Update, Insert, Replace, Remove, and RemoveWindow. These are all write modes supported by Sequential Data Store (SDS). This capability serves both customers and partners for analytics, visualization/dashboarding, rules processing, evolving search indexes, anomaly detection, application providers, transaction processing, and digital service providers.

Change Broker is designed to support the egress of millions of data events per second, retain the events for a period of time (1 hour), and serve that data to multiple, parallel consumers. A Signup is retained for 24 hours relative to the last query made. There is no known limitation on the size of data that can be held in a Signup during the one-hour expiration window.

**Note**: During Change Broker's initial Preview phase, the egress supports hundreds of thousands of data events per second. The number of data events will increase upon the full release of Change Broker.

## REST API

A REST consumer creates a “Signup” for change data from a defined list of Stream IDs in a namespace (for example, data from Stream1 through Stream10). Signups have a lifecycle which includes states such as Active (ready for use) and Inactive (abandoned). Consumers poll an active Signup to pull the change data via GET Updates, and with each response, receive a Bookmark for the next request. 

Reading is not destructive, as with a queue. Reading data from your Signup advances your bookmark, but does not immediately delete the data in the Signup. The data will expire based on the expiration assigned to it. For example, an hour expiration from the activation of a Signup or most recent query.

Bookmarks are unique to a Signup. You cannot use bookmarks for more than one Signup.

To receive change data from streams in different namespaces (for example, MyTenant/MyNamespace and CommunityFriend/TheirNamespace), a Signup is made for each namespace.

## Application for the Change Broker

Some practical uses for Change Broker include:

* Data Science
    * Improves accuracy of algorithms by providing recent data
    * Simplifies integration that sends recent data to an algorithm
    * Supports reference architectures
* Remote Operations Monitoring
    * Allows apps to retrieve near real-time data
    * Reduces components customers must manage
    * Standardizes how change data transfers to trusted business partners
* Maintenance & Risk Reduction
    * Near real-time data feeding alarm systems