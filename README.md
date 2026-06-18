# E-Commerce-Sales-Analytics-Dashboard
"End-to-end e-commerce analytics with Python, SQL, and Power BI — RFM segmentation, geographic analysis, DAX time intelligence" 
# 🛒 E-Commerce Sales & Customer Analytics

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/SQL-4479A1?style=flat&logo=postgresql&logoColor=white" />
  <img src="https://img.shields.io/badge/Power_BI-F2C811?style=flat&logo=powerbi&logoColor=black" />
  <img src="https://img.shields.io/badge/Excel-217346?style=flat&logo=microsoft-excel&logoColor=white" />
  <img src="https://img.shields.io/badge/DAX-512BD4?style=flat" />
</p>

**An end-to-end data analytics project** — from raw data generation in Python, through SQL business queries, to a fully interactive 5-page Power BI dashboard with RFM customer segmentation, geographic revenue analysis, and time-intelligence DAX measures.

**Author:** Diksha Bansal · [LinkedIn](https://www.linkedin.com/in/diksha-bansal-9a0615255) · [Email](mailto:dikshabansal18720@gmail.com)

---

## 📌 Why this project

Most beginner analytics projects stop at "make a chart." This one goes further: it answers concrete business questions an e-commerce company actually asks, using the same RFM segmentation framework used by real retail and marketing teams, and a Power BI data model built with proper relationships and DAX time intelligence — not just drag-and-drop visuals.

**Business questions answered:**

- How is revenue trending month over month, and where are the seasonal peaks?
- Which customers are our most valuable — and which are about to churn?
- Which cities and payment methods drive the most revenue?
- Which products and categories should we double down on?

---

## 📊 Power BI Dashboard — 5 Pages

| Page | What it shows |
|---|---|
| **Executive Overview** | 5 KPI cards (Revenue, Orders, Customers, AOV, Return Rate), monthly revenue trend split by year, category donut, Month-over-Month growth line, order status breakdown |
| **Customer & RFM Analysis** | RFM segment distribution donut, average order value by segment, a 1,000-point scatter chart (Recency × Frequency × Monetary bubble size), top customer lifetime value table |
| **Geography & Payment** | India bubble map of city-level revenue, payment method breakdown, city-wise average order value, revenue ranking by city |
| **Product Performance** | Top 10 products by revenue, category treemap, month-by-product revenue matrix heatmap, waterfall chart of category contribution |
| **RFM Deep Dive** | Segment-level KPI cards, revenue by RFM segment, customer recency distribution histogram, interactive segment slicer |

> 📸 *Dashboard screenshots are in `/screenshots`. Full interactive `.pbix` file available on request or via the link in the file list above.*

---

## 🧠 The hardest part — and what it taught me

The Month-over-Month growth measure looked correct on paper but rendered as a flat line with zero variation. The bug wasn't in the DAX formula — it was in the data model: the date relationship between my calendar table and the orders table wasn't active, and a column I assumed was in "YYYY-MM" format was actually storing plain month names with no year attached.

Fixing it meant rebuilding a proper Date table, marking it correctly, and reconnecting the relationship — which taught me a lesson that stuck: **most "DAX bugs" are data model bugs wearing a DAX costume.** Once that clicked, I started debugging from the model outward instead of rewriting formulas blindly.

---

## 🗂️ Repository Structure

```
E-Commerce-Sales-Analytics/
│
├── data/
│   ├── customers.csv              ← 1,000 customers with demographics
│   ├── orders.csv                 ← 5,000 orders with status & payment method
│   ├── order_items.csv            ← 8,700+ line items with category & revenue
│   └── products.csv               ← 20 products across 5 categories
│
├── output/
│   ├── Ecommerce_Analytics_Dashboard.xlsx
│   ├── monthly_revenue.csv
│   ├── category_analysis.csv
│   ├── top_products.csv
│   ├── city_performance.csv
│   ├── payment_analysis.csv
│   ├── rfm_segmentation.csv
│   └── rfm_segment_summary.csv
│
├── screenshots/                   ← Power BI dashboard page screenshots
│
├── generate_data.py                ← Step 1: synthetic dataset generation
├── analysis.py                     ← Step 2: EDA + RFM scoring in Python
├── build_excel.py                  ← Step 3: Excel dashboard builder
├── queries.sql                     ← 12 SQL queries (CTEs, window functions)
├── Ecommerce_Analytics.pbix         ← Power BI dashboard file
└── README.md
```

---

## 🔍 Methodology

### 1. Data Generation & Cleaning (Python)
Synthetic but realistic dataset — 5,000 orders, 1,000 customers, 20 products across 2 years (2023–2024) with seasonal festival-month weighting. Cleaned for nulls, validated order statuses, and merged across customer/order/product dimensions using Pandas.

### 2. RFM Customer Segmentation
Customers scored on **Recency, Frequency, and Monetary** value, then classified into five segments:

| Segment | Description | Action |
|---|---|---|
| 🏆 Champions | Bought recently, buy often, highest spend | Reward & retain |
| ⭐ Loyal Customers | Regular buyers, respond well to promotions | Upsell |
| 🌱 Potential Loyalists | Recent customers, growing frequency | Nurture with loyalty programs |
| ⚠️ At Risk | Declining recency and frequency | Win-back campaigns |
| 😴 Lost Customers | Long inactive | Deep discount reactivation |

### 3. SQL Analysis
12 queries covering KPI summaries, month-over-month trends using `LAG()`, RFM scoring using `NTILE()`, customer lifetime value, and year-over-year comparisons.

### 4. Power BI Dashboard
Star-schema data model (orders as fact table, customers/products/date as dimensions), DAX measures for revenue, return rate, and time-intelligence growth calculations, and 5 fully interactive pages with cross-page synced slicers.

---

## 💡 Key Insights

- **Champions (21% of customers) generate ~3× more revenue** than the average customer — the clearest single priority for retention spend
- **Festival months (Oct–Dec) drive 35%+ higher revenue** than the yearly average
- **Electronics accounts for 73% of revenue**, led by Laptops and Smartphones
- **Delhi and Mumbai together contribute over a third of total revenue**, while Tier-2 cities show strong untapped growth potential
- **UPI is the leading payment method**, while Cash on Delivery still carries the highest return risk
- **10% overall return rate**, concentrated in Electronics and Fashion — an opportunity to improve product descriptions and sizing information

---

## 🚀 How to Run

```bash
pip install pandas numpy openpyxl

python generate_data.py     # creates the dataset
python analysis.py          # runs EDA + RFM scoring
python build_excel.py       # builds the Excel dashboard
```

For the Power BI dashboard: open `Ecommerce_Analytics.pbix` in [Power BI Desktop](https://powerbi.microsoft.com/desktop) (free) and click Refresh if prompted to reconnect to the local CSV files.

---

## 🛠️ Tools & Technologies

`Python` (Pandas, NumPy) · `SQL` (CTEs, window functions, NTILE, LAG) · `Power BI` (DAX, data modeling, time intelligence) · `Excel` (openpyxl, conditional formatting)

---

## 📈 Skills Demonstrated

End-to-end pipeline design · data cleaning & validation · exploratory data analysis · RFM customer segmentation · star-schema data modeling · DAX time intelligence · SQL window functions · interactive BI dashboard design · business insight storytelling

---

## 👩‍💻 About Me

**Diksha Bansal** — Final-year Computer Science student, Data Analyst Intern at CEPTA Infotech, aspiring Data Analyst.

📧 [dikshabansal18720@gmail.com](mailto:dikshabansal18720@gmail.com) · 🔗 [LinkedIn](https://www.linkedin.com/in/diksha-bansal-9a0615255) · 💻 [GitHub](https://github.com/DikshaAggarwal03)

*Open to Data Analyst opportunities — feel free to reach out.*

---

*Dataset is synthetically generated to simulate realistic e-commerce patterns for portfolio purposes.*
