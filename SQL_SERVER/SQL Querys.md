# **Welcome to SQL Server Collection's of Hadiuzzaman**
- Here I will collect all types of complex queries.
- which was used for my work purposes.

## My First Qyery
```
Select * from tblProduct
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
WITH	Move 'POS_data'		to 'G:\POS32_AUDIT.mdf',
		Move 'POS32_data2'	to 'G:\POS32_AUDIT_2.mdf',
		Move 'POS32_data1'	to 'G:\POS32_AUDIT_1.mdf',
		Move 'POS_log'		to 'G:\POS32_AUDIT_Log.ldf',
		Password='abc'
		--Password='',
		--Password=''
```

# The most useful website for SQL and Others
- https://sqlskull.com/2020/03/15/sql-server-lead-function/
- https://devsonket.com/

















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
-->

