[SQL 56 Pages.pdf](https://github.com/hadicse/My-Collection/files/11514869/SQL.56.Pages.pdf)


# **Welcome to SQL Server Collection's of Hadiuzzaman**
- Here I will collect all types of complex queries.
- which was used for my work purposes.


## My First Query
```sql
Select * from tblProduct
```


---------------------------------------------------------------------------------------------------------------------
![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 01`


# How to Insert Results of Stored Procedure into a Temporary Table
```sql
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


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 02`


# Find Missing Identity Values / Missing Sequence
```sql
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


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 03`



# Overview of SQL RANK functions or Row Counts
###### Click Here For Details of RANK functions
- https://www.sqlshack.com/overview-of-sql-rank-functions/
```sql
	-- 1 column must contain at least one unique value. 
	SELECT Studentname, Subject, Marks, 
		   RANK() OVER(PARTITION BY Studentname ORDER BY Subject DESC) Rank
	FROM ExamResult
	ORDER BY Studentname, 
			 Rank;
```
###### Example of RANK() SQL RANK Function/PARTITION 
![image](https://user-images.githubusercontent.com/110928130/187938455-a9b478ec-0ac6-44e6-be4f-d1aad5256aa1.png)


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)

#  Example of RANK() SQL RANK Function/PARTITION / Serial Based on One Value or 2 Value 
```sql
	
Select TR.intTaxPricingId, TR.intTaxItemGroupId, numBasePrice,
RANK() OVER(PARTITION BY numBasePrice ORDER BY TR.intTaxPricingId DESC) RANK
From tax.tblTaxItemOutputTaxRate TR
Join  TAX.tax.tblTaxItemPriceSetupHeader SH on Sh.intTaxPricingId=TR.intTaxPricingId 
Where intAccountId=10 and TR.intTaxItemGroupId=1526
ORDER BY numBasePrice, RANK

```

![image](https://user-images.githubusercontent.com/110928130/216062339-3f7158e3-f0c3-466d-ba7d-7c8552201181.png)



`Topic No: 04`

# Different ways to SQL delete duplicate rows from a SQL Table
-https://www.sqlshack.com/different-ways-to-sql-delete-duplicate-rows-from-a-sql-table/

```sql
--If All Column Same The You Can Use this
	WITH CTE([Firstname],[Lastname], [Country], Duplicatecount)
	AS (SELECT [FirstName],[Lastname], [Country], 
			   ROW_NUMBER() OVER(PARTITION BY [Firstname], [Lastname], [Country]
			   ORDER BY [Country]) AS DuplicateCount
		FROM [Employee])
	SELECT * FROM CTE


```
![image](https://user-images.githubusercontent.com/110928130/187942489-26aea123-8e4a-4488-bf96-eff7875a76f6.png)



![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 05`

# All SQL Query With Example please click below: 
[SQL 56 Pages.pdf](https://github.com/hadicse/My-Collection/files/11514963/SQL.56.Pages.pdf)


# Copy or delete files from directory/local computer in SQL Server
```sql
--1st Step
SE master; 
GO

-- To allow advanced options to be changed.
EXECUTE sp_configure 'show advanced options', 1; 
GO 
-- To update the currently configured value for advanced options. 
RECONFIGURE; 
GO
```

```sql
--2nd Step
-- To enable the feature. 
EXEC sp_configure 'xp_cmdshell', 1; 
GO 
-- To update the currently configured value for this feature. 
RECONFIGURE;
```

```sql
--Final Step for Copy
--You Need to create SourceData Pathe and  TargetData Path
EXEC xp_cmdshell 
'copy E:\SourceData E:\TargetData';
```
![image](https://user-images.githubusercontent.com/110928130/186835537-348027ff-2e41-4fb0-bf66-df60d5591ca3.png)

```sql
--Delete Step
EXEC xp_cmdshell 
'del E:\TargetData\StudentInfo.txt'
```
![image](https://user-images.githubusercontent.com/110928130/186836048-5bd6363b-0a1c-4fdb-acbc-e08e0896c4c0.png)



![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 06`





# SQL Query to get the list of files in a folder in SQL
```sql
	USE master; 
GO

-- To allow advanced options to be changed.
EXECUTE sp_configure 'show advanced options', 1; 
GO 
-- To update the currently configured value for advanced options. 
RECONFIGURE; 
GO



-- To enable the feature. 
EXEC sp_configure 'xp_cmdshell', 1; 
GO 
-- To update the currently configured value for this feature. 
RECONFIGURE;


--For Find File List From Local Computer (Its Best)
			DECLARE @dirPath nvarchar(500) = 'D:\databasefile' 

			DECLARE @tblgetfileList TABLE
			(FileName nvarchar(500)
			,depth int
			,isFile int)

			INSERT INTO @tblgetfileList
			EXEC xp_DirTree @dirPath,1,1

			SELECT FileName from @tblgetfileList where isFile=1

--For Find File List From Local Computer
--OR Using Below Query


		CREATE TABLE tblgetfileList (excelFileName VARCHAR(100));

		INSERT INTO tblgetfileList

		EXEC xp_cmdshell 'dir /B "D:\databasefile"';

		select * from tblgetfileList

		


```

![image](https://user-images.githubusercontent.com/110928130/186836996-50c7a48a-969f-466e-bc10-03d7da4a93c8.png)


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 07`



# Using SQL Server CHOOSE() function for table column example

```sql
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


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 08`


# SQL GOTO Statement
```sql
Create  PROC Get_NumberEvenOrOdd
@Number INT
AS
------------------------------------------------------------------------------
IF @Number =1
GOTO One

IF @Number =2
GOTO Odd

ELSE
GOTO NotFound
------------------------------------------------------------------------------
One:
SELECT CAST(@Number as VARCHAR) + ' Number is One' AS Output
RETURN
------------------------------------------------------------------------------
Odd:
SELECT CAST(@Number as VARCHAR) + ' Number is Two' AS Output
RETURN
------------------------------------------------------------------------------
NotFound:
SELECT CAST(@Number as VARCHAR) + ' Number is NotFound' AS Output
RETURN
GO
------------------------------------------------------------------------------
```
![image](https://user-images.githubusercontent.com/110928130/186840811-ad509f7f-4a1b-41f6-8e08-5be60bab2891.png)




![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 09`


# How to Delete SQL User History
- Click on Login and Select the User which you need to Delete.
- Then you need to press the delete button.

![GoogleImage](https://github.com/hadicse/My-Collection/blob/main/Source%20Image/Delete%20SQL%20User%20Login%20History.jpg?raw=true) 

![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 9.1`


## Find empty tables in SQL Server database
```sql
Select	schema_name(tab.schema_id) + '.' + tab.name as [table]
		From sys.tables tab
		Inner join sys.partitions part
		On tab.object_id = part.object_id

Where		part.index_id IN (1, 0)	-- 0 - table without PK, 1 table with PK
Group By	schema_name(tab.schema_id) + '.' + tab.name
Having		sum(part.rows) = 0
Order By	[table]
```

![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 10`




# SQL SERVER ROLLUP clause is used to display subtotals and grand totals in the result set. It is always used with GROUP BY CLAUSE.
```sql
SELECT COALESCE(Region ,'GRAND TOTAL' ) AS Region, SUM(Quantity) AS TotalQty
FROM dbo.ItemQty 
GROUP BY ROLLUP(Region) 
```
![SQL SERVER ROLLUP](https://user-images.githubusercontent.com/110928130/184917159-5c2cc363-9ba8-492e-abef-f71c269b231c.jpg)


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 11`




# To display the total purchased quantities by region and items with SubTotal and GrandTotal 
```sql
SELECT COALESCE(Region ,'GRAND TOTAL') AS Region,
COALESCE(Item ,'TOTAL') AS Item, SUM(Quantity) AS TotalQty
FROM dbo.ItemQty
GROUP BY ROLLUP(Region, Item
```

![SubTotal](https://user-images.githubusercontent.com/110928130/184917729-0ca75cfe-8f67-4b28-9e6e-29914fe96c41.jpg)


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 12`




# Row to Colomn SQL Pivot
```sql
SELECT   ShopCOde, Pro_Code, 1 as AreaCode_1, 2 as AreaCode_2 FROM   [dbo].[tblPvot] 
PIVOT (SUM(Stock) FOR [AreaCode] IN ([1], [2])) AS P

Select ShopCode,Pro_Code,AreaCode,Stock from tblPvot

```


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 13`


# SQL UnPivot
https://sqlskull.com/2020/06/06/sql-server-unpivot/



![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 14`


# Disable Relation 
```sql
-- Disable the constraints on a table called tableName:
ALTER TABLE tableName NOCHECK CONSTRAINT ALL

-- Re-enable the constraints on a table called tableName:
ALTER TABLE tableName WITH CHECK CHECK CONSTRAINT ALL
```


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 15`

# Remove all Space from string in SQL Server Using SQL Replace
```sql
Select ColumnA, ColumnB from tblTrims
   
SELECT REPLACE(ColumnA,' ', '') as WithOutSpace , REPLACE(ColumnB,' ', '') as WithOutSpace  from tblTrims
      Select REPLACE(1234.100, '.', '')
 --   '.', Mainly here main value
```

![RemoveSpace](https://user-images.githubusercontent.com/110928130/185178778-e77d4714-a561-4a41-8998-892c0bea9d82.jpg)



![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 16`


# How to find percentage in SQL
```sql
Select ((300/100)*10) as Percentage

--Result
	Percentage
	30
```


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 17`


# RESTORE DATABASE DBNAME
```sql
From Disk='G:\25-06-2020\Backup\Backup.bak'
WITH	Move 'POS_data'		to 'G:\POS_AUDIT.mdf',
		Move 'POS_data2'	to 'G:\POS_AUDIT_2.mdf',
		Move 'POS_data1'	to 'G:\POS_AUDIT_1.mdf',
		Move 'POS_log'		to 'G:\POS_AUDIT_Log.ldf',
		Password='abc'
		--Password='',
		--Password=''
```


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 18`



# SQL Server CREATE SCHEMA
```sql
CREATE SCHEMA customer_services;
GO
Select * from sys.schemas
```
- **Example**

![GoogleImage](https://www.sqlservertutorial.net/wp-content/uploads/SQL-Server-CREATE-SCHEMA.png)



![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 19`

# SQL User disable or user sleep 
```sql
Select Session_id
From Sys.dm.exec_session where login_name='prince'
```



![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 20`


# To get total number of columns in a table in sql
```sql
SELECT COLUMN_NAME FROM INFORMATION_SCHEMA.Columns where TABLE_NAME = 'YourTableName'
```
![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 21`

# Current Month Last Last Date and To get the last day of the previous month:
```sql
--Current Month Last Last Date
DECLARE @test DATETIME
SET @test = GETDATE()  -- or any other date
SELECT DATEADD(month, ((YEAR(@test) - 1900) * 12) + MONTH(@test), -1)

--To get the last day of the previous month:
SELECT DATEADD(DAY, -(DAY(GETDATE())), GETDATE())

```
![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 22`

# Create Indexing or index
```sql
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
![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 23`


# Database Repair or DBCC CheckDB
```sql	
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

![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 24`


# CAST Date
```sql
CAST(ROUND(SUM(Rd.UnitPrice), 2) as numeric (36,2)) as TotalSale 
```

![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 25`


# Round
```sql
Select ReceiptNo, CAST(ROUND(ReceivedAmount,2) as Numeric (36,2) as TotalAmount
Select SUM(CAST(ROUND(ColumnName+ColumnName,2) as Numeric (36,2))) as TotalAmount
```

![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 26`


# SQL query to display the LEN and First 3 characters
```sql
SUBSTRING( string, start_position, length );
SELECT SUBSTRING( column_name, 1, 3 ) FROM table_name;

--Main Data
	IM-APON-DEC21-1
--Result
	--INV
```

![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 27`


# Len Reducer
```sql
Update tblCustomerInfo set Name=RIGHT(Name, LEN(Name)-1)
```

![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 28`


# Dynamic SQL Query
```sql
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


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 29`



# Case Wen
```sql
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
![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 30`

# Having

```sql
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

![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 31`


# IIF Function
```sql
SELECT IIF(3<2, 5, 10)
--Result as 10
```

![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 32`


# PROCEDURE
```sql
CREATE PROCEDURE procedure_name
AS
sql_statement
GO

EXEC procedure_name
```

![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 33`


# UNION ALL
```sql
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


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 34`


# SQL BACKUP DATABASE Statement
```sql
BACKUP DATABASE testDB
TO DISK = 'D:\backups\testDB.bak'
```


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 35`


# SQL Server Functions
###### Click here for details of Functions
- https://docs.microsoft.com/en-us/sql/t-sql/functions/functions?view=sql-server-ver16
- https://www.w3schools.com/sql/sql_ref_sqlserver.asp
- https://www.educba.com/sql-string-functions/?source=leftnav


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 36`


# Update with Inner Join
```sql
UPDATE C
SET IsActive = 1
FROM tblCustomer C
JOIN tblSales S ON C.CustomerID = S.CustomerID
WHERE C.CustomerID=101111101
```


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 37`



# How To Select only Substring
```sql
SELECT  substring('abcde', 2, 3)
```


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 38`

# SQL WHILE loop with simple examples
- https://www.sqlshack.com/sql-while-loop-with-simple-examples/


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 39`


# SQL Print
```sql
DECLARE @Msg VARCHAR(300)= 'My Name is Rajendra Gupta';
PRINT @Msg

or 

DECLARE @Msg VARCHAR(300)
Set @Msg = 'My Name is Rajendra Gupta';
PRINT @Msg
```


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 40`


# Creating a Relationship Between Two Tables Using Query
```sql
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


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 41`




# Get Only numeric or Only Varchar or Mixed (Numeric & Varchar Mixed) value from a column
###### Onlu Numeric
```sql
SELECT ITEM FROM tblProductDetails WHERE ITEM not like '%[^0-9]%' --and ITEM != ''
```

###### Onlu Varchar
```sql
SELECT ITEM FROM tblProductDetails WHERE ITEM not like '%[^A-Z]%' --and ITEM != ''
```

###### Only Mixed
```sql
SELECT ITEM FROM tblProductDetails WHERE ITEM   like '%[^0-9]%[^A-Z]%' or item like  '%[0-9]%[A-Z]%'
```

###### SQL Query to Get Only Numbers or numeric value From a String/varchar
```sql
CREATE FUNCTION dbo.getNumericValue
 (
@inputString VARCHAR(256)
)
RETURNS VARCHAR(256)
AS
BEGIN
  DECLARE @integerPart INT
  SET @integerPart = PATINDEX('%[^0-9]%', @inputString)
  BEGIN
    WHILE @integerPart > 0
    BEGIN
      SET @inputString = STUFF(@inputString, @integerPart, 1, '' )
      SET @integerPart = PATINDEX('%[^0-9]%', @inputString )
    END
  END
  RETURN ISNULL(@inputString,0)
END
GO

SELECT dbo.getNumericValue(StudentName) from (tbl name)
```
![image](https://user-images.githubusercontent.com/110928130/194338456-e23c3ed6-ff96-4106-9f84-7f9a5fef1f8d.png)


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 42`


# Find Date Month year 
```sql
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



![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 43`

# Upper and Lower Font Style in SQL
###### how to display space first letter capital in sql server
###### After Space Letter Capital First Letter in capital, Upper and Lower font style
- https://www.sqlshack.com/overview-of-sql-lower-and-sql-upper-functions/#:~:text=We%20use%20SQL%20UPPER%20function,all%20characters%20into%20capital%20letters.




![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 44`


# Auto Row Count Row Number
```sql
--Auto Row Count Row Number
Select ROW_NUMBER () Over(Order by UserID ) as SLN, UserID from tblUsers
```


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 45`


# Varchar Date Month Year
```sql
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


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 46`


# IF EXISTS

```sql
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


![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 47`


# Bulk Insert From Excel to SQL Using Query
###### Before Bulk Insert Need to Install and Run the Below Query
```sql
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
```sql
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
![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 48`

# Query Execute or Run from Table Data
```sql
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

![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 49`

# Quickest Way to Run the Same Query Multiple Times in SQL Server

```sql
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

![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 50`

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
```sql
select replace(convert(varchar, getdate(),101),'/','')		
select replace(convert(varchar, getdate(),101),'/','') + replace(convert(varchar, getdate(),108),':','')		
```

![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 51`


# Plan_Cursor and FETCH
```sql
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

# Dynamic PIVOT (Dynamic Row to Column)
```sql
DECLARE @Columns NVARCHAR(MAX);
SELECT @Columns = COALESCE(@Columns + ', ', '') + QUOTENAME(WalletName)
FROM (SELECT DISTINCT WalletName FROM ##AllPayment) AS Temp
DECLARE @DynamicSQL NVARCHAR(MAX);
SET @DynamicSQL = 
'SELECT UserName, ' + @Columns + '
FROM ( SELECT UserName, WalletName, Amount FROM ##AllPayment
) AS SourceTable
PIVOT ( SUM(Amount) FOR WalletName IN (' + isnull(@Columns,0) + ')) AS PivotTable'
EXEC sp_executesql @DynamicSQL;
```
![image](https://github.com/hadicse/My-Collection/assets/110928130/e6a3dbff-fcdd-442d-9c87-d821bc51600d)



![#f03cd15](https://via.placeholder.com/15/f03c15/000000?text=+)
`Topic No: 52`

# Script to create dynamic PIVOT queries in SQL Server
```sql
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


# RAISERROR Message Show

```sql
Select intInventoryTransactionId,dteTransactionDate, strReferenceCode,strWarehouseName, numTotalQty ,isApproved into #A  
from [wms].[tblInventoryTransactionHeader]
Where strReferenceCode in (Select strReferenceCode from wms.tblInventoryTransactionHeader	Where intInventoryTransactionId=279703)
and TransactionGroupName='Transfer In' and strReferenceTypeName like '%Transfer%' and isApproved=1

	If((select count(*) from #A A
	Inner join wms.tblInventoryTransactionHeader B on A.dteTransactionDate=B.dteTransactionDate and  A.strReferenceCode=B.strReferenceCode 
							and A.strWarehouseName=B.strWarehouseName and A.numTotalQty=B.numTotalQty 
							where  B.isApproved=0)>0)

		Begin
			RAISERROR('Its a duplicate transfer, please reject it and contact Vendor ',16,1)
		End
		
		Drop table #A


```


# SQL Analytics Functions
```sql
SELECT Account	,TranDate,	TranAmount, FIRST_VALUE(TranAmount) OVER(
		PARTITION BY Account
        ORDER BY Account
		) FIRST_VALUE
FROM  tblTest

SELECT Account	,TranDate,	TranAmount, Last_VALUE(TranAmount) OVER(
		PARTITION BY Account
        ORDER BY Account
		) Last_VALUE
FROM  tblTest
```
![image](https://user-images.githubusercontent.com/110928130/206227711-87ea9166-d4cd-4e85-bfe6-03848ff14b83.png)




# How to rollback using explicit SQL Server transactions
##### BEGIN TRANSACTION, COMMIT, ROLLBACK

```sql
    BEGIN
        BEGIN TRY
            	BEGIN TRANSACTION;
	    	---------------------*** Type Here Your Query ***----------------------------------
			Insert into tblMOB
			Select  '1'
			
			Insert into tblMOB
			Select  '111111111111'
		---------------------*** Type Here Your Query ***----------------------------------
		IF @@TRANCOUNT > 0
		COMMIT;
        END TRY
	
        	BEGIN CATCH
           		 IF @@TRANCOUNT > 0
                	ROLLBACK;
            		SELECT ERROR_NUMBER() AS ErrorNumber;
            		SELECT ERROR_MESSAGE() AS ErrorMessage;
			SELECT Error_Line () AS ErrorLine_Of_Query
        	END CATCH
    END


--Select * from tblMOB
--Delete from tblMOB
```
![image](https://user-images.githubusercontent.com/110928130/206862622-1c8e3dba-d074-46c5-9721-2f4346f55b8d.png)



# How to Get current AUTO_INCREMENT / identity value for any table
```sql
Select IDENT_CURRENT ('[TAX].[dco].[table name]')

-- If +1
Select (Select IDENT_CURRENT ('[TAX].[dco].[table name]')+)

```

# How to GET Bangla Data From SQL Table OR How to Insert Bangla Data into SQL Table
```sql
--Data Type Must be SET nvarchar type
-- How to GET Bangla Data From SQL Table
--Need to set Capital N before Condition Data
Select * from tblAddress Where HouseAddress =N'রংপুর'


--How to Insert Bangla Data into SQL Tbale
--Need to set Capital N before Bangla Data
Insert Into  tblAddress 
Select '5', N'বাংলাদেশ'


```
![image](https://user-images.githubusercontent.com/110928130/209298637-69efc4b1-27ff-4319-b66a-70cbcbfa0211.png)
![image](https://user-images.githubusercontent.com/110928130/209298499-8b97f56b-9eac-4dab-8f82-0ecd3c298d8d.png)





# How to Find Last Executed Query or Query History in SQL SERVER

```sql

--1st Execute Query
Select * from sys.tables

--2nd Step to Find
SELECT        SQLTEXT.text as ExecutedQueryDetails, STATS.last_execution_time as DateandTime
--Into #tmpHistory
FROM          sys.dm_exec_query_stats STATS
CROSS APPLY   sys.dm_exec_sql_text(STATS.sql_handle) AS SQLTEXT
WHERE         STATS.last_execution_time > GETDATE()-1
ORDER BY      STATS.last_execution_time DESC


Select * From #tmpHistory Where ExecutedQueryDetails like '%tables%'



Drop Table Into #tmpHistory
```
![image](https://user-images.githubusercontent.com/110928130/211072193-3fde3254-888c-41de-9fc8-0c2933516bc5.png)


# table name with schima name
```
select schema_name(t.schema_id) as schema_name,
       t.name as table_name
from sys.tables t
where t.object_id in 
    (select c.object_id 
      from sys.columns c
     where c.name like '%Item%')
order by schema_name,
         table_name

```


# How Find table name by table data or table value in  SQL Server

```sql

Declare @SearchStr nvarchar(100)
set @SearchStr = '%AMi Hadi Bolsi%'

CREATE TABLE #Results (ColumnName nvarchar(370), ColumnValue nvarchar(3630))

SET NOCOUNT ON

DECLARE @TableName nvarchar(256), @ColumnName nvarchar(128), @SearchStr2 nvarchar(110)
SET  @TableName = ''
SET @SearchStr2 = QUOTENAME('%' + UPPER(@SearchStr) + '%','''')

WHILE @TableName IS NOT NULL
BEGIN
	SET @ColumnName = ''
	SET @TableName = 
	(
		SELECT MIN(QUOTENAME(TABLE_SCHEMA) + '.' + QUOTENAME(TABLE_NAME))
		FROM 	INFORMATION_SCHEMA.TABLES
		WHERE 		TABLE_TYPE = 'BASE TABLE'
			AND	QUOTENAME(TABLE_SCHEMA) + '.' + QUOTENAME(TABLE_NAME) > @TableName
			AND	OBJECTPROPERTY(
					OBJECT_ID(
						QUOTENAME(TABLE_SCHEMA) + '.' + QUOTENAME(TABLE_NAME)
						 ), 'IsMSShipped'
					       ) = 0
	)

	WHILE (@TableName IS NOT NULL) AND (@ColumnName IS NOT NULL)
	BEGIN
		SET @ColumnName =
		(
			SELECT MIN(QUOTENAME(COLUMN_NAME))
			FROM 	INFORMATION_SCHEMA.COLUMNS
			WHERE 		TABLE_SCHEMA	= PARSENAME(@TableName, 2)
				AND	TABLE_NAME	= PARSENAME(@TableName, 1)
				AND	DATA_TYPE IN ('char', 'varchar', 'nchar', 'nvarchar')
				AND	QUOTENAME(COLUMN_NAME) > @ColumnName
		)

		IF @ColumnName IS NOT NULL
		BEGIN
			INSERT INTO #Results
			EXEC
			(
				'SELECT ''' + @TableName + '.' + @ColumnName + ''', LEFT(' + @ColumnName + ', 3630) 
				FROM ' + @TableName + ' (NOLOCK) ' +
				' WHERE UPPER(' + @ColumnName + ') LIKE ' + @SearchStr2
			)
		END
	END	
END

SELECT * FROM #Results
drop table #Results




```
https://social.msdn.microsoft.com/Forums/sqlserver/en-US/6e823390-25f7-4d7d-8b12-211d22ff5085/how-to-search-for-a-given-value-in-all-fields-in-all-rows-of-all-tables-in-a-given-database?forum=transactsql
https://gist.github.com/csharpforevermore/71289d4b345fb2e0d528adee9bc9cb54






# How do I get only the numbers after the decimal or DOT or Fraction Value in a Numerical Value?
```sql

SELECT ReceivedAmount as MainAmount,  ReceivedAmount - FLOOR(ReceivedAmount) AS OnlyFractionAmount   FROM tblTest

```



# Start Serial after 5 rows like 1,1,1,1,1, 2,2,2,2,2 in SQL Server 
```sql
		--Select * from   tblSerialGroup

		SELECT DENSE_RANK() OVER (ORDER BY BatchNum) AS Serial, ID, Name, ROLL
		FROM ( SELECT (ROW_NUMBER() OVER (ORDER BY ID) - 1) / 3 AS BatchNum,  ID, Name, ROLL
		FROM tblSerialGroup ) AS T


```
![image](https://user-images.githubusercontent.com/110928130/221423686-65c47d80-f6b4-42e7-83d2-7f094c4ee2a1.png)





# To find the substring before the space (1st, 2nd, 3rd, 4th or Multiple Space) in a SQL column 
```sql
--1st Space
SELECT SUBSTRING(names, 0, CHARINDEX(' ', names) - 0) AS names
FROM tblSpace
WHERE names LIKE '% %'

--2nd Space
SELECT SUBSTRING(names, 1, CHARINDEX(' ', names, CHARINDEX(' ', names) + 1) - 1) AS names
FROM tblSpace
WHERE names LIKE '% % %'


--3rd Space
SELECT SUBSTRING(names, 1, CHARINDEX(' ', names, CHARINDEX(' ', names, CHARINDEX(' ', names) + 1) + 1) - 1) AS names
FROM tblSpace
WHERE names LIKE '% % % %'

--4th Space
SELECT SUBSTRING(Names, 1, CHARINDEX(' ', Names, CHARINDEX(' ', Names, CHARINDEX(' ', Names, CHARINDEX(' ', Names) + 1) + 1) + 1) - 1) AS Names
FROM tblSpace
WHERE Names LIKE '% % % % %'
```
![image](https://user-images.githubusercontent.com/110928130/235446993-9eb6899a-400e-4534-a578-b2dd5420de1f.png)





# Use of REPLACE  in SQL
```sql
Select * from tblTest
SELECT REPLACE(ID, 'th', '') AS modified_column FROM tblTest
```

![image](https://github.com/hadicse/My-Collection/assets/110928130/b0afb177-0df0-4d70-9b26-e8debd2ee176)



# To generate a script for creating multiple tables in SQL
```sql
-- Generate script for creating for Multiple table

DECLARE @TableNames TABLE (Name VARCHAR(50))
INSERT INTO @TableNames VALUES ('tblDepartment'), ('tblProduct'), ('tblCustomer'),  ('tblProducer')

DECLARE @TableName VARCHAR(50), @CreateTableQuery NVARCHAR(MAX)
DECLARE TableCursor CURSOR FOR SELECT Name FROM @TableNames OPEN TableCursor FETCH NEXT FROM TableCursor INTO @TableName
WHILE @@FETCH_STATUS = 0

BEGIN		
	SET		@CreateTableQuery = 'CREATE TABLE ' + @TableName + ' (' + STUFF((SELECT ', ' + COLUMN_NAME + ' ' + DATA_TYPE +
	CASE	WHEN CHARACTER_MAXIMUM_LENGTH IS NOT NULL THEN '(' + CAST(CHARACTER_MAXIMUM_LENGTH AS VARCHAR(10)) + ')'
	ELSE	'' END +
	CASE	WHEN IS_NULLABLE = 'NO' THEN ' NOT NULL' ELSE ' NULL' END
	FROM	INFORMATION_SCHEMA.COLUMNS 
	WHERE	TABLE_NAME = @TableName ORDER BY ORDINAL_POSITION FOR XML PATH('')), 1, 2, '') + ');'
	PRINT	@CreateTableQuery -- You can execute the query instead of printing it
	FETCH	NEXT FROM TableCursor INTO @TableName 
END
CLOSE TableCursor DEALLOCATE TableCursor

```



# How to round in SQL, so that if the number is greater than 0.50, it rounds to 1, and if it is less than 0.50, it rounds to 0?"
```sql
SELECT your_column,
CASE WHEN your_column - FLOOR(your_column) >= 0.50 THEN CEILING(your_column)  -- Round up to 1
ELSE FLOOR(your_column)                                                -- Round down to 0
END AS rounded_value
FROM your_table;
```


# GO Using For Page Break
```sql
GO
--Adding Extra Column
ALTER TABLE ##Customer_Final ALTER COLUMN PartnerName VARCHAR(500)
GO
Update ##Customer_Final SET LastName=NULL  WHere LastName=''
Update ##Customer_Final SET PartnerName = PartnerName + ' ' +  LastName COLLATE Latin1_General_CI_AS WHere LastName is not NULL

GO
```


# To split a single row of data into multiple rows in SQL
###### This query will split the data in the your_column column by commas and return each split value as a separate row.
```sql
Select * from tblLine
SELECT value AS SplitData FROM tblLine CROSS APPLY STRING_SPLIT(OneRow, ',')
```
![image](https://github.com/hadicse/My-Collection/assets/110928130/02ec29c1-f3df-4711-9ea5-e992358c4f77)

# How to make custome serial number in SQL

```sql
Select * from tblOne

SELECT One, CONCAT('05092023_', RIGHT('000' + CAST(RowNum AS NVARCHAR(3)), 3)) AS NewColumn
FROM ( SELECT One, ROW_NUMBER() OVER (ORDER BY One) AS RowNum FROM tblOne) AS NumberedData;
```
![image](https://github.com/hadicse/My-Collection/assets/110928130/8a4a573a-6f3b-4fd9-863c-5d6af59e3dbe)



# Ping to Server or Target IP Address using SQL Server
```sql
DECLARE @ServerIP VARCHAR(255)
SET @ServerIP = '192.168.1.100'

DECLARE @Cmd VARCHAR(255)
SET @Cmd = 'ping ' + @ServerIP

DECLARE @PingOutput TABLE (OutputText VARCHAR(MAX))

-- Execute ping command and capture output
INSERT INTO @PingOutput
EXEC xp_cmdshell @Cmd

-- Insert ping results into the database
INSERT INTO PingResults (Hostname, ResultText, Timestamp)
SELECT @ServerIP, OutputText, GETDATE()
FROM @PingOutput
WHERE OutputText IS NOT NULL

-- Clean up any NULL rows
DELETE FROM PingResults WHERE ResultText IS NULL
GO 100

CREATE TABLE PingResults (
    ID INT PRIMARY KEY IDENTITY(1,1),
    Hostname VARCHAR(255),
    ResultText VARCHAR(MAX),
    Timestamp DATETIME
);



-- Enable 'xp_cmdshell'
EXEC sp_configure 'show advanced options', 1;
RECONFIGURE;
EXEC sp_configure 'xp_cmdshell', 1;
RECONFIGURE;
```



# SQL Table Name to Select All Column With Comma 


```sql
DECLARE @TableName NVARCHAR(255) = 'tblDepartment';
DECLARE @Columns NVARCHAR(MAX) = '';

SELECT @Columns += COLUMN_NAME + ', ' FROM INFORMATION_SCHEMA.COLUMNS WHERE TABLE_NAME = @TableName;

SET @Columns = LEFT(@Columns, LEN(@Columns) - 1); DECLARE @SqlQuery NVARCHAR(MAX); SET @SqlQuery = 'SELECT ' + @Columns + ' FROM ' + @TableName;


PRINT @SqlQuery;

```



# How to generate Script with Data (*Database>Task>generate Script>With Schima and Data*)
```sql

DECLARE @NewDatabaseName NVARCHAR(255) = 'YourDatabaseName'; -- Replace with your desired database name
DECLARE @SourceDatabase NVARCHAR(255) = 'PB_Managerium'; -- Replace with the name of your original database

-- Use dynamic SQL to create the new database
DECLARE @CreateDatabaseQuery NVARCHAR(MAX);
SET @CreateDatabaseQuery = 'CREATE DATABASE ' + QUOTENAME(@NewDatabaseName);

-- Execute the CREATE DATABASE statement
EXEC sp_executesql @CreateDatabaseQuery;

-- Generate the USE statement to switch to the newly created database
DECLARE @UseDatabaseQuery NVARCHAR(MAX);
SET @UseDatabaseQuery = 'USE ' + @NewDatabaseName;

-- Execute the USE statement
EXEC sp_executesql @UseDatabaseQuery;

-- Define a table variable to store table names
DECLARE @Tables TABLE (TableName NVARCHAR(255));

-- Insert the names of the tables you want to copy
INSERT INTO @Tables (TableName)
VALUES ('ItemCategory'), ('ItemSubCategory'), ('Partner');

-- Declare variables for cursor
DECLARE @TableName NVARCHAR(255);

-- Declare the cursor
DECLARE TableCursor CURSOR FOR
SELECT TableName FROM @Tables;

-- Open the cursor
OPEN TableCursor;

-- Fetch the first table name
FETCH NEXT FROM TableCursor INTO @TableName;

-- Loop through the tables
WHILE @@FETCH_STATUS = 0
BEGIN
    -- Get column names and data types
    DECLARE @Columns NVARCHAR(MAX) = '';
    SELECT @Columns += COLUMN_NAME + ' ' + DATA_TYPE + 
                      CASE 
                         WHEN CHARACTER_MAXIMUM_LENGTH IS NOT NULL THEN '(' + CAST(CHARACTER_MAXIMUM_LENGTH AS NVARCHAR) + ')' 
                         ELSE '' 
                      END + ', '
    FROM INFORMATION_SCHEMA.COLUMNS
    WHERE TABLE_NAME = @TableName;

    -- Remove the trailing comma and space
    SET @Columns = LEFT(@Columns, LEN(@Columns) - 1);

    -- Generate the CREATE TABLE statement
    DECLARE @CreateTableQuery NVARCHAR(MAX);
    SET @CreateTableQuery = 'CREATE TABLE ' + @NewDatabaseName + '.dbo.' + @TableName + ' (' + @Columns + ')';

    -- Execute the CREATE TABLE statement
    EXEC sp_executesql @CreateTableQuery;

    -- Generate the INSERT INTO statement to copy data
    DECLARE @InsertDataQuery NVARCHAR(MAX);
    SET @InsertDataQuery = 'INSERT INTO ' + @NewDatabaseName + '.dbo.' + @TableName + ' SELECT * FROM ' + @SourceDatabase + '.dbo.' + @TableName;

    -- Execute the INSERT INTO statement
    EXEC sp_executesql @InsertDataQuery;

    -- Fetch the next table name
    FETCH NEXT FROM TableCursor INTO @TableName;
END

-- Close and deallocate the cursor
CLOSE TableCursor;
DEALLOCATE TableCursor;


```


# How to copy file Source to Destination
```sql
-- Enable xp_cmdshell (requires sysadmin role or appropriate permissions)
EXEC sp_configure 'show advanced options', 1;
RECONFIGURE;
EXEC sp_configure 'xp_cmdshell', 1;
RECONFIGURE;

-- Run xp_cmdshell to copy the file
DECLARE @cmd NVARCHAR(1000);
SET @cmd = 'COPY "H:\iBOS\backup\MIRPUR-01\PrinceBazar\FULL\MIRPUR-01_PrinceBazar_FULL_20231231_182747.bak" "\\192.168.100.103\PrinceMirpur01_DBBackUP\"';
EXEC xp_cmdshell @cmd;

-- Disable xp_cmdshell for security reasons
EXEC sp_configure 'xp_cmdshell', 0;
RECONFIGURE;

```



# How remove 1st 3 Letter 
# How to Remove 0 From the string to an integer, Remove leading zeros when converting the string to an integer.
```sql
SELECT SUBSTRING(PartnerCode, 5, LEN(PartnerCode)) AS ModifiedColumnName into #A FROM Partner
Select  CAST(ModifiedColumnName AS INT) AS ResultUsingCast From #A where ModifiedColumnName!='MIR0006'


```

# Exporting data from SQL Server to an Excel sheet using a query
### Method: Using bcp Utility
```sql
sp_configure 'show advanced options', 1;
GO
RECONFIGURE;
GO
sp_configure 'Ad Hoc Distributed Queries', 1;
GO
RECONFIGURE;
GO


```
Open Command Prompt on your computer.
```sql
bcp "SELECT * FROM your_table" queryout "C:\path\to\your\file.csv" -c -t, -S servername -d databasename -U username -P password

-- If Windows authentication
bcp "SELECT * FROM tblAsset" queryout "C:\Users\Administrator\Desktop\HTML Message\SalesData.csv" -c -t, -S MY_LOVE -d TestDB -T

```

# Debit	Credit Data Insert
![image](https://github.com/user-attachments/assets/d1fcb75e-a132-46db-8820-b947d8297027)
```sql

INSERT INTO tblResultData (ID, RollNO, Name, Debit, Credit)
SELECT     ID,     RollNO,     Name, 
    CASE WHEN Sequence = 1 THEN Salary ELSE 0 END AS Debit,
    CASE WHEN Sequence = 2 THEN Salary ELSE 0 END AS Credit
FROM     tblSourceData
CROSS APPLY (   VALUES (1), (2)) AS Seq(Sequence)
ORDER BY ID, Sequence;


```

# How to identify Duplicate entries in the table 
```sql
-- For Duplicate Data

Select P.ReceiveDate, P.PurchaseReceiveId, PL.ItemID,  Quantity, Price, ChallanId
Into ##A from PurchaseReceive P
JOIN PurchaseReceiveLine PL ON PL.PurchaseReceiveId=P.PurchaseReceiveId
WHere isActive=1 and Quantity>0 
Order by ItemID desc

SELECT ReceiveDate, ItemID, Quantity, Price, ChallanId, COUNT(*) as cnt FROM ##A
GROUP BY ReceiveDate, ItemID, Quantity, Price, ChallanId
HAVING COUNT(*) > 1
order by ReceiveDate 

DROP Table ##A


```

# Category /  Layer Management in Database
```sql
--========1st Step Create Table===************************
CREATE TABLE Categories (
    ID INT PRIMARY KEY IDENTITY(1,1),
    CategoryName VARCHAR(100),
    ParentID INT NULL,
    FOREIGN KEY (ParentID) REFERENCES Categories(ID))
----------------------------------------------------------------------------------------
--========2nd Step Insert Data Into Table===************************
INSERT INTO Categories (CategoryName, ParentID)
VALUES ('Food', NULL)

INSERT INTO Categories (CategoryName, ParentID)
VALUES ('Baby Food', 1),  -- Assuming 'Food' has ID 1
       ('Animal Food', 1),
       ('Senior Citizen Food', 1)

INSERT INTO Categories (CategoryName, ParentID)
VALUES ('Baby Chocolate', 2);  -- Assuming 'Baby Food' has ID 2

INSERT INTO Categories (CategoryName, ParentID)
VALUES ('Indian Chocolate', 3),  -- Assuming 'Baby Chocolate' has ID 3
       ('Thailand Chocolate', 3);


INSERT INTO Categories (CategoryName, ParentID)
VALUES ('Tasty Chocolate', 4),  -- Assuming 'Indian Chocolate' has ID 4
       ('Orange Chocolate', 4);

-------------------------------------------------------------------------------------
--========3rd Run If Fixed Layer===************************
WITH CategoryHierarchy AS (
    SELECT 
        ID, 
        CategoryName, 
        ParentID,
        CAST(CategoryName AS VARCHAR(MAX)) AS FullPath,
        1 AS Level
    FROM Categories
    WHERE ParentID IS NULL

    UNION ALL

    SELECT 
        c.ID, 
        c.CategoryName, 
        c.ParentID,
        CAST(ch.FullPath + ' > ' + c.CategoryName AS VARCHAR(MAX)) AS FullPath,
        ch.Level + 1
    FROM Categories c
    INNER JOIN CategoryHierarchy ch ON c.ParentID = ch.ID
)
SELECT 
    FullPath,
    CASE WHEN Level = 1 THEN CategoryName ELSE NULL END AS Layer1,
    CASE WHEN Level = 2 THEN CategoryName ELSE NULL END AS Layer2,
    CASE WHEN Level = 3 THEN CategoryName ELSE NULL END AS Layer3,
    CASE WHEN Level = 4 THEN CategoryName ELSE NULL END AS Layer4
FROM CategoryHierarchy
ORDER BY FullPath;


-------------------------------------------------------------------------------------
--========Start >> Run If Daynamic Layer View You Need===************************
CREATE PROCEDURE GetCategoryHierarchy
AS
BEGIN
    DECLARE @sql NVARCHAR(MAX);
    DECLARE @maxLevel INT;
    DECLARE @level INT;
    DECLARE @caseStatements NVARCHAR(MAX);

    -- Determine the maximum level of hierarchy
    ;WITH CategoryHierarchy AS (
        SELECT 
            ID, 
            CategoryName, 
            ParentID,
            CAST(CategoryName AS VARCHAR(MAX)) AS FullPath,
            1 AS Level
        FROM Categories
        WHERE ParentID IS NULL

        UNION ALL

        SELECT 
            c.ID, 
            c.CategoryName, 
            c.ParentID,
            CAST(ch.FullPath + ' > ' + c.CategoryName AS VARCHAR(MAX)) AS FullPath,
            ch.Level + 1 AS Level
        FROM Categories c
        INNER JOIN CategoryHierarchy ch ON c.ParentID = ch.ID
    )
    SELECT @maxLevel = MAX(Level)
    FROM CategoryHierarchy;

    -- Initialize the SQL query
    SET @sql = '
    WITH CategoryHierarchy AS (
        SELECT 
            ID, 
            CategoryName, 
            ParentID,
            CAST(CategoryName AS VARCHAR(MAX)) AS FullPath,
            1 AS Level
        FROM Categories
        WHERE ParentID IS NULL

        UNION ALL

        SELECT 
            c.ID, 
            c.CategoryName, 
            c.ParentID,
            CAST(ch.FullPath + '' > '' + c.CategoryName AS VARCHAR(MAX)) AS FullPath,
            ch.Level + 1 AS Level
        FROM Categories c
        INNER JOIN CategoryHierarchy ch ON c.ParentID = ch.ID
    )
    SELECT 
        FullPath,';

    -- Construct the CASE statements for each level
    SET @caseStatements = '';

    -- Loop through levels to build CASE statements
    SET @level = 1;
    WHILE @level <= @maxLevel
    BEGIN
        SET @caseStatements = @caseStatements + 
            'CASE WHEN Level = ' + CAST(@level AS NVARCHAR) + ' THEN CategoryName ELSE NULL END AS Layer' + CAST(@level AS NVARCHAR);

        IF @level < @maxLevel
        BEGIN
            SET @caseStatements = @caseStatements + ', ';
        END

        SET @level = @level + 1;
    END

    -- Append the CASE statements and finalize the SQL
    SET @sql = @sql + @caseStatements + '
    FROM CategoryHierarchy
    ORDER BY FullPath;';

    -- Execute the dynamic SQL query
    EXEC sp_executesql @sql;
END;

--========END Run If Daynamic Layer View You Need===************************
EXEC GetCategoryHierarchy;
--========END Run If Daynamic Layer View You Need===************************


--********************************************************************************************************
--========If As POS32 View Start ===************************
-- With Fixed Layer View
WITH CTE AS (
    -- Anchor query: start with the root nodes (where ParentID is NULL)
    SELECT ID,   CategoryName,        ParentID,        CategoryName AS Department,
        CAST(NULL AS VARCHAR(255)) AS Layer2,
        CAST(NULL AS VARCHAR(255)) AS Layer3,
        CAST(NULL AS VARCHAR(255)) AS Layer4,
		CAST(NULL AS VARCHAR(255)) AS Layer5,
		1 AS Level
    FROM Categories
    WHERE ParentID IS NULL

    UNION ALL

    -- Recursive query: join the CTE with the table to build the hierarchy
    SELECT 
        h.ID,
        h.CategoryName,
        h.ParentID,
        c.Department,
        CASE WHEN c.Level = 1 THEN h.CategoryName ELSE c.Layer2 END AS Layer2,
        CASE WHEN c.Level = 2 THEN h.CategoryName ELSE c.Layer3 END AS Layer3,
        CASE WHEN c.Level = 3 THEN h.CategoryName ELSE c.Layer4 END AS Layer4,
		CASE WHEN c.Level = 4 THEN h.CategoryName ELSE c.Layer5 END AS Layer5,
        c.Level + 1
    FROM Categories h
    INNER JOIN CTE c ON h.ParentID = c.ID
)

-- Final select to show the hierarchical structure
SELECT 
    ROW_NUMBER() OVER (ORDER BY Department, Layer2, Layer3, Layer4, Layer5) AS SL,
    Department, Layer2, Layer3, Layer4, Layer5
FROM CTE
WHERE Level = 5 
   OR (Level = 4 AND Layer5 IS NULL) 
   OR (Level = 3 AND Layer4 IS NULL) 
   OR (Level = 2 AND Layer3 IS NULL)
ORDER BY SL;

--========If As POS32 View END ===************************
----------------------------------------------------------------------------------------
```

# Next Next Update
```sql
--BEGIN TRAN

WITH CTE AS (SELECT intIncrementTransactionId,  intEmployeeId,
LAG(intIncrementTransactionId, 1, 0) OVER (PARTITION BY intEmployeeId ORDER BY intIncrementTransactionId) AS intPerviousIncrementTransactionId
FROM saas.tblIncrementTransactionHeader WHERE intEmployeeId = 264)

Select * Into ##CTE from CTE
SELECT intPerviousIncrementTransactionId, * FROM saas.tblIncrementTransactionHeader WHERE intEmployeeId = 264

UPDATE T SET T.intPerviousIncrementTransactionId = CTE.intPerviousIncrementTransactionId
FROM saas.tblIncrementTransactionHeader T
JOIN ##CTE CTE ON T.intIncrementTransactionId = CTE.intIncrementTransactionId
WHERE T.intEmployeeId = 264

SELECT intPerviousIncrementTransactionId, * FROM saas.tblIncrementTransactionHeader WHERE intEmployeeId = 264

DROP Table ##CTE
--ROLLBACK
```
![image](https://github.com/user-attachments/assets/b2659f42-a665-4353-bd6f-e9b5c6381c07)


# Record Change History of Table SQLor  VIP Tips

[SQL VIP tips.docx](https://github.com/user-attachments/files/17184337/SQL.VIP.tips.docx)
https://www.brentozar.com/sql-constantcare/
https://sqlspreads.com/blog/temporal-tables-in-sql-server/
https://www.geeksforgeeks.org/kdd-process-in-data-mining/



# LOG Scalation Query
# Report on SQL Server Lock Escalation Settings for Optimized Concurrency Management

![image](https://github.com/user-attachments/assets/6ef6017b-02cc-4271-9cee-7549dddfd20f)


# ----END----
