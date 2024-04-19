

## Introduction of Datawarehouse and Snowflake(4 Hours)
- **What is Datawarehouse?**
	- Before that, what is DB?
	- A Data warehouse, also known as an Enterprise data warehouse (EDW), is a system used for reporting and analyzing data.
	- A Data Warehouse (DW) is a relational database that is designed for query and analysis rather than transaction processing. It includes historical data derived from transaction data from single and multiple sources.
	- Single Version of Truth(Centralized Repository)
	- A Data Warehouse provides integrated, enterprise-wide, historical data and focuses on providing support for decision-makers for data modeling and analysis.
    - A Data Warehouse provides integrated, enterprise-wide, historical data and focuses on providing support for decision-makers for data modeling and analysis.
- **Limitations of Traditional Data warehouses**
	- Running on on-premise platform(Hardware Maintenance, license cost, support cost, Capex, Limited Scalability and Flexibility)
- **Advantages of Cloud over On-Prem**
	-  Economy of scale, pay as you use, Zero Hardware maintenance, No Capex only Opsex, Highly scalable and flexible
- **What is Snowflake?**
	- Data warehouse runs on a Cloud Platform
	- SaaS Product
	- Cloud Agnostic solution
	- It cannot be run on a private cloud, or on hosted infrastructures.
	- It is primarily available on AWS, Azure and GCP cloud platform.  
	- Snowflake is not a relational database. So, it doesn't enforce primary key and foreign key constraints.
	- However, it offers Snowflake SQL commands like DDL, DML, and SQL functions. It also allows you to create UDFs and Stored Procedures using JavaScript/Python. Also it Supports all forms of ANSI SQLs including Analytical aggregations, Views and Materialized Views
	- Snowflake is a true self-managed service, meaning:
		- There is no hardware (virtual or physical) to select, install, configure, or manage.
		- There is virtually no software to install, configure, or manage.
		- Ongoing maintenance, management, upgrades, and tuning are handled by Snowflake.
-  **Snowflake Architecture**
    - Snowflake’s architecture is a hybrid of traditional shared-disk and shared-nothing database architectures. 
    - Similar to shared-disk architectures, Snowflake uses a central data repository for persisted data that is accessible from all compute nodes in the platform. 
    - But similar to shared-nothing architectures, Snowflake processes queries using MPP (massively parallel processing) compute clusters where each node in the cluster stores a portion of the entire data set locally. 
    - Overall, approach offers the data management simplicity of a shared-disk architecture, but with the performance and scale-out benefits of a shared-nothing architecture.
	![Architecture overview](https://docs.snowflake.com/en/_images/architecture-overview.png)

Snowflake’s unique architecture consists of three key layers:

- Database Storage
- Query Processing
- Cloud Services
    

### Database Storage

- When data is loaded into Snowflake, Snowflake reorganizes that data into its internal optimized, compressed, columnar format. Snowflake stores this optimized data in cloud storage.
- Snowflake manages all aspects of how this data is stored — the organization, file size, structure, compression, metadata, statistics, and other aspects of data storage are handled by Snowflake.
- The data objects stored by Snowflake are not directly visible nor accessible by customers; 
- They are only accessible through SQL query operations run using Snowflake.

### Query Processing

- Query execution is performed in the processing layer. 
- Snowflake processes queries using “virtual warehouses”. 
- Each virtual warehouse is an MPP compute cluster composed of multiple compute nodes allocated by Snowflake from a cloud provider.
- Each virtual warehouse is an independent compute cluster that does not share compute resources with other virtual warehouses. As a result, each virtual warehouse has no impact on the performance of other virtual warehouses.


### Cloud Services

- The cloud services layer is a collection of services that coordinate activities across Snowflake. 
- These services tie together all of the different components of Snowflake in order to process user requests, from login to query dispatch.
- The cloud services layer also runs on compute instances provisioned by Snowflake from the cloud provider.
- Services managed in this layer include:
	- Authentication
	- Infrastructure management
	- Metadata management
	- Query parsing and optimization
	- Access control
##### **Create Snowflake trial account**
Factors contributing to the creation of Snowflake account:
1. Snowflake edition
2. Cloud Provider
3. Geographical Location
- **Explore - Databases, Schemas and Table**

