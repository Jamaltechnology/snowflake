
## Output of this Overview:

1. What is Snowflake?
2. Why Snowflake?
3. Onboard/Offload Data into Snowflake
4. Snowflake Supporting File formats
5. Snowflake Functionalities
6. AL/ML into Snowflake
7. Ways to connect to Snowflake
	1. Web UI (Snowsight)
	2. ODBC/JDBC (DBeaver)
	3. Command Line Utility (SnowSQL)
	4. Python (Snowpark)


## What is Snowflake?
- Data warehouse runs on a Cloud Platform
- SaaS Product
- Cloud Agnostic vs Cloud Native
	- Snowflake
	- AWS Redshift
- It cannot be run on a private cloud, or on hosted infrastructures.
- It is primarily available on AWS, Azure and GCP cloud platform.  
- Snowflake is not a relational database. So, it doesn't enforce primary key and foreign key constraints.
- However, it offers Snowflake SQL commands like DDL, DML, and SQL functions. It also allows you to create UDFs and Stored Procedures using JavaScript/Python. Also it Supports all forms of ANSI SQLs including Analytical aggregations, Views and Materialised Views
- Webserver -> MySQL  (7 days)-> CDC-> Snowflake (10 years of history)  -> Tableau
- OLTP  vs OLAP 
	- Online Transaction Processing
	- Online Analytical Processing
- ETL vs ELT
	- Extract Transform Load
	- Extract Load Transform
- CapEX vs OpsEx
	- Capital expenditure (onpremise)
	- Operational expenditure
- Economy of scale
	- Server: AWS EC2
	- Data platform: Snowflake
	- pay as you go
- CPU <-> Disk storage
	- VW
- Alternatives of Snowflake
	- Teradata 
	- adding node 
## Why Snowflake?

Snowflake Architecture
    Separation of storage and compute recourses. In Snowflake, you will have a notion of two things.
		 1. Database
		 2. Virtual Warehouse
Data Sharing
Horizontal and Vertical Scaling
- Size
	- XSMALL  - 1 node
	- SMALL    - 2 node
	- MEDIUM  - 4 node
	- LARGE     - 8 node
	- XLARGE  - 16 node
- SQL1, cost credit
	- XSMALL - 10 min   ( size x time)
	- LARGE - 1 min        
Time-Travel & Failsafe
- undrop (90 days)
	- instantaneous
- Failsafe  (Snowflake support, 7 days)
- Apache Airtable ()
Micro-partitioning
Zero-copy Cloning
- Table A   --- Table B  (source data)
- Table A insert 200 records
	- source data + diff 200 records
- Table B 2000 delete 
	- source data + diff 2000 records

#### Onboard/Offload Data into Snowflake
Stages 
  Internal Stage: (Load data directly from Local Machine)
  External Stage: (Load data from Amazon S3, Azure Blob and GCP Bucket)
    Copy command

#### Snowflake Supporting File formats:
   Structured          : CSV
   Semi-Structured: JSON, AVRO, XML, ORC and Parquet

### Snowflake Functionalities
  Snowpipe
  Tasks and Stream
  
### AI/ML into Snowflake
Snowflake Cortex
	 Snowflake co-pilot
	 Document AI
	 Universal Search
Snowpark 

#### Ways to connect to Snowflake
1. Web UI (Snowsight)
	1. Workbook SQL
	2. Workbook Python
		1. Pandas
2. ODBC/JDBC (DBeaver)
3. Command Line Utility (SnowSQL)
4. Python (Snowpark)
5. Dashboards (streamlit)
	1. Python Streamlit

# Questions?





 
  












