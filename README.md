# MySQL

![](https://github.com/AklimaRimi/Learning_MySQL/assets/59701116/2e897ced-be5f-4270-856d-b1ce214c9457)


Let's Nothing Talk about MySQL. We all know that it is used to store, manipulate, and delete huge amounts of data. Yeah, it's as simple as that.

It has several terms, like
* DDL - Data Definition Language
* DML - Data Manipulation Language
* DCL - Data Control Language
* TCL - Transaction Control Language

## Data Definition Language
---

It's a part of MySQL, which is a set of statements that allow the `user` to `define` or `modify` tables, not data
  ### Keywords
  * `CREATE` table
  * `ALTER` or modify the table
  * `DROP` Table

## Data Manipulation Language
---
DML allows manipulating `data` in the table, using DML we can `create` a new column, `modify`, `delete`, and `read` the data from the table.
  ### Keywords
  * `SELECT`
  * `UPDATE`
  * `DELETE`
  * `CREATE`

## Data Control Language
---
DCL uses to access or revoke permission for users.
  ### Keywords
  * `REVOKE`
  * `GRANT `

## Transaction Control Language
---
TCL helps save and restore any changes after performing DCL.
  ### Keywords
  * `COMMIT`
  * `ROLLBACK`


<br>
<br>

# Relationship

SQL provides a term called Relational Database Management System (RBDMS) which means there could be multiple tables in a database that can be related to others or have common columns in multiple tables.

There are some columns that are identified differently from other columns to do there have some special keywords
  1. `Primary` Key
  2. `Unique` Key
  3. `Foreign` Key


## Primary key

When we use `PRIMARY KEY` keyword during building a table, beside a column name that means all of the values inside of a column will be unique.

  * Each table may or may not contain a primary key column, but only one primary column is acceptable, more than one primary key is not allowed.
  * Cannot contain `NULL` values
    
    ### Code
    
``` MySQL
   
    CREATE TABLE Products (
          product_id INT,
          product_name VARCHAR(100),
          price DECIMAL(5,3),           
          PRIMARY KEY (product_id)

        );
```

## Foreign Key

Foreign Key helps to connect one table with another. It represents common columns between 2 or multiple tables.

  * Each table may have multiple or 0 foreign key columns.
  * May have `NULL` values
  *  identifies the relationships between tables, not the tables themselves.

 ### Code

 ``` MySQL

  CREATE TABLE Customers (
            customer_id INT,
            customer_name VARCHAR(100),
            email VARCHAR(100),
            product INT,
            PRIMARY KEY (customer_id),
            FOREIGN KEY (product) REFERENCES Products(product_id)
          );
  
 ```

## Unique Key

As we know, the primary key contains Unique values in a column, but there are some entities that also need to be unique like email, address, and phone number. So, here `UNIQUE KEY` comes.

  * We can use multiple times this key in a table.
  * May contain `NULL` values
    

```MySQL
CREATE TABLE Customers (
          customer_id INT,
          customer_name VARCHAR(100),
          email VARCHAR(100) unique key,
          phone VARCHAR(11) unique key,
          product INT,
          PRIMARY KEY (customer_id)
        );

```

## Relationship

A customer can buy multiple products, A customer can have only one unique order_id, customers can purchase various products, and products can be purchased by many customers. So these are the relationships between customer and product. <br>
  * It represents how multiple tables need to be implemented.
  * Depicts how a database is organized
  * It is a blueprint.
    
There are commonly 3 types of relationships that can be created among tables.
  1. One to One
  2. One to Many
  3. Many to Many


# Variables

|Data type     | Keyword | Maximum Byte size | useful for|
|---------     |---------|-----------|-----------|
| Character    | `CHAR`  | 255       |  CHAR stores a fixed number of characters, padding any extra space with blank characters. If we set CHAR(10) and a value store 'Hello' CHAR not only store 'Hello' but also 5 extra spaces 'Hello_____' |
| Variable Character  |`VARCHAR`| 65, 535| VARCHAR stores only the actual characters used in the string, without padding any extra spaces. If we set VARCHAR(10) and a value store 'Hello' VARCHAR just store the value without extra spaces|
|Enumerate| `ENUM('x','y','z')`| 255| Error will through if we input value instead of x,y,z|
|Tiny Integer | `TINYINT`| 1 | Use according to data, range (-128, 127) digits|
|Small Integer| `SMALLINT`| 2 range| Use according to data, range (-32768, 32787) digits|
|Medium Interger| `MEDIUMINT`| 3 | Use according to data, range (-8388608, 8388607 ) digits|
| Integer| `INT`| 4 | Use according to data, range (-2147483648, 2147483647) digits|
|BIG Integer| `BIGINT`| 8 | Use according to data, (-9223372036854775808, 9223372036854775807) digits|
| Float | `FLOAT(p,s)`| 4 | Maximum Digit 23|
| Double | `DOUBLE(p,s)` | 8 | Maximum Digit 53|
| Date Time | `DATE` `DATETIME` `TIMESTAMP` |2, 4, 8| 



# Working on Database using DDL 

## Create Database
  ```MySQL
  CREATE DATABASE Sale;
  ```

or

  ```MySQL
  CREATE DATABASE IF NOT EXISTS Sale;
  ```
## Create Table
  ```MySQL
  CREATE TABLE Customers (
          customer_id INT,
          customer_name VARCHAR(100),
          email VARCHAR(100) unique key,
          phone VARCHAR(11) unique key,
          product INT,
          PRIMARY KEY (customer_id)
        );
  ```

or

  ```MySQL
  CREATE DATABASE IF NOT EXISTS Sale;
  ```
## ALTER Database

  ```MySQL
  ALTER DATABASE IF EXISTS Sale RENAME TO product_sale';
  ```
## Drop Database/ Table

  ```MySQL
  DROP DATABASE product_sale;
  ```

  ```MySQL
  DROP TABLE table_name;
  ```





# Working on Table using DML


  ## Insert value
  * Just insert value according to the column and data types
  ```MySQL
    INSERT into Customers (customer_id, customer_name, email, phone, product)  values (0, 'Rimi','Rimi@gmail.com', '12345', 'soap');
    INSERT into Customers (customer_id, customer_name, email, phone, product)  values (1, 'A','A@gmail.com', '2345', 'soap');
    INSERT into Customers (customer_id, customer_name, email, phone, product)  values (2, 'B','B@gmail.com', '3456', 'Laptop');
    INSERT into Customers (customer_id, customer_name, email, phone, product)  values (3, 'C','c@gmail.com', '4567', 'Mouse');
  ```
  ## SELECT
  * Retrieve or fetch data from Table
  * Extract Information

    ### Code
    ```MySQL
    SELECT COLUMN_NAMES FROM TABLE_NAME;


    Like

    SELECT * FROM Customer;
    ```

    ***This will show all of the column values from Customer Table***

## WHERE (Condition)
  
`WHERE` clause set a condition, using this clause we can make our query more specifically what part of the data we are looking for.

  ### Code

  ```MySQL
SELECT * FROM Customers WHERE customer_name = 'RIMI';
```

## AND (Operator)

`AND` operation uses conditions; we all know if all the conditions are true, then it will provide output.

x = 0 <br> 
y = 0 <br>
if x == 0 and y == 0 : output will be 0

  ```MySQL
  SELECT * FROM Customers WHERE customer_name = 'Rimi' AND product = 'soap';
  ```

 ## OR (Operator)
 If we have different conditions and satisfy at least one condition, the result will be shown.

   ```MySQL
    SELECT * FROM Customers WHERE product = 'laptop' or product = 'soap';
   ```
The output will be all of the results which have product names `laptop` and `soap`.

## **What if we have to use `AND` and `OR` operators at the same condition? Which operator will perform first?**

suppose we write this sql code..
  ```MySQL
    SELECT * FROM Customers WHERE customer_name = 'Rimi' AND product = 'laptop' or product = 'soap';
   ```
So SQL Precedence law says `AND` operation will perform first then `OR` will.

So the above code executes `customer_name = 'Rimi' AND product = 'laptop'` then `OR` operator will be executed. 

If we want to the code perform `OR` operator first then `AND` we can use parenthesis like that:
 
  ```MySQL
    SELECT * FROM Customers WHERE customer_name = 'Rimi' AND (product = 'laptop' or product = 'soap');
   ```

## NOT IN (Operator)

We can not write all the time. Show me the list which has the name Rimi, a,b,c,d,e, and so on. This gonna be a huge condition. Instead of the whole condition, we can just say show me the  list which doesn't have name B using `NOT IN` operation in the condition. So the code will be

  ```MySQL
    SELECT * FROM Customers WHERE customer_name NOT IN ('B');
  ```

## Pattern

Sometimes we need to look for some string but can not remember the whole string or string having common words or letters or patterns. In that case, we can retrieve the data using the pattern or word using `LIKE` operator.

  ```MySQL
    SELECT * FROM Customers WHERE LIKE('Ri%);
  ```

There are some rules for finding data using patterns.
|Pattern|Meaning|Example|
|-------|-------|--------|
|AB%    |Returns all the values that start with AB and Length doesn't matter|AB, ABC, ABCDBCDFBVDVFBFB|
|%AB    | Returns all the values that end with AB and also length doesn't matter| lfihdoginosAB, AB, AAB, CAB|
|%AB%   | Returns all the value that has middle value AB, length doesn't matter| lkjlkABpofjpo, AB, xABm|
|AB_    | Returns all the values that start with AB and string size `3`| ABC, ABX, ABH|
| _AB   | Returns all the values that end with AB and string size `3`| CAB, XAB, GAB|
| _AB_  | Returns all the values that middle value AB and string size `4`| CABH, XABA, GABA|
|_A%    | Return values which have 2nd letter A| xAlfdgijdoignodfi, BA, AA|
| A%B   | Return values which have start value A and end value B| AB, ADGDGFDB|


## BETWEEN.. AND..

If we want to see information and there is a range, we can simply use Between keyword. Suppose, we want to see Student information whose code range from 564 to 1000. We can use
  ```MySQL
    SELECT * FROM Student WHERE Code BETWEEN 564 AND 1000;
  ```
On the opposite, if we want to see the information except the code from 564 to 1000 we can do 

  ```MySQL
    SELECT * FROM Student WHERE Code NOT BETWEEN 564 AND 1000;
  ```

## DISTINCT
 To find Unique values, we can use DISTINCT keyword

  ```MySQL
    SELECT DISTINCT Product FROM Customers;     
  ```

## Aggregate functions
  Applied to multiple rows of a single column of a table and returns an output of a single value. Some functions are:-
  * COUNT()
  * SUM()
  * MIN()
  * MAX()
  * AVG()

    ### COUNT()
      COUNT uses for counting unique values in a column or how frequently a value occurs.
    ```MySQL
    SELECT COUNT(Product) FROM Customers WHERE Product = 'Laptop';     
    ```
    ### SUM()
      To find the numeric sum of a column. 
    ```MySQL
    SELECT SUM(Product) FROM Customers;     
    ```

    ### MIN()
      To find the minimum value of a column. 
    ```MySQL
    SELECT MIN(Product) FROM Customers;     
    ```

    ### MAX()
      To find the maximum value of a column. 
    ```MySQL
    SELECT MAX(Product) FROM Customers;     
    ```

    ### AVG()
      To find the average value of a column. 
    ```MySQL
    SELECT AVG(Product) FROM Customers;     
    ```
## ORDER BY
  To make arranged data, we can use `ORDER BY` keyword. We can arrange the data in ascending or descending.
  ```MySQL
    SELECT * FROM Customers ORDER BY Product,Name ASC; 
  ```
Or
  ```MySQL
    SELECT * FROM Customers ORDER BY Product DSC; 
  ```

## GROUP BY 
  As the name suggests, give the Group some columns or information. To do that 

  ```MySQL
    SELECT * FROM Customers WHERE GROUP BY (Product) ORDER BY Name;
  ```
## AS
To rename any column name or any value name, we can use  `AS`. 

  ```MySQL
    SELECT Product As P FROM Customers ;
    SELECT COUNT(Product) AS product_count FROM Customers; 
  ```
## HAVING 
refines the output from data that does not satisfy a certain condition.
- Frequently implemented with `GROUP BY`
- `HAVING` is like `WHERE` condition but applied to the `GROUP BY` block.
- After `HAVING` condition we can use `aggregate function`. We cannot use the `aggregate function` inside of `WHERE` condition.

  ```MySQL
    SELECT * FROM Customers
    WHERE COUNT(product) > 2;
  ```
  This will give us an error because `COUNT` function doesn't work inside of `WHERE` Condition instead we can write..

  ```MySQL
    SELECT * FROM Customers
    GROUP BY product
    HAVING COUNT(product) = 2;
  ```

## Conflict to use `WHERE` and `HAVING` condition
  - We should use where normal data and look for every data inside of an if-else condition we can use `WHERE` clause.
  - When we want the data where  we must have to use aggregate function then we need to use `HAVING` clause. But there is another clause we need to use which is `GROUP BY` cluse. 



















