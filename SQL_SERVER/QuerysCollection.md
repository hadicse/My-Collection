# **Welcome to SQL Server Collection's of Hadiuzzaman**
- Here I will collect all types of complex queries.
- which was used for my work purposes.


## My First Qyery
```
Select * from tblProduct
```


---------------------------------------------------------------------------------------------------------------------

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

# Using SQL Server CHOOSE() function for table column example

```
SELECT top 10 [NationalIDNumber]
,[JobTitle] ,[HireDate] ,
CHOOSE(MONTH([HireDate]),'January','February','March','April','May','June', 'July','August','September','October','November','December') As [HireMonth]
,[MaritalStatus]
 FROM [AdventureWorks].[HumanResources].[Employee]
  -------------------------------------------------
	SELECT CHOOSE(2, 'First', 'Second', 'Third') Result
-------------------------------------------------

	SELECT	Order_id, order_date, status,
			CHOOSE(status,'Pending', 'Processing', 'Rejected', 'Completed') AS order_status
	FROM	tblorders
	ORDER BY Order_date ASC

	Select * from tblorders
```
![image](https://user-images.githubusercontent.com/110928130/186479633-bee42a0e-0669-41ff-ab87-528fb5c1efff.png)

![image](https://user-images.githubusercontent.com/110928130/186477750-4d6b88bf-f707-4469-b23f-bcc156fcac71.png)


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

# Dynamic SQL Query
```
DECLARE 
    @sql NVARCHAR(MAX),
	@top NVARCHAR(MAX),
	@attributes NVARCHAR(MAX),
	@table NVARCHAR(MAX),
	@id NVARCHAR(MAX);
 
-- run query using parameters(s)
SET @top = ' TOP 3 ';
SET @attributes = ' * ';
SET @table = ' customer '
SET @id = N'0';
SET @sql = N'SELECT ' + @top + @attributes + N'FROM ' + @table + N' WHERE id > ' + @id;
SELECT @sql AS query;
EXEC sp_executesql @sql;
```
![image](https://user-images.githubusercontent.com/110928130/186487165-c7b41c6b-d6e3-498f-8b84-28a265c1e2d3.png)

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
- https://www.sqlshack.com/learn-sql-sql-data-types/
- 
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






