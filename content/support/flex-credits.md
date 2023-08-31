---
uid: flex-credits
---

# How AVEVA Data Hub charges flex credits

This document outlines the key concepts and processes behind flex credits and their application within AVEVA Data Hub.

## Flex credit transactions

Flex credits are units of virtual currency that represent usage within AVEVA Data Hub (or other applications available on AVEVA Connect). You can commit to an amount of flex credits for cloud offerings and spend them how you like across a portfolio of cloud offerings, allowing you the flexibility to adjust mid-contract how your spend those flex credits based on how your usage evolves.

For AVEVA Data Hub, these credits are consumed based on the volume of data streams stored and accessed by a customer. Each interaction with data streams results in a flex credit transaction. There are two main types of flex credit transactions: _streams stored_ and _streams accessed_.

Flex credit transactions occur at the end of each day. AVEVA Data Hub records usage of streams throughout the day and reports the final summary to Connect after the day completes. When that report is sent, the credit deduction occurs.

### Streams stored

Streams stored flex credit transactions occur when data streams are stored within AVEVA Data Hub. Every namespace that a tenant has is associated with streams stored transactions. For instance, if a customer has two namespaces, they could have up to two streams stored transactions.

### Streams accessed

Streams accessed flex credit transactions occur when data streams are accessed by users. You are charged based on unique data streams accessed. No matter the application/user, AVEVA Data Hub does not count the access more than once for the same stream within a day. Similar to streams stored, these transactions are tied to namespaces and communities. Accessing streams from multiple namespaces or communities generates corresponding streams accessed transactions.

## Overage charges

The charging process with flex credits provides a balance between usage and cost. You are charged only when you exceed the usage thresholds outlined in your rate plan. For example, the following table describes a rate plan that includes **500 streams** accessed as part of your base capacity:

| Tenant Namespaces | Streams Accessed | Streams Charged |
|--|--|--|
| Namespace 1 | 550 | 50 |
| Namespace 2 | 99 | 99 |

- When 550 streams accessed are posted, only 50 streams are counted for charging. This excess usage is multiplied by the flex credit per stream stored rate specified in your rate plan.

- If another 99 streams accessed are used in a different namespace, and the customer has already consumed their 500 streams accessed capacity, the entire 99 streams accessed is considered for charging based on the rate plan.

The same principle applies to streams stored and shared streams accessed transactions.

## Evolution of rate plans

While the structure of rate plans remains consistent, the pricing and features they include may evolve over time. The rate plans aim to accommodate varying customer needs and usage patterns.

## Flex credit customer support

In cases of confusion or inquiries about flex credits, customers can seek clarification from the [AVEVA support team](https://softwaresupport.aveva.com/).

## Additional flex credit documentation

For more information about flex credits, such as information about credit agreements or rate plans, see the [AVEVA Connect documentation](https://docs.aveva.com/bundle/aveva-connect/page/885356.html).
