# 📊 Nestlé Product Analytics — Product Comparison Dashboard (Power BI)

A hybrid project combining real business-style analysis with a structured case study dataset.  
This dashboard was developed to help Nestlé’s Growth & Strategy team evaluate current product performance before expanding into new product lines.

---

## 📌 Problem Statement

Nestlé plans to expand its business by adding new product lines. Before doing so, the Head of Growth & Strategy requested a deep analysis of current product performance to support the expansion decision.

This project answers the following questions:

- What is the trend of total sales per product over the last 3 years?  
- What is the monthly sales trend?  
- Which product generates the maximum and minimum revenue?  
- Which location has the highest and lowest sales?  
- What insights can be generated from each sales medium?

This project delivers an interactive **Product Comparison Dashboard** that supports strategic decision-making.

---

## 🎯 Business Objectives

1. Compare performance across all existing products.  
2. Identify top and low-performing products.  
3. Understand regional differences in sales.  
4. Compare effectiveness of various sales mediums.  
5. Provide insights to guide Nestlé on product expansion.

---

## 📁 Dataset Description

Dataset contains 3 years of product sales data:

- Date  
- Product Name  
- Product Category  
- Quantity Sold  
- Revenue  
- Sales Medium (Retail, Distributor, Online, etc.)  
- Location (Region/State/City)

Dataset provided with the Nestlé case study.

---

## 🛠️ Tools & Technologies

- **Power BI Desktop**  
- **Power Query** (Data cleaning)  
- **Microsoft Excel**  
- **GitHub** (Portfolio hosting)  
- **Canva/PowerPoint** (Documentation)

---

## 🧼 Data Cleaning & Preparation (Power Query)

- Removed duplicates and null values  
- Standardized text fields  
- Created Date, Month, Year & Month-Year columns  
- Ensured correct data types  
- Created lookup tables (Products, Locations, Channels)  
- Built a clean **star-schema data model**

---

## 🧩 Data Model (Star Schema)

**Fact Table**  
- FactSales: DateKey, ProductKey, LocationKey, ChannelKey, Quantity, Revenue  

**Dimension Tables**  
- DimProduct  
- DimDate  
- DimLocation  
- DimChannel  

---

## 🔢 Key DAX Measures

```DAX
Total Revenue = SUM(FactSales[Revenue])

Total Quantity = SUM(FactSales[Quantity])

Revenue YTD = 
CALCULATE([Total Revenue], DATESYTD(DimDate[Date]))

Revenue MoM % =
VAR PrevMonth =
    CALCULATE([Total Revenue], DATEADD(DimDate[Date], -1, MONTH))
RETURN
IF(
    NOT ISBLANK(PrevMonth),
    ([Total Revenue] - PrevMonth) / PrevMonth,
    BLANK()
)
