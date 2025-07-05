# Sales-Overview - Power-BI

This project provides a comprehensive **Sales Analytics Dashboard** built using **Power BI**. It analyzes transactional data across multiple markets and products, enabling business users to gain actionable insights into product performance, sales trends, and customer behavior.


## 🚀 Project Overview

The dashboard provides a business-friendly interface to analyze:
- Total revenue and sales quantity
- Revenue trends over time
- Top-performing products and customers
- Market-wise sales distribution
- Data integrity issues (e.g., unmatched or blank product codes)

This project was designed to offer clarity and actionability to stakeholders making product, marketing, or inventory decisions.


## 📁 Data Model & Schema

This project uses a **star schema** design with the `transactions` table at the center:

### 🔗 Relationships

| Fact Table     | Related Dimension | Key Field        | Type           |
|----------------|-------------------|------------------|----------------|
| transactions   | products           | `product_code`   | Many-to-One    |
| transactions   | customers          | `customer_code`  | Many-to-One    |
| transactions   | markets            | `market_code`    | Many-to-One    |
| transactions   | date               | `order_date` → `cy_date` | Many-to-One |


## 🧹 Data Cleaning & Transformation

The following data preparation steps were applied:

### 🔧 Cleaning Steps
- **Datatype Mismatches**: Corrected inconsistent data types (e.g., `sales_amount` and `sales_qty` as decimal/integer)
- **Currency Normalization**: Standardized currency values to a common format (INR → USD) using conversion logic
- **Blank Handling**: Removed or filled missing values in critical fields like `product_code`, `market_code`, and `customer_code`
- **Text Cleanup**: Trimmed and cleaned text columns to remove invisible characters (e.g., `\r`, `\n`, spaces)
- **Invalid Records**: Filtered out transactions with invalid amounts or missing product references
- **Currency Column Fixes**: Detected and removed currency mismatches before aggregation

## 📊 Key Dashboard Features

- **KPI Cards**: Total Revenue and Sales Quantity
- **Revenue by Market**: Horizontal bar chart
- **Sales Quantity by Market**: Horizontal bar chart
- **Revenue Trend**: Time-series line chart with slicers for year/month
- **Top 5 Customers**: Bar chart sorted by revenue
- **Top 5 Products**: Bar chart highlighting top-selling products
  - Includes logic to handle blank/missing values


## 🧪 Measures & Enhancements

- `sales_amount` and `sales_qty` were aggregated by dimension
- Normalized sales (`norm_sales_amount`) can be extended for multi-currency comparison
