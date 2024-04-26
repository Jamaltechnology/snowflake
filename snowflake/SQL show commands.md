```
SHOW <object_type_plural> [ LIKE '<pattern>' ] [ IN <scope_object_type> [ <scope_object_name> ] ]
```
# Show commands examples

```sql
	show views like '%test%';
	select sysdate();
	show roles;
	show databases;
	show databases history;
	show schemas;
	show warehouses;
	SHOW ORGANIZATION ACCOUNTS;

	-- Current permissions on a schema
	SHOW GRANTS ON SCHEMA <database_name>.<schema_name>;
	show grants of role SUPPORT_USER;
	show grants to role MGR;
	
	show grants to user demo;
	show grants of role analyst;
	show grants on database DATAHUB;
	show grants on schema sales.public;
	show future grants in schema sales.public;

-- Account operations
	show parameters;
	show connections;
	show globalaccounts;
	show regions;
	show replication accounts;
	show replication databases;

-- Session/User operations
	show parameters;
		show parameters in warehouse WH
	show variables;
	show transactions;
	show locks;

-- acccount object types
	show parameters;
	show procedures;
	show functions;
		show functions like 'invoker_role%'
	show network policies;
	show shares;
	show roles;
	show grants;
	show users;
	show warehouses;
	show databases;
	show integrations;          -- Email notifications
	show notification integrations;
	show session policies;

-- database objects types
	show schemas;
	show schemas history;
	show objects like 'line%' in mydb.public;
	show tables like 'line%' in tpch.public;
	show tables history in tpch.public;
	SHOW COLUMNS IN table_name;
	show columns in table dt_test;

	show external tables like 'line%' in tpch.public;
	
	show views like 'line%' in mydb.public;
	show materialized views;
	show materialized views like 'mv1%';
	show masking policies;

	show row access policies;
	
	show schemas;
	show sequences;
	show session policies;
	show shares;
	show shares in failover group myrg;
	show stages;
	show streams like 'line%' in tpch.public;
	show tables like 'line%' in tpch.public;
	show tables history in tpch.public;
	show tags in schema my_db.my_schema;
	SHOW TASKS IN tpch.public;
	show tasks like 'line%' in tpch.public;
	show transactions;
	show user functions;
	show users;
	SHOW USERS LIMIT 10000 FROM 'JOE';
	show variables;
	show views like 'line%' in mydb.public;
	show warehouses like 'test%';
```