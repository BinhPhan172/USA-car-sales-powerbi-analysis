# USA Car Sales Power BI Analysis

## Project Overview

This project analyzes USA car sales data from 2018 to 2024 using Power BI.

The dashboard focuses on sales performance, revenue, profitability, customer behavior, product performance, payment methods, and regional trends.


## Dataset

The dataset contains more than 1 million car sales transaction records from 2018 to 2024.

Key fields include:

- Transaction Date
- Customer Information
- Car Make and Model
- Car Year
- Quantity
- Sale Price
- Cost
- Profit
- Discount
- Payment Method
- Commission
- Sales Region

## Data Model

The Power BI report uses a Star Schema with one central fact table and multiple dimension tables.

### Fact Table
- Fact_Sales

### Dimension Tables
- Dim_calendar
- Dim_Customer
- Dim_Product
- Dim_Market
- Dim_Payment
- Dim_Salesperson
## Dashboard Pages

### 1. Executive Sales Overview

The Executive Sales Overview provides a high-level view of overall business performance.

Key metrics include:

- Total Sales
- Total Revenue
- Average Sale Price
- Total Profit
- Year-over-Year Performance
- Sales Trend
- Revenue by Region
- Revenue by Car Make
- Sales by Payment Method

![Executive Sales Overview](images/overview.png)

### 2. Customer Behavior Analysis

This page focuses on customer demographics and purchasing behavior.

Key analysis includes:

- Total Customers
- Average Sales per Customer
- Average Revenue per Customer
- Repeat Purchase Rate
- Customer Segmentation
- Customer Age Group
- Customer Gender

![Customer Behavior Analysis](images/customer.png)

### 3. Product Portfolio & Brand Analysis

This page analyzes vehicle brands and product performance.

Key analysis includes:

- Total Models
- Top Brand Sales
- Average Revenue per Model
- Sales by Brand
- Revenue by Brand
- Product Portfolio Performance
- Sales Trend by Top Brands

![Product Portfolio & Brand Analysis](images/brand-product.png)
## Tools Used

- Power BI
- Power Query
- DAX
- Data Modeling
- Data Visualization
- Git & GitHub

## Key Insights

- Approximately 2 million vehicles were sold during the analyzed period.
- Total revenue reached approximately $198.72 billion.
- Total profit was approximately $13.97 billion.
- Mercedes generated the highest revenue among the analyzed car brands.
- Cash, Lease, and Loan payment methods showed a relatively balanced distribution.
- Sales remained relatively stable from 2018 to 2024, with the highest level recorded in 2024.

## Project Structure

```text
USA-car-sales-powerbi-analysis/
│
├── images/
│   ├── overview.png
│   ├── customer.png
│   └── brand-product.png
│
├── powerbi/
│   └── USA Car Sales 2018-2024.pbix
│
└── README.md
```

## Author

**Binh Phan**

GitHub: [BinhPhan172](https://github.com/BinhPhan172)