---
uid: omfVsSds
---

# Data collection - OMF vs. SDS data writes

When it comes to collecting data programatically, developers have the option of using either the Open Message Format ([OMF](https://docs.osisoft.com/bundle/omf/page/index.html)) or Sequential Data Store ([SDS](https://osisoft-prod.zoominsoftware.io/bundle/ocs/page/developer-guide/sequential-data-store-dev/sds-write-data.html)) data writes. Each option has its pros and cons, and the purpose of this guide is to highlight the key differences. In general, it is recommended that developers utilize OMF if possible, for the reasons that will be discussed in the following sections.

## Future support
The APIs used in SDS could potentially be updated in future, requiring upkeep of your applications. OMF on the other hand, can continue to be used as it is up to the platform to interpret the messages and store the contained data appropriately.

## Cross-platform
While SDS data writes can only be used for ADH and EDS, OMF can be also be used to write to a PI Core Server through the PI Web API. This makes OMF cross-platform, which is one of the main reasons that it is used in AVEVA’s Adapter technology. In addition, other platforms could potentially adopt the OMF standard to ingress data, widening the interoperability of your applications.

## Bidirectionality
If a requirement of your application is both reading and writing from ADH, then SDS data writes are preferable to avoid the need for interacting with two separate APIs. Using the SDS API allows for reuse of objects such as types and streams in your application.

## Security
Since OMF is unidirectional, it is inherently more secure than direct SDS data writes.

## Performance

Since there is overhead associated with parsing the OMF json payloads, direct SDS calls may be more performant. This will of course also depend on how many REST calls are being made to SDS and how data is batched. Therefore, in cases where performance is critical, direct SDS calls may be necessary. This is often not the case, however.
