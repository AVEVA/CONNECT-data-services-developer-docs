---
uid: flex-credits
---

# How AVEVA Data Hub charges flex credits

This document outlines the key concepts and processes behind flex credits and their use within AVEVA Data Hub.

## Flex credit transactions

Flex credits are units of virtual currency used to pay for consumption within AVEVA Data Hub (or other AVEVA Connect applications). You can commit to an amount of flex credits for cloud offerings and spend them how you like across a portfolio of cloud offerings, allowing you the flexibility to adjust mid-contract how you spend those flex credits based on how your usage evolves.

For AVEVA Data Hub, flex credits are debited from your account based on the daily volume of data streams stored and accessed in your tenant.

There are three main types of flex credit transactions for AVEVA Data Hub: _streams stored_, _streams accessed_, and _shared streams accessed_ (details below). For each AVEVA Data Hub namespace, there is a daily transaction each for streams stored and streams accessed; and for each AVEVA Data Hub community that an AVEVA Data Hub tenant is a part of, there is a daily transaction for shared streams accessed.

Each tenant is billed a fixed monthly price for a base plan that provides daily base thresholds for each transaction type. For example, a starter plan allocates the following thresholds:

| Transaction type        | Daily thresholds |
|-------------------------|------------------|
| streams stored          | 500              |
| streams accessed        | 200              |
| shared streams accessed | 400              |

Under this plan, users in your tenant can store or access streams up to the daily threshold at no additional cost. However, if your tenant exceeds the threshold, additional flex credit transactions are incurred. For more information on when these additional costs are incurred, see [Overage charges](#overage-charges).

Flex credit transactions are executed daily at 12:00 AM UTC. AVEVA Data Hub records stream usage throughout the day, presenting a final summary to Connect after the day's conclusion. When that summary is sent, the credit deduction occurs. Transactions covered under your base plan show up in Connect as transactions that do not debit your flex credits. For overage charges, Connect displays the number of flex credits debited to cover the overage.

### Streams stored

_Streams stored_ usage is recorded when data streams are stored within AVEVA Data Hub. Every namespace that a tenant has is associated with streams stored transactions. For instance, if you store a stream in a tenant that has two namespaces, you incur two streams stored transactions.

### Streams accessed

_Streams accessed_ usage is recorded when data streams are accessed by users and clients. You are charged based on unique data streams accessed. No matter the user, AVEVA Data Hub does not count the access more than once for the same stream within a day. For example, if two separate users access the same stream, only a single stream is recorded toward usage.

Similar to streams stored, these transactions are tied to namespaces. Accessing streams from multiple namespaces generates corresponding streams accessed transactions.

### Shared streams accessed

_Shared streams accessed_ flex usage is recorded when you access a data stream that is part of a community. This stream could be one that you shared, or one shared by another tenant. This could be a stream that you shared or a stream that another tenant has shared into a community. Like streams accessed, you are charged based on unique data streams accessed and are not charged multiple times for accessing the same stream. You are not debited for sharing streams into a community.

## Overage charges

Charges for stored or accessed streams involve fixed and variable components, striking a balance between cost predictability and usage flexibility. There is a fixed monthly charge for your base plan that lets you store or access streams at your threshold at no additional cost. Within a given day, if you exceed a threshold in your base plan, then additional variable, per-stream charges are applied for each stream. After 12:00 AM UTC, the counter on each usage metric is reset so that you are no longer charged overages.

Take for example, the starter plan previously mentioned in [Flex credit transaction](#flex-credit-transactions). If the tenant exceeds their daily threshold for _streams accessed_ of 200, each additional stream accessed incurs additional flex credit debits. The same principle applies to streams stored and shared streams accessed transactions.

## Evolution of rate plans

While the structure of rate plans remains consistent, the pricing and features they include may evolve over time. The rate plans aim to accommodate varying customer needs and usage patterns.

## Flex credit customer support

In cases of confusion or inquiries about flex credits, customers can seek clarification from the [AVEVA support team](https://softwaresupport.aveva.com/).

## Additional flex credit documentation

- For more information about flex credits, such as information about credit agreements or rate plans, see the [AVEVA Connect documentation](https://docs.aveva.com/bundle/aveva-connect/page/885356.html).

- For a description of each AVEVA cloud service available, see [AVEVA Service Descriptions for Cloud Services](https://www.aveva.com/en/legal/service-description/).
