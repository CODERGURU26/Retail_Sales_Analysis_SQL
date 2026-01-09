# 🛍️ Retail Sales Analysis SQL Project

![SQL](https://img.shields.io/badge/SQL-PostgreSQL-blue)
![Status](https://img.shields.io/badge/Status-Complete-success)
![License](https://img.shields.io/badge/License-MIT-green)

A comprehensive SQL project analyzing retail sales data to uncover business insights through data cleaning, exploration, and advanced querying techniques.

---

## 📑 Table of Contents

- [Project Overview](#-project-overview)
- [Database Schema](#-database-schema)
- [Project Structure](#-project-structure)
- [Installation & Setup](#-installation--setup)
- [Data Analysis](#-data-analysis)
- [Key Business Questions](#-key-business-questions)
- [Technologies Used](#-technologies-used)
- [SQL Concepts Covered](#-sql-concepts-covered)
- [Results & Insights](#-results--insights)
- [Contributing](#-contributing)
- [License](#-license)
- [Author](#-author)

---

## 🎯 Project Overview

This project demonstrates end-to-end SQL data analysis on a retail sales dataset. It showcases skills in:

- Database design and table creation
- Data cleaning and quality assurance
- Exploratory data analysis (EDA)
- Writing complex SQL queries to solve business problems
- Deriving actionable insights from data

The analysis answers 10 critical business questions that help understand sales patterns, customer behavior, and operational performance.

---

## 🗄️ Database Schema

### Table: `retail_sales`

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| `transactions_id` | INT | Primary key, unique transaction identifier |
| `sale_date` | DATE | Date when the sale occurred |
| `sale_time` | TIME | Time when the sale occurred |
| `customer_id` | INT | Unique customer identifier |
| `gender` | VARCHAR(10) | Customer gender (Male/Female) |
| `age` | INT | Customer age |
| `category` | VARCHAR(15) | Product category (Clothing/Beauty/Electronics) |
| `quantiy` | INT | Quantity of items purchased |
| `price_per_unit` | FLOAT | Price per unit of product |
| `cogs` | FLOAT | Cost of goods sold |
| `total_sale` | FLOAT | Total sale amount (quantity × price_per_unit) |

---

## 📂 Project Structure

```
retail-sales-analysis/
│
├── retail_sales_analysis.sql    # Main SQL file with all queries
├── README.md                     # Project documentation
├── data/                         # Sample data files (if applicable)
└── results/                      # Query results and visualizations (optional)
```

---

## 🚀 Installation & Setup

### Prerequisites

- PostgreSQL 12+ (or any SQL database)
- pgAdmin, DBeaver, or any SQL client
- Basic understanding of SQL

### Setup Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/CODERGURU26/retail-sales-analysis.git
   cd retail-sales-analysis
   ```

2. **Create the database**
   ```sql
   CREATE DATABASE retail_db;
   ```

3. **Execute the SQL script**
   ```bash
   psql -U your_username -d retail_db -f retail_sales_analysis.sql
   ```

4. **Load your data** (if you have a CSV file)
   ```sql
   COPY retail_sales FROM '/path/to/your/data.csv' 
   DELIMITER ',' CSV HEADER;
   ```

---

## 🔍 Data Analysis

### Phase 1: Data Cleaning

- Identified and removed records with NULL values
- Ensured data integrity across all columns
- Validated data types and formats

### Phase 2: Data Exploration

- **Total Sales Count**: Analyzed overall transaction volume
- **Unique Customers**: Identified distinct customer base
- **Category Analysis**: Explored product category distribution

### Phase 3: Business Intelligence

Answered 10 strategic business questions using SQL queries (see below)

---

## 💼 Key Business Questions

### Q1: Daily Sales Report
Retrieve all sales made on a specific date (2022-11-05)

### Q2: Category-Specific Analysis
Find all Clothing transactions with quantity ≥ 4 in November 2022

### Q3: Category Performance Metrics
Calculate total sales and order count for each category

### Q4: Customer Demographics
Determine average age of customers in the Beauty category

### Q5: High-Value Transactions
Identify all transactions exceeding $1000

### Q6: Gender-Category Distribution
Analyze transaction patterns by gender across categories

### Q7: Best Selling Month
Find the top-performing month for each year based on average sales

**Sample Query:**
```sql
SELECT year, month, avg_sale
FROM (
    SELECT 
        EXTRACT(YEAR FROM sale_date) AS year,
        EXTRACT(MONTH FROM sale_date) AS month,
        AVG(total_sale) AS avg_sale,
        RANK() OVER(PARTITION BY EXTRACT(YEAR FROM sale_date) 
                    ORDER BY AVG(total_sale) DESC) AS rank
    FROM retail_sales
    GROUP BY year, month
) AS t1
WHERE rank = 1;
```

### Q8: Top 5 Customers
Identify highest-spending customers

### Q9: Customer Reach by Category
Count unique customers per product category

### Q10: Sales by Time Shift
Categorize orders into Morning (< 12), Afternoon (12-17), and Evening (> 17) shifts

---

## 🛠️ Technologies Used

- **Database**: PostgreSQL
- **Language**: SQL
- **Tools**: pgAdmin / DBeaver
- **Concepts**: DDL, DML, Aggregations, Window Functions, CTEs

---

## 📚 SQL Concepts Covered

- ✅ Database and table creation
- ✅ Data insertion and deletion
- ✅ SELECT queries with filtering (WHERE, HAVING)
- ✅ Aggregate functions (COUNT, SUM, AVG, ROUND)
- ✅ GROUP BY and ORDER BY clauses
- ✅ Date and time functions (EXTRACT, TO_CHAR)
- ✅ Window functions (RANK, PARTITION BY)
- ✅ Common Table Expressions (CTEs)
- ✅ CASE statements for conditional logic
- ✅ Subqueries and derived tables
- ✅ DISTINCT for unique values
- ✅ LIMIT for result set restriction

---

## 📊 Results & Insights

This analysis provides valuable insights into:

- 📈 **Sales Trends**: Monthly and yearly performance patterns
- 👥 **Customer Behavior**: Demographics and purchasing habits
- 🕐 **Operational Efficiency**: Peak business hours identification
- 💰 **Revenue Analysis**: High-value customers and transactions
- 🎯 **Category Performance**: Product line effectiveness

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👨‍💻 Author

**Gururaj Krishna Sharma**

- GitHub: [@CODERGURU26](https://github.com/CODERGURU26)
- Project Link: [Retail Sales Analysis](https://github.com/CODERGURU26/retail-sales-analysis)

---

## 🌟 Acknowledgments

- Inspired by real-world retail analytics challenges
- Built as a portfolio project to demonstrate SQL proficiency
- Open for feedback and improvements

---

⭐ **If you found this project helpful, please consider giving it a star!** ⭐

---

**Happy Analyzing! 📊✨**
