# Pizza-Sales-Analysis-using-SQL-Power-BI
Explore and interpret key performance indicators (KPIs) of pizza sales data through structured SQL queries and advanced Power BI visualizations.
# 🍕 Pizza Sales Analysis using SQL & Power BI  
**Prepared by: Jeevitha G**  

---

## 📘 Overview  
The *Pizza Sales Analysis Project* explores key performance indicators (KPIs) and customer behavior patterns using **SQL** and **Power BI**.  
It aims to identify revenue trends, top-performing products, and sales distributions across various dimensions such as category, size, and time.  
This end-to-end analysis transforms raw transactional data into meaningful insights that support data-driven business decisions.

---

## 🎯 Objectives  
- Calculate KPIs such as Total Revenue, Total Orders, and Average Order Value.  
- Identify peak sales days, hours, and months.  
- Determine the most and least popular pizzas by revenue, quantity, and orders.  
- Analyze category and size preferences among customers.  
- Visualize all findings in an interactive Power BI dashboard.  

---

## 🧩 Dataset Overview  
The dataset represents pizza sales transactions with details about each order.  
**Table Name:** `pizza_sales`  

| Column | Description |
|--------|--------------|
| pizza_id | Unique identifier for each pizza |
| order_id | Unique identifier for each order |
| pizza_name_id | Encoded name ID for each pizza |
| quantity | Number of pizzas sold |
| order_date | Date of the order |
| order_time | Time of the order |
| unit_price | Price per pizza |
| total_price | Total price of the order |
| pizza_size | Size of the pizza (S, M, L, XL) |
| pizza_category | Category (Classic, Supreme, Veggie, Chicken, etc.) |
| pizza_ingredients | Ingredients used |
| pizza_name | Full name of the pizza |

---

## ⚙️ Tools & Technologies Used  
- **Microsoft SQL Server (SSMS)**  
- **Power BI Desktop**  
- **DAX (Data Analysis Expressions)**  
- **Power Query Editor**  

---

## 🧮 Data Loading and Preparation  

### In SQL Server  
1. Created a new database named `pizza_sales`.  
2. Imported the dataset using SQL Server Import Wizard.  
3. Verified data types and structure.  
4. Executed SQL queries to calculate key metrics and validate data quality.  

### In Power BI  
1. Connected Power BI to SQL Server database using the **SQL Server connector**.  
2. Cleaned data using **Power Query Editor**:  
   - Removed duplicates and nulls.  
   - Converted date and time columns to proper formats.  
   - Added new columns: **Month Name**, **Day Name**, **Day Number**.  
3. Created DAX measures for KPIs:  
   - **Total Revenue** = `SUM(pizza_sales[total_price])`  
   - **Average Order Value** = `DIVIDE(SUM(pizza_sales[total_price]), DISTINCTCOUNT(pizza_sales[order_id]))`  
   - **Total Pizzas Sold** = `SUM(pizza_sales[quantity])`  
   - **Total Orders** = `DISTINCTCOUNT(pizza_sales[order_id])`  
   - **Average Pizzas per Order** = `DIVIDE(SUM(pizza_sales[quantity]), DISTINCTCOUNT(pizza_sales[order_id]))`  

---

## 📊 SQL Analysis  
### Key Queries and Metrics:
```sql
-- Total Revenue
SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;


-- Average Order Value
SELECT SUM(total_price)/COUNT(DISTINCT order_id) AS AverageOrderValue FROM pizza_sales;


-- Total Pizzas Sold
SELECT SUM(quantity) AS TotalPizzaSold FROM pizza_sales;


-- Total Orders
SELECT COUNT(DISTINCT order_id) AS TotalOrders FROM pizza_sales;


-- Average Pizza Per Order
SELECT CAST(SUM(quantity) AS DECIMAL(10,2)) / CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS AvgPizzaPerOrder FROM pizza_sales;


```

Other analyses included:
- **Daily Trend for Orders**
<img width="220" height="217" alt="image" src="https://github.com/user-attachments/assets/f7fae339-e23c-43eb-b9bb-dc589ed86041" />

<img width="510" height="60" alt="image" src="https://github.com/user-attachments/assets/2faf2d5f-a3b6-4737-94d2-212b72cb235c" />
  


- **Monthly Trend for Orders**

<img width="218" height="279" alt="image" src="https://github.com/user-attachments/assets/5977a695-f2bf-46d5-ac0a-acb7779d5676" />

<img width="445" height="59" alt="image" src="https://github.com/user-attachments/assets/d87ef460-159a-46eb-a4f4-c18ea278c829" />
  


- **Sales % by Category and Size**

<img width="327" height="160" alt="image" src="https://github.com/user-attachments/assets/58d47a48-5103-4f41-886d-1b9b7c23e566" />

<img width="510" height="72" alt="image" src="https://github.com/user-attachments/assets/91c449ac-7bff-4cbc-8b1f-9043fd53a89a" />
  
<img width="355" height="148" alt="image" src="https://github.com/user-attachments/assets/a05c2f48-e07a-4342-9be1-9f650600bf3c" />
  
<img width="510" height="87" alt="image" src="https://github.com/user-attachments/assets/69fc561c-2eb6-4556-8fe3-80a743373a71" />
  

- **Top & Bottom 5 Pizzas by Revenue, Quantity, and Orders**

<img width="420" height="191" alt="image" src="https://github.com/user-attachments/assets/46f15712-ef55-441d-99e0-3751111bac1f" />

<img width="393" height="58" alt="image" src="https://github.com/user-attachments/assets/918a5720-3ebf-4e9d-ba8e-c0a5c97f4df6" />
  
<img width="464" height="192" alt="image" src="https://github.com/user-attachments/assets/8843e22a-52ff-4a7b-8cbd-931bf74c5600" />

<img width="392" height="58" alt="image" src="https://github.com/user-attachments/assets/17c485cf-57d0-4f03-a07b-41afac53cf6c" />
  
<img width="442" height="181" alt="image" src="https://github.com/user-attachments/assets/8acc69b0-0f09-47cd-bb12-0642a3bd93a8" />

<img width="428" height="59" alt="image" src="https://github.com/user-attachments/assets/8d1ce49d-959e-4b0f-81e9-cabfe66e1554" />
  
<img width="439" height="184" alt="image" src="https://github.com/user-attachments/assets/9e8ce088-64b7-413c-898d-cc5cc9704025" />
  
<img width="427" height="60" alt="image" src="https://github.com/user-attachments/assets/b5e51595-d1b2-4504-9deb-88e160481755" />
  
<img width="400" height="166" alt="image" src="https://github.com/user-attachments/assets/5ed912b4-a047-4c84-8422-86f09b704f66" />

<img width="464" height="60" alt="image" src="https://github.com/user-attachments/assets/0e748892-acf0-4285-940c-ed825ab64eb6" />
  
<img width="459" height="223" alt="image" src="https://github.com/user-attachments/assets/e059c189-1c7f-4cfe-b1b6-396022d21186" />
  
<img width="465" height="61" alt="image" src="https://github.com/user-attachments/assets/1ab35f19-f052-4ef0-8f8a-fbbdfbf6dd23" />
  


- **Peak Sales Hours Analysis**

<img width="395" height="384" alt="image" src="https://github.com/user-attachments/assets/a0522e98-00cf-4d41-8f8f-f04bd62cd391" />

<img width="370" height="89" alt="image" src="https://github.com/user-attachments/assets/42f2ffc1-50e5-4a69-a24e-921d37efef05" />
  
---

## 📈 Power BI Dashboard Visuals  
<img width="902" height="483" alt="image" src="https://github.com/user-attachments/assets/4d78b465-4f9e-42ee-88d8-2a398e22806a" />

<img width="851" height="462" alt="image" src="https://github.com/user-attachments/assets/ddb920ed-7597-436a-98ea-18a04c6856d1" />


### Dashboard Includes:
- KPI Cards (Revenue, Orders, Pizzas Sold, Avg. Order Value)  
- Daily and Monthly Order Trends  
- Sales Distribution by Pizza Category  
- Sales by Pizza Size  
- Funnel Chart: Pizzas Sold by Category  
- Top & Bottom 5 Pizzas by Revenue, Quantity, and Orders  
- Peak Hour Analysis  

---

## 🔍 Analytical Insights  
- **Thai Chicken Pizza** contributes the maximum revenue.  
- **Classic Deluxe Pizza** records the highest quantity sold and total orders.  
- **Orders peak on weekends**, especially **Friday and Saturday evenings**.  
- **July and January** witness the highest number of orders.  
- The **Classic category** dominates both sales and order volume.  
- **Large-sized pizzas** generate the highest share of total revenue.  

---

## 💡 Key Business Recommendations  
1. Focus marketing promotions on **weekends and evening hours**.  
2. Highlight **Classic Deluxe and Thai Chicken** pizzas as best-sellers.  
3. Offer **combo deals** on **Large-sized pizzas** to maximize sales.  
4. Introduce **new variants** under the popular Classic category.  
5. Optimize inventory planning around **July and January** sales peaks.  

---

## 🧠 Significance of the Project  
This project demonstrates how SQL and Power BI can be integrated to transform raw data into actionable business insights.  
By visualizing trends and performance metrics, restaurant owners can make data-backed decisions to enhance customer experience, optimize sales, and improve profitability.

---

## 📁 Project Deliverables  
- `pizza_sales_kpi.sql` — SQL Query Scripts  
- `pizza_sales_dashboard.pbix` — Power BI Dashboard  
- `Pizza_Sales_Analysis_Comprehensive_Report_JeevithaG.docx` — Full Project Report  
- `README.md` — Documentation  

---

## 🏁 Conclusion  
The *Pizza Sales Analysis* project successfully applies SQL and Power BI to analyze and visualize business performance.  
It highlights sales trends, customer preferences, and revenue drivers — empowering the business to strategize more effectively.  

---

> 🔗 **Author:** Jeevitha G  
> 📧 *For queries or collaboration, feel free to connect via GitHub or LinkedIn.*  
