
# Financial analysis of Company(LT Foods)



## Problem Statement

This dashboard provides insights into a company's financial health over the past decade, derived from its Profit & Loss (P&L) sheets, balance sheets, and cash flow statements. By using these historical records, the dashboard enables stakeholders to assess year-over-year (YOY) growth, gauge Compound Annual Growth Rate (CAGR),Reserves and debts and analyze complete financial health of the compant. The insights aid in understanding trends, identifying growth areas, and making informed decisions for strategic planning.

## What Differenciates this project
This project showcases my ability to not only use carry out complete data modelling, cleaning and manipulation and data analytics skills but also my knowledge about the financials and business of how a company works and operates.

### Steps followed 

- Step 1: Data Collection and Initial Setup
Collected raw data of P&L, balance sheet, and cash flow statements for 10 years.
Restructured the dataset from a horizontal layout to a vertical format, making it compatible with Power BI’s table structures.
Image suggestion: Screenshot of the raw data in its original format alongside the reorganized vertical structure.


![Snap_1](https://github.com/user-attachments/assets/e441ae8c-d538-411d-94a3-f0c9ba8ca098)


- Step 2: Data Cleaning and Transformation
Loaded data into Power BI Desktop and utilized Power Query Editor to enable “Column Distribution,” “Column Quality,” and “Column Profile” views to assess data quality.
Identified and handled null values, ensuring data integrity for reliable calculations in subsequent steps.


- Step 3: Structuring Fact and Dimension Tables
Segregated data into Fact and Dimension tables for each financial statement (P&L, Balance Sheet, Cash Flow).
Established relationships between tables for seamless data flow, enabling comprehensive analysis across different financial parameters.
![Snap_2](https://github.com/user-attachments/assets/491897a0-6eac-4d61-a591-d79ce81698a4)

- Step 4: Building the Data Model
Created an optimized data model by defining relationships and hierarchies across the tables.
Enabled cross-filtering and drill-through options for dynamic insights, allowing for intuitive exploration of financial metrics.
![Snap_2](
https://github.com/user-attachments/assets/f8a25516-62a2-4c7f-b32a-ddc2d7db6773)

- Step 5: DAX Calculations for Key Metrics

### Used DAX expressions to calculate essential financial metrics
CAGR (Compound Annual Growth Rate) to analyze growth over time.
```
CAGRsale = ([sale_end]/[SaleStart])^(1/5)-1

SaleStart = CALCULATE(SUM('P&L_fact'[Value]),'P&L_fact'[P&L_main_head]="Sales",Date_dim[Year]=2019)

sale_end = CALCULATE(SUM('P&L_fact'[Value]),'P&L_fact'[P&L_main_head]="Sales",Date_dim[Year]=2024)
```
Revenue growth, expense ratios, and net income trends for a holistic view of financial performance.
```
Sales = CALCULATE(SUM('P&L_fact'[Value]),'P&L_fact'[P&L_main_head]="Sales")

Net profit = CALCULATE(SUM('P&L_fact'[Value]),'P&L_dim'[P&L_main_head]="Net Profit +")

Ebitda = CALCULATE(SUM('P&L_fact'[Value]),'P&L_dim'[P&L_main_head]="Operating Profit")
```
Calculated aggregated metrics like YOY revenue changes and profitability margins to provide a comprehensive financial snapshot.
```
Sales%yoy = 
VAR CurrentYearSales = [Sales]
VAR PreviousYearSales =[Sales Previous Year SPLY]
RETURN 
IF(
    ISBLANK(PreviousYearSales),
    BLANK(),  -- This will return BLANK for the first year where there's no previous year data
    DIVIDE(CurrentYearSales - PreviousYearSales, PreviousYearSales)
)

Ebitdayoy% = ([Ebitda]-[Ebitdaprev])/[Ebitda]
```


- Step 6: Designing the Dashboard Layout
### Sales & Profitability Overview: 
Displays total sales, revenue, EBITDA, and COGS, including each metric’s YoY growth rate, contribution across geographies, and projected sales for the next five years. The dashboard also features a tree map of the complete profit and loss (P&L) structure, offering a detailed breakdown of company profitability.
![Snap_2](https://github.com/user-attachments/assets/f6669c6e-a18f-4f79-b1f1-7e0c8b013569)

### Reserves, Debt & Financial Health: 
Highlights reserves vs. debt, current and non-current asset growth, and liabilities. It includes sales trend insights and key indicators of financial health, including CAGR growth for COGS, EBITDA, net profit, and sales, providing a comprehensive view of financial sustainability.
![Snap_2](https://github.com/user-attachments/assets/fdf92d14-e745-45b0-a28d-777338160ac8)


### Balance Sheet Analysis: 
Presents a detailed balance sheet analysis, showing trends and proportions within assets, liabilities, and equity, allowing for a deep dive into the company’s structural financial health.
![Snap_2](https://github.com/user-attachments/assets/2bb4866d-36f2-42a4-af49-5ea05726a046)


Cash Flow Analysis: Illustrates year-wise free cash flow, demonstrating robust cash flow health with consistent positive free cash. This dashboard supports analysis of operational cash inflows and outflows, highlighting the company’s liquidity and ability to meet financial obligations.
![Snap_2](https://github.com/user-attachments/assets/e5dbc576-918f-4f84-a6c4-86295ed89e4d)



- Step 8: Insights and Key Findings
Revenue Trends: Identified periods of growth and decline, supported by visual data for easy comparison.
Profitability Ratios: Calculated and visualized key ratios, helping stakeholders understand fiscal health.
Growth Rate Analysis: Showed CAGR calculations, spotlighting areas of consistent growth over the decade.
  

# Insights

A Multiple page report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;

LT Foods has shown impressive financial performance over the past few years, demonstrating solid growth and profitability. Key financial indicators such as Sales, EBITDA, and Net Profit have consistently improved, reflecting a healthy and sustainable business. As a leader in the rice industry, LT Foods primarily deals in premium rice and its varieties, serving top-quality rice to customers worldwide. Additionally, the company is committed to empowering farmers through collaborative efforts, supporting sustainable agricultural practices that benefit both the company and its partners. This report outlines LT Foods' performance highlights and provides insights into the company’s robust financial health, geographic contributions, and projected growth.

LT Foods is in an exceptionally strong position, financially and strategically. The company's growth across multiple regions, combined with disciplined cost management, a focus on top-quality rice, and proactive investments, has built a resilient business model. Moving forward, LT Foods is well-equipped to capitalize on market opportunities, drive revenue growth, and enhance profitability. This robust financial performance reflects both the management’s foresight and the company’s ability to deliver sustainable value to its stakeholders.

#### Key Performance Indicators (KPIs)
Sales Growth: Year-over-year, LT Foods has achieved consistent growth in sales, highlighted by a positive trend in sales volume across all regions. This steady increase indicates strong market demand for high-quality rice products and effective sales strategies.
Profitability: Net profit and EBITDA have shown significant improvement, underscoring the company’s focus on cost management and operational efficiency. These figures suggest LT Foods is maintaining a profitable core business while investing in future growth.
Cost of Goods Sold (COGS): Despite a moderate increase in production costs, LT Foods has effectively managed its expenses. This efficiency has enabled the company to maintain high gross margins, showcasing disciplined cost management.



