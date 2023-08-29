---
uid: flex-credits
---

# Flex credits: How they work

Flex credits are the currency used for transactions in AVEVA Data Hub, designed to provide customers with flexible pricing based on their usage. This document outlines the key concepts and processes behind flex credits and their application within AVEVA Data Hub.

## Flex credit transactions

Flex credits are units of virtual currency that represent usage within AVEVA Data Hub (or other applications available on AVEVA Connect). For AVEVA Data Hub, these credits are consumed based on the volume of data streams stored and accessed by a customer. Each interaction with data streams results in a flex credit transaction. There are two main types of flex credit transactions: _streams stored_ and _streams accessed_.

### Streams stored

_Streams stored_ flex credit transactions occur when data streams are stored within AVEVA Data Hub. Every namespace that a tenant has is associated with streams stored transactions. For instance, if a customer has two namespaces, they could have up to two streams stored transactions.

### Streams accessed

_Streams accessed_ flex credit transactions occur when data streams are accessed by users. Similar to streams stored, these transactions are tied to namespaces and communities. Accessing streams from multiple namespaces or communities generates corresponding streams accessed transactions.

## Charges

The charging process with flex credits provides a balance between usage and cost. You are charged only when you exceed the usage thresholds outlined in your rate plan. For example, if you have a rate plan that includes 500 streams stored as part of your base capacity:

- When 550 streams stored are posted, only 50 streams are counted for charging. This excess usage is multiplied by the flex credit per stream stored rate specified in your rate plan.

- If another 99 streams stored are used in a different namespace, and the customer has already consumed their 500 streams stored capacity, the entire 99 streams stored is considered for charging based on the rate plan.

The same principle applies to streams accessed and shared streams accessed transactions.

## Evolution of rate plans

While the structure of rate plans remains consistent, the pricing and features they include may evolve over time. The rate plans aim to accommodate varying customer needs and usage patterns.

## Flex credit customer support

In cases of confusion or inquiries about flex credits, customers can seek clarification from the [AVEVA support team](https://softwaresupport.aveva.com/).
