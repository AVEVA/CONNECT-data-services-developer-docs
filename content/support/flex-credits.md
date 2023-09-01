---
uid: flex-credits
---

# How AVEVA Data Hub charges flex credits

This document outlines the key concepts and processes behind flex credits and their use within AVEVA Data Hub.

## Flex credit transactions

Flex credits are units of virtual currency that represent usage within AVEVA Data Hub (or other AVEVA Connect applications). You can commit to an amount of flex credits for cloud offerings and spend them how you like across a portfolio of cloud offerings, allowing you the flexibility to adjust mid-contract how your spend those flex credits based on how your usage evolves.

For AVEVA Data Hub, flex credits are debited from your account based on the volume of data streams stored and accessed in your tenant.

Each interaction with data streams results in a flex credit transaction. There are three main types of flex credit transactions for AVEVA Data Hub: streams stored, streams accessed, and shared streams accessed (details below).

Each tenant is billed a fixed monthly price for a base plan that provides daily base thresholds for each transaction type. For example, a starter plan allocates the following thresholds:

| Transaction type        | Daily thresholds |
|-------------------------|------------------|
| streams stored          | 500              |
| streams accessed        | 200              |
| shared streams accessed | 400              |

Under this plan, users in your tenant can store or access streams up to the daily threshold at no additional cost. However, if your tenant exceeds the threshold, additional flex credit transactions are incurred. For more information on when these additional costs are incurred, see [Overage charges](#overage-charges).

Flex credit transactions are executed daily at 12:00 AM. AVEVA Data Hub records stream usage throughout the day, presenting a final summary to Connect after the day's conclusion. When that summary is sent, the credit deduction occurs. Transactions covered under your base plan show up in Connect as transactions that do not debit your flex credits. For overage charges, Connect displays the number of flex credits debited to cover the overage.

### Streams stored

_Streams stored_ flex credit transactions occur when data streams are stored within AVEVA Data Hub. Every namespace that a tenant has is associated with streams stored transactions. For instance, if you store a stream in a tenant that has two namespaces, you incur two streams stored transactions.

### Streams accessed

_Streams accessed_ flex credit transactions occur when data streams are accessed by users. You are charged based on unique data streams accessed. No matter the user, AVEVA Data Hub does not count the access more than once for the same stream within a day. For example, if two separate users access the same stream, only a single flex credit transaction occurs.

Similar to streams stored, these transactions are tied to namespaces. Accessing streams from multiple namespaces generates corresponding streams accessed transactions.

### Shared streams accessed

_Shared streams accessed_ flex credit transactions occur when you access a data stream that is shared into a community by another tenant. Like streams accessed, you are charged based on unique data streams accessed and will not be charged multiple times for accessing the same stream.

Shared stream accessed flex credit transactions only occur when you _access_ shared streams. You are not debited for share streams into a community.

## Overage charges

Charges for stored or accessed streams involve fixed and variable components, striking a balance between usage and cost. There is a fixed monthly charge for your base plan that lets you store or access streams at your threshold at no additional cost. Within a given day, if you exceed a threshold in your base plan, then additional variable, per-stream charges are applied for each stream. After 12:00 AM, the counter on each usage metric is reset so that you are no longer charged overages.

Take for example, the starter plan previously mentioned in [Flex credit transaction](#flex-credit-transactions). If the tenant exceeds their daily threshold for _streams accessed_ of 200, each additional stream accessed incurs additional flex credit debits. The same principle applies to streams stored and shared streams accessed transactions.

## Evolution of rate plans

While the structure of rate plans remains consistent, the pricing and features they include may evolve over time. The rate plans aim to accommodate varying customer needs and usage patterns.

## Flex credit customer support

In cases of confusion or inquiries about flex credits, customers can seek clarification from the [AVEVA support team](https://softwaresupport.aveva.com/).

## Additional flex credit documentation

For more information about flex credits, such as information about credit agreements or rate plans, see the [AVEVA Connect documentation](https://docs.aveva.com/bundle/aveva-connect/page/885356.html).
