# RetailReveal


Data Model & Table Relationships
Tables and Keys
•	Product: PROD_KEY (Primary Key)
•	Store: STORE_KEY (Primary Key)
•	Sales: TRANS_ID (PK), PROD_KEY (FK), STORE_KEY (FK)
•	Inventory: CAL_DT (FK), STORE_KEY (FK), PROD_KEY (FK)
•	Calendar: CAL_DT (PK)
Relationships
 
Note:  
 Sales is the Fact Table (transactions).  
 Inventory is another Fact Table (snapshot of stock/waste, etc.).  
 Product, Store, Calendar are Dimension Tables.
Star Schema: Both Sales and Inventory connect to Product, Store, and Calendar.
Import Data
Load all 5 tables into Power BI.
•	In the Model View, create 1-to-many relationships as specified above.
•	Make sure all foreign keys are of matching data types.
•	Cardinality: Each relationship should be Many-to-One (from Fact to Dimension).
Data Cleaning and Preparation
•	Format dates (ensure TRANS_DT and CAL_DT are Date type).
•	Change the Store_key, Prod_key to text type.
•	Create calculated columns/measures as needed.
PowerBI Report
Main Page 
•	KPIs: 
o	Total Sales (`SALES_AMT`)
o	Total Units Sold (`SALES_QTY`)
o	Total Margin (`SALES_MGRN`)
o	Inventory on Hand (`INVENTORY_ON_HAND_QTY`)
•	Sales Trend: Line chart (xaxis: `CAL_DT` from Calendar; yaxis: `SALES_AMT`)
•	Sales by Store: Map or filled map (Location: `REGION`/`STORE_DESC`; Value: `SALES_AMT`)
•	Top 5 Products by Sales: Bar/column chart (`PROD_NAME` vs. `SALES_AMT`)
•	Slicers: Year, City, 
•	Drillthrough Targets:
o	Product Details
o	Store Details
Product Details
Drillthrough Field: `PROD_KEY` (Product)
•	KPI: 
o	Selected Product’s Total Sales
o	Selected Product’s Total Units Sold
o	Selected Product’s Total Margin
•	Sales Trend: Line chart `CAL_DT` vs. `SALES_AMT` (filtered for the selected product)
•	Sales by Store: Line chart (`STORE_DESC` vs. `SALES_AMT`)
•	Out of Stock Events: Table (`CAL_DT`, `OUT_OF_STOCK_FLG`)
•	Product Attributes: Table (`PROD_NAME`,  ` PROD_KEY`, `CATEGORY_NAME`, `SUBCATEGORY_NAME`, `STATUS_CODE `)
•	Slicers: Category, Sub category



Store Details
Drillthrough Field: `STORE_KEY` (Store)
•	KPI: 
o	Store’s Total Sales
o	Store’s Total Units Sold
o	Store’s Total Margin
•	Sales Trend: Line chart (`CAL_DT` vs. `SALES_AMT`)
•	Top Products Sold: Bar chart (`PROD_KEY` vs. `SALES_AMT`)
•	Inventory Over Time: Line chart (`CAL_DT` vs. `INVENTORY_ON_HAND_QTY`)
•	Out of Stock/Waste/PROMO: Stacked bar (`OUT_OF_STOCK_FLG`, `WASTE_QTY`, `PROMOTION_FLG`)
•	Store Info: Card (`STORE_DESC`,  `STORE_TYPE_CD`, `STORE_KEY`)
•	Slicers: Year

