---
uid: SecurityReliability
---

# Security and reliability

AVEVA manages, operates, and maintains all aspects of the AVEVA Data Hub platform. AVEVA Data Hub is built and deployed on Microsoft Azure and operates outside the AVEVA corporate firewall. Currently, AVEVA Data Hub runs in three Azure regions: West US, West Europe, and Australia. By housing the platform in multiple regions, AVEVA Data Hub accommodates regulations that mandate where data must be stored.

## Secure and robust data infrastructure
AVEVA Data Hub is built from the ground up to ensure security. The AVEVA Data Hub platform is based on industry standard techniques to ensure the strongest possible data integrity. User authentication is handled through AVEVA Connect. Authenticated users can only perform actions for which their role is authorized. Machine access to AVEVA Data Hub is controlled through a variety of defensive strategies. All data in AVEVA Data Hub is fully encrypted in transit and at rest.

## Elastic resource allocation
Due to its microservice-based architecture, AVEVA Data Hub dynamically adapts to workload changes by automatically provisioning and de-provisioning resources. Each microservice performs a subset of the system’s overall capabilities, and when orchestrated together, they function as a complete platform. 

When AVEVA Data Hub is turned on in a folder for a tenant in AVEVA Connect, a new set of microservices and all the necessary data storage is provisioned for that folder/namespace. As the tenant’s needs for the namespace grow, AVEVA Data Hub automatically provisions additional microservices and storage so the namespace can expand horizontally. Similarly, if requirements shrink, AVEVA Data Hub can reduce the number of required microservices and de-allocate storage. 

## Interruption resilience
To prevent data interruptions or loss, AVEVA Data Hub incorporates many safeguards and is designed for high availability. You are not required to perform any specific actions to ensure continuous access to reliable, distributed data storage.

AVEVA Data Hub is continuously tested to ensure the platform is performing reliably. Both the platform and the underlying operating systems are updated regularly. In addition, frequent threat analyses are conducted to thwart potential exploitations. Load balancing precludes distributed denial of service attacks. A gateway prevents unauthorized access to resources.

## Service description
For more information on operational topics relating to AVEVA Data Hub, such as data ownership, data privacy, database backup and redundancy, see the [AVEVA Data Hub Service Description](https://www.aveva.com/en/legal/service-description/).
