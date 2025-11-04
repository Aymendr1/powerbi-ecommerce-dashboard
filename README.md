# E-commerce Sales Performance (Power BI)


**KPIs:** Total CA, Total Qty, **AOV**, **YoY / MoM**, performance by **channel** (Instagram, Site Web, WhatsApp)..

## Method
- **Power Query:** types, trim/clean, remove duplicates, standardized column names.  
- **Star Schema:** `FactSales(Amount, Quantity, OrderId, DateKey, ProductKey, ChannelKey, CustomerKey)` + `DimProduct`, `DimCustomer`, `DimChannel`, `Calendar`.  
- **Calendar:** created with `CALENDAR()` and **marked as Date table** for time intelligence.  
- **DAX (core)**  
  ```DAX
  Total CA := SUM(FactSales[Amount])
  Orders   := DISTINCTCOUNT(FactSales[OrderId])
  AOV      := DIVIDE([Total CA], [Orders])
  CA LY    := CALCULATE([Total CA], SAMEPERIODLASTYEAR('Calendar'[Date]))
  YoY %    := DIVIDE([Total CA] - [CA LY], [CA LY])

## Files
- report/PROJECT_ECOMMERCE.pbix
