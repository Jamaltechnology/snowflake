### Interview Based Topics (Snowflake)

- **What is Snowflake?**
	- Data warehouse runs on a Cloud Platform
	- SaaS Product
	- Cloud Agnostic solution - AWS, Azure, GCP(Cloud native: Redshift with AWS and  Bigquery with GCP) 
	- It cannot be run on a private cloud, or on hosted infrastructures(on-prem).
	- It is primarily available on AWS, Azure and GCP cloud platform.  
	- Snowflake is not a relational database. So, it doesn't enforce primary key and foreign key constraints.
	- However, it offers Snowflake SQL commands like DDL(Create,drop), DML(Ins.Upd,del), and SQL functions. It also allows you to create UDFs and Stored Procedures using JavaScript/Python. Also it Supports all forms of ANSI SQLs including Analytical aggregations, Views and Materialized Views
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
	Snowflake’s unique architecture consists of three key layers
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

## Factors to Create Snowflake Account
##### Snowflake edition
The Snowflake Edition that your organization chooses determines the unit costs for the credits and the data storage you use.
	 **Standard** - Standard Edition is our introductory level offering, providing full, unlimited access to all of Snowflake’s standard features. It provides a strong balance between features, level of support, and cost.
	- **Enterprise** - Enterprise Edition provides all the features and services of [Standard Edition](https://docs.snowflake.com/en/user-guide/intro-editions#label-snowflake-editions-standard), with additional features designed specifically for the needs of large-scale enterprises and organizations.
	- **Business Critical** - Business Critical Edition, formerly known as Enterprise for Sensitive Data (ESD), offers even higher levels of data protection to support the needs of organizations with extremely sensitive data, particularly PHI data. It includes all the features and services of [Enterprise Edition](https://docs.snowflake.com/en/user-guide/intro-editions#label-snowflake-editions-enterprise), with the addition of enhanced security and data protection
##### Cloud Provider
- AWS, Azure and GCP
##### Geographical Location
- Data centers in different Location (|US East (N. Virginia),Canada (Central),Asia Pacific (Mumbai))
## Scaling in Snowflake
**Warehouse Size**
- XSMALL  - 1 node
- SMALL    - 2 node
- MEDIUM  - 4 node
- LARGE     - 8 node
- XLARGE  - 16 node
- ### Horizontal 
	- Scale up(Increasing the size of the Warehouse)
	- Scale Down(Decreasing the size of the warehouse)
	-Use Case: Long/Short running Query
- ### Vertical
	- Scale-in (increase the number of Warehouse)
	- Scale-out (Decrease the number of warehouse)
	- Elastic Data Warehouse - min 1 max 10
	-Use case: Handling Multiple queries

Snowflake Credit Calculation :
- Size of the Warehouse
- How long the Warehouse runs(Response Time)

## Snowflake Supporting file formats
- Structured: CSV/TSV
- Semi-Structured: JSON, XML,ORC,PARQUET,AVRO 

### Caching in Snowflake
- **Metadata Cache** - Snowflake stores certain information about each table like row count, min/max values of a column in its metadata in the cloud services layer so that certain queries about the table can be easily answered without reading the table data.
- **Result Cache**
	- When a query is executed in Snowflake, the query results are stored for a defined period of time(24 hrs) The results are purged from the system at the end of time period. The persisted query results are referred to as Query Result Cache.
	- The Query Result cache helps avoiding re-executing the queries when a same query is submitted by user which was previously executed and there is no change in the underlying table data.
- **Warehouse Cache (or) Local Disk Cache** 
	- Every time a virtual warehouse extracts data from a table, it caches that data locally. The subsequent queries can reuse the data in the cache rather than reading from the table in the cloud storage. 
	- This cache which gets stored at the local disk is referred to as Virtual Warehouse Cache or Local Disk Cache in Snowflake.
	- Reading data from a local cache is a much more efficient operation than reading data from the remote cloud storage. Therefore the warehouse cache improves performance of queries which can take advantage of it.
	- **The Virtual Warehouse Cache is removed if the virtual warehouse is suspended.**

![Snowflake's Architecture showing cache location in different layers](https://thinketl.com/wp-content/uploads/2023/06/Cache-representation-in-Snowflake-Architecture.png)

Snowflake’s Architecture showing cache location in different layers

- Since Metadata cache and the Query Result cache are part of the Cloud Services Layer, they can run without the need of an active virtual warehouse.
- The **Virtual Warehouse** cache is part of the Query Processing Layer and hence it is local to each virtual warehouse.
For more details, kindly refer https://thinketl.com/caching-in-snowflake/

## Snowflake Cortex:
Intelligent, fully managed service that offers machine learning and AI solutions to Snowflake users. Snowflake Cortex capabilities include:
- Snowflake Copilot 
- Universal Search 

### Time Travel and Fail-safe:
Snowflake provides powerful Backup features for ensuring the maintenance and availability of your historical data (i.e. data that has been changed or deleted accidentially):

 - Querying, cloning, and restoring historical data in tables, schemas, and databases for up to 90 days through Snowflake Time Travel.
 - Disaster recovery of historical data (by Snowflake) through Snowflake **Fail-safe.**(7 Days)

These features are included standard for all accounts, i.e. no additional licensing is required; however, standard Time Travel is 1 day. Extended Time Travel (up to 90 days) requires Snowflake Enterprise Edition. In addition, both Time Travel and Fail-safe require additional data storage, which has associated fees.

SQL: 
The query selects historical data from a table as of the date and time represented by the specified [timestamp](https://docs.snowflake.com/en/sql-reference/data-types-datetime):
**SELECT * FROM my_table AT(TIMESTAMP => 'Fri, 01 May 2015 16:20:00 -0700'::timestamp_tz);**
    





