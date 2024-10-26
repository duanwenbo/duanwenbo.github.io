---
title: Note | Quick Notes on SQL
date: 2023-06-26 23:54:22
mathjax: true
tags:
- MySQL
- reading
categories:
- Notes
ShowToc: true
---

## Concept

- What is a database?

  - A **structured** set of computerized data with **accessible interface**

- SQL:

  - Structure Query Language (SQL), A standard language used in all relational database management system

- Install the database

  - Two components:

    1. MySQL
    2. SQL workbench

  - Add the mysql to the environment variable

    ```shell
    open ~/.zshrc
    ## add the mysql bin
    ## no spaces around the = 
    export PATH=${PATH}:/usr/local/mysql/bin
    ## The save the file
    source ./zshrc
    ```

    

- Hierachy:

  - Server -> Multiple database -> Multiple sheets



## Basic

- **Select, Create, Delete**

  ```Sql
  CREATE DATABASE tea_shop;
  USE tea_shop; 
  DROP DATABASE tea_shop;
  -- show current selection
  SELECT database();
  -- show the whole sever
  SHOW DATABASES;
  ```

- **Tables**

  - Create: A database is just a bunch of tables (core of the relational database)

    ```sql
    CREATE TABLE cat (
    	name VARCHAR(50),
    	agen INT
    );
    ```

  - Query: A collection of related data held in a **Structured format** within a database

    ```sql
    -- Remember the current cursor is on the database
    SHOW TABLES;
    SHOW COLUMNS FROM tea_shop;
    -- Describ
    DESC <table name>
    ```

  - Drop:

    ```sql
    DROP TABLE <table name>;
    ```

  - Insert:

    ```sql
    INSERT INTO <table name> (name, age)
    VALUE("JACK", 10); 
    ```

    

- Data Types
  - INT, VARCHAR,..

- **Basic Attributes of table**

  - **NOT NUlL constrains**

    ```sql
    CREATE TABLE cat2 (
      name VARCHAR(50) NOT NULL,
      age INT NOT NULL
    );
    ```

  - Tips: Use  '  first instead of " to avoid confusion

  - **Default Values**

    ```sql
    CREATE TABLE cats3 (
    	name VARCHAR(50) DEFAULT 'unnamed',
    	age INT DEFAULT 99
    );
    -- Note: The default setting won't prevent you from inserting the NULL mannually !
    ```

  - **Key**: We need a unique ID to differentiate the rows even though they looks the same.	

    - Primary Key: A unique identifier

      ```sql
      CREATE TABLE unique_cats (
        cats_id INT NOT NULL PRIMARY KEY,
      	name VARCHAR(50) DEFAULT 'unnamed',
      	age INT DEFAULT 99
      );
      ```

      ```sql
      -- alternative way
      CREATE TABLE unique_cats (
        cats_id INT NOT NULL,
      	name VARCHAR(50) DEFAULT 'unnamed',
      	age INT DEFAULT 99,
        PRIMARY KEY(cats_id)
      );
      ```

    - Auto increament: Only valid for the primary key column

      ```sql
      mysql> CREATE TABLE unique_cat(
          -> name VAECHAR(50) DEFAULT 'unnamed',
          -> id INT AUTO_INCREMENT,
          -> age INT,
      		-> PRIMARY KEY(id));
      ```

      ```shell
      mysql> DESC unique_cat;
      +-------+-------------+------+-----+---------+----------------+
      | Field | Type        | Null | Key | Default | Extra          |
      +-------+-------------+------+-----+---------+----------------+
      | name  | varchar(50) | YES  |     | unnamed |                |
      | id    | int         | NO   | PRI | NULL    | auto_increment |
      | age   | int         | YES  |     | NULL    |                |
      +-------+-------------+------+-----+---------+----------------+
      3 rows in set (0.01 sec)
      ```




## String Function

- **CONCAT() **/ CONCAT_WS (with_seperator):

  ```sql
  SELECT CONCAT(<column name>,' ') AS new_name FROM <table name>
  ```

- **SUBSTRING()** / SUBSTR()

  Silimiar to the slice operation in Python

  ```sql
  SELECT SUBSTRING(<full string>, <start position>, <end position>)
  ```

- When nesting the query:

  ```sql
  SELECT
  ... your combination
  FROM <table name>
  -- do code beautifier for your co-worker :)
  ```

- **REPLACE()**

  ```sql
  SELECT
  	REPLACE ('hello world', 'hell', '*Q#Q*');
  -- Case sensitive
  ```

- **REVERSE()**

  ```sql
  SELECT 
   REVERSE ('长恨送年芳');
  ```

- **CHAR_LENGTH()**

  ```shell
  ## LENGTH mearsures in bits
  mysql> SELECT 
      -> LENGTH('海豚');
  +------------------+
  | LENGTH('海豚')   |
  +------------------+
  |                6 |
  +------------------+
  1 row in set (0.00 sec)
  
  mysql> SELECT 
      -> CHAR_LENGTH('海豚');
  +-----------------------+
  | CHAR_LENGTH('海豚')   |
  +-----------------------+
  |                     2 |
  +-----------------------+
  1 row in set (0.00 sec)
  ```

- **UPPER**/ UCASE  and  **LOWER**/LCASE

- **INSERT**

- **REPEAT**

- **TRIM**

  ```shell
  mysql> SELECT TRIM( TRAILING '.' FROM '..em..' );
  +------------------------------------+
  | TRIM( TRAILING '.' FROM '..em..' ) |
  +------------------------------------+
  | ..em                               |
  +------------------------------------+
  1 row in set (0.00 sec)
  ```



Pratice time 🙌

- Tips on writting function:

  - Always following a '(' after the calling function, do not leave the space. E.g. This will cause error:

    ```shell
    ## Error demostration
    mysql> SELECT TRIM (LEADING '.' FROM '...emmm...');
    
    ## Instead:
    mysql> SELECT TRIM(LEADING '.' FROM '...emmm...');
    +-------------------------------------+
    | TRIM(LEADING '.' FROM '...emmm...') |
    +-------------------------------------+
    | emmm...                             |
    +-------------------------------------+
    1 row in set (0.00 sec)
    ```

  - Put the Aliases name in to ' ' although the single word without quotation marks can be encoded correctly

[Function Cheatsheet](https://dev.mysql.com/doc/refman/8.0/en/string-functions.html)



### Selection

- select distinct elements

  ```sql
  SELECT DISTINCT <column name> FROM <table name>;
  
  -- DISTINCT Applies to all following keys
  ```

- ORDER BY

  ```sql
  SELSELECT DISTINC author_lname, author_fname FROM books ORDER BY author_lname DESC;
  -- ORDER BY 2 (2nd selected columns)
  -- ORDER BY author_lname, author_fname
  
  ```

- LIMIT: limit the number of query return

  ```sql
  SELECT DISTINC author_lname, author_fname FROM books ORDER BY author_lname DESC 
  LIMIT 5,10;
  -- LIMITE from 5 to 10th row
  ```

- SEARCH: searching the characture

  ```sql
  SELECT title, author_lname FROM books
  WHERE author_lname LIKE
  "%da%";
  -- r'%'' is equivlent to r'.*' in regular expression
  ```

  ```
  SQL search cheatsheet
  
  % == .*
  _ == .
  ' == $ (at the end of the string)
  \ == \ (转义)
  ```

  

Pratice time 🙌

- Tips:

  ```sql
  SELECT <colum name> AS another_name FROM books
  
  -- AS goes first before FROM
  ```






## CRUP

- **CRUD**: Create, Read, Update, Delete

- Read:

  - Conditional Statement: **WHERER**

    ```sql
    SELECT <column name>, <column name> 
    FROM <table name> 
    WHERE <BOOL expression>;	
    ```

  - Aliases Statement: **AS**, Temporary only for this query

    ```Shell
    mysql>  SELECT name AS kettyname FROM cats;
    +----------------+
    | kettyname      |
    +----------------+
    | Ringo          |
    | Cindy          |
    | Dumbledore     |
    | Egg            |
    | Misty          |
    | George Michael |
    | Jackson        |
    +----------------+
    ```

- Update:

  - Always from a table prospect using the SQL

  - ```sql
    UPDATE <able name> SET <cloumn name> = <value> WHERE ...
    ```

  - Rule of 👍: Try selecting before update. Make sure your target is correct.
  - Notice the data type when amending.

- Delete (Destroy:/ ):

  - ```sql
    DELETE FROM <table name> WHERE ..
    ```

  - Notice the difference from DROP: DELETE will at least leave an empty set.
  - Try Selecting before as well.



Pratice time 🙌

- Leave enough space when naming each column. If not:

  ```sql
  -- modify the attributes of column
  ALTER <table name> MODIFY COLUMN <column name> <new data type>
  ```

- The PRIMARY KEY setting will set NOT NULL by default






## Data Type (Time)

- Text

- Decimal ```DECIMAL(5,2)```

- FLoat

- DATE: ```YYYY-MM-DD```

- TIME: ``hh:mm:ss``

- DATETIME: ``YYYY-MM-DD hh:mm:ss``

- CURDATE / CURTIME / NOW

- `IFNULL(<column name>, replacement)`

- Time Stamp : Similar to datetime by only supports much smaller range 

- **On update**: one more extra

  ```shell
  mysql> DESC caption;
  +-----------+--------------+------+-----+-------------------+-----------------------------+
  | Field     | Type         | Null | Key | Default           | Extra                       |
  +-----------+--------------+------+-----+-------------------+-----------------------------+
  | text      | varchar(200) | YES  |     | NULL              |                             |
  | create_at | timestamp    | YES  |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED           |
  | update_at | timestamp    | YES  |     | NULL              | on update CURRENT_TIMESTAMP |
  +-----------+--------------+------+-----+-------------------+-----------------------------+
  
  
  mysql> INSERT INTO caption (text) VALUES('hello');
  Query OK, 1 row affected (0.00 sec)
  
  mysql> SELECT * FROM caption;
  +-------+---------------------+-----------+
  | text  | create_at           | update_at |
  +-------+---------------------+-----------+
  | hello | 2023-06-16 14:38:47 | NULL      |
  +-------+---------------------+-----------+
  
  
  mysql> UPDATE caption SET text = 'hello!!';
  Query OK, 1 row affected (0.01 sec)
  Rows matched: 1  Changed: 1  Warnings: 0
  
  mysql> SELECT * FROM caption;
  +---------+---------------------+---------------------+
  | text    | create_at           | update_at           |
  +---------+---------------------+---------------------+
  | hello!! | 2023-06-16 14:38:47 | 2023-06-16 14:39:37 |
  +---------+---------------------+---------------------+
  
  ```

  

- Change the format of time:

  - **DATE_FORMAT**

    ```shell
    mysql>  SELECT DATE_FORMAT(NOW(), '%d-%m-%Y');
    +--------------------------------+
    | DATE_FORMAT(NOW(), '%d-%m-%Y') |
    +--------------------------------+
    | 16-06-2023                     |
    +--------------------------------+
    ```

  - [format Ref](https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html)





## Logical Operation

- Not equal  `!=`

- Not like `NOT LIKE`

- Greater than `>`

- AND `AND`

- OR `OR`

- BETWEEN `BETWEEN .. AND ...`

- IN `IN: `(NOT IN as well)

  ```sql
  WHERE author_lname IN ('Bobby', 'Baobi', 'Buobi')
  ```

- CASE STATMENT

  ```sql
  SELECT title, released_year,
  CASE
  	WHEN released_year >= 2000 THEN 'Morden lit'
  	WHEN .. THEN .. 
  	WHEN .. THEN .. 
  	ELSE .. 
  END AS ..
  FROM books;
  ```

- `IS NULL`



## Aggregation

- Count

  ```sql
  SELECT COUNT(author_laname) FROM books
  -- COUNT(*) has only_form_by_whole_group attribute
  -- COUNT omits the NULL values
  ```

  

- **Group By** (the result is like clustering)#

  ```shell
  mysql> SELECT COUNT(*) FROM books GROUP BY author_lname;
  +----------+
  | COUNT(*) |
  +----------+
  |        2 |
  |        3 |
  |        3 |
  |        1 |
  |        1 |
  |        2 |
  |        1 |
  |        1 |
  |        2 |
  |        2 |
  |        1 |
  +----------+
  11 rows in set (0.00 sec)
  
  mysql> SELECT COUNT(*) FROM books;
  +----------+
  | COUNT(*) |
  +----------+
  |       19 |
  +----------+
  1 row in set (0.00 sec)
  
  mysql> SELECT * FROM books GROUP BY author_lname;
  ERROR 1055 (42000): Expression #1 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'book_shop.books.book_id' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by
  
  mysql> SELECT author_lname FROM books GROUP BY author_lname;
  +----------------+
  | author_lname   |
  +----------------+
  | Lahiri         |
  | Gaiman         |
  | Eggers         |
  | Chabon         |
  | Smith          |
  | Carver         |
  | DeLillo        |
  | Steinbeck      |
  | Foster Wallace |
  | Harris         |
  | Saunders       |
  +----------------+
  11 rows in set (0.00 sec)
  
  # notice how * refers to different targets when using GROUP BY
  
  
  mysql> SELECT CONCAT(author_lname,' ',author_fname) AS author FROM books GROUP BY author;
  +----------------------+
  | author               |
  +----------------------+
  | Lahiri Jhumpa        |
  | Gaiman Neil          |
  | Eggers Dave          |
  | Chabon Michael       |
  | Smith Patti          |
  | Carver Raymond       |
  | DeLillo Don          |
  | Steinbeck John       |
  | Foster Wallace David |
  | Harris Dan           |
  | Harris Freida        |
  | Saunders George      |
  +----------------------+
  12 rows in set (0.00 sec)
  ```

- MIN/MAX

- Sub query

  ```shell
  mysql> SELECT title, pages FROM books WHERE pages=(SELECT MAX(pages) FROM books);
  +-------------------------------------------+-------+
  | title                                     | pages |
  +-------------------------------------------+-------+
  | The Amazing Adventures of Kavalier & Clay |   634 |
  +-------------------------------------------+-------+
  1 row in set (0.00 sec)
  ```

- Group BY + MIN/Max

  ```sql
  ## Not working :(
  mysql> SELECT author_lname, released_year 
      -> FROM books
      -> GROUP BY author_lname;
  ERROR 1055 (42000): Expression #2 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'book_shop.books.released_year' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by
  
  
  ## working :)
  mysql> SELECT author_lname, MIN(released_year)
      -> FROM books
      -> GROUP BY author_lname;
  +----------------+--------------------+
  | author_lname   | MIN(released_year) |
  +----------------+--------------------+
  | Lahiri         |               1996 |
  | Gaiman         |               2001 |
  | Eggers         |               2001 |
  | Chabon         |               2000 |
  | Smith          |               2010 |
  | Carver         |               1981 |
  | DeLillo        |               1985 |
  | Steinbeck      |               1945 |
  | Foster Wallace |               2004 |
  | Harris         |               2001 |
  | Saunders       |               2017 |
  +----------------+--------------------+
  11 rows in set (0.00 sec)
  ```

- Notice the concept of **Aggregation Function**, Group By only works with the aggregation functions (MIN/MAX/SUM/AVG)



Reference: https://dev.mysql.com/doc/refman/8.0/en/aggregate-functions.html



## Constrains & Alter

- Unique

  ```sql
  CREATE TABLE contacts (
  	Name VARCHAR(150) NOT NULL,
  	Phone VARCHAR(12) NOT NULL UNIQUE
  );
  ```

  ```shell
  mysql> DESC contacts;
  +-------+--------------+------+-----+---------+-------+
  | Field | Type         | Null | Key | Default | Extra |
  +-------+--------------+------+-----+---------+-------+
  | Name  | varchar(150) | NO   |     | NULL    |       |
  | Phone | varchar(12)  | NO   | PRI | NULL    |       |
  +-------+--------------+------+-----+---------+-------+
  ```

- Check / Constrains

  ```sql
  CREATE TABLE partiers (
  	Name VARCHAR(150) NOT NULL,
  	Age INT NOT NULL CHECK (age > 18)
  );
  
  -- Equivlent
  CREATE TABLE partiers (
  	Name VARCHAR(150) NOT NULL,
  	Age INT NOT NULL,
  	CONSTRAINT adult_check CHECK (Age > 18)
  	);
  ```

- Multi-column Constrains

  ```sql
  CREATE TABLE companies (
  	name VARCHAR(150) NOT NULL,
  	address VARCHAR(300) NOT NULL,
  	CONSTRAINT name_address UNIQUE(name, address)
  );
  ```

- ALL in one place to change the attribute of the table: ALTER

  ```sql
  -- Add a column
  ALTER TABLE companies
  ADD COLUMN type VARCHAR(50) NOT NULL DEFAULT 'Ltd';
  
  -- Drop a column
  ALTER TABLE companies
  DROP COLUMN type VARCHAR(50) NOT NULL DEFAULT 'Ltd';
  
  -- Rename a table
  ALTER TABLE companies
  RENAME TO ''suppliers
  
  -- Rename a column
  ALTER TABLE companies
  RENAME COLUMN type TO Categories
  
  -- Modify the existing column
  ALTER TABLE companies
  MODIFY COLUMN <new constraint>
  
  ```

  

- Tips: Check all constraints

  ```sql
  SELECT * FROM USER_CONSTRAINTS
  
  -- It will return all constraints in the selected database
  ```

- 

## One 2 Many

- How to manage the data ?  by relationship:
  - **One to one relationship**
    - table 1: basic info of customers | table2: details of  customers | customer as the key 
  - **One to Many relationship (*)**
    - One book to many of reviews
  - **Many to many relationship**
    - Books and authors: books can have multiple authors, the author can also have many books

- **One to many**: Take customers and orders for example:

- <img src="https://p.ipic.vip/wbh0re.png" alt="customer-order exmaple" style="zoom: 25%;" />

  - **Primary Key**: Some particular column that always unique

  - **Foreign Key**: Reference to other table

    ```sql
    
    -- how to use foreign key to link two tables?
    
    -- table 1
    CREATE TABLE customers (
    id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    email VARCHAR(50) UNIQUE);
        
    -- table 2
    CREATE TABLE orders(
    id INT PRIMARY KEY AUTO_INCREMENT,
    order_date DATE,DES
    customer_id INT,
    FOREIGN KEY (customer_id) REFERENCES customers(id)
    );
    ```

  - Cross Join: dummy emmumerated combination of two table

  - Inner Join:

    ```sql
    SELECT * FROM customers  
    JOIN orders on orders.customer_id = customers.id;
    ```

    ```sql
    mysql> SELECT * FROM customers  JOIN orders on orders.customer_id = customers.id;
    +----+------------+-----------+------------------+----+------------+--------+-------------+
    | id | first_name | last_name | email            | id | order_date | amount | customer_id |
    +----+------------+-----------+------------------+----+------------+--------+-------------+
    |  1 | Boy        | George    | george@gmail.com |  1 | 2016-02-10 |  99.99 |           1 |
    |  1 | Boy        | George    | george@gmail.com |  2 | 2017-11-11 |  35.50 |           1 |
    |  2 | George     | Michael   | gm@gmail.com     |  3 | 2014-12-12 | 800.67 |           2 |
    |  2 | George     | Michael   | gm@gmail.com     |  4 | 2015-01-03 |  12.50 |           2 |
    |  5 | Bette      | Davis     | bette@aol.com    |  5 | 1999-04-11 | 450.25 |           5 |
    +----+------------+-----------+------------------+----+------------+--------+-------------+
    5 rows in set (0.00 sec)
    
    ```

  

  - Left Join / Right  join:

    ```sql
    SELECT * FROM customers  
    LEFT JOIN orders on orders.customer_id = customers.id;
    ```

    ```sql
    mysql> SELECT * FROM customers LEFT JOIN orders on orders.customer_id = customers.id;
    +----+------------+-----------+------------------+------+------------+--------+-------------+
    | id | first_name | last_name | email            | id   | order_date | amount | customer_id |
    +----+------------+-----------+------------------+------+------------+--------+-------------+
    |  1 | Boy        | George    | george@gmail.com |    1 | 2016-02-10 |  99.99 |           1 |
    |  1 | Boy        | George    | george@gmail.com |    2 | 2017-11-11 |  35.50 |           1 |
    |  2 | George     | Michael   | gm@gmail.com     |    3 | 2014-12-12 | 800.67 |           2 |
    |  2 | George     | Michael   | gm@gmail.com     |    4 | 2015-01-03 |  12.50 |           2 |
    |  3 | David      | Bowie     | david@gmail.com  | NULL | NULL       |   NULL |        NULL |
    |  4 | Blue       | Steele    | blue@gmail.com   | NULL | NULL       |   NULL |        NULL |
    |  5 | Bette      | Davis     | bette@aol.com    |    5 | 1999-04-11 | 450.25 |           5 |
    +----+------------+-----------+------------------+------+------------+--------+-------------+
    
    # Notice some customer doesn't have order info but still be merged into the new table
    ```

  - Delete with the foriegn key constraints

    ```sql
    -- table 2
    CREATE TABLE orders(
    id INT PRIMARY KEY AUTO_INCREMENT,
    order_date DATE,DES
    customer_id INT,
    FOREIGN KEY (customer_id) REFERENCES customers(id) ON DELETE CASECADE
    );
    ```

    





## View

- VIEWS

  - Creating a cache table

  ```sql
  CREATE VIEW new_list AS 
  SELECT ...
  ```

  - Can & Can't
    - can't:  Join, Update (Depend on the view table type )
  - Over-write to correct

  ```sql
  CREATE OR REPLACE VIEW ...
  ```

  

- GROUP BY HAVING:
  - Silimar to `WHERE` but applied with`GROUP BY`

- GROUP BY WITH ROLLUP:

  - The Aggrigation of aggrigation 

- SQL MODES

  ```sql
  SELECT @@GLOBAL.sql_mode
  SET GLOBAL sql_mode='modes'
  
  
  SELECT @@SESSION.sql_mode
  SET SESSION sql_mode = 'mode,..'
  ```

  ```sql
  +-----------------------------------------------------------------------------------------------------------------------+
  | @@GLOBAL.sql_mode                                                                                                     |
  +-----------------------------------------------------------------------------------------------------------------------+
  | ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION |
  +-----------------------------------------------------------------------------------------------------------------------+
  ```

  

  - Modes:
    - STRICT_TRANS_TABLES:  Strict constraints on the data type conversion
    - ONLY_FULL_BY:



## Window function

- Window function
  - Silimar to window function But append aggregation results on each row 

- OVER( PARTITION BY )

```sql
mysql> SELECT department, salary, AVG(salary) OVER(x BY department) FROM employees;
+------------------+--------+-------------------------------------------+
| department       | salary | AVG(salary) OVER(PARTITION BY department) |
+------------------+--------+-------------------------------------------+
| customer service |  38000 |                                46571.4286 |
| customer service |  45000 |                                46571.4286 |
| customer service |  61000 |                                46571.4286 |
| customer service |  40000 |                                46571.4286 |
| customer service |  31000 |                                46571.4286 |
| customer service |  56000 |                                46571.4286 |
| customer service |  55000 |                                46571.4286 |
| engineering      |  80000 |                                81285.7143 |
| engineering      |  69000 |                                81285.7143 |
```

- OVER( ORDER BY): rolling style

```sql
mysql> SELECT department, salary, SUM(salary) OVER(PARTITION BY department ORDER BY salary ASC) AS depart_avg_rolling, SUM(salary) OVER(PARTITION BY department) as depart_avg FROM employees;
+------------------+--------+--------------------+------------+
| department       | salary | depart_avg_rolling | depart_avg |
+------------------+--------+--------------------+------------+
| customer service |  31000 |              31000 |     326000 |
| customer service |  38000 |              69000 |     326000 |
| customer service |  40000 |             109000 |     326000 |
| customer service |  45000 |             154000 |     326000 |
| customer service |  55000 |             209000 |     326000 |
| customer service |  56000 |             265000 |     326000 |
| customer service |  61000 |             326000 |     326000 |
| engineering      |  67000 |              67000 |     569000 |
| engineering      |  69000 |             136000 |     569000 |
| engineering      |  70000 |             206000 |     569000 |
| engineering      |  80000 |             286000 |     569000 |
```

- `RANK() OVER( ORDER BY)`

```sql
mysql> SELECT department, salary,RANK() OVER(PARTITION BY department ORDER BY salary DESC) AS depart_rank, RANK() OVER(ORDER BY salary DESC) AS over_rank FROM employees;
+------------------+--------+-------------+-----------+
| department       | salary | depart_rank | over_rank |
+------------------+--------+-------------+-----------+
| sales            | 159000 |           1 |         1 |
| engineering      | 103000 |           1 |         2 |
| engineering      |  91000 |           2 |         3 |
| engineering      |  89000 |           3 |         4 |
| engineering      |  80000 |           4 |         5 |
| sales            |  72000 |           2 |         6 |
| engineering      |  70000 |           5 |         7 |
| sales            |  70000 |           3 |         7 |
| engineering      |  69000 |           6 |         9 |
| engineering      |  67000 |           7 |        10 |

```

- `NTLE`

- `FIRST VALUE`
- `LAG`: Shift down for 1 row