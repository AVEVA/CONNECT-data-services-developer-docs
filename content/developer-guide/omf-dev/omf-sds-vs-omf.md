---
uid: omfVsSds
---

# Data collection - OMF vs. SDS data writes
When it comes to collecting data programatically, developers have the option of using either the Open Message Format ([OMF](https://docs.osisoft.com/bundle/omf/page/index.html)) or Sequential Data Store ([SDS](https://osisoft-prod.zoominsoftware.io/bundle/ocs/page/developer-guide/sequential-data-store-dev/sds-write-data.html)) data writes. Each option has its pros and cons, and the purpose of this guide is to highlight the key differences. Which option you should choose is situation dependent, but omf is typically the best option for simple and efficient data collection.    

**OMF pros:**
- [Future support](#future-support)
- [Cross-platform](#cross-platform)

**SDS data write pros:**
- [Flexibility](#flexibility)

**Situation dependent factors:**
- [Security](#security)
- [Performance](#performance)

## Future support
The APIs used in SDS could potentially be updated in the future, requiring upkeep of your applications. OMF on the other hand, can continue to be used as it is up to the platform to interpret the messages and store the contained data appropriately.  

**Winner:** OMF 

## Cross-platform
While SDS data writes can only be used for ADH and EDS, OMF can be also be used to write to a PI Core Server through the PI Web API. This makes OMF cross-platform, which is one of the main reasons that it is used in AVEVA’s Adapter technology. In addition, other platforms could potentially adopt the OMF standard to ingress data, widening the interoperability of your applications.  

**Winner:** OMF

## Flexibility
SDS data writes afford greater flexibility than OMF, which may make it the clear winner for certain use cases.  
If a requirement of your application is both reading and writing from ADH, then SDS data writes are preferable to avoid the need for interacting with two separate APIs. Using the SDS API allows for reuse of objects such as types and streams in your application.  

In some situations, the functionality that you need may not be currently supported in the OMF specification. Certain property overrides and nested types are two instances where this would be true. Platform specific features like dataviews or assets are also not accessible through OMF. Direct calls to the ADH REST API would be preferred for these situations.  

Additionally, not all OMF end points will respond with the same error codes due to asynchronous message processing, which could result in a successful http status code being returned when a SDS data write would result in a client error status code. This could happen if a message adheres to the OMF specification, but is not writing to a valid container.  

**Winner:** SDS data writes

## Security
Both SDS and OMF utilize the same authentication mechanism when connecting to ADH, so neither is inherently more secure. It is always important to follow best practices for security as outlined in the [Identity and access management](https://docs.osisoft.com/bundle/data-hub/page/developer-guide/identity-dev/dev-guide-identity-access-management.html) section of the Developer guide.  

When connecting the PI Web API, OMF connections can only use basic authentication, while other options such as Kerberos are available for all other parts of the PI Web API.  

**Winner:** Situation dependent

## Performance
Since there is overhead associated with parsing the OMF json payloads, direct SDS calls may be more performant in theory. That said, with OMF you can send data for multiple containers (equivalent to an ADH stream or PI System tag) in a single payload. This reduces the number of requests needed and makes batching data easier. With SDS data writes, parallel tasks are needed to realize the full potential of ADH.  

Another consideration for performance is compression of message payloads, which both options support through gzip when specified headers are provided.  

**Winner:** Situation dependent
