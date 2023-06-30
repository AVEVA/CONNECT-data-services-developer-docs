---
uid: WhoUsesADH
---

# Platform uses

AVEVA Data Hub extends the data infrastructure seamlessly by integrating existing AVEVA products and third-party vendors from edge to cloud. This extensibility allows data to be shared across the entire infrastructure, reaching new people such as developers creating custom applications, data scientists engaged in data modeling, operations staff who monitor real-time performance, and data analysts using visualized data. 

Extending the collection and accessibility of operational data allows new analysis and decision-making processes to benefit your company. Some of the possible uses of this data include:

- [Remote operations monitoring](#remote-monitoring)

- Aggregating data from multiple PI systems and other sources for monthly or environmental reporting

- Providing real-time troubleshooting data for support personnel

- [Data science analysis](#data-science-analysis)

- [Sharing data with external partners](#sharing-data-with-business-partners)

- Providing data to third party applications like Power BI, Grafana, or custom applications

- Connect manufacturing data streams to an AI analysis application to facilitate process optimization

## Remote monitoring

AVEVA Data Hub provides the ability to integrate data infrastructure from edge to cloud seamlessly. Designed to serve as a "system of systems," AVEVA Data Hub supports data usage across the global enterprise. 

In the past, data was often isolated at remote locations due to unreliable network connectivity. For instance, farms need data to answer questions such as how much grain is in a silo or what is the predicted corn harvest this season. Mining companies require data from mining trucks to know when maintenance is necessary. This untapped data can provide valuable insights for an enterprise and its decision making. 

Accessing and integrating these "dark" data locations is possible with AVEVA Data Hub. With pervasive data collectors, AVEVA Adapters, Edge Data Store, and custom OMF applications, operational assets that were previously inaccessible are now viable data sources. 

The benefits of seamless integration of data infrastructure include: 

- Confidence that data across the entire spectrum is authoritative. 

- Data is compatible and native to the infrastructure across the spectrum. 

- Operational data can be accessed and used anywhere; it is no longer isolated in one facility or system. 

- New sources of operational data are available by storing the data in the cloud. 

- Existing edge and PI Server data is integrated into AVEVA Data Hub.

## Data science analysis

Data scientists can easily integrate operational data from multiple sources for a variety of applications, such as process optimization and maintenance. Better data modeling enables smart decision-making based on clear answers about what is most relevant to a company’s goals. AVEVA Data Hub uses the entire data infrastructure to gather the right type of data for modeling tools that answer business questions such as maintenance and demand forecasting. 

AVEVA Data Hub improves business insight by: 

- Allowing the operations department and data scientists to share data and collaborate more effectively.

- Providing an environment in which data analysis artifacts are saved, enabling the data scientist to modify their models and workflow more efficiently.

- Ensuring that high-quality data is available for analysis.

Some of the advantages of using AVEVA Data Hub for data science include:

**Data is easier to consume.** Curating and preparing data are the most time-consuming tasks when data scientists create their models. Bad data and data gaps decrease the integrity of results. In contrast, data that is contextualized, structured, filtered for relevancy, and presented in a format that is compatible for modeling tools and applications increases the efficiency of data scientists and the accuracy of their results. 

**More data is available.** AVEVA Data Hub removes the challenges of complicated and overbuilt data solutions, such as data lakes and relational databases, and provides a direct option for extending the data infrastructure. Because of the flexibility of the AVEVA Data Hub REST API, data can be consumed by many software applications that data scientists use to perform their analysis. 

**Data is prepared for efficient consumption.** Use data views to organize and configure AVEVA Data Hub data to be compatible with specific tools or applications. Add context to data through data views for easy identification and classification. Organize operational data in tabular form so it can easily be consumed by external tools via the REST API. Use data views to configure data sets for algorithms and modeling tools. 

**Data modeling is flexible.** Data scientists need to experiment with and update their models. The REST API gives data scientists freedom to work with many different contemporary data modeling tools and applications. The REST API also provides flexibility as data science technology evolves. 

**Data is contextualized.** Data science models are only as good as the data used in those models. Identifying the data that is relevant is as important as the model used. AVEVA Data Hub uses metadata rules to provide the context that makes it easy to search for data. AVEVA Data Hub metadata rules parse and store data that match specific patterns. Additionally, AVEVA Data Hub parses for user-provided context to identify patterns. When it finds a pattern, it attaches metadata.

**APIs integrate operational data with applications.** AVEVA Data Hub supports easy integration with custom applications, extending the enterprise data infrastructure to in-house and partner applications. AVEVA Data Hub offers ease of integration with a modern, secure REST API that is compatible with R and Python applications. Application developers use the REST API to interact with operational data on AVEVA Data Hub. 

## Sharing data with business partners

With the Communities feature, industrial companies can share their data streams with external business partners, service providers, and analytics providers. This is done in real-time, on a secure cloud platform. Only the information you specify is shared and no external users log directly into your tenant.

Analysis of aggregated data can bring multiple participants of the supply chain together to drive value, improve efficiency, and support compliance requirements.

To learn more about this feature, see [Communities](xref:communities).
