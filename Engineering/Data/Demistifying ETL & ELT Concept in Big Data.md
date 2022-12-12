---
tags: engineering/data, ETL, ELT
author: Hao Ngo
date: 2022-12-12
---

A common problem that organizations face is how to gather data from multiple sources, in multiple formats. Then you'd need to move it to one or more data stores. The destination might not be the same type of data store as the source. Often the format is different, or the data needs to be shaped or cleaned before loading it into its final destination.

The following sections highlight the common methods used to perform these tasks:

## The ETL Process
ETL (or Extract, Transform, Load) is the process of gathering data to a central data warehouse for analytics. 
-   **Extract**: Your traditional ETL process first extracts the data. In this step the data validity should be checked, any invalid data can be returned or corrected. 
-   **Transform**: Next any necessary transformations are performed. Transformations are a series of rules or functions as required by business and technical requirements. They can be anything from ensuring the correct format of the data to combining it with other data sources.
-   **Load**: Lastly, the data will be loaded into the end target system. This can be anything from a simple flat file to a cloud-based data warehouse.

![](_assets/etl_process.png)


## The ELT Process
So that’s the ETL process, but what about the ELT process? Well, remember: it’s all about when you transform. 
Depending on the transformations necessary and the type endpoint you chose, you may want to transform the data _after_ loading it. This is referred to as an ELT process (or Extract, Load, Transform). This is useful when loading to an end target that provides enough processing power to perform any transformations required.

![](_assets/elt_process.png)


## The difference between ETL and ELT
With ETL, the raw data is not available in the data warehouse because it is transformed before it is loaded. With ELT, the raw data is loaded into the data warehouse (or [data lake](https://www.techtarget.com/searchaws/definition/data-lake)) and transformations occur on the stored data.

Staging areas are used for both ELT and ETL, but with ETL the staging areas are built into the ETL tool being used. With ELT, the staging area is in a database used for the data warehouse.

![](_assets/differences_of_ETL_ELT.png)


## When to choose ETL vs ELT
It’s all about when and how you transform. If your transformations are simple and/or your endpoint does not support complex transformations, then you should definitely choose an ETL process and perform the transformations prior to loading. However, if your transformations are complex and subject to frequent changes and your endpoint supports the processing power, then an ELT process gives you the flexibility to run any transformations after loading the data.


## References

- https://learn.microsoft.com/en-us/azure/architecture/data-guide/relational-data/etl
- https://www.startdataengineering.com/post/what-and-why-staging/
- https://www.techtarget.com/searchaws/definition/data-lake
