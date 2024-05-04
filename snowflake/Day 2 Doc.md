#### Decoupling Storage and Compute
## Connecting to Snowflake
Snowflake supports multiple ways of connecting to the service:

- A web-based user interface from which all aspects of managing and using Snowflake can be accessed.
- Command line clients (e.g. SnowSQL) which can also access all aspects of managing and using Snowflake.
- ODBC and JDBC drivers that can be used by other applications (e.g. DBeaver) to connect to Snowflake.
- Native connectors (e.g. Python, Spark) that can be used to develop applications for connecting to Snowflake.
- Third-party connectors that can be used to connect applications such as ETL tools (e.g. Informatica) and BI tools (e.g. ThoughtSpot) to Snowflake.
##### **Create Snowflake trial account**
Factors contributing to the creation of Snowflake account:
1. Snowflake edition
    The Snowflake Edition that your organization chooses determines the unit costs for the credits and the data storage you use.
	- **Standard** - Standard Edition is our introductory level offering, providing full, unlimited access to all of Snowflake’s standard features. It provides a strong balance between features, level of support, and cost.
	- **Enterprise** - Enterprise Edition provides all the features and services of [Standard Edition](https://docs.snowflake.com/en/user-guide/intro-editions#label-snowflake-editions-standard), with additional features designed specifically for the needs of large-scale enterprises and organizations.
	- **Business Critical** - Business Critical Edition, formerly known as Enterprise for Sensitive Data (ESD), offers even higher levels of data protection to support the needs of organizations with extremely sensitive data, particularly PHI data. It includes all the features and services of [Enterprise Edition](https://docs.snowflake.com/en/user-guide/intro-editions#label-snowflake-editions-enterprise), with the addition of enhanced security and data protection
2. Cloud Provider
	- AWS, Azure and GCP
3. Geographical Location
	- Data centers in different Location (|US East (N. Virginia),Canada (Central),Asia Pacific (Mumbai))
- **Explore - Databases, Schemas and Table**
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
	- Elastic Data Warehouse
	-Use case: Handling Multiple queries

Snowflake Credit Calculation :
- Size of the Warehouse
- How long the Warehouse runs(Response Time)

## Snowflake Supporting file formats
- Structured: CSV/TSV
- Semi-Structured: JSON, XML,ORC,PARQUET,AVRO 
-Apache Iceberg

### Caching in Snowflake
- Metadata Cache
- Result Cache
- Warehouse Cache
```sql

```


