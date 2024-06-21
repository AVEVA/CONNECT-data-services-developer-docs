---
uid: sds-dev-lp
---

# Sequential Data Store

The Sequential Data Store (SDS) is a streaming database optimized for storing sequential data, typically time-series data. It can store any data that is indexed by an ordered sequence. For each namespace that is created, an SDS instance or SDS resource is created. The services and storage are scoped to a particular region. Data is written into SDS using REST APIs. Use SDS to store, retrieve, and analyze data.

[Types](xref:sdsTypes) define the shape of a single measured event or object. A type gives structure to your data. For example, if you are measuring three things (longitude, latitude, speed) from a device at the same time, then you want those three properties to be included in your type.

[Streams](xref:sdsStreams) are a collection of ordered events, or a series of events, where each event is an instance of the type you have defined. You create and write data to streams using a simple REST API. The streams you create can be used to store simple or complex data types to suit your application needs.

You can define simple or complex [indexes](xref:sdsIndexes) to arrange and relate your data. An assortment of methods with customizable behaviors are available to read data and obtain needed information.

## Samples

The best way to get started with SDS is to run one or more of the code samples. Code samples available in different programming languages provide examples of how to interact with SDS. The code samples are available on GitHub in the [Sample library](https://github.com/osisoft/OSI-Samples). Obtain SDS REST API access keys from the [AVEVA Data Hub portal](https://datahub.connect.aveva.com) before running the sample code.

Each sample includes a README file that describes the steps required to run the sample and a brief description of the sample's functionality. Read the README file to understand how the sample works.

After you finish the introduction and work with one of the samples, refer to the [Quick start](xref:sdsQuickStart) section, which describes interacting with various SDS objects and helps you get started with your own application.
