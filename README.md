# USA Car Sales Power BI Analysis

## Project Overview

This project analyzes USA car sales transaction data from 2018 to 2024 using Power BI.

The objective is to transform more than one million sales records into an interactive business intelligence dashboard that provides insights into sales performance, revenue, profitability, customer behavior, vehicle brands, payment methods, and regional trends.

The project demonstrates the complete Power BI workflow, including data preparation, data modeling, DAX calculations, dashboard development, and business insight generation.

---

## Business Questions

This analysis was designed to answer the following business questions:

- How did vehicle sales perform from 2018 to 2024?
- How much revenue and profit were generated?
- Which car brands generated the highest revenue?
- Which regions contributed the most to total revenue?
- How did sales performance change over time?
- What payment methods were most commonly used?
- What customer segments contributed to vehicle purchases?
- What proportion of customers made repeat purchases?
- Which brands and products performed best within the portfolio?
- Are there any unusual transactions or potential outliers that may affect financial KPIs?

---

## Dataset

The dataset contains more than **1 million car sales transaction records** from 2018 to 2024.

Key fields include:

- Transaction Date
- Salesperson
- Customer Name
- Customer Age
- Customer Gender
- Car Make
- Car Model
- Car Year
- Quantity
- Sale Price
- Cost
- Profit
- Discount
- Payment Method
- Commission Rate
- Commission Earned
- Sales Region

### Data Source

Dataset: **USA Car Sales Dataset 2018–2024**

Source: [Kaggle – USA Car Sales Dataset 2018–2024](https://www.kaggle.com/datasets/anjaliprajapati307/usa-car-sales-dataset-2018-2024)

The original raw dataset is not included in this repository because of its file size.

---

## Data Limitations

Several data quality considerations were identified during the analysis:

- The original dataset contains inconsistencies between the `Date` field and the provided `Sale Year` field.
- Time-based analysis therefore uses the `Date` field through the dedicated `Dim_calendar` table.
- The dataset does not provide a native customer identifier.
- A surrogate `Customer_ID` was created from available customer attributes for analytical purposes.
- Some transactions contain unusually high sale prices, costs, or negative profits and should be treated as potential outliers.
- Repeat customer analysis should therefore be interpreted as an analytical approximation rather than CRM-level customer tracking.

---

## Data Model

The Power BI report uses a **Star Schema** with one central fact table connected to multiple dimension tables.

### Fact Table

- `Fact_Sales`

### Dimension Tables

- `Dim_calendar`
- `Dim_Customer`
- `Dim_Product`
- `Dim_Market`
- `Dim_Payment`
- `Dim_Salesperson`

The main relationship structure follows:

```text
Dim_calendar
      │
Dim_Customer
      │
Dim_Product
      │
Dim_Market ─────── Fact_Sales
      │
Dim_Payment
      │
Dim_Salesperson
```

The dimension tables filter the central `Fact_Sales` table using one-to-many relationships and single-direction filtering.

---

# Dashboard Pages

## 1. Executive Sales Overview

The Executive Sales Overview provides a high-level view of overall business performance.

Key metrics and analysis include:

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

---

## 2. Customer Behavior Analysis

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

---

## 3. Product Portfolio & Brand Analysis

This page analyzes vehicle brand and product performance.

Key analysis includes:

- Total Models
- Top Brand Sales
- Average Revenue per Model
- Sales by Brand
- Revenue by Brand
- Product Portfolio Performance
- Sales Trend by Top Brands

![Product Portfolio & Brand Analysis](images/brand-product.png)

---

# Key Measures & DAX

Some of the main DAX measures used in this project include:

## Total Sales

```DAX
Total Sales =
SUM(Fact_Sales[Quantity])
```

This measure calculates the total number of vehicles sold.

---

## Total Revenue

```DAX
Total Revenue =
SUMX(
    Fact_Sales,
    Fact_Sales[Quantity] * Fact_Sales[Sale Price]
)
```

This measure calculates revenue by multiplying the number of vehicles sold by the sale price for each transaction.

---

## Average Sale Price

```DAX
Average Sale Price =
AVERAGE(Fact_Sales[Sale Price])
```

---

## Total Profit

```DAX
Total Profit =
SUM(Fact_Sales[Profit])
```

---

## Profit Margin

```DAX
Profit Margin =
DIVIDE(
    [Total Profit],
    [Total Revenue],
    0
)
```

---

## Total Customers

```DAX
Total Customers =
DISTINCTCOUNT(Fact_Sales[Customer_ID])
```

---

## Repeat Customers

```DAX
Repeat Customers =
COUNTROWS(
    FILTER(
        VALUES(Dim_Customer[Customer_ID]),
        CALCULATE(COUNTROWS(Fact_Sales)) > 1
    )
)
```

---

## Repeat Purchase Rate

```DAX
Repeat Purchase Rate =
DIVIDE(
    [Repeat Customers],
    [Total Customers],
    0
)
```

---

## Previous Year Revenue

```DAX
Revenue LY =
CALCULATE(
    [Total Revenue],
    SAMEPERIODLASTYEAR(Dim_calendar[Date])
)
```

---

## Revenue YoY %

```DAX
Revenue YoY % =
DIVIDE(
    [Total Revenue] - [Revenue LY],
    [Revenue LY],
    0
)
```

---

# Key Insights

Several important insights were identified from the dashboard:

- More than **2.1 million vehicles** were sold during the analyzed period.
- Total revenue reached approximately **$198.72 billion**.
- Total profit reached approximately **$13.97 billion**.
- The average recorded sale price was approximately **$86.64K**.
- **Mercedes** generated the highest revenue among the analyzed car brands.
- Sales remained relatively stable across the 2018–2024 period, with **2024 recording the highest sales volume**.
- Cash, Lease, and Loan transactions showed a relatively balanced payment distribution.
- Approximately **940K unique customer profiles** were identified using the surrogate customer identifier.
- The estimated repeat purchase rate was approximately **5.3%**.
- Regional revenue distribution shows that sales performance varies significantly across the United States.
- Several transactions contain unusually high prices, costs, or negative profits, indicating potential outliers that should be considered when interpreting financial KPIs.

---

# Tools Used

- **Power BI**
- **Power Query**
- **DAX**
- **Data Modeling**
- **Data Cleaning**
- **Data Visualization**
- **Business Intelligence**
- **Git**
- **GitHub**

---

# Skills Demonstrated

This project demonstrates practical skills in:

- Data cleaning and transformation
- Star schema design
- Fact and dimension table modeling
- One-to-many relationship management
- Calendar table implementation
- DAX measure development
- Time intelligence calculations
- KPI development
- Customer segmentation
- Product performance analysis
- Regional analysis
- Dashboard UI design
- Data storytelling
- Business insight generation
- Git version control
- GitHub project documentation

---

# Project Workflow

The project followed the workflow below:

```text
Raw Dataset
     │
     ▼
Data Cleaning
Power Query
     │
     ▼
Data Transformation
     │
     ▼
Star Schema
Data Modeling
     │
     ▼
DAX Measures
     │
     ▼
Dashboard Development
     │
     ▼
Business Insights
     │
     ▼
GitHub Portfolio
```

---

# Project Structure

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
├── .gitignore
│
└── README.md
```

---

# How to View the Project

### Option 1: View Dashboard Screenshots

Dashboard screenshots are available in the `images` folder.

### Option 2: Open the Power BI File

Download:

```text
powerbi/USA Car Sales 2018-2024.pbix
```

Then open the file using **Microsoft Power BI Desktop**.

---

# Repository Purpose

This repository was created as a Data Analytics portfolio project to demonstrate practical Power BI, data modeling, DAX, visualization, and business analysis skills.

The project focuses not only on dashboard design but also on building a structured analytical model and translating transactional sales data into business insights.

---

# Author

**Binh Phan**

GitHub: [BinhPhan172](https://github.com/BinhPhan172)