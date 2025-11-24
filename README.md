# 📊 Superstore Sales & Profitability Analysis (Power BI Project)

This project is a comprehensive analytics dashboard built in **Power BI**, using a *Superstore dataset*.  
The goal was to transform raw transactional data into a clear, interactive, and executive-ready insight system covering **Sales**, **Profit**, **Customers**, **Products**, **Regions**, and **States**.

---

## 🚀 Project Overview

This report provides a full analytical view of business performance, answering key questions such as:

- Which regions and states generate the highest revenue?
- Which product categories drive profitability?
- Who are the top customers by sales?
- Which products consistently underperform?
- How do sales and profits trend month-to-month and year-over-year?
- What customer segment contributes most to revenue and profit?

Designed with clean visuals, strong DAX modeling, and KPI-driven storytelling, the dashboard serves as a decision-support tool for stakeholders.

---

## 🧠 Key Features & Insights

### 🔹 Executive KPI Summary
- **Total Sales:** $2.30M  
- **Total Profit:** $286K  
- **Profit Margin:** 12%  
- Month-over-month & year-over-year KPI indicators  
- 793 unique customers and 5009 orders  

### 🔹 Sales & Profit Trends
- Monthly sales and profit trend visuals  
- Dynamic YOY and MOM comparison  
- Seasonal performance patterns

### 🔹 Customer Analysis
- Segment contribution (Consumer, Corporate, Home Office)  
- **781 repeat customers** vs **12 single-purchase customers**  
- Top 10 customers by sales  
- Customer distribution across U.S. regions

### 🔹 Product & Category Analytics
- Revenue per product category  
- Best-selling and underperforming products  
- Profit margin by sub-category  
- Lowest profitability category: **Furniture**

### 🔹 Regional & State-Level Performance
- West region recorded the highest total revenue  
- California ranked the **best-performing state**  
- Order and profit distribution across all 49 states  
- Region × State × Revenue matrix visualization

---

## 🛠 Tech Stack

- **Power BI Desktop**
- **DAX (Data Analysis Expressions)**
- **Power Query**
- **Star Schema Data Modeling**
- **PDF Export Generation**

---

## 📁 Files in This Repository

- `Incredibuilds_DSN_Sales_Report.pdf` — Final exported analytical report  
- `.pbix` *(optional if included)*  
- `README.md` — Project documentation  

---

## 📐 Data Model Overview

The report follows a clean **star schema** structure:

### **Fact Table**
- `Orders` → Sales, Profit, Quantity, Discounts, Date, Product, Customer, State

### **Dimension Tables**
- `Products` → Category, Sub-Category, Product Name  
- `Customers` → Segment, Customer Name  
- `States` → State, Region  
- `Date` → Calendar table with full time-intelligence support  

---

## 📘 DAX Highlights

### Time Intelligence Measures
```DAX
Sales LY = CALCULATE([Total Sales], SAMEPERIODLASTYEAR('Date'[Date]))
Sales LM = CALCULATE([Total Sales], DATEADD('Date'[Date], -1, MONTH))
```

## 🏆 Best Region (DAX Measure)

This measure identifies the region with the highest total sales using a `TOPN` ranking approach.

```DAX
Best Region =
VAR TopRegionTable =
    TOPN(
        1,
        SUMMARIZE(
            'States',
            'States'[Region],
            "RegionSales", [Total Sales]
        ),
        [RegionSales],
        DESC
    )
RETURN
MAXX(TopRegionTable, 'States'[Region])
```
---
## 🎯 What I Learned

- Building dynamic KPIs using advanced DAX expressions  
- Implementing time-intelligence calculations (Month-over-Month and Year-over-Year)  
- Designing clean, professional, and business-ready Power BI dashboards  
- Creating context-aware measures (Best State, Best Region, Lowest Profit Category, etc.)  
- Working with star-schema modeling and proper relationship management  
- Using slicers, filters, and visual interactions effectively  
- Performing deep profitability analysis across products, categories, states, and regions  
- Enhancing dashboard storytelling for business decision-making  
