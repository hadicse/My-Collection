--SP modify name


SELECT [name], create_date, modify_date
FROM sys.procedures where name='sprInsurancePost'
ORDER BY modify_date DESC
