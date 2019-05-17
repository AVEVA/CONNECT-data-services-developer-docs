---
uid: omfIngressToOCS
---

Data ingress to Cloud Services using OMF
========================================

You can use OSIsoft Message Format (OMF) to achieve high-throughput asynchronous data ingress 
into the OCS data store. The following terms might be useful for understanding the information
in this and subsequent topics:

* A producer of OMF messages needs a *Client* identity to authenticate and send messages.
* Messages are sent to a queue called a *Topic*. 
* A *Subscription* receives messages from a Topic and writes them to the OCS 
  data store.
