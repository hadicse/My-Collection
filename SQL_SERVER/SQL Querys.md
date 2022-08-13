# **Welcome to SQL Server Collection's of Hadiuzzaman**
- Here I will collect all types of complex queries.
- which was used for my work purposes.

## My First Qyery
```
Select * from tblProduct
```

# The most useful website for SQL and Others
- https://www.w3schools.com/sql/sql_intro.asp
- https://www.w3resource.com/sql-exercises/
- https://sqlskull.com/2020/03/15/sql-server-lead-function/
- https://devsonket.com/
- 
###### You Can Download Some Book From Here
- https://www.db-book.com/db6/practice-exer-dir/index.html
###### TOP-70 MOST IMPORTANT SQL QUERIES IN 2022
- https://bytescout.com/blog/20-important-sql-queries.html?utm_referer=https%3A%2F%2Fwww.google.com%2F#35
###### Join over 16 million developers in solving code challenges on (Best Practice Site for SQL)
- https://www.hackerrank.com/domains/sql


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
# Row to Colomn SQL Pivot
```
SELECT   ShopCOde, Pro_Code, 1 as AreaCode_1, 2 as AreaCode_2 FROM   [dbo].[tblPvot] 
PIVOT (SUM(Stock) FOR [AreaCode] IN ([1], [2])) AS P

Select ShopCode,Pro_Code,AreaCode,Stock from tblPvot

```

# Disable Relation 
```
-- Disable the constraints on a table called tableName:
ALTER TABLE tableName NOCHECK CONSTRAINT ALL

-- Re-enable the constraints on a table called tableName:
ALTER TABLE tableName WITH CHECK CHECK CONSTRAINT ALL
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



















<!-- For Color Tex
```diff
-dsglhfg
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@

--For Hyperlink
- ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) `#f03c15`
```
---->





