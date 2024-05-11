
```sql


use schema UNIQ_TRAINING.SNOWFLAKE_COURSE;
use role accountadmin;
use warehouse compute_wh;

create or replace table sales (customerid int,product string,quantity int,price float);
create or replace table customers (customerid int,CustomerName string, city string);

insert into sales(customerid,product,quantity,price) values(1,'Shirt',2,20);
insert into sales(customerid,product,quantity,price) values(2,'Hat',1,15);
insert into sales(customerid,product,quantity,price) values(3,'Hat1',5,30);
insert into sales(customerid,product,quantity,price) values(3,'Hat1',5,30);

insert into customers(customerid,CustomerName,city) values(1,'John Doe','New York');
insert into customers(customerid,CustomerName,city) values(2,'Jane Smith','Seattle');
insert into customers(customerid,CustomerName,city) values(3,'Jane1 Smith1','Seattle1');


CREATE OR REPLACE DYNAMIC TABLE Sales_By_Customer
    LAG = '1 MINUTE'
    WAREHOUSE=compute_wh
AS
SELECT 
  c.CustomerName,
  SUM(s.Quantity * s.Price) AS TotalSales
FROM sales s
JOIN customers c ON s.CustomerID = c.CustomerID
GROUP BY c.CustomerName;

select * from Sales_By_Customer;


```