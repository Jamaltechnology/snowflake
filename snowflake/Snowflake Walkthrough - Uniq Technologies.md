In today's video, I am going to talk about Snowflake Cloud Data Warehouse, and I will cover three items in this first video.

1. What is Snowflake, and what can you do with Snowflake?
2. How Snowflake architecture separates storage and compute and help you optimize your cost. You will learn the notion of Snowflake database and Snowflake Virtual Warehouse.
3. Finally, I will talk about the Snowflake Storage Architecture. How snowflake database tables are stored and accessed when you execute SQLs. And this item would be the most exciting part. So, make sure you watch it to the end. 

## What is Snowflake?

Snowflake is a Data Warehouse that runs entirely on cloud infrastructure, and it cannot be run on a private cloud, or on hosted infrastructures. It is primarily available on AWS and Azure cloud platform.  
Snowflake is not a relational database. So, it doesn't enforce primary key and foreign key constraints. But it offers Snowflake SQL commands like DDL, DML, and SQL functions. It also allows you to create UDFs and Stored Procedures using JavaScript. Interesting! Right?  
The Snowflake SQL is rich enough to meet most of the data warehousing requirements. It supports, select statements, joins, subqueries, insert, update, delete, merge statements, views, materialized views, and ACID transactions.  
It also supports common analytical aggregations such as the cube, rollup, grouping sets, windowing functions, connect-by, and recursive CTE.

## Snowflake Integration

Like any typical Data Warehouse, it allows connection from most of the popular data integration tools, self-service BI tools and visualization tools such as IBM Data Stage, Informatica, Talend, Pentaho, Power BI, Tableau, QlikView, Spot fire, Apache Kafka, Apache Spark, and Databricks.  
If this is not enough, you can use JDBC/ODBC drivers to connect from your application. You will be amazed to know that it also offers native connectors for languages like Python, Go Lang, and Node.js.  
For Adhoc querying, you can use a snowflake web interface which offers almost every feature that you would expect from a SQL worksheet or a database IDE. Alternatively, you can install Snowflake CLI on your local machine or connect using DBeaver.
  

Again Impressive! Right?  
But I am not yet. Because all this is anyway offered by almost every data warehouse system.

## What makes Snowflake different?

Well. It is the snowflake architecture.  
The snowflake system is designed in a way to scale and peations. So, you do not have multiple knobs to tune the database performance. It just works. At least, what the vendor claims. But you have few of knobs to tune your cost and optimize your pay per use bills.  
Sounds interesting. Yes, it is. Let's try to understand how this fantastic data warehouse system architecture is designed to achieve all that.
## Snowflake Architecture

The first great thing that the Snowflake does is a real separation of storage and compute recourses. In Snowflake, you will have a notion of two things.

1. Database
2. Virtual Warehouse

The database is the storage layer. It allows you to define a database, a bunch of schemas, and then add tables to the schema. Once you have tables, you can start loading data into those tables. This is the typical structure that we follow in any data warehouse. Right?  
But there is one thing which is unique in Snowflake. The data in the tables are stored in Amazon S3, and it consumes storage only cost. There is no compute cost attached to the database unless you are executing DDL or DML queries. What it means, you will pay for the compute cost while you are running DDL statements to create a database, a schema, table, or other structural objects.  
If all these activities take 30 minutes, you will pay for the 30 minutes of computing cost. Once your table structure is in place, you would want to load some data into your tables. If your data load job is running for an hour in a day, you pay for the compute cost for an hour. Rest of the time, you will be paying only for the storage cost. Similarly, if you are running Queries for three hours a day, you will be paying to compute-cost for those many hours. That's how it works at a high level.

![[Pasted image 20240416075630.png]]


Fig.4- Snowflake storage and compute

The next part of the Snowflake is the Virtual Warehouse, which is nothing but a compute cluster. They are named after Virtual Machines. But instead of machines, Snowflake termed them as Warehouse. In short, we call them VW instead of VM. You can create VW of various sizes depending upon your requirement. It could be a single node VW, or it could be a multi-node VW such as 2 nodes, 4 nodes, 8 nodes, 16 nodes, and so on. These nodes are nothing but Amazon EC2 instances, but they are internal to VW, and you don't directly interact with them. Right?  
Creating a VW does not have any cost associated with it. It is just a metadata creation. And you can have more than one VW configurations. For example, you might want to create a single node VW for executing DDLs or performing some other low resource consuming activities. At the same time, you can also define a 4 node VW which you want to use only for the data loading activity. And you can create one more a 32 node VW which you wish to apply for a high performing computation job that triggers every hour and completes in less than 5 minutes.

![[Pasted image 20240416075726.png]]


Fig.5- Snowflake Virtual Warehouse

The point is straightforward. You create your compute resource definition and start it only when you want to do some computation and shut it down when the computation activity is over. In this way, you pay the compute cost only when your VW is running. And the best part is, you also know, which job is costing you how much money? Right? A job that runs for 5 minutes on a 32 node VW, and triggers 24 times a day is charging you for 2 hours of a 32 node VW. Right? And that's valuable information for the business. Isn't it?  
You can also use the same VW to execute multiple concurrent queries. In that case, as the queries are submitted to a VW, the Warehouse allocates resources to each query and begins running them. If sufficient resources are not available to execute all the queries, additional queries will be queued until the necessary resources become available. So, you have all the flexibility to plan the compute workload and reuse your VWs.

## Snowflake Multi-cluster

The notion of VW doesn't stop there. Snowflake also offers a unique idea of multi-cluster VW for auto-scaling.  
For example, you created a multi-cluster VW and started a query on the VW. Snowflake would start your query normally in the same VW. However, if you start submitting more and more queries on the same VW, at some point, they will consume all the resources and additional queries will be queued until existing ones are complete.  
But you created a multi-cluster warehouse. A multi-cluster VW will detect this scenario and automatically launch a new VW to execute the queued SQLs. The point is straightforward. Snowflake allows you to configure automatic scale-up by starting additional VWs and scale-down by shutting down the VWs depending upon the workload. This feature is powerful if you have strict performance SLAs.  
Great! So, you can draw a high-level architecture diagram using the discussion that we had so far. It looks like this.

![[Pasted image 20240416075839.png]]


Fig.6- Snowflake Architecture

You have databases at the bottom. These are storage only. Then you have VWs on top. These VWs are compute-only.  
There is another separate layer which is for managing metadata, security, automatic performance optimization, transactions, and concurrency management. This layer is what enables Snowflake to act as a database and comes mostly at a nominal fixed price. Your main cost is associated with the storage and compute requirements.  
Great! Looks impressive? Not yet.  
Separation of storage and compute is available with many other products, including Amazon EMR and Data Bricks. You also have a rich enough SQL offered by Spark SQL. So, most of those things that I discussed are available with a few other products as well. Snowflake provides better user experience and makes it simple to implement, but it doesn't make Snowflake unique enough yet. Isn't it?  
Let's deep dive into the database storage layer, and I am sure you will be impressed almost immediately.

## Snowflake Micro Partition Architecture

Snowflake decided to use S3 as its storage layer. That was a contrarian decision for database storage because we all know that S3 comes with varying performance and put up several restrictions. For example, S3 has a much higher latency and CPU overhead compared to the local storage. That is why? HDFS on local storage works a lot better than S3. The second problem, we can only overwrite files in S3. It does not support updating or even appending the same file. These two problems are so critical that they often put a hold on the decision to use S3 as database storage.  
I mean, you can dump files in there. But using it as a database storage layer would be a NO-NO talk. Right?  
However, the Snowflake team found two main technical reasons to use S3.  
High availability and durability - You already understand these things. Right? The S3 doesn't go down and once saved, you cannot lose your files.  
Now the second and most critical reason. S3 APIs allowed them to read a part of the data from an S3 file. What does it mean? Well, the ability to read in parts without even loading the entire file is a kind of random-access capability. Isn't it? Not truly, but a kind-of. Right?  
And that could be a powerful feature if you have something like an index that allows you to read exactly what you want to read and avoid reading unnecessary volumes.  
Great! So, the next question is - How exactly Snowflake leveraged these S3 capabilities.  
Let's assume that you have a large table. For a simple illustration, consider this table. This one is a relatively small table, but the idea that I am going to explain is applicable for a super-large table as well. The first thing that Snowflake does is to break the table into multiple smaller partitions. And they call it micro-partitions which is not more than 500 MB in size. So, each table partition is between 50 to 500 MB of uncompressed data. The next thing that they do is reorganize the data in each partition to make is columnar. What does it mean? Simple! Column values in the partition are stored together. The next step is to compress each column. And that's unique. You are not compressing the entire partition. You are compressing only the column values individually. Finally, they add a header to each micro partition. The header contains an offset and length of each column stored within the micro partition. They also store some other metadata information in the header, but the column offsets are the most critical information for us to understand the read pattern.

![[Pasted image 20240416075920.png]]
  

Fig.7- Snowflake Micro Partitions

Now, these micro partitions are stored in S3 as immutable files, and a lot of additional metadata and statistics about these micro partitions is maintained in the snowflake metadata layer. And that's why they call the cloud services layer of the Snowflake as the brain of the Snowflake.  
When you fire a SQL query, Snowflake would know which tables and what columns you want to read. Which micro partition files in S3 belong to the desired table. So, they know, which files to read. But instead of reading a complete file, they first read the header and then read-only those columns which you wanted to read. And this is possible because S3 APIs allow them to read part of a file based on offset and length.  
Amazing! Isn't it? I assume that you are getting a sense of how this storage architecture allows them to optimize their I/O operation.  
Let me elaborate a little.  
Snowflake stores metadata and statistics about all the data stored in a micro-partition. So, they know the range of the values and the number of distinct values for each of the columns in the micro-partition. So, when you apply a filter in a where clause, they know which micro-partitions would have the desired data. This allows the first level of partition pruning and targets only those micro-partitions where the desired data is stored. In the next step, they first read the micro-partition header and then only read the desired columns. And this allows the second level of column pruning and minimize the overall I/O for the SQL.  
In other words, they automatically apply a generic partitioning strategy and columnar storage and take away this headache from the database designers.  
In most of the cases, this generic partitioning works very well due to the tiny size of each micro-partition. If you have a time series data and your queries are filtering on a timeframe, this partitioning strategy works like a charm. In certain other use cases, when you already know your commonly used filtering columns, they also give you an option to define table clustering key to increase the degree of partition pruning. The notion of clustering key is like what we see in Cassandra. That means, the data is ordered by the clustering key and stored close to each other.