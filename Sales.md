# 🛍️ Retail Sales Analytics — Power BI Portfolio Project

## 📌 Project Overview
A full end-to-end sales analytics project built with **Power Query** and **Power BI**, covering data cleaning, modeling, DAX measures, and interactive dashboards across 5 real-world datasets.

---

## 📂 Datasets Used

| File | Rows | Description |
|------|------|-------------|
| Product-Sales-Region.xlsx | 1,500 | Regional sales transactions |
| Online-Store-Orders.xlsx | 1,200 | E-commerce orders |
| Retail-Store-Transactions.xlsx | 2,000 | In-store transactions |
| Customer-Purchase-History.xlsx | 1,800 | Customer purchase records |
| Inventory-Tracking.xlsx | 500 | Stock and supplier data |

**Total: 7,000+ rows of sales data**

---

## 🔧 Tools & Skills

- **Power Query** — Data cleaning, transformation, custom columns, Merge Queries
- **Power BI** — Data modeling, DAX measures, interactive dashboards
- **DAX** — SUMX, DIVIDE, FILTER, COUNTROWS, ADDCOLUMNS, CALENDAR

---

## 🧹 Data Cleaning (Power Query)

- Changed column data types (Date, Whole Number, Decimal)
- Applied Text.Trim to remove hidden spaces from all text columns
- Replaced null values with meaningful labels:
  - `Promotion` → "No Promotion"
  - `CouponCode` → "No Coupon"
- Added custom calculated columns:
  - `Delivery Days` = DeliveryDate - OrderDate
  - `Discount Label` = Low / Medium / High / No Discount
  - `Revenue Band` = Small / Medium / Large
  - `Rating Label` = Positive / Neutral / Negative
  - `Stock Status` = Out of Stock / Low Stock / Moderate / Well Stocked
  - `Inventory Value` = QuantityInStock × UnitCost
- Merged **Product Sales** with **Inventory Tracking** via Product key

---

## 🗂️ Data Model

- Built a **Star Schema** with Date Table at the center
- Created a DAX Date Table with: Year, Month Name, Month Number, Quarter, Week Day
- Established relationships between all fact tables and the Date Table
- Marked Date Table as official date table for time intelligence

---

## 📊 DAX Measures

```dax
Total Revenue     = SUM('Product Sales by Region'[TotalPrice])
Total Orders      = COUNTROWS('Product Sales by Region')
Total Profit      = SUMX(..., TotalPrice - ShippingCost)
Avg Order Value   = DIVIDE([Total Revenue], [Total Orders])
Total Quantity    = SUM('Product Sales by Region'[Quantity])
Return Rate       = Returned Orders / Total Orders
Low Stock Items   = Products where Stock ≤ ReorderPoint
Fulfillment Rate  = Delivered Orders / Total Orders
Customer Revenue  = SUM('Customer Purchase History'[TotalPrice])
```

---

## 📈 Dashboards

### 1️⃣ Executive Overview
- KPI Cards: Total Revenue, Total Profit, Total Orders, Return Rate
- Revenue trend by Month (Line Chart)
- Revenue by Region (Bar Chart)
- Revenue by Product (Bar Chart)
- Year Slicer for time filtering

### 2️⃣ Regional Sales Performance
- Salesperson performance ranking
- Sales by Customer Type (Retail vs Wholesale)
- Discount impact on revenue
- Region Slicer for geographic filtering

### 3️⃣ Customer Intelligence
- Top Customers by Revenue
- Sales by Product Category
- Rating Label distribution
- Payment Method Slicer

### 4️⃣ Inventory & Supply Chain
- Stock Status distribution
- Inventory Value by Supplier
- Products sorted by lowest stock (ascending)
- Stock Status Slicer

---

## 💡 Key Business Insights

> These insights were discovered through dashboard analysis:

1. **North region generates the least revenue** compared to all other regions — potential area for sales strategy review.

2. **East & West regions declined in 2025 vs 2024** — both regions performed better in 2024, signaling a possible market shift or increased competition.

3. **Top 3 best-selling products: Tablet, Laptop, Printer** — Electronics dominate sales across all regions.

4. **Cash is the most used payment method**, surpassing Credit Card — suggests the customer base prefers traditional payment methods.

---

## 🧠 Lessons Learned

- DAX Measures must belong to the same table as their related Slicers for interactivity to work correctly.
- CustomerID was not consistent across datasets — product-level joins were used instead.
- DateTime columns must be converted to Date type before using time intelligence functions.
- ADDCOLUMNS + CALENDAR is the cleanest way to build a Date Table in one DAX expression.

---

## 👤 Author
**Hassib**
Aspiring Data Analyst | Power BI & Power Query

