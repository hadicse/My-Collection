# **Welcome to SQL Server Collection's of Hadiuzzaman**
- Here I will collect all types of complex queries.
- which was used for my work purposes.

## My SQL GURU

```
- Khan Mohammad Sohel Zaman Bhai
- Nazir Ali Bhai
- Shahadat Bhai
- Forhad Bhai
- Rubel Bhai
- Rahat Bhai
- Omar Faruk Shamim Bhai
- Ahsan Kabir
```

## My First Qyery
```
Select * from tblProduct
Learn from Nazir Ali Bhai (Ex Southtech Colleague)
```
# Introduction to SQL
###### What is SQL?
- SQL stands for Structured Query Language
- SQL lets you access and manipulate databases
- SQL became a standard of the American National Standards Institute (ANSI) in 1986, and of the International Organization for Standardization (ISO) in 1987
- 
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



# How to Insert Results of Stored Procedure into a Temporary Table
```
	-- Create a Stored Procedure
	CREATE PROCEDURE TestSP
	AS
	SELECT * from TestDB.dbo.tblSeq
	GO
	-- Execute Stored Procedure
	EXEC TestSP
	GO
	
	-- Enable Ad Hoc Distributed Queries
	sp_configure 'Show Advanced Options', 1
	GO
	RECONFIGURE
	GO
	sp_configure 'Ad Hoc Distributed Queries', 1
	GO
	RECONFIGURE
	GO


	-- Insert into Temp Table
	SELECT * INTO #TempTable
	FROM OPENROWSET('SQLNCLI', 'Server=MY_LOVE\SQLSERVER2008R2;Trusted_Connection=yes;','EXEC TestSP')
	GO
	-- Select Data from Temp Table
	SELECT * FROM #TempTable
	GO
```
![SQL-0101s](https://user-images.githubusercontent.com/110928130/185967586-e37d8113-aca3-4ecf-8b68-4ad9875bcb13.jpg)



## Find empty tables in SQL Server database
```
Select	schema_name(tab.schema_id) + '.' + tab.name as [table]
		From sys.tables tab
		Inner join sys.partitions part
		On tab.object_id = part.object_id

Where		part.index_id IN (1, 0)	-- 0 - table without PK, 1 table with PK
Group By	schema_name(tab.schema_id) + '.' + tab.name
Having		sum(part.rows) = 0
Order By	[table]
```

# SQL SERVER ROLLUP clause is used to display subtotals and grand totals in the result set. It is always used with GROUP BY CLAUSE.
```
SELECT COALESCE(Region ,'GRAND TOTAL' ) AS Region, SUM(Quantity) AS TotalQty
FROM dbo.ItemQty 
GROUP BY ROLLUP(Region) 
```
![SQL SERVER ROLLUP](https://user-images.githubusercontent.com/110928130/184917159-5c2cc363-9ba8-492e-abef-f71c269b231c.jpg)

# To display the total purchased quantities by region and items with SubTotal and GrandTotal 
```
SELECT COALESCE(Region ,'GRAND TOTAL') AS Region,
COALESCE(Item ,'TOTAL') AS Item, SUM(Quantity) AS TotalQty
FROM dbo.ItemQty
GROUP BY ROLLUP(Region, Item
```

![SubTotal](https://user-images.githubusercontent.com/110928130/184917729-0ca75cfe-8f67-4b28-9e6e-29914fe96c41.jpg)


# Row to Colomn SQL Pivot
```
SELECT   ShopCOde, Pro_Code, 1 as AreaCode_1, 2 as AreaCode_2 FROM   [dbo].[tblPvot] 
PIVOT (SUM(Stock) FOR [AreaCode] IN ([1], [2])) AS P

Select ShopCode,Pro_Code,AreaCode,Stock from tblPvot

```
# SQL UnPivot
https://sqlskull.com/2020/06/06/sql-server-unpivot/

# Disable Relation 
```
-- Disable the constraints on a table called tableName:
ALTER TABLE tableName NOCHECK CONSTRAINT ALL

-- Re-enable the constraints on a table called tableName:
ALTER TABLE tableName WITH CHECK CHECK CONSTRAINT ALL
```



# Remove all Space from string in SQL Server Using SQL Replace
```
Select ColumnA, ColumnB from tblTrims
   
SELECT REPLACE(ColumnA,' ', '') as WithOutSpace , REPLACE(ColumnB,' ', '') as WithOutSpace  from tblTrims
   
```

![RemoveSpace](https://user-images.githubusercontent.com/110928130/185178778-e77d4714-a561-4a41-8998-892c0bea9d82.jpg)

# How to find percentage in SQL
```
Select ((300/100)*10) as Percentage

--Result
	Percentage
	30

```

# RESTORE DATABASE DBNAME
```
From Disk='G:\25-06-2020\Backup\Backup.bak'
WITH	Move 'POS_data'		to 'G:\POS_AUDIT.mdf',
		Move 'POS_data2'	to 'G:\POS_AUDIT_2.mdf',
		Move 'POS_data1'	to 'G:\POS_AUDIT_1.mdf',
		Move 'POS_log'		to 'G:\POS_AUDIT_Log.ldf',
		Password='abc'
		--Password='',
		--Password=''
```


# SQL Server CREATE SCHEMA
```
CREATE SCHEMA customer_services;
GO
Select * from sys.schemas
```
- **Example**

![GoogleImage](https://www.sqlservertutorial.net/wp-content/uploads/SQL-Server-CREATE-SCHEMA.png)




# SQL User disable or user sleep 
```
Select Session_id
From Sys.dm.exec_session where login_name='prince'
```

# To get total number of columns in a table in sql
```
SELECT COLUMN_NAME FROM INFORMATION_SCHEMA.Columns where TABLE_NAME = 'YourTableName'
```
# Current Month Last Last Date and To get the last day of the previous month:
```
--Current Month Last Last Date
DECLARE @test DATETIME
SET @test = GETDATE()  -- or any other date
SELECT DATEADD(month, ((YEAR(@test) - 1900) * 12) + MONTH(@test), -1)

--To get the last day of the previous month:
SELECT DATEADD(DAY, -(DAY(GETDATE())), GETDATE())

```

# Create Indexing or index
```
--For Indexing or index
Create INDEX IX_SalesReceiptNO
ON [dbo].[tblSalesTransactionDetails]
([ReceiptNo] ASC)

###### 2 (two) Cloumn Indexing or index
--For Indexing or index
Create INDEX IX_SalesReceiptNO
ON [dbo].[tblSalesTransactionDetails]
([ReceiptNo] ASC)
or
Create INDEX IX_SalesReceiptNO
ON [dbo].[tblSalesTransactionDetails]
(ReceiptNo ASC, Barcode asc)

```


# Database Repair or DBCC CheckDB
```	
--1st Step  Delete All Temp Table
USE [master]

Alter Database [DBNAME] Set Single_USer 
OR
Alter Database [DBNAME] Set Single_USer with no_Wait
Go
		Select * from  sys.sysprocesses where dbid=DB_ID('DBNAME')
		Kill 52 --(request_Session)

DBCC CheckDB ('DBNAME', Repair_Rebuild)

Alter Database [DBNAME] Set Multi_USer

DBCC CHECKDB('DBNAME')

--2nd Step Table Check
	DBCC CHECKTable('tblProduct')
	DBCC CHECKTable('tblProductdetails')
	-- Need All Table al Slow Tables

--3rd Step Log File or may be Data Shrink

--4th Step Indexing  by Start a Task Weserd
```

# CAST Date
```
CAST(ROUND(SUM(Rd.UnitPrice), 2) as numeric (36,2)) as TotalSale 
```
# Round
```
Select ReceiptNo, CAST(ROUND(ReceivedAmount,2) as Numeric (36,2) as TotalAmount
Select SUM(CAST(ROUND(ColumnName+ColumnName,2) as Numeric (36,2))) as TotalAmount
```

# SQL query to display the LEN and First 3 characters
```
SUBSTRING( string, start_position, length );
SELECT SUBSTRING( column_name, 1, 3 ) FROM table_name;

--Main Data
	IM-APON-DEC21-1
--Result
	--INV
```
# Len Reducer
```
Update tblCustomerInfo set Name=RIGHT(Name, LEN(Name)-1)
```

# Case Wen
```
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    WHEN conditionN THEN resultN
    ELSE result
END

SELECT OrderID, Quantity,
CASE
    WHEN Quantity > 30 THEN 'The quantity is greater than 30'
    WHEN Quantity = 30 THEN 'The quantity is 30'
    ELSE 'The quantity is under 30'
END AS QuantityText
FROM OrderDetails
```


# Having

```
SELECT column_name(s) FROM table_name
WHERE condition
GROUP BY column_name(s)
HAVING condition
ORDER BY column_name(s)
----------------------------
SELECT COUNT(CustomerID), Country FROM Customers
GROUP BY Country
HAVING COUNT(CustomerID) > 5
ORDER BY COUNT(CustomerID) DESC;
```

# IIF Function
```
SELECT IIF(3<2, 5, 10)
--Result as 10
```

# PROCEDURE
```
CREATE PROCEDURE procedure_name
AS
sql_statement
GO

EXEC procedure_name
```

# SQL Data Types
- https://www.w3schools.com/sql/sql_datatypes.asp


# UNION ALL
```
SELECT City, Name FROM Customers
UNION ALL
SELECT City,Name FROM Suppliers
ORDER BY City

--Result
City	Name
A	Hadi
B	Sumon
C	NULL
D	NULL
X	Siam
Y	Sami
Z	NULL

```

# SQL BACKUP DATABASE Statement
```
BACKUP DATABASE testDB
TO DISK = 'D:\backups\testDB.bak'
```

# SQL Server Functions
###### Click here for details of Functions
- https://docs.microsoft.com/en-us/sql/t-sql/functions/functions?view=sql-server-ver16
- https://www.w3schools.com/sql/sql_ref_sqlserver.asp
- https://www.educba.com/sql-string-functions/?source=leftnav

# Update with Inner Join
```
UPDATE C
SET IsActive = 1
FROM tblCustomer C
JOIN tblSales S ON C.CustomerID = S.CustomerID
WHERE C.CustomerID=101111101
```

# How To Select only Substring
```
SELECT  substring('abcde', 2, 3)
```

# SQL WHILE loop with simple examples
- https://www.sqlshack.com/sql-while-loop-with-simple-examples/

# SQL Print
```
DECLARE @Msg VARCHAR(300)= 'My Name is Rajendra Gupta';
PRINT @Msg

or 

DECLARE @Msg VARCHAR(300)
Set @Msg = 'My Name is Rajendra Gupta';
PRINT @Msg
```

# Overview of SQL RANK functions or Row Counts
###### Click Here For Details of RANK functions
- https://www.sqlshack.com/overview-of-sql-rank-functions/
```
SELECT Studentname, 
       Subject, 
       Marks, 
       RANK() OVER(PARTITION BY Studentname ORDER BY Marks DESC) Rank
FROM ExamResult
ORDER BY Studentname, 
         Rank;
```
###### Example of RANK() SQL RANK Function/PARTITION 
![GoogleImage](https://www.sqlshack.com/wp-content/uploads/2019/07/ranksql-rank-function.png) 


# Different ways to SQL delete duplicate rows from a SQL Table
-https://www.sqlshack.com/different-ways-to-sql-delete-duplicate-rows-from-a-sql-table/

# How to Delete SQL User History
- Click on Login and Select the User which you need to Delete.
- Then you need to press the delete button.

![GoogleImage](https://github.com/hadicse/My-Collection/blob/main/Source%20Image/Delete%20SQL%20User%20Login%20History.jpg?raw=true) 

# Creating a Relationship Between Two Tables Using Query
```
Create Database POSDB

Use POSDB

CREATE TABLE tblProduct(
ProductCode int PRIMARY KEY NOT NULL,
ProductName Varchar (50),
CosePrice Numeric (8,2))

CREATE TABLE tblProductDetails(
ID INT PRIMARY KEY NOT NULL,
ProductCode INT FOREIGN KEY REFERENCES tblProduct (ProductCode),
Item Varchar (50),
Quantity Numeric (8,2))
```
###### You can watch this video (Creating a Relationship Between Two Tables).
https://user-images.githubusercontent.com/110928130/184592294-c79c9934-b5d6-4b85-a369-ba201f58a33f.mp4



# Get Only numeric or Only Varchar or Mixed (Numeric & Varchar Mixed) from a column
###### Onlu Numeric
```
SELECT ITEM FROM tblProductDetails WHERE ITEM not like '%[^0-9]%' --and ITEM != ''
```

###### Onlu Varchar
```
SELECT ITEM FROM tblProductDetails WHERE ITEM not like '%[^A-Z]%' --and ITEM != ''
```

###### Only Mixed
```
SELECT ITEM FROM tblProductDetails WHERE ITEM   like '%[^0-9]%[^A-Z]%' or item like  '%[0-9]%[A-Z]%'
```

# Find Missing Identity Values / Missing Sequence
```
--Main Table
Select ID	,Name from tblSeq

--For Get Seq.
SELECT Seq FROM (SELECT ROW_NUMBER() OVER (ORDER BY c1.column_id) Seq
FROM sys.columns c1
CROSS JOIN sys.columns c2) SequenceTable
LEFT JOIN tblSeq ON tblSeq.ID = SequenceTable.Seq
WHERE tblSeq.ID IS NULL AND Seq < (SELECT MAX(ID) FROM tblSeq)
```
![image](https://user-images.githubusercontent.com/110928130/185956825-0bfba03b-b149-40c9-bd10-498d35ead801.png)

# Find Date Month year 
```
--Find Date Month year 
Select FDate, FMonth, FYear from #FDateTimeYear

CREATE TABLE #FDateTimeYear
( [FDate] [varchar](2) NOT NULL,
[FMonth] [varchar](3) NULL,
[FYear] [varchar](4) NULL )

Insert Into #FDateTimeYear
SELECT DATENAME(D,GETDATE()) 'FDate',
Convert(char(3), GetDate(), 0) as FMonth , DATENAME(YEAR,GETDATE()) 'FYear'

Select FDate + '-' + FMonth + '-' as PDateMonth,Fyear into #FromDate From #FDateTimeYear
Select PDateMonth+FYear from #FromDate
Select PDateMonth+PYear from #Todate

Select FDate + '-' + FMonth + '-' as PDateMonth,
Case When Fyear >0 Then Fyear-1 END AS PYear
Into #Todate From #FDateTimeYear

# DateMonthYear
--DateMonthYear
SELECT CONVERT(VARCHAR(19), SYSDATETIME(), 120)
SELECT DATEADD(dd, -1, DATEADD(yy, DATEDIFF(yy, 0, GETDATE()), 0))
```

# Upper and Lower Font Style in SQL
###### how to display space first letter capital in sql server
###### After Space Letter Capital First Letter in capital, Upper and Lower font style
- https://www.sqlshack.com/overview-of-sql-lower-and-sql-upper-functions/#:~:text=We%20use%20SQL%20UPPER%20function,all%20characters%20into%20capital%20letters.

# Auto Row Count Row Number
```
--Auto Row Count Row Number
Select ROW_NUMBER () Over(Order by UserID ) as SLN, UserID from tblUsers
```


# Varchar Date Month Year
```
--Varchar Date Month Year
SELECT CONVERT(VARCHAR(19), (SELECT DAY(GETDATE())), 103) as DAY 
SELECT CONVERT(VARCHAR(19), (SELECT UPPER(Convert(char(3), GetDate(), 0))), 103) as MONTH 
SELECT CONVERT(VARCHAR(19), (SELECT YEAR(GETDATE())), 103) as YEAR
Create Table #DayMonthYear
(Day varchar (20), Month varchar (20), Year varchar (20), LastYear varchar (20))
Insert Into #DayMonthYear
SELECT CONVERT(VARCHAR(19), (SELECT DAY(GETDATE())), 103) as DAY ,
CONVERT(VARCHAR(19), (SELECT UPPER(Convert(char(3), GetDate(), 0))), 103) as MONTH ,
CONVERT(VARCHAR(19), (SELECT YEAR(GETDATE())), 103) as YEAR,
Year(Getdate())- 1 as LastYear
--------------------------------------------------------------------------------------------
Select Day + '-' + Month + '-' + Year as FromDate into #FromDate from #DayMonthYear
Select Day + '-' + Month + '-' + LastYear as ToDate Into #ToDate from #DayMonthYear

Drop table #FromDate
Drop table #DayMonthYear
```


# IF EXISTS

```
Declare @Return as Varchar (MAX)
	IF EXISTS (Select * from tblUsers where UserID='ADMN2')
	
		Begin
		Select @Return		=	'FOUND'
		END
			ELSE
			BEGIN
			Select @Return	=	'NotFound'	--IF not Found Then Insert LastDateOFPreviousMonth
			END
			
			Select @Return as Result   --Forhad Bhai KKHO
---------------------------------------------------------------------------------------------------------
IF EXISTS (Select * from #Result where Prod_CodeInsert_OK_To_tblRequisition like '01%')

BEGIN
        PRINT 'Found'
END
ELSE
		BEGIN
		PRINT	'NotFound'	--IF not Found Then Inser LastDateOFPreviousMonth
		END
```


# Bulk Insert From Excel to SQL Using Query
###### Before Bulk Insert Need to Install and Run the Below Query
```
---------------------------
--SQL Ad Hoc Access to OLE DB
EXEC sp_configure 'show advanced options', 1
RECONFIGURE
GO
EXEC sp_configure 'ad hoc distributed queries', 1
RECONFIGURE
GO
-----------------------------------------------------------------------------
"C:\Users\abluhadi\Documents\Downloade\AccessDatabaseEngine_x64.exe" /passive
https://www.microsoft.com/en-us/download/confirmation.aspx?id=13255
```
###### Bulk Insert From Excel to SQL Using Query
```
--Bulk Insert From Excel to SQL Using Query
Create table tblemployees
(ID int primary key identity(1,1),
Name varchar (500),
Type varchar (500),
F_Name varchar (500),
M_Name varchar (500),
S_Name varchar (500),
District varchar (500),
Country varchar (500),
Thana varchar (500),
Roll varchar (500),
Salary decimal)

Select * from tblemployees

BULK INSERT tblemployees
FROM 'C:\DATA\PERSONAL\TESTWORK\TBLEMPLOYEES.CSV'
WITH	(ROWTERMINATOR ='\n',
		FIELDTERMINATOR=',',
		FIRSTROW=2		)

Delete from tblemployees
Drop table tblemployees

--Bulk Insert From Excel to SQL Using Query

--OR you can use

SELECT * FROM OPENROWSET(
'Microsoft.ACE.OLEDB.12.0'
,'Excel 12.0;Database=F:\Backup\SQLAuthority.xlsx;HDR=YES'
,'SELECT * FROM [Sheet2$]')

```


# Query Execute or Run from Table Data
```
--Query Execute/Run from Table Data

-Create Table
CREATE TABLE [dbo].[tblNulltbl](
	[ID] [varchar](500) NULL,
	[Name] [varchar](50) NULL
) ON [PRIMARY]

--Insert Date or Query into Table
Insert Into tblNulltbl
Values ('Select 5+5', '1')
Delete from tblNulltbl



DECLARE @Queries TABLE (ID INT IDENTITY(1,1),SQLScript VARCHAR(MAX))
DECLARE @STR_QUERY VARCHAR(MAX);
DECLARE @StartLoop INT
DECLARE @EndLoop INT


INSERT INTO @Queries
SELECT ID as QueryResult
FROM tblNulltbl Where Name='1'

SELECT @EndLoop = MAX(ID), @StartLoop = MIN(ID)
FROM @Queries

WHILE @StartLoop < = @EndLoop
BEGIN
    SELECT @STR_QUERY = SQLScript 
  FROM @Queries
    WHERE ID = @StartLoop
	
    EXEC (@STR_QUERY)

    SET @StartLoop = @StartLoop + 1
END
```



# Quickest Way to Run the Same Query Multiple Times in SQL Server

```
--Quickest Way to Run the Same Query Multiple Times in SQL Server

CREATE TABLE LoopTest
(    LoopTestId uniqueidentifier NOT NULL DEFAULT NEWID(),
    InsertDate datetime2(7) NOT NULL DEFAULT GETDATE() );
GO
INSERT LoopTest (LoopTestId, InsertDate)
VALUES (DEFAULT, DEFAULT);
GO 20
-- GO 20 means This will run 20 times.
Select * from LoopTest
```

# Multiple Date & Time Formate 
##### You can try by using 1,2,3,4,5,6,7,... 103. The following is just one example.
##### Click on below link for details

| SerialNo | Query | Format | Sample |
| --- | --- | --- | --- |
| 01 | select convert(varchar, getdate(), 1) | mm/dd/yy | 12/30/06 |
| 02 | select convert(varchar, getdate(), 2) | yy.mm.dd | 06.12.30 |
| 03 | select convert(varchar, getdate(), 3) | dd/mm/yy | 30/12/06 |
| 04 | select convert(varchar, getdate(), 4) | dd.mm.yy | 30.12.06 |
| 05| select convert(varchar, getdate(), 5) | dd-mm-yy | 39081 |

- https://www.sqlshack.com/sql-convert-date-functions-and-formats/

###### Convert Date time to Number
```
select replace(convert(varchar, getdate(),101),'/','')		
select replace(convert(varchar, getdate(),101),'/','') + replace(convert(varchar, getdate(),108),':','')		
```


# Plan_Cursor and FETCH
```
DECLARE @id varchar(50) ,@maxDayQty numeric(14,2), @startDate numeric(14), @raminingQty numeric(14)
DECLARE @tempDate numeric(14)

DECLARE plan_cursor CURSOR FOR
SELECT ID, MaxDayQty, StartDate, RemainingQty FROM tblPlan where RemainingQty > 0 --AND  ID = '103'
order by ID;

OPEN plan_cursor

FETCH NEXT FROM plan_cursor
INTO @id,@maxDayQty,@startDate,@raminingQty

SET @tempDate = @startDate

WHILE @@FETCH_STATUS = 0
BEGIN
	
	WHILE (@raminingQty >0)
		BEGIN
				IF((@raminingQty - @maxDayQty) > 0)
					BEGIN
						Insert into tblDateWiseQuantity
						Select @id AS ID ,@tempDate as ProductionDate, @maxDayQty AS MaxDayQty 

						update tblPlan set RemainingQty = RemainingQty - @maxDayQty,EndDate = @tempDate
						where ID = @id
					END
				ELSE
					BEGIN
						Insert into tblDateWiseQuantity
						Select @id AS ID ,@tempDate as ProductionDate, @raminingQty AS MaxDayQty
						update tblPlan set RemainingQty = 0,EndDate = @tempDate  
						where ID = @id
					END

				SET @tempDate = @tempDate + 1;
				SET @raminingQty = (select RemainingQty from tblPlan where ID = @id)

		END
	

    FETCH NEXT FROM plan_cursor
	INTO @id,@maxDayQty,@startDate,@raminingQty
	SET @tempDate = @startDate
END
CLOSE plan_cursor;
DEALLOCATE plan_cursor;
```




# Script to create dynamic PIVOT queries in SQL Server
```
--If You Ned to Drop or Delete
--Delete  tblStudentGrades
--Drop table tblStudentGrades
--Drop PROCEDURE dbo.usp_Dyna_Pivot


--CREATE PROCEDURE
CREATE PROCEDURE dbo.usp_Dyna_Pivot (
   @unknownValsCol NVARCHAR (100),
   @objNameToPivot NVARCHAR (100),
   @aggFuncOfPivot NVARCHAR (3),
   @aggColOfPivot NVARCHAR (100),
   @leadColPivot NVARCHAR (100))
AS
BEGIN
   DECLARE @columns NVARCHAR (2000),
      @tsql NVARCHAR (2000)
   DECLARE @distinctVals TABLE (val NVARCHAR (50))

   SET NOCOUNT ON
   SET @columns = N'';
   SET @tsql = CONCAT ('SELECT DISTINCT ', @unknownValsCol,' FROM ',@objNameToPivot)
   INSERT @distinctVals EXEC (@tsql)

   SELECT @columns += CONCAT ('[', Val,']',',')
   FROM @distinctVals

   SET @columns = LEFT (@columns, LEN (@columns) - 1)
   SET @tsql = CONCAT ( 'SELECT ', @leadColPivot,   ',', @columns,' FROM ',' ( SELECT ',@leadColPivot,',',
         @aggColOfPivot,',',   @unknownValsCol,   ' FROM ',   @objNameToPivot,   ') as t ',
         ' PIVOT (', @aggFuncOfPivot,   '(', @aggColOfPivot,   ')',' FOR ',   @unknownValsCol,
         '   IN (', @columns,')) as pvt ',' ORDER BY ',   @leadColPivot)
   EXEC (@tsql)
   SET NOCOUNT OFF
END
GO



--CREATE TABLE
CREATE TABLE [dbo].[tblStudentGrades]
   ([studentName] [varchar](40) NULL, [courseName] [varchar](40) NULL, [year_study] [int] NULL, 
    [Grade] [int] NULL) ON [PRIMARY] 
GO 

--Date Insert
INSERT [dbo].[tblStudentGrades] ([studentName], [courseName], [year_study], [grade]) VALUES (N'adir s', N'oracle', 2017, 90) 
INSERT [dbo].[tblStudentGrades] ([studentName], [courseName], [year_study], [grade]) VALUES (N'anat a', N'oracle', 2018, 96) 
INSERT [dbo].[tblStudentGrades] ([studentName], [courseName], [year_study], [grade]) VALUES (N'anat a', N'oracle', 2019, 100) 
INSERT [dbo].[tblStudentGrades] ([studentName], [courseName], [year_study], [grade]) VALUES (N'ofir r ', N'oracle', 2017, 95) 
INSERT [dbo].[tblStudentGrades] ([studentName], [courseName], [year_study], [grade]) VALUES (N'ofir r', N'oracle', 2018, 96) 
INSERT [dbo].[tblStudentGrades] ([studentName], [courseName], [year_study], [grade]) VALUES (N'ofir r', N'oracle', 2019, 100) 
INSERT [dbo].[tblStudentGrades] ([studentName], [courseName], [year_study], [grade]) VALUES (N'adir s', N'sql', 2017, 100) 
INSERT [dbo].[tblStudentGrades] ([studentName], [courseName], [year_study], [grade]) VALUES (N'adir s', N'sql', 2018, 100) 
INSERT [dbo].[tblStudentGrades] ([studentName], [courseName], [year_study], [grade]) VALUES (N'adir s', N'sql', 2019, 100) 
INSERT [dbo].[tblStudentGrades] ([studentName], [courseName], [year_study], [grade]) VALUES (N'anat a', N'sql', 2017, 99) 
INSERT [dbo].[tblStudentGrades] ([studentName], [courseName], [year_study], [grade]) VALUES (N'anat a', N'sql', 2018, 89) 
INSERT [dbo].[tblStudentGrades] ([studentName], [courseName], [year_study], [grade]) VALUES (N'anat a', N'sql', 2019, 90) 
INSERT [dbo].[tblStudentGrades] ([studentName], [courseName], [year_study], [grade]) VALUES (N'ofir r ', N'sql', 2017, 76) 
INSERT [dbo].[tblStudentGrades] ([studentName], [courseName], [year_study], [grade]) VALUES (N'ofir r', N'sql', 2018, 80) 
INSERT [dbo].[tblStudentGrades] ([studentName], [courseName], [year_study], [grade]) VALUES (N'ofir r', N'sql', 2019, 100) 

--------------------------------------------------------------------------------------------------------------------------------------------
--For Final Result
EXEC dbo.usp_Dyna_Pivot  
   @unknownValsCol  = 'year_study',			-- get list of unique values
   @objNameToPivot  = 'tblStudentGrades',	-- table that holds data
   @aggFuncOfPivot  = 'AVG',				-- type of operation to perform
   @aggColOfPivot   = 'grade',				-- column value for pivot operation
   @leadColPivot    = 'courseName'			-- order results by column
GO  
--------------------------------------------------------------------------------------------------------------------------------------------
```







































<!-- For Color Tex
```diff
-dsglhfg
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@

--For Hyperlink
- ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) `#f03c15`
---->
```






