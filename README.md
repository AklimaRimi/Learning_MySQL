# MySQL

![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2FAklimaRimi%2FLearning_MySQL&label=Reads&countColor=%23263759)

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
  - We should use where normal data and look for every data inside of an if-else condition. We can use `WHERE` clause.
  - When we want the data where we must use the aggregate function, then we need to use `HAVING` clause. But there is another clause we need to use which is `GROUP BY` clause.

**Suppose, Let's find some Name that is applied 100 times before January, 2023, Hired in January**
  Here is, not to be pointed out that 1. we need to count names, 2. find data that have information on January

  So to solve the 1st problem we have to use the `HAVING` clause and for the 2nd problem need to use `WHERE` condition. The code will be: 

  ```MySQL
    SELECT Name COUNT(Name) AS cnt_name Month FROM Employee
    GROUP BY Name
    HAVING COUNT(Name) >= 100
    WHERE Month = 'January, 2023';
  ```
Where first we grouped the data based on the `Name` column the Month `column` also affected. But I need data where no columns cannot be affected. It is a good practice to use `WHERE` clause first, Also If we use `WHERE` clause beginning of `GROUP BY` what will be the answer? First data will be filtered by January then `COUNT` Names. That is what we wanted.

  ```MySQL
    SELECT Name COUNT(Name) AS cnt_name Month FROM Employee
    WHERE Month = 'January, 2023'
    GROUP BY Name
    HAVING COUNT(Name) >= 100;
  ```

## LIMIT
Limit shows the limited rows of data

```MySQL
    SELECT Name COUNT(Name) AS cnt_name Month FROM Employee
    WHERE Month = 'January, 2023'
    GROUP BY Name
    HAVING COUNT(Name) >= 100
    ORDER BY cnt_name
    LIMIT 10;
  ```
The output will show the first 10 rows, which indicate the top 10 employee names who applied more than 100 times before January 2023.

# Joins
Simply join multiple tables using a common column and make another new table by joining. 

Point to be noted that two columns must have a common column or `FOREIGN KEY` Column.

  ## INNER JOIN
  - Only returns Common or matching values between 2 tables.

 ```MySQL
  SELECT table_1.column1, table_1.column2, table_1.column3, table_2.column1, table_2.column2, table_2.column3

 FROM table_1
 INNER JOIN table_2 ON table_1.column1 = table_2.column1;
 ```

Note: `INNER JOIN` and `JOIN` are both the same.

  ## LEFT JOIN
  - When we are performing a join of 2 tables, the 1st table is the left table and the 2nd one is the right table.
  - In the Left Join the 1st table's common column will be prioritized.
  - Performing `LEFT JOIN` that will return all of the values of the common column of 1st table.
  - If the Left Column value doesn't match with the right column value the row will fill with NULL value

    | ID| Name|
    |---|-----|
    |1|A|
    |2|B|
    |3|C|

Another Table is
|ID| Work|
|--|---|
|1|X|
|3|Y|

And perform the `LEFT JOIN` 

```MySQL
SELECT table_1.ID, table_1.Name, table_2.Work
FROM table_1
LEFT JOIN table_2 on table_1.ID = table_2.ID;
```
Output:

  | ID| Name|Work|
  |---|-----|----|
  |1|A|X|
  |2|B|NULL|
  |3|C|Y|

## RIGHT JOIN

If you figured out how the `LEFT JOIN` works, I know you are smart enough to understand what `RIGHT JOIN` will do.

## UNION vs UNION ALL

`UNION` and `UNION ALL` works almost identical. No matter if there creates a NULL value both tables are important.

BUT BUT BUT.....

The problem creates when the table or tables contains duplicate values

    `UNION` keyword returns distinct columns.

    `UNION ALL` returns whole tables with duplicate columns.

  ## Let's talk about some weird join
  1. `LEFT OUTER JOIN`  : LOL, this is same as `LEFT` join. This is just another name to make us uncomfortable
  2. `RIGHT OUTER JOIN`: LOL again, you guessed it right.
  3. `CROSS JOIN`: I don't know where this join is used for. 2 tables do cartesian product, or do some combination to join 2 tables
     |Table 1|
     |---|
     |A|
     |B|

     |Table 2|
     |--|
     |C|
     |D|

     Output:
     |row|row|
     |--|--|
     |A|C|
     |B|C|
     |A|D|
     |B|D|
4. `SELF JOIN`: Join 2 columns inside of a table based on another column.
     


 ## Multiple Table Join

  Shut up, It's simple. Just join with a common column in  another table.
  
| ID| Name|
  |---|-----|
  |1|A|
  |2|B|
  |3|C|

|ID| Work|
|--|---|
|1|X|
|2|Z|
|3|Y|


|Name| Address|
|--|---|
|A|Ca|
|B|US|
|C|SL|


  ```MySQL
    SELECT table1.ID, table1.Name,table2.Work, table3.Address
    FROM table1
    JOIN table2
    ON table1.ID = table2.ID
    JOIN table3
    ON table1.Name = table3.Name;
  ```
Output:

|ID|Name|Work|Address|
|--|----|----|-------|
|1|A|X|Ca|
|2|B|Y|US|
|3|C|Z|SL|

# Nested Query, SubQuery, Inner Query

  ```MySQL
  SELECT * FROM TABLE WHERE condition;
  ```
Yeah, Subquery is the same as what we did previously.
But
 - it is written in the main `WHERE` condition
 - must have to use () parenthesis
 - the output of the subqueries could be a list or value or a table.

  ```MySQL
  SELECT *
  FROM TABLE1
  WHERE (
    SELECT *
    FROM TABLE2) ;
  ```

Question: Assign employee number 100 as a manager to all employees from  101 to 120 and employee number 129 as a manager to all employees from 131 to 140. 


  ```MySQL
  SELECT first.* FROM
  (SELECT employe_NO, (SELECT emp_no FROM manager WHERE emp_no = 100) as Manager_id
  From manager
  WHERE employe_id BETWEEN 101 AND 120)  AS first

  UNION

  SELECT second* FROM
  (SELECT employe_NO, (SELECT emp_no FROM manager WHERE emp_no = 129) as Manager_id
  From manager
  WHERE employe_id BETWEEN 131 AND 140)  AS second

ORDER BY Manager_id;
  ```

## VIEWS

Suppose, we have 10 tables, and whenever we work on something in SQL, we have to `JOIN` the 10 tables again and again. As we know, this needs a huge line of code to join them. So what we are going to do write the long code again and again or do something to solve the issue? In that case, There is a keyword, we are going to use `VIWES`. It creates a virtual table and stores it in a database for further use.

Why we are going to use `VIEWS`:
  - Saves time
  - Stops redundancy
  - easy to use
  - Memory efficient

for example:

  ```MySQL
    SELECT table_1.ID, table_1.name, table_2.Work, table_3.Address
    FROM table_1
      JOIN table_2
          ON table_1.ID = table_2.ID
      JOIN table_3
          ON table_1.Name = table_3.Name
  ```

Instead of writing the code again and again, we can store the data virtually based on `BASE` table. We can do this as..

  ```MySQL
  CREATE OR REPLACE VIEW new_table AS 
    SELECT table_1.ID, table_1.name, table_2.Work, table_3.Address
    FROM table_1
      JOIN table_2
          ON table_1.ID = table_2.ID
      JOIN table_3
          ON table_1.Name = table_3.Name;
  ```

For this code, the output will be, Create a new virtual table in views named `new_name` and store the 3 joined tables. So, that's going to be easy to perform any query. Such as

  ```MySQL
    SELECT col_name from daatabase_name.virtual_table_name;
            -- SO we can write
    SELECT name, Work from db.new_table;
  ```

# Stored Routine

  A SQL statement or a list of SQL statements/instructions  that can be stored in an SQL server. It helps a user use Database.
  
  Users use the SQL by 1. calling the statement, 2. referencing, or 3. Revoke the SQL server. 
  
  There are 2 types of routines:
    1. stored procedure
    2. Function
  
  
## Stored Procedure
  
  Code
  ```MySQL
  DELIMITER $$
  CREATE PROCEDURE procedure_name()
  
  BEGIN
      Statements/ Query;
  END $$
  
  
  CALL procedure_name()
  ```
  Here `DELIMITER $$` indicates the `PROCEDURE` will end when there have `$$` symbols. And then call the function using `CALL` and then the procedure name.
saved
  
  When a Procedure is created, the procedure saves under the database procedure store. So we can call a procedure by
  
  ```MySQL
  CALL db.procedure_name()
  ```

**Input Parameterized Procedure**

  Code
  ```MySQL
  DELIMITER $$
  CREATE PROCEDURE procedure_name(IN variable datatype)
  
  BEGIN
      Statements/ Query;
  END $$ 
  
  CALL procedure_name(value)

    ---------------------
  DELIMITER $$
  CREATE PROCEDURE procedure_name (in salary FLOAT)
  
  BEGIN
      SELECT * FROM employee
      WHERE
          Salary = salary;
  END $$

  DELIMITER ;
  
  CALL procedure_name(1000);
  ```


  ## Input and return parameters in Procedure
  
  ```MySQL
    DELIMITER $$
    CREATE PROCEDURE procedure_name(in salary FLOAT, out avg DECIMAL(10,2))
    
    BEGIN
        SELECT AVG(e.Salary)
        INTO avg
        FROM employee AS e
        WHERE
            Salary = salary;
    END $$
  
    DELIMITER ;

    SET @avg =0 ;
    CALL procedure_name(1000,@avg);
    SELECT @avg;
  ```

**NOTE:** Here we can see a new term called `SET`. `SET` is used to set a value inside of `@avg` variable. Another important thing is when we declare a variable to set a value we need to start the variable name with `@`. 


## Function
  writing function code is almost similar to writing..
  
  Code
  ```MySQL
    DELIMITER $$
    CREATE FUNCTION function_name(variable datatype) return datatype
    
    BEGIN
        DECLARE output_value datatype;
        SELECT
            columns name
        INTO
            output_value
        FROM
            Statements/ Query;
    END $$ 
    DELIMITER ;
    SELECT procedure_name(value);
  ```

## Difference between `PROCEDURE` and `FUNCTION`

|PROCEDURE|FUNCTION|
|---------|--------|
|There is no return type for a procedure. But utilizing the OUT arguments, it returns values. | The value that a function returns is of a certain kind. |
|Procedures support DML queries like insert, update, select, etc. |Using Data Manipulation queries, a function cannot be used. Functions may only use Select queries.|
|A process accepts input and output variables. |Output parameters are not permitted by a function.|
|Throughout a procedure, transactions can be managed. |Transaction management is not possible within a function.|
|A function can be called from a stored process. |From a function, you cannot call stored procedures.|
|Using choose statements to invoke a process is not possible.|You can use a choose statement to invoke a function.|
|find output by calling `CALL` procedure| use `SELECT` function|
|Can Multiple `OUT` parameters | can return a single value only |
| slow compare to `FUNCTION`| Faster than `PROCEDURE`|





# ========== THE END ===========






































