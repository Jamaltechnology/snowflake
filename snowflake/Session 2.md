## Recap - Session 1
- Installation - Docker / Postgres / Dbeaver
- Primary key - Foreign Key
## Introduction to SQL(Seequel)
 # Introduction to SQL
SQL is a standard language for accessing and manipulating databases.
## What is SQL?
- SQL stands for Structured Query Language
- SQL lets you access and manipulate databases
## What Can SQL do?
- SQL can execute queries against a database
- SQL can retrieve data from a database - Select
- SQL can insert records in a database
- SQL can update records in a database
- SQL can delete records from a database
- SQL can create new databases
- SQL can create new tables in a database
- SQL can create stored procedures in a database
- SQL can create views in a database
- SQL can set permissions on tables, procedures, and views

Although SQL is an ANSI/ISO standard, there are different versions of the SQL language. However, to be compliant with the ANSI standard, they all support at least the major commands (such as `SELECT`, `UPDATE`, `DELETE`, `INSERT`, `WHERE`) in a similar manner.
 - What is ANSI? - American National Standards Institute
 - what are data types?
	 -  Integer
	 - Charecter
	 - Date
	 - Decimal/Float
## Short Overview on SQL

Structured Query Language (SQL), is the database language by the use of which we can perform certain operations on the existing database, and also we can use this language to create a database. [SQL](https://www.geeksforgeeks.org/structured-query-language/) uses certain commands like CREATE, DROP, INSERT, etc. to carry out the required tasks. 

[SQL commands](https://www.geeksforgeeks.org/basic-sql-commands/) are like instructions to a table. It is used to interact with the database with some operations. It is also used to perform specific tasks, functions, and queries of data. SQL can perform various tasks like creating a table, adding data to tables, dropping the table, modifying the table, set permission for users.

These [SQL](https://www.geeksforgeeks.org/sql-concepts-and-queries/) commands are mainly categorized into five categories: 

1. DDL – Data Definition Language(Create, Drop)
2. DQL – Data Query Language (Select)
3. DML – Data Manipulation Language(Insert,update,delete)
4. DCL – Data Control Language()
5. TCL – Transaction Control Language

Now, we will see all of these in detail.  
 

![SQL commands](https://media.geeksforgeeks.org/wp-content/uploads/20210920153429/new.png)

## ****DDL (Data Definition Language)****

[DDL](https://www.geeksforgeeks.org/features-of-structured-query-language-sql/) or Data Definition Language actually consists of the SQL commands that can be used to define the database schema. It simply deals with descriptions of the database schema and is used to create and modify the structure of database objects in the database. DDL is a set of SQL commands used to create, modify, and delete database structures but not data. These commands are normally not used by a general user, who should be accessing the database via an application.

List of DDL commands: 

- [****CREATE****](https://www.geeksforgeeks.org/sql-create/): This command is used to create the database or its objects (like table, index, function, views, store procedure, and triggers).
- [****DROP****](https://www.geeksforgeeks.org/sql-drop-truncate/): This command is used to delete objects from the database.
- [****ALTER****](https://www.geeksforgeeks.org/sql-alter-add-drop-modify/)****:**** This is used to alter the structure of the database.
- [****TRUNCATE****](https://www.geeksforgeeks.org/sql-drop-truncate/)****:**** This is used to remove all records from a table, including all spaces allocated for the records are removed.
- [****COMMENT****](https://www.geeksforgeeks.org/sql-comments/): This is used to add comments to the data dictionary.
- [****RENAME****](https://www.geeksforgeeks.org/sql-alter-rename/)****:**** This is used to rename an object existing in the database.

## ****DQL (Data Query Language)****

****DQL**** statements are used for performing queries on the data within schema objects. The purpose of the DQL Command is to get some schema relation based on the query passed to it. We can define DQL as follows it is a component of SQL statement that allows getting data from the database and imposing order upon it. It includes the SELECT statement. This command allows getting the data out of the database to perform operations with it. When a SELECT is fired against a table or tables the result is compiled into a further temporary table, which is displayed or perhaps received by the program i.e. a front-end.

List of DQL: 

- [****SELECT****](https://www.geeksforgeeks.org/sql-select-clause/)****:**** It is used to retrieve data from the database.

## ****DML(Data Manipulation Language)****

The SQL commands that deal with the manipulation of data present in the database belong to DML or Data Manipulation Language and this includes most of the SQL statements. It is the component of the SQL statement that controls access to data and to the database. Basically, DCL statements are grouped with DML statements.

List of DML commands: 

- [****INSERT****](https://www.geeksforgeeks.org/sql-insert-statement/): It is used to insert data into a table.
- [****UPDATE****](https://www.geeksforgeeks.org/sql-update-statement/)****:**** It is used to update existing data within a table.
- [****DELETE****](https://www.geeksforgeeks.org/sql-delete-statement/): It is used to delete records from a database table.
- [****LOCK:****](https://www.geeksforgeeks.org/sql-lock-table/) Table control concurrency.
- ****CALL:**** Call a PL/SQL or JAVA subprogram.
- ****EXPLAIN PLAN:**** It describes the access path to data.

## ****DCL (Data Control Language)****

DCL includes commands such as GRANT and REVOKE which mainly deal with the rights, permissions, and other controls of the database system. 

List of  DCL commands: 

[****GRANT:****](https://www.geeksforgeeks.org/mysql-grant-revoke-privileges/) This command gives users access privileges to the database.

****Syntax:****

> GRANT SELECT, UPDATE ON MY_TABLE TO SOME_USER, ANOTHER_USER;  

[****REVOKE:****](https://www.geeksforgeeks.org/difference-between-grant-and-revoke/) This command withdraws the user’s access privileges given by using the GRANT command.

****Syntax:****

> REVOKE SELECT, UPDATE ON MY_TABLE FROM USER1, USER2;  

## ****TCL (Transaction Control Language)****

Transactions group a set of tasks into a single execution unit. Each transaction begins with a specific task and ends when all the tasks in the group are successfully completed. If any of the tasks fail, the transaction fails. Therefore, a transaction has only two results: success or failure. You can explore more about transactions [_****here****_](https://www.geeksforgeeks.org/sql-transactions/). Hence, the following TCL commands are used to control the execution of a transaction: 

****BEGIN:**** Opens a Transaction.

[****COMMIT****](https://www.geeksforgeeks.org/sql-transactions/)****:**** Commits a Transaction.

****Syntax:****

> COMMIT;  

[****ROLLBACK****](https://www.geeksforgeeks.org/sql-transactions/)****:**** Rollbacks a transaction in case of any error occurs.

****Syntax:****

> ROLLBACK;



********************************************************End of Session**************************


 - Login to Postgres
 - Create tables: Student and Department
 - Load Data and explain Select/Insert/Update/Delete
 - EXplain PK and FK
 
 ### **Introduction to SQL Joins**
  - Inner Join
  - Left Outer Join
  - Right Outer Join
  - Self Join
  - Product Join
  ### **Subquery**
  Handling **Null**
  
  
 
 
 
 





# Topic
## Topic
#### Topic

	 