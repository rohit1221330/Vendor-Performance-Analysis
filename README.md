# 🏪 Vendor Performance Analysis
> **End-to-End Data Analytics Project** | Python · SQL (SQLite) · Power BI

![Python](https://img.shields.io/badge/Python-3.13-blue?logo=python)
![SQLite](https://img.shields.io/badge/SQLite-Database-lightgrey?logo=sqlite)
![PowerBI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow?logo=powerbi)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

## 📌 Project Overview

This project performs a complete end-to-end analysis of an inventory management system for a **liquor distribution business**.

Raw data was spread across **6 large CSV files with 1.6 crore+ rows**. The goal was to extract meaningful business insights about vendor performance, profitability, promotional opportunities, and inventory risks — and present them through an interactive **Power BI dashboard**.

> 📄 Full project report available in the [`Reports/`](./Reports/) folder.

---

## ❓ Business Questions Answered

| # | Question |
|---|---|
| 1 | Which vendors contribute the most to total procurement and revenue? |
| 2 | Which brands have high profit margins but low sales — promotional candidates? |
| 3 | Does bulk purchasing lead to lower unit prices? |
| 4 | How much capital is locked in unsold inventory per vendor? |
| 5 | Is there a statistically significant difference in profit margins between top and low performing vendors? |

---

## 🗂️ Dataset

> ⚠️ Raw CSV files are too large to upload on GitHub.
>
> 📥 **Download Dataset Here:** [Raw Data](https://drive.google.com/drive/folders/1Cgwoe4CjqIpsitcRB6hDFzfAFsil7Qfl?usp=sharing)

After downloading, place all CSV files inside a `data/` folder:

```
data/
├── begin_inventory.csv       ← 2,06,529 rows  | Stock at start of year per store
├── end_inventory.csv         ← 2,24,489 rows  | Stock at end of year per store
├── purchases.csv             ← 23,72,474 rows | All vendor purchase transactions
├── purchase_prices.csv       ← 12,261 rows    | Master price list per brand
├── sales.csv                 ← 1,28,25,363 rows | All sales transactions
└── vendor_invoice.csv        ← 5,543 rows     | Invoice + freight cost per vendor
```

---

## 📁 Project Structure

```
Vendor-Performance-Analysis/
│
├── 📁 Dashboard/
│   ├── Vendor_Performance_Dashboard.pbix   ← Power BI file
│   └── dashboard_screenshot.png            ← Dashboard preview
│
├── 📁 Reports/
│   ├── Vendor_Performance_Report.pdf       ← Full project report (PDF)
│   └── Vendor_Performance_Report.pptx      ← Project presentation (PPT)
│
├── 📄 Business Problem.png                 ← Problem statement
│
├── 📓 ingestion_db.ipynb                   ← Step 1: CSV to SQLite ingestion
├── 📓 EDA_data_preparation.ipynb           ← Step 2: SQL + cleaning + feature engineering
├── 📓 Vendor_Performance_Analysis.ipynb    ← Step 3: EDA + stats + visualizations
│
├── 📊 vendor_sales_summary.csv             ← Final aggregated output table
│
└── 📄 README.md
```

---

## 🚀 How to Run

**1. Clone the repository**
```bash
git clone https://github.com/rohit1221330/Vendor-Performance-Analysis.git
cd Vendor-Performance-Analysis
```

**2. Install dependencies**
```bash
pip install pandas numpy matplotlib seaborn scipy sqlalchemy
```

**3. Download dataset and place CSVs in `data/` folder**

**4. Run notebooks in order**

| Order | Notebook | What it does |
|---|---|---|
| 1 | `ingestion_db.ipynb` | Loads CSVs into SQLite DB in chunks |
| 2 | `EDA_data_preparation.ipynb` | SQL CTEs, data cleaning, feature engineering |
| 3 | `Vendor_Performance_Analysis.ipynb` | EDA, statistical analysis, visualizations |

**5. Open Power BI**

Open `Dashboard/Vendor_Performance_Dashboard.pbix` in Power BI Desktop.

---

## 🔧 Tech Stack

| Tool / Library | Purpose |
|---|---|
| `pandas`, `numpy` | Data cleaning and transformation |
| `SQLite` + `SQLAlchemy` | Database creation and SQL aggregations |
| `scipy` | Hypothesis testing and confidence intervals |
| `matplotlib`, `seaborn` | EDA visualizations |
| `Power BI` | Interactive business dashboard |

---

## 📊 Project Pipeline

```
Raw CSVs  →  ingestion_db.ipynb  →  SQLite DB (inventory.db)
                                            ↓
                            EDA_data_preparation.ipynb
                         (SQL CTEs + Joins + Data Cleaning
                          + Feature Engineering)
                                            ↓
                       vendor_sales_summary  (10,692 rows)
                                            ↓
                      Vendor_Performance_Analysis.ipynb
                     (EDA + Stats + Hypothesis Testing)
                                            ↓
                         Power BI Dashboard
```

---

## 📈 Key Findings

### 💰 Overall KPIs
| Metric | Value |
|---|---|
| Total Sales Revenue | **$441.41 Million** |
| Total Purchase Cost | **$307.34 Million** |
| Total Gross Profit | **$134.07 Million** |
| Average Profit Margin | **38.72%** |
| Total Unsold Capital | **$2.71 Million** |

### 🏆 Top 5 Vendors by Sales
| Vendor | Total Sales | Purchase Contribution % |
|---|---|---|
| DIAGEO NORTH AMERICA INC | $67.99M | 16.30% |
| MARTIGNETTI COMPANIES | $39.33M | 8.30% |
| PERNOD RICARD USA | $32.06M | 7.78% |
| JIM BEAM BRANDS COMPANY | $31.42M | 7.64% |
| BACARDI USA INC | $24.85M | 5.67% |

### 🔑 Key Insights
- 📦 **Top 10 vendors = 66% of total procurement** — high supply chain concentration
- 🎯 **Brands needing promotion** identified — high margin + low sales quadrant
- 📉 **Low stock turnover vendors** flagged for supply chain review
- 💡 **Bulk purchasing = lower unit prices** — supports larger order negotiation
- 🔬 **T-Test (p < 0.05)** — significant profit margin difference between top and low vendors
- 📊 Low-volume vendors have **higher margins (40–42%)** vs high-volume vendors **(30–31%)**

---

## 📸 Dashboard Preview

![Vendor Performance Dashboard](Dashboard/dashboard_screenshot.png)

---

## 📄 Reports

| File | Description |
|---|---|
| [📄 PDF Report](./Reports/Vendor_Performance_Report.pdf) | Full project report with methodology and findings |
| [📊 PPT Presentation](./Reports/Vendor_Performance_Report.pptx) | Project presentation slides |

---

## ✨ Project Highlights

- ✅ **Chunked ingestion** — 1.6 crore rows loaded without RAM overflow
- ✅ **SQL CTEs** — complex multi-table joins for aggregation
- ✅ **Feature Engineering** — GrossProfit, ProfitMargin, StockTurnover, SalesToPurchaseRatio
- ✅ **Statistical Testing** — Welch's Two-Sample T-Test + 95% Confidence Intervals
- ✅ **Interactive Dashboard** — 2 slicers, 8 visuals, 5 KPI cards

---

## 👤 Author

**Rohit**
- GitHub: [@rohit1221330](https://github.com/rohit1221330)
- LinkedIn: [LinkedIn](https://www.linkedin.com/in/rohit-dhyani-51b25b32a/)
