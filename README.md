# MySQL

Let's Nothing Talk about MySQL. We all know that it is used to store, manipulate, and delete huge amounts of data. Yeah, it's as simple as that.

It has several terms, like
* DDL - Data Definition Language
* DML - Data Manipulation Language
* DCL - Data Control Language
* TCL - Transaction Control Language

## Data Definition Language
---

It's a part of MySQL, which is a set of statements that allow the `user` to `define` or `modify` table not data
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


































