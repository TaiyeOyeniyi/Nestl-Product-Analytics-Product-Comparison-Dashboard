# 📊 Nestlé Product Analytics — Product Comparison Dashboard (Power BI)

## Project Overview
Nestlé is considering expanding its product portfolio, so the goal of this analysis was to understand how existing products are performing before introducing new ones.

I looked at sales performance across products, time, locations, and sales channels to identify patterns, strengths, and gaps that could inform smarter expansion decisions.

---

<img width="925" height="521" alt="Screenshot 2025-11-19 150438" src="https://github.com/user-attachments/assets/09ac29db-f77e-426f-8a45-237783a7e414" />

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
- **Canva and PowerPoint** 

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

<img width="974" height="571" alt="Screenshot 2025-11-19 151432" src="https://github.com/user-attachments/assets/dc12cfd7-2379-4723-bc86-cdd8fb9d088a" />


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
    BLANK())
```

---

## 📈 Key Insights

### 🧃 Product Performance
- **Milo** is the strongest performer, generating the highest revenue (5.95M).
- **Nescafe** and **Nesquik Duo** follow as solid secondary performers.
- **Nescafe Gold** records the lowest revenue.
- Revenue is largely concentrated around a few core products.

<img width="925" height="524" alt="Screenshot 2025-11-19 150511" src="https://github.com/user-attachments/assets/4ce59030-426f-4ffe-a6d8-7d90fe84f684" />

---

### 📆 Sales Trends Over Time
- Sales generally increase from **Q1 to mid-year (May–June)**.
- A steady decline begins around **July**, with the lowest sales in **December**.
- This pattern indicates a clear **seasonal effect** across products.

---

### 🌍 Geographic Performance
- **South Australia** generates the highest revenue.
- Tasmania, Queensland, and New South Wales also perform well.
- **Western Australia / ACT** show the lowest sales, indicating weaker market penetration.

<img width="925" height="517" alt="Screenshot 2025-11-19 150538" src="https://github.com/user-attachments/assets/e772af82-c8d9-4b12-9f14-1eb626cd4d10" />

---

### 🛒 Sales Channel Insights
- **Direct sales dominate**, contributing approximately **77%** of total revenue.
- **Online sales** account for about **23%**, showing potential for further growth.

---

## 💡 Recommendations
- Anchor expansion strategies around high-performing products such as Milo and Nescafe.
- Reduce over-reliance on a single product by improving the performance of mid-tier products.
- Time new product launches and promotions around mid-year peak demand.
- Use high-performing regions as pilot markets before scaling nationwide.
- Invest more in online sales channels to diversify and grow revenue.

---

## 🚀 Conclusion
This analysis highlights strong core products and clear seasonal sales patterns, alongside opportunities to improve geographic balance and digital sales performance. Addressing these areas before introducing new product lines can help reduce risk and support sustainable business growth.
