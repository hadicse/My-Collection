
![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Serial No: 01`



# Introduction to SQL
###### What is SQL?
- SQL stands for Structured Query Language
- SQL lets you access and manipulate databases
- SQL became a standard of the American National Standards Institute (ANSI) in 1986, and of the International Organization for Standardization (ISO) in 1987


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


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Serial No: 02`




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

![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Serial No: 03`



# SQL Advanced Concepts (These are required if you want to learn at the advanced level).
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

###### SQL Server Triggers
- SQL Server Triggers Overview
- DML Trigger
- After Trigger
- Instead Of Trigger
- DDL Trigger
- LogOn Triggers Trigger

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


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Serial No: 04`



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

![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Serial No: 05`




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

![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Serial No: 06`



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


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Serial No: 07`

# কী ফিল্ড (Key) – প্রাইমারি কী, কম্পোজিট প্রাইমারি কী, ফরেন কী
- কী ফিল্ড
- প্রাইমারি কী
- কম্পোজিট প্রাইমারি কী
- ফরেন কী
- প্রাইমারি কী এবং ফরেন কী এর মধ্যে পার্থক্য

```
যে ফিল্ডের উপর ভিত্তি করে ডেটাবেজের ফিল্ডের তথ্যাবলি / রেকর্ড শনাক্ত , অনুসন্ধান , সম্পর্ক স্থাপন ইত্যাদি কাজ করা হয় তাকে
কী বা কী – ফিল্ড (Key) বলা হয় । এক বা একাধিক অবস্থা বর্ণনা করার জন্য কী ফিল্ড ব্যবহার করা হয়। একটি উদাহরণ দেয়া যাকঃ
” কোন ক্লাশে ১০ জন ছাত্র আছে, আর তাদের সবারই আলাদা আলাদা রোল নম্বর আছে। 
একটি ডেটাবেজ এ ঐসব ছাত্রদের তথ্য দেয়া আছে। সেখান থেকে আলাদা আলাদা তথ্য খুজে বের করার জন্য তাদের রোল নম্বরের ভিত্তিতে খুজলেই হবে। 
তো ঐ ডেটাবেজে রোল নম্বরকে আমরা কী ফিল্ড বা কী বলতে পারি। “
কী ফিল্ডের সাহায্যে দুই বা ততোধিক ফাইলের মধ্যে সম্পর্ক স্থাপন বা রেকর্ড সনাক্ত ছাড়াও বিভিন্ন কাজ করা যায়। কী ফিল্ড প্রধানত তিন (৩) প্রকারঃ

প্রাইমারি কী (Primary Key)
কম্পোজিট প্রাইমারি কী (Composite Primary Key)
ফরেন কী (Foreign Key)
```


# প্রাইমারি কী (Primary Key)
```
যে ফিল্ড কোন একটি রেকর্ডকে অদ্বিতীয়ভাবে (Unique) সনাক্ত করে তাকে প্রাইমারি কী বলে। অর্থাৎ, ডেটা টেবিলের যে 
ফিল্ডের মানসমূহ দ্বারা একটি রেকর্ডকে অন্যান্য রেকর্ড থেকে সম্পূর্ণরূপে আলাদা করা যায় সেই ফিল্ডকে প্রাইমারি কী বলা হয়।
এ জাতীয় ফিল্ডের  প্রতিটি ডেটা ভিন্ন হতে হয় অর্থাৎ কোন ডুপ্লিকেট ডেটা থাকতে পারে না। কোন ফাইলে সাধারণত এক বা
একাধিক ফিল্ড থাকে । এই ফিল্ডগুলোর মধ্যে কমপক্ষে একটি ফিল্ড থাকবে যার ডেটাগুলো অদ্বিতীয়।
উদাহরনঃ নিচের টেবিলটিতে একটি ক্লাসের ছাত্রদের রোল, নাম, প্রাপ্ত নম্বর দেখানো হয়েছে। এখানে প্রতিটি ছাত্রের রোল অদ্বিতীয়। 
এই ফিল্ডের সাহায্যেই একাধিক ফাইলের মধ্যে সম্পর্ক স্থাপন সম্ভব। তাই এটিই (Roll No.) হলো প্রাইমারি কী (Primary Key)।

```


# কম্পোজিট প্রাইমারি কী (Composite Primary Key)
```
অনেক ক্ষেত্রে কোন টেবিলে সুনির্দিষ্ট কোন প্রাইমারি কী নাও থাকতে পারে । 
এক্ষেত্রে দু’টি ফিল্ডের সমন্বয়ে প্রাইমারি কী গঠন করা হয়ে থাকে যার সাহায্যে ঐ টেবিলের যে কোন রেকর্ডকে অদ্বিতীয়ভাবে (Unique) সনাক্ত করা যায় ।
তাদেরকে বলা হবে কম্পোজিট প্রাইমারি কী । এ প্রাইমারি কী – গুলোর একটিকে প্রাথমিক কী বিবেচনা করে বাকিগুলোকে বলা হবে অল্টারনেট কী ।
উদাহরনঃ নিচের টেবিলটিতে একটি স্কুলের ডেটাবেজে সব শ্রেণির ছাত্রের নাম, রোল, ক্লাসের নাম দেয়া আছে। এখান থেকে 
আমরা যদি কোনো একজন ছাত্রের তথ্য খুজতে চাই তবে কীভাবে করবো? এখানে তো, রোল নম্বর ধরে খুজতে গেলে বিভিন্ন ক্লাসে 
একই রোল নম্বর আছে, আবার নামও একই হতে পারে। তাই যদি আমরা প্রথমে রোল সিলেক্ট করি এবং পরে কোন ক্লাসে খুজবো সেটা 
সিলেক্ট করে নিই তবে সহজেই তথ্য বের করতে পারবো। তাই এই টেবিলটি তে Roll NO. এবং Class মিলে তৈরি হয়েছে কম্পোজিট প্রাইমারি কী ।
```
![image](https://user-images.githubusercontent.com/110928130/186972792-0ca3a556-e17a-4408-ad3b-52e9f03de4f6.png)

# ফরেন কী (Foreign Key)
```
একটি টেবিলের প্রাইমারি কী অন্য ডেটা টেবিলে সাধারণ কী হিসাবে ব্যবহৃত হয় তাহলে প্রথম ফাইলের / 
টেবিলের প্রাইমারি কী – কে দ্বিতীয় ফাইলের / টেবিলের জন্য ফরেন কী বলা হয় ।
এটি সাধারনত হয় রিলেশনাল ডেটাবেজের ক্ষেত্রে । ফরেন কীর সাহায্যে একটি টেবিলের সাথে অন্য টেবিলের সম্পর্ক স্থাপন করা হয় ।
উদাহরনঃ নিচের প্রথম টেবিলটিতে প্রাইমারি কী হলো product ID এবং দ্বিতীয় টেবিলটিতে product ID একটি
সাধারন কী হিসেবে ব্যবহার করা হয়েছে । প্রথম টেবিল এ প্রোডাক্ট লিস্ট রয়েছে । 
আর ২য় টিতে প্রোডাক্ট বিক্রির তালিকা রয়েছে যা Product ID এর দ্বারা
রিলেশন করা যায়। দ্বিতীয় টেবিলে প্রাইমারি কী হলো invoice ID ।
সুতরাং, product ID হলো ফরেন কী ।
```
![image](https://user-images.githubusercontent.com/110928130/186972844-52223c5c-bcb9-40a7-94e1-d416e3e341ae.png)

# প্রাইমারি কী এবং ফরেন কী এর মধ্যে পার্থক্য (Difference between Primary Key and Foreign Key)
![image](https://user-images.githubusercontent.com/110928130/186973455-f8963b9a-3a1f-4e71-b9d6-24322b321a5f.png)

