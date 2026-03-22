# 🛒 Walmart Store Sales Analysis - SQL-Driven Business Intelligence

> *"Data isn't just numbers - it's the story of business decisions waiting to be discovered."*

![SQL](https://img.shields.io/badge/SQL-MySQL-blue?style=flat-square&logo=mysql)
![Status](https://img.shields.io/badge/Status-Completed-success?style=flat-square)
![Domain](https://img.shields.io/badge/Domain-Retail%20Analytics-orange?style=flat-square)

---

## 🧵 The Business Problem

Walmart operates hundreds of stores across the U.S., each facing unique pressures - holiday rushes, economic shifts, regional trends, and unpredictable customer behavior. Knowing *why* some stores consistently outperform others is critical for inventory planning, staffing, and promotions.

**This project answers one core question:**
### 💬 *"What truly drives sales performance at Walmart stores?"*

---

## 🧠 Hypothesis

| # | Hypothesis |
|---|-----------|
| 1 | Holiday weeks generate significantly higher sales than regular weeks |
| 2 | Economic factors (CPI, fuel price, unemployment) influence weekly sales |
| 3 | Certain stores are consistent top performers regardless of economic conditions |

---

## 📦 Dataset Overview

| Column | Description |
|--------|-------------|
| `Store` | Unique store identifier |
| `Date` | Weekly sales date |
| `Weekly_Sales` | Total sales per store per week |
| `Holiday_Flag` | 1 = Holiday week, 0 = Regular week |
| `Temperature` | Regional temperature at time of sale |
| `Fuel_Price` | Local fuel cost |
| `CPI` | Consumer Price Index |
| `Unemployment` | Regional unemployment rate |

---

## 🎯 Objectives

- 🧹 Clean and standardize inconsistent date formats
- 🏆 Rank stores by total sales using SQL window functions
- 📅 Compare holiday vs. non-holiday week performance
- 📈 Identify monthly and yearly sales trends
- 🔗 Analyze economic factors and their impact on sales

---

## 🛠️ Tech Stack

```
MySQL · Window Functions · Aggregation · CASE WHEN Logic · Data Cleaning
```

---

## 🔍 Analysis Highlights

### 🏆 1. Store Performance Ranking
```sql
SELECT Store_id, 
       SUM(Weekly_Sales) AS Total_Sales,
       RANK() OVER (ORDER BY SUM(Weekly_Sales) DESC) AS Rank_Position
FROM walmart.walmart
GROUP BY Store_id;
```
> **Store 20** achieved the highest overall sales — consistently ranked #1.

---

### 🎉 2. Holiday vs. Non-Holiday Sales
```sql
SELECT Holiday_Flag,
       AVG(Weekly_Sales) AS Avg_Sales,
       COUNT(*) AS Total_Weeks
FROM walmart.walmart
GROUP BY Holiday_Flag;
```
> Holiday weeks showed a **15–25% average sales boost** across most stores.

---

### 📅 3. Monthly Sales Trends
```sql
SELECT MONTH(Date) AS Month,
       ROUND(AVG(Weekly_Sales), 2) AS Avg_Monthly_Sales
FROM walmart.walmart
GROUP BY MONTH(Date)
ORDER BY Month;
```
> Peak sales: **November–December** | Lowest: **June–July**

---

### 📉 4. Economic Factor Correlation
> CPI and unemployment showed **moderate correlation** with weekly sales.  
> Fuel price had **minimal standalone impact**.

---

## 📊 Key Findings

| Finding | Result |
|---------|--------|
| 🎉 Holiday Impact | ✅ Confirmed - 15–25% sales increase during holiday weeks |
| 🏪 Top Performers | Store 20 & Store 4 - consistent leaders |
| ⛽ Fuel Price | ❌ Minimal effect on sales volume |
| 📉 CPI & Unemployment | ⚠️ Moderate correlation observed |
| ☀️ Seasonal Trends | Summer months more stable; winter peaks in Nov–Dec |

---

## 🖼️ Sample Output

![Ranked Stores Output](ranked_stores_output.png)
*Store rankings by total weekly sales using SQL RANK() window function*

---

## 📈 What I Learned

- Translating raw retail data into **actionable business insights**
- Applying advanced SQL (window functions, CASE WHEN) to real-world scenarios
- Strengthening **data storytelling** - from hypothesis to conclusion

---

## 🚀 Future Improvements

- [ ] Build Tableau / Power BI dashboard for visual storytelling
- [ ] Automate the SQL pipeline using Python
- [ ] Add predictive forecasting for future sales trends

---

## 👩‍💻 Author

**Nikitha Katta**  
🎓 MS in Computer & Information Sciences - University of Delaware  
📧 nikithakatta.06@gmail.com
