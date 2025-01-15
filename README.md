# Databricks-proj

SELECT *
FROM dbo.Sales_Orders
WHERE LastUpdated >= '@{formatDateTime(convertTimeZone(variables('LastLoadtime'), 'UTC', 'India Standard Time'), 'yyyy-MM-dd HH:mm:ss')}'
  AND LastUpdated >= '@{formatDateTime(activity('Lookup1').output.firstRow.LastUpdated, 'yyyy-MM-dd HH:mm:ss')}'
