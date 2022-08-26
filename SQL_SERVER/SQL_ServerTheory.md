

> __Note__
> Serial No: 01

# Introduction to SQL
###### What is SQL?
- SQL stands for Structured Query Language
- SQL lets you access and manipulate databases
- SQL became a standard of the American National Standards Institute (ANSI) in 1986, and of the International Organization for Standardization (ISO) in 1987

> __Note__
> Serial No: 02


###### Some of The Most Important SQL Commands
- SELECT - extracts data from a database
- DATE - updates data in a database
- LETE - deletes data from a database
- SERT INTO - inserts new data into a database
- EATE DATABASE - creates a new database
- ER DATABASE - modifies a database
- EATE TABLE - creates a new table
- TER TABLE - modifies a table
- OP TABLE - deletes a table
- EATE INDEX - creates an index (search key)
-ROP INDEX - deletes an index


> __Note__
> Serial No: 03

###### What Can SQL do?
- SQL can execute queries against a database
- SQL can retrieve data from a database
- SQL can insert records in a database
- SQL can update records in a database
- SQL can delete records from a database
- SQL can create new databases
- SQL can create new tables in a database
- SQL can create stored procedures in a database
- SQL can create views in a database
- SQL can set permissions on tables, procedures, and views


> __Note__
> Serial No: 04

----------
# Many people do not understand which topics of SQL they need to learn. This topic is for them.
----------
# SQL Fundamental Concepts (These are the first topics to learn).
###### SQL, Create Database, Attach SQL Database, Detach SQL Database
###### SQL SERVER Data Types
- VARCHAR, NVARCHAR, CHAR, NCHAR, DATE
###### SQL DDL (Data Definition Language) 
- Create table, Alter , Drop, Truncate
###### SQL DML (Data Manipulation Language)
- Insert, Update
- 	Update from select statement
- Delete, DELETE TOP
- SELECT Queries, Into, Insert Into, 
- Order By, Group By, Having, Over Clause, Distinct, Where,TOP, Case Statement, Temporary/Temp table
- IS NULL, IS NOT NULL, NULLIF
- 
###### SQL Operators
- Exists Operator, Between Operator, Like Clause, Intersect, Except, Union, Union ALL 

###### SQL Constraints
- Primary Key, Composite Key, Foreign key, Cascading referential integrity in Foreign Key
- SQL Server NOT NULL Constraint, Default Constraint, Unique Key, Server Check Constraint

###### SQL Joins
- Join Overview, Inner Join, Left Join, Right Join, Full Join, Cross Join, Cross Apply VS Outer Apply
- Subquery
###### SQL  Functions
###### SQL System Functions
- ISNUMERIC(), @@IDENTITY, NEWID(), NEWSEQUENTIALID(), @@ERROR, ISNULL(), 

###### SQL Ranking/Window Functions
- ROW_NUMBER(), RANK(), DENSE_RANK()
###### SQL Conversion Functions
- TRY_CAST(), PARSE Function
###### Logical Functions 
- IIF (), CHOOSE()
###### SQL Date Functions
- DATEPART(), DATEDIFF(), GETDATE(), CURRENT_TIMESTAMP() EOMONTH(), DATEADD(), DATEFROMPARTS(), DATENAME()
- Date and Time Conversions in SQL Server using Convert function
######  SQL String Functions
- CHARINDEX(), LEN(), DATALENGTH(), SUBSTRING(), REPLACE(), REPLICATE(), UPPER(), LOWER(), TRIM(), LRTIM(), RTIM(), SPACE()
- TRANSLATE(), STUFF(), SQL COALESCE(), STRING_SPLIT(), CONCAT_WS(), REVERSE(), FORMAT(), STRING_AGG(), PATINDEX(), QUOTENAME(),
###### SQL Aggregate Functions
- SUM(), MAX(), MIN(), AVG(), COUNT()
###### SQL Analytics Functions
- LEAD(), LAG(), FIRST_VALUE(), LAST_VALUE()
###### SQL Mathematical Functions 
- CEILING(), FLOOR(), ROUND(), RAND()

> __Note__
> Serial No: 05

----------
# SQL Advanced Concepts (These are required if you want to learn at the advanced level).
----------
- SQL Server Stored Procedure
- Encrypt SQL Stored Procedure
- Store the Output of stored procedure into table/temp table
- SQL Server Views
- SQL Server Output Clause
- SQL Server Merge
- SQL Server Pivot
- SQL Server Dynamic Pivot
- SQL Server Unpivot
- SQL Server ROLLUP
- SQL Server Cube
- SQL Server Grouping Sets
- SQL User Defined Functions
- SQL Server Table Type and Table Valued Parameters
- SQL Server Sequence
- SQL Server CTE (Common Table Expression)
- SQL Recursive CTE
- SQL Server Create Schema
- SQL Server Synonyms
- SQL Server Identify objects Dependencies
- SQL Server OFFSET FETCH Clause
- SQL Server Change Data Capture (CDC)
- SQL Server Temporal Table (System-Versioned Table)
- SQL Server Cursor
- SQL IDENT_CURRENT Function
- DROP IF EXISTS
###### SQL Server Control of flow Statement
- SQL WAITFOR
- Try..Catch
- While Loop
- IF..ELSE
- GOTO Statement
- RETURN
###### SQL Server JSON
- FOR JSON Clause
- JSON_QUERY
- JSON_VALUE
- JSON_MODIFY
###### SQL Server XML
- FOR XML
###### SQL Server SET Statement
- SQL Server SET XACT_ABORT
- SQL Server SET DATEFORMAT
- SQL Server SET IDENTITY_INSERT
- SQL Server SET NOCOUNT ON | OFF
- SQL Server SET ROWCOUNT
- SQL SET LANGUAGE
- SQL STATISTICS IO ON | OFF
###### SQL Server Indexes
- SQL Clustered Index
- Clustered Vs Non-Clustered Indexes
###### SQL Server Configuration Functions
- SQL Server @@version
- SQL Server @@spid
- SQL Server @@Language
- SQL Server @@servicename
- 
###### SQL Server Triggers
- SQL Server Triggers Overview
- DML Trigger
- After Trigger
- Instead Of Trigger
- DDL Trigger
- LogOn Triggers Trigger
- 
###### SQL Server Transactions 
- Transaction Concurrency: Dirty reads problem in concurrent transactions
- Transaction Concurrency: Lost update problem in concurrent transactions
- SQL RollBack Transaction
###### SQL Server Agent
- Job Scheduling in SQL Server
###### SQL Server System Stored Procedures
- SQL Server sp_rename
- SQL Server sp_help
- SQL Server sp_monitor
- SQL Server sp_executesql
- SQL Server Startup procedures Sp_Procoption
- SQL Server Sp_helptext
###### Read SQL Server Error logs
- xp_readerrorlog
###### SQL Server Database Mail Configurations
###### SQL Server Database Mail configuration
- Troubleshooting SQL Server Database mail failure
- Send a SQL Server Query result in text format using database e-mail
###### SQL Query Optimization and Performance check
- Identify Blocked Processes in SQL Server
###### Data Import/Export in Database
###### SQL Server Import .CSV file in Database
- Export data from SQL Server to an Excel file
- SQL Server Bulk Insert(BCP)
- Copy or Delete files from directory in SQL Server
###### SQL Server Collations
- View Collation information at Server, Database, and Column Level
- Change the column collation to case sensitive
###### SQL Server Metadata Functions
- PARSENAME
- OBJECT_ID
###### SQL Server Data Security
- Dynamic Data Masking in SQL Server
- Data discovery and classification
- Implementing a ROW_LEVEL security in SQL Server
- Column Level Encryption/Decryption Using SYMMETRIC Keys
- SQL Vulnerability Assessment
###### SQL Server Scripts Objects
- Generate database scripts with Schema and Data
- Script a table in SQL Server


> __Note__
> Serial No: 06

# Basic Structure of SQL Queries:
The fundamental structure of SQL queries includes three clauses that are select, from, and where clause. What we want in the final result relation is specified in the select clause. Which relations we need to access to get the result is specified in from clause. How the relation must be operated to get the result is specified in the where clause.

- **Select** 
	- Column Name
- **From** 
	- Table Name
- **Where**
	- Condition
- **Group By** 
- **Having** 
- **Order By**
###### Example:
```
Select ID, COUNT(Quantity) from tblProductDetails
Where Quantity=1
Group By ID
Having COUNT(Quantity) =1
Order By ID DESC
```
###### Basic example of SQL
![SQL_CHEATSHEET](https://user-images.githubusercontent.com/110928130/184686403-0c740700-51ab-430b-9047-cb1755dc1436.jpg)

> __Note__
> Serial No: 07


# The most useful website for SQL and Others
- https://www.w3schools.com/sql/sql_intro.asp
- https://www.w3resource.com/sql-exercises/
- https://sqlskull.com/2020/03/15/sql-server-lead-function/
- https://devsonket.com/
- https://blog.sqlauthority.com/?s=dynamic+pivot


![MY_FAVORITE_FREE_LEARNING_RESOURCES](https://user-images.githubusercontent.com/110928130/184687321-08948d09-1bc1-41c3-a8c5-0b005126d142.jpg)



###### You Can Download Some Book From Here
- https://reconshell.com/top-sql-books-for-beginner-and-professional/
- https://www.db-book.com/db6/practice-exer-dir/index.html

###### TOP-70 MOST IMPORTANT SQL QUERIES IN 2022
- https://bytescout.com/blog/20-important-sql-queries.html?utm_referer=https%3A%2F%2Fwww.google.com%2F#35
###### Join over 16 million developers in solving code challenges on (Best Practice Site for SQL)
- https://www.hackerrank.com/domains/sql

> __Note__
> Serial No: 08

# Date Type

- https://www.w3schools.com/sql/sql_datatypes.asp
- https://www.sqlshack.com/learn-sql-sql-data-types/

## The Model
Before doing anything else, we’ll take one quick look at the model we’re using in this series.
![image](https://user-images.githubusercontent.com/110928130/186480644-01dd51d8-5d61-404f-b460-2a332c5405f2.png)

- So, let’s quickly review textual data types first. In the table below, you’ll find Transact-SQL string/textual data types with short descriptions.
![image](https://user-images.githubusercontent.com/110928130/186481012-45174bb7-fbcc-4226-9f04-2f2789fb0870.png)

###### Numeric Data Types
![image](https://user-images.githubusercontent.com/110928130/186481194-add50e09-d8bb-437c-a4e5-a757fdbf8d4a.png)
###### Date & Time
![image](https://user-images.githubusercontent.com/110928130/186481252-9a3281e4-072e-4b60-b3cc-c7975546189a.png)

![image](https://user-images.githubusercontent.com/110928130/186481301-ddcaab3b-5ca3-4354-ba77-852bf6345383.png)




- https://www.youtube.com/watch?v=l20gpdb4kXs
![image](https://user-images.githubusercontent.com/110928130/186830901-e4fb648c-045f-461d-bde7-c52f19895f9d.png)
